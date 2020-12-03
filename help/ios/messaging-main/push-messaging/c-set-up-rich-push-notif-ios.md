---
description: Potete allegare file di immagine alle notifiche Apple. L'aggiunta di componenti visivi può aumentare notevolmente il coinvolgimento degli utenti con le notifiche push.
seo-description: Potete allegare file di immagine alle notifiche Apple. L'aggiunta di componenti visivi può aumentare notevolmente il coinvolgimento degli utenti con le notifiche push.
seo-title: Ricevi notifiche push potenziate
title: Ricevi notifiche push potenziate
uuid: 0dbda409-cf49-4eb8-90ee-baf27911dc07
translation-type: tm+mt
source-git-commit: d028fe0f9477bc011aa8fda21a0a389808df0fce
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 35%

---


# Ricevere notifiche push potenziate {#receive-rich-push-notifications}

Potete allegare file di immagine alle notifiche Apple. L&#39;aggiunta di componenti visivi può aumentare notevolmente il coinvolgimento degli utenti con le notifiche push.

Per ricevere notifiche push potenziate nell&#39;app iOS:

1. Implementa i messaggi push per l&#39;app, completando i passaggi descritti in  [Messaggi push](/help/ios/messaging-main/push-messaging/push-messaging.md).
1. Verifica di poter inviare un messaggio di testo push all&#39;app.
1. Aggiungete un’estensione del servizio di notifica completando i seguenti passaggi:

   1. In your Xcode project, select  **[!UICONTROL File]** > **[!UICONTROL New]** > **[!UICONTROL Target]**.
   1. Seleziona **[!UICONTROL Estensione servizio notifiche]**.
   1. Verifica che esista il file `NotificationService.m`.

1. Apri il file `NotificationService.m` e verifica che siano presenti i seguenti metodi delegate:

   * Un metodo per ricevere una richiesta di notifica.
   * Un metodo per gestire la scadenza dell’estensione del servizio.

      Per ricevere notifiche push potenziate, viene utilizzato il primo metodo:

      ```objective-c
      (void)didReceiveNotificationRequest:(UNNotificationRequest *)request withContentHandler:(void (^)(UNNotificationContent *contentToDeliver))contentHandler;
      ```

      Con questo metodo, puoi ottenere l’URL del file multimediale da `userInfo` usando la chiave `attachment-url`. Dopo aver scaricato il file in una directory locale, aggiungi il percorso locale a `bestAttemptContent.attachments`.

      Esempio del codice per questo metodo:

      ```objective-c
      - (void)didReceiveNotificationRequest:(UNNotificationRequest *)request withContentHandler:(void (^)(UNNotificationContent * _Nonnull))contentHandler {
      self.contentHandler = contentHandler;
      self.bestAttemptContent = [request.content mutableCopy];
         NSDictionary* userInfo = request.content.userInfo;
      if(userInfo[@"attachment-url"]){
         NSURL* url = [[NSURL alloc] initWithString:userInfo[@"attachment-url"]];
         NSURLSessionDownloadTask* task = [[NSURLSession sharedSession] downloadTaskWithURL:url completionHandler:^(NSURL * _Nullable location, NSURLResponse * _Nullable response, NSError * _Nullable error) {
             if(!location){
                 return;
             }
             NSString* tmpDirectory = NSTemporaryDirectory();
             NSString* tmpFilePath = [NSString stringWithFormat:@"file://%@%d%d%@", tmpDirectory, arc4random_uniform(100000),
                                    arc4random_uniform(100000), [url lastPathComponent]];
             NSURL* tmpUrl = [[NSURL alloc] initWithString:tmpFilePath];
             NSError * fileError = nil;
             [[NSFileManager defaultManager] moveItemAtURL:location toURL:tmpUrl error:&amp;fileError];
             if(fileError){
                 return;
             }
             UNNotificationAttachment* attachment = [UNNotificationAttachment attachmentWithIdentifier:@"video" URL:tmpUrl options:nil error:&amp;fileError];
             if(fileError){
                 return;
             }
             self.bestAttemptContent.attachments = @[attachment];
             self.contentHandler(self.bestAttemptContent);
         }];
         [task resume];
       }
      }
      ```


For more information about rich push notifications with iOS, see [UNNotificationAttachment](https://developer.apple.com/documentation/usernotifications/unnotificationattachment).
