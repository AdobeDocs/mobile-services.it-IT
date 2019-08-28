---
description: Puoi allegare file di immagini alle notifiche Android. L'aggiunta di componenti visivi può aumentare notevolmente il coinvolgimento degli utenti con le notifiche push.
seo-description: Puoi allegare file di immagini alle notifiche Android. L'aggiunta di componenti visivi può aumentare notevolmente il coinvolgimento degli utenti con le notifiche push.
seo-title: Ricevere notifiche push potenziate
title: Ricevere notifiche push potenziate
uuid: 4 a 0340 a 6-666 b -49 b 6-907 a -9 afc 966 dfdba
translation-type: tm+mt
source-git-commit: dca3663986b3ecc6e9fb736cc99513279715225c

---


# Receive rich push notifications {#receive-rich-push-notifications}

Puoi allegare file di immagini alle notifiche Android. L'aggiunta di componenti visivi può aumentare notevolmente il coinvolgimento degli utenti con le notifiche push.

## Handle the incoming rich push message (FCM) {#section_AF1A3BC2312C4E1DA517CC90296C11E2}

Se l'app è in primo piano, il messaggio push sarà gestito dall'app che estende la classe `FirebaseMessagingService` ed è dichiarato nel file manifesto come segue:

```java
<service
    android:name=".MyFirebaseMessagingService"
    android:exported="false">
    <intent-filter>
        <action android:name="com.google.firebase.MESSAGING_EVENT" />
    </intent-filter>
</service>
```

>[!IMPORTANT]
>
>La classe che contiene l `onMessageReceived()` 'implementazione gestisce i dati ricevuti.

If the push message contains a Media URL, the URL will be available in the `RemoteMessage` parameter that is passed to the `onMessageReceived()` function. La chiave da utilizzare è `attachment-url`, come mostrato nel seguente esempio di codice:

```java
public class MyFirebaseMessagingService extends FirebaseMessagingService {
        @Override
        public void onMessageReceived(RemoteMessage remoteMessage) {
      Log.d("Remote Message", "RemoteMessage: " + remoteMessage.toString());
            // Check if message contains a data payload.
            if (remoteMessage.getData().size() > 0) {
                Log.d("Remote Message", "RemoteMessage: " + remoteMessage.getData());
                sendNotification(remoteMessage);
            }
    }
 
private void sendNotification(RemoteMessage message) {
        Intent intent = new Intent(this, MainActivity.class);
    intent.addFlags(Intent.FLAG_ACTIVITY_CLEAR_TOP);
    PendingIntent pendingIntent = PendingIntent.getActivity(this, 0 /* Request code */, intent, PendingIntent.FLAG_ONE_SHOT);

     String channelId = getString(R.string.default_notification_channel_id);
     Uri defaultSoundUri = RingtoneManager.getDefaultUri(RingtoneManager.TYPE_NOTIFICATION);
     NotificationCompat.Builder notificationBuilder =
                new NotificationCompat.Builder(this, channelId)
                        .setSmallIcon(R.drawable.ic_stat_ic_notification)
                        .setContentTitle(getString(R.string.fcm_message))
                        .setContentText(message.getData().get("body"))
                        .setAutoCancel(true)
                        .setSound(defaultSoundUri)
                        .setContentIntent(pendingIntent);
  
    //Handle image url if present in the push message 
        String attachmentUrl = message.getData().get("attachment-url");
  
    if (attachmentUrl != null) { 
    Bitmap image = getBitmapFromURL(attachmentUrl); 
    if (image != null) { 
      notificationBuilder.setStyle(new        NotificationCompat.BigPictureStyle().bigPicture(image)); 
        } 
        } 

     NotificationManager notificationManager =
              (NotificationManager) getSystemService(Context.NOTIFICATION_SERVICE);

     // Since android Oreo notification channel is needed.
     if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.O) {
        NotificationChannel channel = new NotificationChannel(channelId,
                    "Channel human readable title",
                    NotificationManager.IMPORTANCE_DEFAULT);
            notificationManager.createNotificationChannel(channel);
     }

     notificationManager.notify(0 /* ID of notification */, notificationBuilder.build());
    }
}
```

>[!IMPORTANT]
>
>When you set `NotificationCompat.BigPictureStyle`, large images might not be displayed. Per fare in modo che siano sempre visualizzate, imposta il parametro nativo `Notification.BigPictureStyle`.

## Sample rich push notification {#section_6819316BEDDE45108413B541CA2BB2DC}

Esempio di notifica push potenziata con un'immagine:

![](assets/rich-push-notification_example.png)

Per ulteriori informazioni sulle notifiche push potenziate con Android, vedi [Coinvolgere con le notifiche potenziate](https://developer.android.com/distribute/best-practices/engage/rich-notifications.html).
