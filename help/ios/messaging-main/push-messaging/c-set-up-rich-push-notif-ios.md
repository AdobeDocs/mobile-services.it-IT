---
description: Puoi allegare dei file di immagini alle notifiche Apple. L'aggiunta di elementi visivi può notevolmente migliorare il tasso di coinvolgimento degli utenti con le notifiche push.
seo-description: Puoi allegare dei file di immagini alle notifiche Apple. L'aggiunta di elementi visivi può notevolmente migliorare il tasso di coinvolgimento degli utenti con le notifiche push.
seo-title: Ricevere notifiche push potenziate
title: Ricevere notifiche push potenziate
uuid: 0dbda409-cf49-4eb8-90ee-baf27911dc07
translation-type: tm+mt
source-git-commit: d028fe0f9477bc011aa8fda21a0a389808df0fce

---


# Receive rich push notifications {#receive-rich-push-notifications}

Puoi allegare dei file di immagini alle notifiche Apple. L'aggiunta di elementi visivi può notevolmente migliorare il tasso di coinvolgimento degli utenti con le notifiche push.

Per Ricevere notifiche push potenziate nell'app iOS:

1. Implementa i messaggi push per l'app, completando i passaggi descritti in [Messaggi push](/help/ios/messaging-main/push-messaging/push-messaging.md).
1. Verifica di poter inviare un messaggio di testo push all'app.
1. Aggiungi un'estensione del servizio di notifica, completando i passaggi descritti di seguito:

   1. In your Xcode project, select  **[!UICONTROL File]** &gt; **[!UICONTROL New]** &gt; **[!UICONTROL Target]**.
   1. Seleziona **[!UICONTROL Estensione servizio notifiche]**.
   1. Verifica che esista il file `NotificationService.m`.

1. Apri il file `NotificationService.m` e verifica che siano presenti i seguenti metodi delegate:

   * Un metodo per la ricezione di una richiesta di notifica.
   * Un metodo per la gestione della scadenza dell'estensione del servizio.

      Per Ricevere notifiche push potenziate, si usa il primo metodo:

      ```objective-c
      (void)didReceiveNotificationRequest:(UNNotificationRequest *)request withContentHandler:(void (^)(UNNotificationContent *contentToDeliver))contentHandler;
      ```

      In this method, you can get the Media URL from  by using the  key. `userInfo``attachment-url` After you download the file to a local directory, add the local path to .`bestAttemptContent.attachments`

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


Per ulteriori informazioni sull'uso di notifiche push avanzate in iOS, vedi [UNNotificationAttachment](https://developer.apple.com/documentation/usernotifications/unnotificationattachment).
