---
description: 'Puoi configurare le opzioni relative all''esperienza dei messaggi push standard e potenziati: nome, testo del messaggio e opzioni di destinazione. Puoi anche configurare opzioni avanzate quali quelle relative al payload e le opzioni personalizzate per i dispositivi iOS.'
keywords: dispositivi mobili
seo-description: 'Puoi configurare le opzioni relative all''esperienza dei messaggi push standard e potenziati: nome, testo del messaggio e opzioni di destinazione. Puoi anche configurare opzioni avanzate quali quelle relative al payload e le opzioni personalizzate per i dispositivi iOS.'
seo-title: Messaggio push esperienza
solution: Marketing Cloud, Analytics
title: Messaggio push esperienza
topic: Metrics (Metriche)
uuid: 1 a 8 baf 3 e -9 fea -452 c-b 0 fc -4 ac 8 ac 270861
translation-type: tm+mt
source-git-commit: e9691f9cbeadd171948aa752b27a014c3ab254d6

---


# Experience: push message {#experience-push-message}

Puoi configurare le opzioni relative all'esperienza dei messaggi push standard e potenziati: nome, testo del messaggio e opzioni di destinazione. Puoi anche configurare opzioni avanzate quali quelle relative al payload e le opzioni personalizzate per i dispositivi iOS.

1. Nella pagina Pubblico di un nuovo messaggio push, fai clic **[!UICONTROL su Esperienza]**.

   ![esperienza messaggio push, schermata](assets/experience-push-message.png)

1. Specifica un nome per il messaggio.
1. Compila i seguenti campi nella sezione **[!UICONTROL Messaggio]:**

   * **[!UICONTROL Contenuto]**

      Specifica il testo del messaggio. Puoi immettere fino a 140 caratteri.

   * **[!UICONTROL URL contenuto multimediale]**

      Inserisci l'URL del file multimediale che intendi utilizzare nel messaggio di notifica push. Per requisiti per l'utilizzo delle notifiche push potenziate, vedi *Requisiti per notifiche push potenziate* di seguito.

      >[!IMPORTANT]
      >
      >Per visualizzare un'immagine o un video in una notifica push, tieni presente quanto segue:
      > * I dati `attachment-url` vengono gestiti dal payload push.
      > * L'URL del contenuto multimediale deve essere in grado di gestire i picchi di richieste.


   * **[!UICONTROL Destinazione]**

      Seleziona una destinazione specifica, ad esempio un collegamento web, profondo o ibrido, alla quale indirizzare l'utente che fa clic sul messaggio. For more information, see [Destinations](/help/using/acquisition-main/c-create-destinations.md).

      >[!TIP]
      >
      >When you use the * **[!UICONTROL Web Link]** or **[!UICONTROL Custom Link]** destination types, the destination type is not tracked. Solo i **[!UICONTROL collegamenti profondi]vengono tracciati.**

## Requisiti per notifiche push potenziate

Di seguito sono illustrati i requisiti per l'invio di notifiche push potenziate:

* **Versioni supportate**

   Le notifiche push potenziate sono supportate nelle seguenti versioni:
   * Android 4.1.0 o successivo
   * iOS 10 o successivo

      >[!IMPORTANT]
      >
      >Considerazioni da ricordare:
      >* I messaggi push potenziati inviati alle versioni precedenti continueranno a essere inviati, ma viene visualizzato solo il testo.
      >* Al momento il supporto per gli orologi non è disponibile.


* **Formati file**

   Sono supportati i formati file seguenti:
   * Immagini: JPG e PNG
   * Animazioni (solo iOS): GIF
   * Video (solo iOS): MP4

* **Formati URL**
   * Solo HTTPS

* **Dimensioni**
   * Le immagini devono essere in formato 2:1 oppure vengono ritagliate.

Per ulteriori informazioni sulla configurazione delle notifiche push potenziate, vedi:

