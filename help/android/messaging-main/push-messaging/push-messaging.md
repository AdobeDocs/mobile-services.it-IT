---
description: Adobe Mobile e SDK di Adobe Mobile consentono di inviare messaggi push agli utenti. L'SDK consente inoltre di segnalare facilmente gli utenti che hanno aperto l'app dopo aver fatto clic su un messaggio push.
seo-description: Adobe Mobile e SDK di Adobe Mobile consentono di inviare messaggi push agli utenti. L'SDK consente inoltre di segnalare facilmente gli utenti che hanno aperto l'app dopo aver fatto clic su un messaggio push.
seo-title: Messaggi push
solution: Experience Cloud,Analytics
title: Messaggi push
topic: Sviluppatore e implementazione
uuid: 729d4010-3733-4dff-b188-ad45bd3e7cc4
translation-type: ht
source-git-commit: 17cb91a28966cf32f955a2cb724e89ab228de5b8

---


# Messaggi push {#push-messaging}

Adobe Mobile e SDK di Adobe Mobile consentono di inviare messaggi push agli utenti. L'SDK consente inoltre di segnalare facilmente gli utenti che hanno aperto l'app dopo aver fatto clic su un messaggio push.

Per usare la funzione per messaggi push, **devi** disporre della versione 4.6 o successiva dell'SDK.

>[!IMPORTANT]
>
>Non impostare manualmente l'Experience Cloud ID all'interno dell'app. Questo provocherebbe infatti la creazione di un nuovo utente univoco che non riceverà i messaggi push a causa del suo stato di consenso. Ad esempio, un utente che ha acconsentito a ricevere i messaggi push accede all'app. Dopo l'accesso, se imposti manualmente l'ID all'interno dell'app, viene creato un nuovo utente univoco che non ha acconsentito alla ricezione di messaggi push. Questo nuovo utente non riceverà quindi alcun messaggio push.
>
>Lo spostamento dell’app a una nuova suite di rapporti non è supportato. Se si effettua la migrazione a una nuova suite di rapporti, la configurazione push può interrompersi e i messaggi potrebbero non essere inviati.

## Abilitare i messaggi push {#section_CBD63C5B11FE4424BC2BF552C23F2BD9}

>[!TIP]
>
>Se la tua app è già configurata per l’uso dei messaggi mediante Firebase Cloud Messaging (FCM), alcuni dei passaggi seguenti potrebbero essere già stati completati.

1. Verifica che il file `ADBMobileConfig.json` contenga le impostazioni richieste per i messaggi push.

   L'oggetto `"marketingCloud"` deve avere la propria proprietà `"org"` configurata per i messaggi push.

   ```js
   "marketingCloud": { 
     "org": <org-id-string> 
    }
   ```

1. Per ottenere l'ID/token di registrazione, utilizza l'API Firebase Cloud Messaging (FCM).

   * Per ulteriori informazioni sulla configurazione di FCM, vedi [Configurare un'app client Firebase Cloud Messaging su Android](https://firebase.google.com/docs/cloud-messaging/android/client).
   ```js
   String token = FirebaseInstanceId.getInstance().getToken();
   ```

1. L'ID/token di registrazione deve essere passato all'SDK usando il metodo `Config.setPushIdentifier(final String registrationId)`.

   ```js
   Config.setPushIdentifier(token); // token was obtained in step 2
   ```

1. Abilita i rapporti passando la tua attività nel metodo `collectLifecycleData`.

   Questi sono i requisiti per abilitare i rapporti di click-through tramite push:

   * Nella tua implementazione di `FireBaseMessageService`, l'oggetto Bundle contenente i dati del messaggio, che viene passato nel metodo `onMessageReceived` con l’oggetto RemoteMessage, deve essere aggiunto all'Intent utilizzato per aprire l'attività di destinazione su un click-through. Questa operazione può essere eseguita utilizzando il metodo `putExtras`. Per ulteriori informazioni, consulta [putExtras](https://developer.android.com/reference/android/content/Intent.html#putExtras(android.os.Bundle))).
   ```java
   Intent intent = new Intent(this, MainActivity.class);
      intent.addFlags(Intent.FLAG_ACTIVITY_CLEAR_TOP);
   // get the bundle from the RemoteMessage object
      intent.putExtras(message.toIntent().getExtras());
   ```

   * Nell'attività di destinazione del click-through, l'attività deve essere passata nell'SDK con la chiamata `collectLifecycleData`.

      Considerazioni da ricordare:

      * Usa `Config.collectLifecycleData(this)` o `Config.collectLifecycleData(this, contextData)`.

      * **Non** usare `Config.collectLifecycleData()`.



