---
description: You can configure your app to use Apple Push Notification Service (APNS) or Firebase Cloud Messaging (FCM).
keywords: dispositivi mobili
seo-description: Potete configurare l'app per l'utilizzo di APNS (Apple Push Notification Service) o FCM (Firebase Cloud Messaging).
seo-title: Configurare l'app per l'utilizzo di APNS o FCM
solution: Marketing Cloud,Analytics
title: Configurare l'app per l'utilizzo di APNS o FCM
topic: Metrics (Metriche)
uuid: fa411f2a-ba47-4499-bbe5-1aedef6b49ad
translation-type: tm+mt
source-git-commit: 608384f1fee2a05699ff13fbd51c3cc43aeb693c

---


# Configure your app to use APNS or FCM{#configure-app-to-use-apns-or-fcm}

Potete configurare l'app per l'utilizzo di APNS (Apple Push Notification Service) o FCM (Firebase Cloud Messaging).

## App Android {#section_41D304102CDF4586911EC1413AD35A10}

### Se FCM non è abilitato nell'app

To configure your Android app to use FCM in this scenario:

1. Go to [https://firebase.google.com/](https://firebase.google.com/) and log in with your Google Dev credentials.

1. Click Get Started and select Add Project.********

1. Enter a project name and if opting in to Google Analytics for Firebase data, click the checkbox accepting the controller-controller terms.

1. Click Create project and wait for the project to be created.****

1. Click on the created project and the Project Overview page for the created project should be shown. **** Click the button with the Android icon to add an Android app to the project.

1. Immetti il nome del pacchetto dell'app, il nickname dell'app e il certificato di firma, se necessario.

1. Follow the additional steps suggested by the setup wizard. After verifying the Firebase setup by testing communication with the Firebase servers, return to the Project Overview page.****

1. Click the gear icon to the right of the Project Overview button and click Project Settings.********

1. Fate clic sulla scheda **[!UICONTROL Cloud Messaging]** .

1. Copy the **[!UICONTROL Legacy server key]** and **[!UICONTROL Sender ID]** for later use.

   Ad esempio:

   ```
   - Legacy server key = AIzaSyC6FNgsCOpBL5eXhDvwf8979mWba6x7Roo
   ```

   ```
   - Sender ID = 835015092250
   ```

### Se FCM è abilitato nell'app

Per configurare la tua app Android per l'utilizzo di FCM in questo scenario:

1. Go to [https://firebase.google.com/](https://firebase.google.com/) and log in with your Google Dev credentials.

1. Fate clic su **[!UICONTROL Inizia]**. Viene aperta la pagina dell’indice del progetto. Trova il progetto abilitato Firebase collegato alla tua app Android e fai clic sulla scheda del progetto.

1. È quindi necessario caricare la Panoramica **[!UICONTROL del]** progetto. Fate clic sull'icona a forma di ingranaggio a destra del pulsante Panoramica **** progetto e fate clic su Impostazioni **** progetto.

1. Fate clic sulla scheda **[!UICONTROL Cloud Messaging]** .

1. Copy the **[!UICONTROL Legacy server key]** and **[!UICONTROL Sender ID]** for later use.

   Ad esempio:

   ```
   - Legacy server key = AIzaSyC6FNgsCOpBL5eXhDvwf8979mWba6x7Roo
   ```

   ```
   - Sender ID = 835015092250
   ```



## iOS apps {#section_2031DAB485FC4D2B9027E42AD90B294D}

Per configurare la tua app iOS per l'uso di APNS:

1. Vai a [https://developer.apple.com/account](https://developer.apple.com/account) e accedi al tuo [account Apple Developer](https://developer.apple.com/account).
1. Under **[!UICONTROL iOS Apps]**, select **[!UICONTROL Identifiers]**.
1. Se disponete di un ID app impostato per il push, andate al passaggio 11.
1. Press the **[!UICONTROL +]** button to create a new App ID.
1. Immetti una descrizione per l'App ID.
1. Immetti un suffisso per l'App ID.

   >[!IMPORTANT]
   >
   >To support push, you must use an Explicit App ID that does **not** use a wild card (for example, `- com.tester.pushSample`).

1. In **[!UICONTROL Servizi app]**, seleziona la casella di controllo **[!UICONTROL Notifiche push]**.
1. Click **[!UICONTROL Continue]**.
1. Click **[!UICONTROL Submit]**.
1. Fai clic su **[!UICONTROL Fine]**.
1. Seleziona dall’elenco l’App ID configurato per l’utilizzo dei messaggi push, e fai clic su **[!UICONTROL Modifica]**.
1. Se hai già creato un certificato push, passa al punto 15.
1. Scorri fino a **[!UICONTROL Notifiche push]** e fai clic sul pulsante **[!UICONTROL Crea certificato]** appropriato.

   Il pulsante su cui fate clic dipende dal fatto che state creando un certificato per lo sviluppo o la produzione.
1. Seguite i passaggi per creare un CSR sul sito Web di Apple, caricare il CSR e generare il certificato.
1. Scorri fino alla sezione **[!UICONTROL Notifiche push]** e scarica il certificato SSL appena creato.
1. Fate doppio clic sul certificato scaricato per aggiungerlo al Keychain.

### Certificato SSL e chiavi private

Per ottenere il certificato SSL e la chiave privata (APNS):

1. Apri **[!UICONTROL Accesso Portachiavi]**.
1. Fai clic su **[!UICONTROL I miei certificati]** e trova il certificato **[!UICONTROL iOS Services Certificate]** appropriato per l’app e l’ambiente.

   Per identificare il certificato corretto, confrontalo con il bundle ID e verifica se si tratta di un certificato di sviluppo (Development) o produzione (Production).

1. Espandi il certificato e verifica che contenga una chiave privata.
1. Right-click the private key and select **[!UICONTROL Export "*`<name of key>`*]**.
1. Digitare le informazioni necessarie nella finestra di dialogo e salvare il nuovo `.p12` file.

   Non è necessario digitare una password.

1. In the **[!UICONTROL Private Key]**, type the `.p12` file.

