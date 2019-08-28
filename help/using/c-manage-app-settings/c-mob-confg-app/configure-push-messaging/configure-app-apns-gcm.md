---
description: Puoi configurare l'app per l'utilizzo di APNS (Apple Push Notification Service) o di Firebase Cloud Messaging (FCM).
keywords: dispositivi mobili
seo-description: Puoi configurare l'app per l'utilizzo di APNS (Apple Push Notification Service) o di Firebase Cloud Messaging (FCM).
seo-title: Configurare l'app per l'utilizzo di APNS o FCM
solution: Marketing Cloud, Analytics
title: Configurare l'app per l'utilizzo di APNS o FCM
topic: Metrics (Metriche)
uuid: fa 411 f 2 a-ba 47-4499-bbe 5-1 aedef 6 b 49 ad
translation-type: tm+mt
source-git-commit: 608384f1fee2a05699ff13fbd51c3cc43aeb693c

---


# Configurare l'app per l'utilizzo di APNS o FCM{#configure-app-to-use-apns-or-fcm}

Puoi configurare l'app per l'utilizzo di APNS (Apple Push Notification Service) o di Firebase Cloud Messaging (FCM).

## App Android {#section_41D304102CDF4586911EC1413AD35A10}

### Se FCM non è abilitato nell'app

Per configurare la tua app Android per l'utilizzo di FCM in questo scenario:

1. Go to [https://firebase.google.com/](https://firebase.google.com/) and log in with your Google Dev credentials.

1. Fate clic su **[!UICONTROL Introduzione]** e selezionate **[!UICONTROL Aggiungi progetto]**.

1. Immettete un nome di progetto e, se accedete a Google Analytics per i dati Firebase, fate clic sulla casella di controllo che accetta i termini del controller controller.

1. Fate clic su **[!UICONTROL Crea progetto]** e attendete che venga creato il progetto.

1. Fate clic sul progetto creato e dovrebbe essere visualizzata **[!UICONTROL la pagina Panoramica]** progetti relativa al progetto creato. Fate clic sul pulsante con l'icona Android per aggiungere un'app Android al progetto.

1. Immettete il nome del pacchetto app, il pseudonimo dell'app e il certificato di firma, se necessario.

1. Seguite i passaggi aggiuntivi suggeriti dalla procedura guidata di configurazione. Dopo aver verificato la configurazione Firebase sottoponendo a test la comunicazione con i server Firebase, tornate alla **[!UICONTROL pagina Panoramica]** progetto.

1. Fate clic sull'icona a forma di ingranaggio a destra del **[!UICONTROL pulsante Panoramica]** progetto e fate clic **[!UICONTROL su Impostazioni progetto]**.

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

1. Fate clic su **[!UICONTROL Introduzione]**. Viene aperta la pagina dell'indice del progetto. Trova il progetto abilitato per Firebase collegato alla tua app Android e fai clic sulla scheda del progetto.

1. La panoramica **[!UICONTROL del progetto]** per il progetto deve essere caricata. Fate clic sull'icona a forma di ingranaggio a destra del **[!UICONTROL pulsante Panoramica]** progetto e fate clic **[!UICONTROL su Impostazioni progetto]**.

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
1. Se hai un ID app impostato per push, vai al passaggio 11.
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

   Il pulsante che fate clic dipende dal tipo di certificato di sviluppo o produzione.
1. Seguite i passaggi su come creare il CSR sul sito Web di Apple, caricare il CSR e generare il certificato.
1. Scorri fino alla sezione **[!UICONTROL Notifiche push]** e scarica il certificato SSL appena creato.
1. Fate doppio clic sul certificato scaricato per aggiungerlo al Keychain.

### Certificato SSL e chiavi private

Per ottenere il certificato SSL e la chiave privata (APNS):

1. Apri **[!UICONTROL Accesso Portachiavi]**.
1. Fai clic su **[!UICONTROL I miei certificati]** e trova il certificato **[!UICONTROL iOS Services Certificate]** appropriato per l’app e l’ambiente.

   Per identificare il certificato corretto, confrontalo con il bundle ID e verifica se si tratta di un certificato di sviluppo (Development) o produzione (Production).

1. Espandi il certificato e verifica che contenga una chiave privata.
1. Right-click the private key and select **[!UICONTROL Export "*`<name of key>`*]**.
1. Digitate le informazioni necessarie nella finestra di dialogo e salvate il nuovo `.p12` file.

   Non è necessario digitare una password.

1. In the **[!UICONTROL Private Key]**, type the `.p12` file.

