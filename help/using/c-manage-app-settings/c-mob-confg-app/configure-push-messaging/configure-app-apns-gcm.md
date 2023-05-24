---
description: Puoi configurare l’app per l’uso di APNS (Apple Push Notification Service) o FCM (Firebase Cloud Messaging).
keywords: dispositivi mobili
solution: Experience Cloud Services,Analytics
title: Configurare l’app per l’uso di APNS o FCM
topic-fix: Metrics
uuid: fa411f2a-ba47-4499-bbe5-1aedef6b49ad
exl-id: 9064e1f3-f176-4699-b1e6-90f29e1af0d3
source-git-commit: 7cfaa5f6d1318151e87698a45eb6006f7850aad4
workflow-type: tm+mt
source-wordcount: '629'
ht-degree: 100%

---

# Configurare l’app per l’utilizzo di APNS o FCM {#configure-app-to-use-apns-or-fcm}

{#eol}

Puoi configurare l’app per l’uso di APNS (Apple Push Notification Service) o FCM (Firebase Cloud Messaging).

## App Android {#section_41D304102CDF4586911EC1413AD35A10}

### Se FCM non è abilitato nell’app:

Per configurare la tua app Android per l’utilizzo di FCM in questo scenario:

1. Vai a [https://firebase.google.com/](https://firebase.google.com/) e accedi con le tue credenziali Google Dev.

1. Fai clic su **[!UICONTROL Inizia]** e seleziona **[!UICONTROL Aggiungi progetto]**.

1. Immetti un nome per il progetto e, se scegli di accedere a Google Analytics per i dati Firebase, fai clic sulla casella di controllo per accettare i “Termini applicabili al Titolare del trattamento”.

1. Fai clic su **[!UICONTROL Crea progetto]** e attendi la creazione del progetto.

1. Fai clic sul progetto creato per visualizzare la pagina di **[!UICONTROL panoramica del progetto]** creato. Fai clic sul pulsante con l’icona Android per aggiungere un’app Android al progetto.

1. Immetti il nome del pacchetto dell’app, il nome alternativo dell’app e il certificato di firma, se necessario.

1. Segui i passaggi aggiuntivi suggeriti dalla procedura guidata di configurazione. Dopo aver verificato la configurazione di Firebase effettuando un test sulla comunicazione con i server Firebase, ritorna alla pagina della **[!UICONTROL panoramica del progetto]**.

1. Fai clic sull’icona a forma di ingranaggio a destra del pulsante **[!UICONTROL Panoramica progetto]** e fai clic su **[!UICONTROL Impostazioni progetto]**.

1. Fai clic sulla scheda **[!UICONTROL Messaggistica Cloud]**.

1. Copia la **[!UICONTROL Server key legacy]** e l’**[!UICONTROL ID mittente]**, da utilizzare in un secondo momento.

   Ad esempio:

   ```
   - Legacy server key = AIzaSyC6FNgsCOpBL5eXhDvwf8979mWba6x7Roo
   ```

   ```
   - Sender ID = 835015092250
   ```

### Se FCM è abilitato nell’app:

Per configurare la tua app Android per l’utilizzo di FCM in questo scenario:

1. Vai a [https://firebase.google.com/](https://firebase.google.com/) e accedi con le tue credenziali Google Dev.

1. Fai clic su **[!UICONTROL Inizia]**. Viene aperta la pagina dell’indice del progetto. Trova il progetto abilitato Firebase collegato alla tua app Android e fai clic sulla scheda del progetto.

1. A questo punto viene caricata la pagina di **[!UICONTROL panoramica del progetto]**. Fai clic sull’icona a forma di ingranaggio a destra del pulsante **[!UICONTROL Panoramica progetto]** e fai clic su **[!UICONTROL Impostazioni progetto]**.

1. Fai clic sulla scheda **[!UICONTROL Messaggistica Cloud]**.

1. Copia la **[!UICONTROL Server key legacy]** e l’**[!UICONTROL ID mittente]**, da utilizzare in un secondo momento.

   Ad esempio:

   ```
   - Legacy server key = AIzaSyC6FNgsCOpBL5eXhDvwf8979mWba6x7Roo
   ```

   ```
   - Sender ID = 835015092250
   ```



## App iOS {#section_2031DAB485FC4D2B9027E42AD90B294D}

Per configurare la tua app iOS per l’uso di APNS:

1. Visita [https://developer.apple.com/account](https://developer.apple.com/account) e accedi al tuo [account Apple Developer](https://developer.apple.com/account).
1. In **[!UICONTROL App iOS]**, seleziona **[!UICONTROL Identificatori]**.
1. Se hai un App ID impostato per il push, passa al punto 11.
1. Premi il pulsante **[!UICONTROL +]** per creare un nuovo App ID.
1. Immetti una descrizione per l’App ID.
1. Immetti un suffisso per l’App ID.

   >[!IMPORTANT]
   >
   >Per supportare il push, devi utilizzare un App ID esplicito **senza** alcun carattere jolly (ad es. `- com.tester.pushSample`).

1. In **[!UICONTROL Servizi app]**, seleziona la casella di controllo **[!UICONTROL Notifiche push]**.
1. Fai clic su **[!UICONTROL Continua]**.
1. Fai clic su **[!UICONTROL Invia]**.
1. Fai clic su **[!UICONTROL Fine]**.
1. Seleziona dall’elenco l’App ID configurato per l’utilizzo dei messaggi push, e fai clic su **[!UICONTROL Modifica]**.
1. Se hai già creato un certificato push, passa al punto 15.
1. Scorri fino a **[!UICONTROL Notifiche push]** e fai clic sul pulsante **[!UICONTROL Crea certificato]** appropriato.

   Il pulsante su cui fai clic dipende dal fatto che stai creando un certificato per lo sviluppo o la produzione.
1. Segui i passaggi per creare un CSR sul sito web di Apple, carica il CSR e genera il certificato.
1. Scorri fino alla sezione **[!UICONTROL Notifiche push]** e scarica il certificato SSL appena creato.
1. Fai doppio clic sul certificato scaricato per aggiungerlo al tuo portachiavi.

### Certificato SSL e chiave privata

Per ottenere il certificato SSL e la chiave privata (APNS):

1. Apri **[!UICONTROL Accesso Portachiavi]**.
1. Fai clic su **[!UICONTROL I miei certificati]** e trova il certificato **[!UICONTROL iOS Services Certificate]** appropriato per l’app e l’ambiente.

   Per trovare il certificato corretto, confrontalo con il bundle ID e verifica se si tratta di un certificato di sviluppo o produzione.

1. Espandi il certificato e verifica che contenga una chiave privata.
1. Fai clic con il pulsante destro del mouse sulla chiave privata e seleziona **[!UICONTROL Esporta “*`<name of key>`*]**.
1. Digita le informazioni necessarie nella finestra di dialogo e salva il nuovo file `.p12`.

   Non è necessario digitare una password.

1. In **[!UICONTROL Chiave privata]**, digita il file `.p12`.
