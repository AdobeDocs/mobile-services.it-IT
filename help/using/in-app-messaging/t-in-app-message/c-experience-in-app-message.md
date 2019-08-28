---
description: Configura le opzioni relative all'esperienza per i messaggi in-app, incluso tipo (schermo intero, avviso o notifica) e visualizzazione, testo e pulsante.
keywords: dispositivi mobili
seo-description: Configura le opzioni relative all'esperienza per i messaggi in-app, incluso tipo (schermo intero, avviso o notifica) e visualizzazione, testo e pulsante.
seo-title: Messaggio in-app Esperienza
solution: Marketing Cloud, Analytics
title: Messaggio in-app Esperienza
topic: Metrics (Metriche)
uuid: 4 c 6 d 6756-47 fb -4 f 1 b -8338-0 b 0 c 9 b 0 fceb 0
translation-type: tm+mt
source-git-commit: e9691f9cbeadd171948aa752b27a014c3ab254d6

---


# Experience: in-app message {#experience-in-app-message}

Configura le opzioni relative all'esperienza per i messaggi in-app, incluso tipo (schermo intero, avviso o notifica) e visualizzazione, testo e pulsante.

1. In your app, click **[!UICONTROL Messaging]** &gt; **[!UICONTROL Manage Messages]** &gt; **[!UICONTROL Create Message]** &gt; **[!UICONTROL Create In-App]**.
1. Nella pagina Esperienza, specifica un nome per il messaggio.
1. Compila i campi nella sezione **[!UICONTROL Tipo]:**

   * **[!UICONTROL Tipo]**
Seleziona il tipo di messaggio per la campagna messaggi in-app:

      * **[!UICONTROL Schermo intero]**
      * **[!UICONTROL Avviso]**
      * **[!UICONTROL Notifica locale]**
   * **[!UICONTROL Modello]**

      Puoi personalizzare un modello di messaggio reattivo a tema per il contenuto.

      >[!TIP]
      >
      >This option is displayed only when you select the **[!UICONTROL Full Screen]** message type.

   * **[!UICONTROL Personalizzato]**

      Carica un tuo contenuto HTML personalizzato (solo per messaggi a schermo intero). Devi fornire un collegamento click-through o un collegamento di annullamento.

      1. Fai clic su **[!UICONTROL Sfoglia]e scarica un file HTML o trascina un documento HTML sulla finestra.**
      1. Fai clic su **[!UICONTROL Scarica esempio]per visualizzare un esempio di contenuto HTML personalizzato.**
      >[!TIP]
      >
      >This option is displayed only when you select the **[!Full Screen]** message type.



1. Compila i campi nella sezione **[!UICONTROL Visualizzazione]:**

   * **[!UICONTROL Tema]**
   Seleziona un tema per il messaggio.

   * **[!UICONTROL Layout]**

      Seleziona il layout dell'app sullo schermo del dispositivo.

   * **[!UICONTROL URL immagine]**

      L'URL di un'immagine. If you have sizing issues when using the full-screen template, see *My image does not fit exactly into the space provided by the template* in [Troubleshooting in-app messaging](/help/using/in-app-messaging/t-in-app-message/in-apps-ts.md).

   * **[!UICONTROL Immagine nel pacchetto]**

      Percorso di un'immagine contenuta nel pacchetto di codice dell'app. Questa opzione va utilizzata quando non è presente un'immagine oppure l'immagine non è disponibile (ad esempio perché il dispositivo è offline). If you have sizing issues when using the full-screen template, see *My image does not fit exactly into the space provided by the template* in [Troubleshooting in-app messaging](/help/using/in-app-messaging/t-in-app-message/in-apps-ts.md).


1. Compila i campi nella sezione **[!UICONTROL Testo]:**

   * **[!UICONTROL Intestazione]**

      Inserisci il testo per l'intestazione del messaggio.

   * **[!UICONTROL Contenuto]**

      Inserisci il testo per il contenuto del messaggio.

1. Compila i campi nella sezione **[!UICONTROL Pulsanti]:**

   * **[!UICONTROL Pulsante Click-through]**

      Etichetta per il pulsante di **[!UICONTROL click-through].** Toccando questo pulsante viene visualizzato un click-through con esito positivo. L'utente viene reindirizzato alla destinazione.

   * **[!UICONTROL Destinazione]**

      Seleziona una destinazione specifica, ad esempio un collegamento web, profondo o ibrido, alla quale indirizzare l'utente che fa clic sul messaggio. L'URL di reindirizzamento per un click-through con esisto positivo.

      Questo URL potrebbe contenere le seguenti informazioni:

      * `{userId}`, che viene sostituito con l'identificatore utente o lasciato vuoto quando l'identificatore utente non è impostato.
      * `{trackingId}`, che viene sostituito con l'aid (correlato al *cookie s_ vi* ).
      * `{messageId}`, che viene sostituito con l'ID univoco per il messaggio in-app.
      * `{lifetimeValue}`, che viene sostituito con il valore del ciclo di vita o con 0 se non esiste alcun valore del ciclo di vita.
      Ecco un esempio di tracciamento dell'ID utente: `https://www.mysite.com?uid={userId}`.

      If the click-through URL uses `https://` or `https://`, the URL opens in the device browser outside the app. In caso contrario, ogni piattaforma supporta schemi che consentono di aprire l'app o farvi riferimento se l'app è stata sviluppata per supportare lo schema personalizzato.

      >[!TIP]
      >
      >When you use the **[!UICONTROL Web Link]** or **[!UICONTROL Custom Link]** destination types, the destination type is not tracked. Solo i **[!UICONTROL collegamenti profondi]vengono tracciati.** For more information, see [Destinations](/help/using/acquisition-main/c-create-destinations.md).


1. (Facoltativo) Per verificare il layout del messaggio, fai clic sulle icone seguenti:

   * **[!UICONTROL Riepilogo]** nasconde il riquadro di anteprima.

      Click ![preview](assets/icon_preview.png) to redisplay the preview pane.

   * **[!UICONTROL Modificare l'orientamento]**

      To change the orientation of the preview from portrait to landscape mode, click ![orientation](assets/icon_orientation.png). Per gli orologi, l'orientamento cambia da rotondo a quadrante quadrato.

   * **[!UICONTROL Anteprima sull'orologio di un utente]**

      Per visualizzare l'anteprima del messaggio così come apparirà sull'orologio di un utente, fai clic sull'icona ![del visualizzatore](assets/icon_watch.png).

   * **[!UICONTROL Anteprima sul cellulare di un utente]**

      Per visualizzare l'anteprima del messaggio così come apparirà sul cellulare di un utente, fai clic ![sull'icona](assets/icon_phone.png)del telefono.

   * **[!UICONTROL Anteprima sul tablet di un utente]**

      Per visualizzare l'anteprima del messaggio nel tablet di un utente, fai clic ![sull'icona tablet](assets/icon_tablet.png).

      Nella parte inferiore del riquadro di anteprima puoi visualizzare una descrizione del pubblico che hai selezionato nel passaggi precedente. Puoi anche visualizzare, nella parte inferiore del riquadro di anteprima, una descrizione del pubblico che hai selezionato nel passaggio precedente.

1. Configura le [opzioni di pianificazione](/help/using/in-app-messaging/t-in-app-message/c-schedule-in-app-message.md).
