---
description: Dopo aver configurato l'URL di collegamento profondo (deep linking) nell'interfaccia utente di Adobe Mobile Services, tale URL si troverà nel payload push con la chiave adb_deeplink.
title: Implementare i messaggi push con collegamenti profondi
uuid: e24f9248-8d48-4e57-84af-3a05b72e2a09
exl-id: ab97db32-d9d2-41ec-aae8-a951c7745df8
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '154'
ht-degree: 74%

---

# Implementare i messaggi push con collegamenti profondi {#implement-push-messaging-with-deep-linking}

Dopo aver configurato l&#39;URL di collegamento profondo (deep linking) nell&#39;interfaccia utente di Adobe Mobile Services, tale URL si troverà nel payload push con la chiave adb_deeplink.

Puoi ottenere l’URL chiamando `remoteMessage.getData().get("adb_deeplink")` nel `FirebaseMessagingService`.

>[!TIP]
>
>Puoi definire intenti diversi in base al fatto che il payload abbia o meno un URL di collegamento diretto.

1. Completa una delle seguenti attività:

   * Se l&#39;URL di collegamento profondo **si trova** nel payload push, crea un intento `ACTION_VIEW` con l&#39;URL.

      Quando l&#39;utente fa clic sul messaggio push, viene attivato un collegamento profondo.

   * Se l&#39;URL di collegamento profondo **non è** nel payload push, crea un intento che aprirà una delle tue attività.

## Esempio

Questo è un esempio di implementazione per la classe che si estende da `FirebaseMessagingService`:

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
