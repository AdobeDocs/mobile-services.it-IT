---
description: Adobe Mobile e SDK di Adobe Mobile consentono di inviare messaggi push agli utenti. L'SDK consente inoltre di segnalare facilmente gli utenti che hanno aperto l'app dopo aver fatto clic su un messaggio push.
seo-description: Adobe Mobile e SDK di Adobe Mobile consentono di inviare messaggi push agli utenti. L'SDK consente inoltre di segnalare facilmente gli utenti che hanno aperto l'app dopo aver fatto clic su un messaggio push.
seo-title: Messaggi push
solution: Marketing Cloud, Analytics
title: Messaggi push
topic: Sviluppatore e implementazione
uuid: 729 d 4010-3733-4 dff-b 188-ad 45 bd 3 e 7 cc 4
translation-type: tm+mt
source-git-commit: 17cb91a28966cf32f955a2cb724e89ab228de5b8

---


# Push messaging {#push-messaging}

Adobe Mobile e SDK di Adobe Mobile consentono di inviare messaggi push agli utenti. L'SDK consente inoltre di segnalare facilmente gli utenti che hanno aperto l'app dopo aver fatto clic su un messaggio push.

Per usare la funzione per messaggi push, **devi** disporre della versione 4.6 o successiva dell’SDK.

>[!IMPORTANT]
>
>Non impostare manualmente l'ID Experience Cloud all'interno dell'app. Questo provocherebbe infatti la creazione di un nuovo utente univoco che non riceverà i messaggi push a causa del suo stato di consenso. Ad esempio, un utente che ha acconsentito a ricevere i messaggi push accede all'app. Dopo l'accesso, se imposti manualmente l'ID all'interno dell'app, viene creato un nuovo utente univoco che non ha acconsentito alla ricezione di messaggi push. Questo nuovo utente non riceverà quindi alcun messaggio push.
>
>Lo spostamento dell'app in una nuova suite di rapporti non è supportato. Se si effettua la migrazione a una nuova suite di rapporti, la configurazione push può interrompersi e i messaggi potrebbero non essere inviati.

## Enable push messaging {#section_CBD63C5B11FE4424BC2BF552C23F2BD9}

>[!TIP]
>
>Se l'app è già configurata per utilizzare i messaggi tramite Firebase Cloud Messaging (FCM), alcuni dei passaggi seguenti potrebbero essere già stati completati.

1. Verify that the `ADBMobileConfig.json` file contains the required settings for push messaging.

   The `"marketingCloud"` object must have its `"org"` property configured for push messaging.

   ```js
   "marketingCloud": { 
     "org": <org-id-string> 
    }
   ```

1. Per ottenere l’ID/token di registrazione, utilizza l’API Firebase Cloud Messaging (FCM).

   * Per ulteriori informazioni sulla configurazione di FCM, vedi [Configurare un'app client Firebase Cloud Messaging su Android](https://firebase.google.com/docs/cloud-messaging/android/client).
   ```js
   String token = FirebaseInstanceId.getInstance().getToken();
   ```

1. The registration ID/token must be passed to the SDK by using the `Config.setPushIdentifier(final String registrationId)` method.

   ```js
   Config.setPushIdentifier(token); // token was obtained in step 2
   ```

1. Abilita i rapporti passando la tua attività nel metodo `collectLifecycleData`.

   Questi sono i requisiti per abilitare i rapporti di click-through tramite push:

   * In your implementation of `FireBaseMessageService`, the Bundle object that contains the message data, which is passed into the `onMessageReceived` method with the RemoteMessage object, must be added to the Intent that is used to open the target activity on a click-through. Questo può essere fatto utilizzando il `putExtras` metodo. For more information, see [putExtras](https://developer.android.com/reference/android/content/Intent.html#putExtras(android.os.Bundle))).
   ```java
   Intent intent = new Intent(this, MainActivity.class);
      intent.addFlags(Intent.FLAG_ACTIVITY_CLEAR_TOP);
   // get the bundle from the RemoteMessage object
      intent.putExtras(message.toIntent().getExtras());
   ```

   * Nell'attività di destinazione del click-through, l'attività deve essere passata nell'SDK con la chiamata `collectLifecycleData`.

      Considerazioni da ricordare:

      * Utilizzate `Config.collectLifecycleData(this)` o `Config.collectLifecycleData(this, contextData)`.

      * **Non** utilizzate `Config.collectLifecycleData()`.



