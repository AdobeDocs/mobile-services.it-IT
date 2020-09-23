---
description: Configura le opzioni relative all’esperienza per i messaggi in-app, incluso tipo (schermo intero, avviso o notifica) e visualizzazione, testo e pulsante.
keywords: mobile
seo-description: Configura le opzioni relative all’esperienza per i messaggi in-app, incluso tipo (schermo intero, avviso o notifica) e visualizzazione, testo e pulsante.
seo-title: Esperienza messaggio in-app
solution: Experience Cloud,Analytics
title: Esperienza messaggio in-app
topic: Metrics
uuid: 4c6d6756-47fb-4f1b-8338-0b0c9b0fceb0
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '686'
ht-degree: 92%

---


# Esperienza: messaggio in-app {#experience-in-app-message}

Configura le opzioni relative all’esperienza per i messaggi in-app, incluso tipo (schermo intero, avviso o notifica) e visualizzazione, testo e pulsante.

1. In your app, click **[!UICONTROL Messaging]** > **[!UICONTROL Manage Messages]** > **[!UICONTROL Create Message]** > **[!UICONTROL Create In-App]**.
1. Nella pagina Esperienza, specifica un nome per il messaggio.
1. Compila i campi nella sezione **[!UICONTROL Tipo]**:

   * **[!UICONTROL Tipo]**
Seleziona il tipo di messaggio per la campagna messaggi in-app:

      * **[!UICONTROL Schermo intero]**
      * **[!UICONTROL Avviso]**
      * **[!UICONTROL Notifica locale]**
   * **[!UICONTROL Modello]**

      Puoi personalizzare un modello di messaggio reattivo a tema per il contenuto.

      >[!TIP]
      >
      >Questa opzione è visibile solo se hai selezionato il tipo di messaggio **[!UICONTROL Schermo intero]**.

   * **[!UICONTROL Personalizzato]**

      Caricate il contenuto HTML personalizzato (solo schermo intero). Devi fornire un collegamento click-through e un collegamento di annullamento.

      1. Fai clic su **[!UICONTROL Sfoglia]** e scarica un file HTML o trascina un documento HTML sulla finestra.
      1. Fai clic su **[!UICONTROL Scarica esempio]** per visualizzare un esempio di contenuto HTML personalizzato.

      >[!TIP]
      >
      >Questa opzione è visibile solo se hai selezionato il tipo di messaggio **[!FSchermo intero]**.



1. Compila i campi nella sezione **[!UICONTROL Visualizzazione]**:

   * **[!UICONTROL Tema]**

   Seleziona un tema per il messaggio.

   * **[!UICONTROL Layout]**

      Seleziona il layout dell’app sullo schermo del dispositivo.

   * **[!UICONTROL URL immagine]**

      L’URL di un’immagine. Se riscontri problemi di dimensioni quando usi il modello a schermo intero, vedi *La mia immagine non rientra esattamente nello spazio disponibile nel modello* in [Risoluzione dei problemi dei messaggi in-app](/help/using/in-app-messaging/t-in-app-message/in-apps-ts.md).

   * **[!UICONTROL Immagine nel pacchetto]**

      Percorso di un’immagine contenuta nel pacchetto di codice dell’app. Questa opzione va utilizzata quando non è presente un’immagine oppure l’immagine non è disponibile (ad esempio perché il dispositivo è offline). Se riscontri problemi di dimensioni quando usi il modello a schermo intero, vedi *La mia immagine non rientra esattamente nello spazio disponibile nel modello* in [Risoluzione dei problemi dei messaggi in-app](/help/using/in-app-messaging/t-in-app-message/in-apps-ts.md).


1. Compila i campi nella sezione **[!UICONTROL Testo]**:

   * **[!UICONTROL Header]**

      Inserisci il testo per l’intestazione del messaggio.

   * **[!UICONTROL Contenuto]**

      Inserisci il testo per il contenuto del messaggio.

1. Compila i campi nella sezione **[!UICONTROL Pulsanti]**:

   * **[!UICONTROL Pulsante Click-through]**

      Etichetta per il pulsante di **[!UICONTROL click-through]**. Ogni tocco di questo pulsante è calcolato come un click-through con esito positivo. L’utente viene reindirizzato alla destinazione.

   * **[!UICONTROL Destinazione]**

      Seleziona una destinazione specifica, ad esempio un collegamento web, profondo o ibrido, alla quale indirizzare l’utente che fa clic sul messaggio. L’URL di reindirizzamento per un click-through con esisto positivo.

      Questo URL potrebbe contenere le seguenti informazioni:

      * `{userId}`: viene sostituito con l’identificatore utente o lasciato vuoto se l’ID utente non è impostato.
      * `{trackingId}`, che viene sostituito con l’aiuto (correlato con il cookie *s_vi*).
      * `{messageId}`, viene sostituito con l’ID univoco del messaggio in-app.
      * `{lifetimeValue}`, viene sostituito con il valore del ciclo di vita o con 0 se questo non esiste.

      Ecco un esempio di tracciamento dell’ID utente: `https://www.mysite.com?uid={userId}`.

      Se l’URL di click-through usa `https://` o `https://`, l’URL si apre nel browser del dispositivo, all’esterno dell’app. In caso contrario, ogni piattaforma supporta schemi che consentono di aprire l’app o farvi riferimento se l’app è stata sviluppata per supportare lo schema personalizzato.

      >[!TIP]
      >
      >I tipi di destinazione **[!UICONTROL Collegamento web]** o **[!UICONTROL Collegamento personalizzato]** non vengono tracciati. Solo i **[!UICONTROL collegamenti profondi]** vengono tracciati. Per ulteriori informazioni, vedi [Destinazioni](/help/using/acquisition-main/c-create-destinations.md).


1. (Facoltativo) Per verificare il layout del messaggio, fai clic sulle icone seguenti:

   * **[!UICONTROL Riepilogo]** nasconde il riquadro di anteprima.

      Fai clic su ![anteprima](assets/icon_preview.png) per visualizzare di nuovo il riquadro di anteprima.

   * **[!UICONTROL Modificare l’orientamento]**

      Per cambiare l’orientamento dell’anteprima da verticale a orizzontale, fai clic su ![orientamento](assets/icon_orientation.png). Per gli orologi, l’orientamento cambia da quadrante rotondo a quadrante quadrato.

   * **[!UICONTROL Anteprima sull’orologio di un utente]**

      Per visualizzare l’anteprima del messaggio così come verrà visualizzata sull’orologio di un utente, fai clic sull’icona dell’![orologio](assets/icon_watch.png).

   * **[!UICONTROL Anteprima sul cellulare di un utente]**

      Per visualizzare l’anteprima del messaggio così come verrà visualizzata sul telefono cellulare di un utente, fai clic sull’icona del ![telefono](assets/icon_phone.png).

   * **[!UICONTROL Anteprima sul tablet di un utente]**

      Per visualizzare l’anteprima del messaggio sul tablet di un utente, fai clic sull’icona del ![tablet](assets/icon_tablet.png).

      Nella parte inferiore del riquadro di anteprima puoi visualizzare una descrizione del pubblico che hai selezionato nel passaggi precedente. Potete anche visualizzare una descrizione del pubblico selezionato nel passaggio precedente, nella parte inferiore del riquadro di anteprima.

1. Configurare le opzioni [di](/help/using/in-app-messaging/t-in-app-message/c-schedule-in-app-message.md)pianificazione.
