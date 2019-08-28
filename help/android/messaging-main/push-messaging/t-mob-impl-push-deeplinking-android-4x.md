---
description: Dopo aver configurato l'URL di collegamento profondo (deep linking) nell'interfaccia utente di Adobe Mobile Services, tale URL si troverà nel payload push con la chiave adb_deeplink.
seo-description: Dopo aver configurato l'URL di collegamento profondo (deep linking) nell'interfaccia utente di Adobe Mobile Services, tale URL si troverà nel payload push con la chiave adb_deeplink.
seo-title: Implementare i messaggi push con collegamenti profondi
title: Implementare i messaggi push con collegamenti profondi
uuid: e 24 f 9248-8 d 48-4 e 57-84 af -3 a 05 b 72 e 2 a 09
translation-type: tm+mt
source-git-commit: 13ff2cb549c4b82a4e0285e1c7c6b3f9c1a5bd4b

---


# Implement push messaging with deep linking {#implement-push-messaging-with-deep-linking}

Dopo aver configurato l'URL di collegamento profondo (deep linking) nell'interfaccia utente di Adobe Mobile Services, tale URL si troverà nel payload push con la chiave adb_deeplink.

Puoi ottenere l'URL chiamando `remoteMessage.getData().get("adb_deeplink")` in `FirebaseMessagingService`.

>[!TIP]
>
>Puoi definire intenti diversi a seconda che il payload abbia un URL di collegamento profondo.

1. Completa una delle seguenti attività:

   * Se l'URL di collegamento profondo **si trova** nel payload push, crea un intento `ACTION_VIEW` con l'URL.

      Quando l'utente fa clic sul messaggio push, viene attivato un collegamento profondo.

   * Se l'URL di collegamento profondo **non si trova** nel payload push, crea un intento che aprirà una delle tue attività.

## Esempio

Here is a sample implementation for the class extending from `FirebaseMessagingService`:

```java
public void onMessageReceived(RemoteMessage message) { 
 
       Map<String, String> data = message.getData(); 
       String messageStr = data.get("message"); 
       String deepLink = data.get("adb_deeplink"); 
 
       sendNotification(deepLink, messageStr, data); 
    } 
 
private void sendNotification(String deeplink, String message, Map<String, String> data) { 
       Intent intent; 
 
       if (deeplink!=null) { 
           intent = new Intent(Intent.ACTION_VIEW, Uri.parse(deeplink)); 
       } else { 
           intent = new Intent(this, MainActivity.class); 
       } 
 
       intent.addFlags(Intent.FLAG_ACTIVITY_CLEAR_TOP); 
 
       //put the data map into the intent to track clickthroughs 
       Bundle pushData = new Bundle(); 
       Set<String> keySet = data.keySet(); 
       for (String key : keySet) { 
           pushData.putString(key, data.get(key)); 
       } 
 
       intent.putExtras(pushData); 
 
       PendingIntent pendingIntent = PendingIntent.getActivity(this, 0, intent, 
               PendingIntent.FLAG_ONE_SHOT); 
 
       Uri defaultSoundUri= RingtoneManager.getDefaultUri(RingtoneManager.TYPE_NOTIFICATION); 
 
       NotificationCompat.Builder notificationBuilder = new NotificationCompat.Builder(this) 
                .setSmallIcon(R.drawable.icon) 
                .setContentTitle("FCM Deep Link Push") 
                .setContentText(message) 
                .setAutoCancel(true) 
                .setSound(defaultSoundUri) 
                .setContentIntent(pendingIntent); 
 
       NotificationManager notificationManager =  
       (NotificationManager)getApplicationContext().getSystemService(Context.NOTIFICATION_SERVICE); 
           notificationManager.notify(0, notificationBuilder.build()); 
       } 
```