* [Ricevere notifiche push in Android](/help/android/messaging-main/push-messaging/c-set-up-rich-push-notif-android.md)
* [Ricevere notifiche push potenziate in iOS](/help/ios/messaging-main/push-messaging/c-set-up-rich-push-notif-ios.md)

Per configurare un messaggio push nella pagina Esperienza:

1. **(Facoltativo**) Fai clic sul **[!UICONTROL collegamento Mostra opzioni]** avanzate per configurare altre opzioni:

   * **[!UICONTROL Payload: Dati]**

      Specifica un payload push personalizzato in JSON da inviare all'app tramite una notifica push o locale. Il limite per Android e iOS è di 4 KB.

   * **[!UICONTROL Opzioni Apple: Categoria]**

      Specifica una categoria per le notifiche push e locali. Per maggiori informazioni, vedi [Managing Your App's Notification Support](https://developer.apple.com/library/content/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/SupportingNotificationsinYourApp.html#//apple_ref/doc/uid/TP40008194-CH4-SW9) nella *iOS Developer Library*.

   * **[!UICONTROL Opzioni Apple: Suono]**

      Specifica il nome del file audio da riprodurre nel pacchetto dell'app. Se non viene impostato, viene utilizzato un avviso sonoro predefinito. Per maggiori informazioni, vedi [Managing Your App's Notificaton Support](https://developer.apple.com/library/content/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/SupportingNotificationsinYourApp.html#//apple_ref/doc/uid/TP40008194-CH4-SW10) nella *iOS Developer Library*.

   * **[!UICONTROL Opzioni Apple: Contenuto disponibile]**

      Seleziona questa opzione affinché, all'arrivo del messaggio, iOS riattivi l'app in background e le consenta di eseguire un codice in base al payload del messaggio. Per maggiori informazioni, vedi [Apple Push Notification Service](https://developer.apple.com/library/content/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/APNSOverview.html#//apple_ref/doc/uid/TP40008194-CH8-SW1) nella *iOS Developer Library*.

1. (Facoltativo) Per verificare il layout del messaggio, fai clic sulle icone seguenti:

   * **[! UICONTROL x Summary}**

      Nasconde il riquadro di anteprima. Fate clic ![su Anteprima](assets/icon_preview.png) per visualizzare di nuovo il riquadro di anteprima.

   * **[!UICONTROL Modificare l'orientamento]**

      To change the orientation of the preview from portrait to landscape mode, click ![orientation](assets/icon_orientation.png). Per gli orologi, l'orientamento cambia da quadrante rotondo a quadrante quadrato.

   * **[!UICONTROL Anteprima sull'orologio di un utente]**

      Per visualizzare l'anteprima del messaggio così come apparirà sugli orologi di un utente, fai clic sull'icona ![dell'orologio](assets/icon_watch.png).

   * **[!UICONTROL Anteprima sul cellulare di un utente]**

      Per visualizzare l'anteprima del messaggio così come apparirà sui telefoni cellulari di un utente, fai clic ![sull'icona Telefono](assets/icon_phone.png).

   * **[!UICONTROL Anteprima sul tablet di un utente]**

      Per visualizzare l'anteprima del messaggio nel tablet di un utente, fai clic ![sull'icona tablet](assets/icon_tablet.png).
   Nella parte inferiore del riquadro di anteprima puoi visualizzare una descrizione del pubblico che hai selezionato nel passaggi precedente.

1. **(Facoltativo**) Fai clic su **[!UICONTROL Prova per]** inviare il messaggio a dispositivi specificati a scopo di test.
1. Seleziona il servizio e digita i token di push per almeno uno dei dispositivi ai quali vuoi inviare il messaggio push.

   Per inviare il messaggio a più dispositivi, specifica i vari token in un elenco di voci separate da virgole.

1. Configura le opzioni di pianificazione per il messaggio.

   Per ulteriori informazioni, consulta [Pianificazione: messaggio push](/help/using/in-app-messaging/t-create-push-message/c-schedule-push-message.md).
