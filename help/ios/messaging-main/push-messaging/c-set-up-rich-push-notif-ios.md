---
description: Puoi allegare file di immagine alle notifiche Apple. L’aggiunta di componenti visivi può aumentare notevolmente il coinvolgimento degli utenti con le notifiche push.
title: Ricevere notifiche push potenziate
uuid: 0dbda409-cf49-4eb8-90ee-baf27911dc07
exl-id: 1167ae4b-04ad-4c0d-a9db-67d30693f697
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 39%

---

# Ricevere notifiche push potenziate {#receive-rich-push-notifications}

Puoi allegare file di immagine alle notifiche Apple. L’aggiunta di componenti visivi può aumentare notevolmente il coinvolgimento degli utenti con le notifiche push.

Per ricevere notifiche push potenziate nell’app iOS:

1. Implementa i messaggi push per l&#39;app, completando i passaggi descritti in  [Messaggi push](/help/ios/messaging-main/push-messaging/push-messaging.md).
1. Verifica di poter inviare un messaggio push di testo all’app.
1. Aggiungi un&#39;estensione del servizio di notifica completando i seguenti passaggi:

   1. Nel progetto Xcode, seleziona **[!UICONTROL File]** > **[!UICONTROL Nuovo]** > **[!UICONTROL Target]**.
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


Per ulteriori informazioni sulle notifiche push potenziate con iOS, consulta [UNNotificationAttachment](https://developer.apple.com/documentation/usernotifications/unnotificationattachment).
