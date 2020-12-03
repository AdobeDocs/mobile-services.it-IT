---
description: 'Puoi configurare le opzioni relative all’esperienza dei messaggi push standard e potenziati: nome, testo del messaggio e opzioni di destinazione. Puoi anche configurare varie opzioni avanzate, comprese le opzioni di payload e quelle personalizzate per i dispositivi iOS.'
keywords: mobile
seo-description: 'Puoi configurare le opzioni relative all’esperienza dei messaggi push standard e potenziati: nome, testo del messaggio e opzioni di destinazione. Puoi anche configurare varie opzioni avanzate, comprese le opzioni di payload e quelle personalizzate per i dispositivi iOS.'
seo-title: Esperienza - Messaggio push
solution: Experience Cloud,Analytics
title: Esperienza - Messaggio push
topic: Metrics
uuid: 1a8baf3e-9fea-452c-b0fc-4ba8ac270861
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '799'
ht-degree: 100%

---


# Esperienza: messaggio push {#experience-push-message}

Puoi configurare le opzioni relative all’esperienza dei messaggi push standard e potenziati: nome, testo del messaggio e opzioni di destinazione. Puoi anche configurare varie opzioni avanzate, comprese le opzioni di payload e quelle personalizzate per i dispositivi iOS.

1. Nella pagina Pubblico per un nuovo messaggio push, fai clic su **[!UICONTROL Esperienza]**.

   ![schermata messaggio push esperienza](assets/experience-push-message.png)

1. Specifica un nome per il messaggio.
1. Compila i seguenti campi nella sezione **[!UICONTROL Messaggio]**:

   * **[!UICONTROL Contenuto]**

      Specifica il testo del messaggio. Il testo può contenere un massimo di 140 caratteri.

   * **[!UICONTROL URL file multimediale]**

      Inserisci l’URL del file multimediale che intendi utilizzare nel messaggio di notifica push. Per i requisiti per l’utilizzo di notifiche push potenziate, consulta *Requisiti per le notifiche push composite* di seguito.

      >[!IMPORTANT]
      >
      >Per visualizzare un’immagine o un video in una notifica push, tieni presente quanto segue:
      > * I dati `attachment-url` vengono gestiti dal payload push.
      > * L’URL del contenuto multimediale deve essere in grado di gestire i picchi di richieste.


   * **[!UICONTROL Destinazione]**

      Seleziona una destinazione specifica, ad esempio un collegamento web, profondo o ibrido, alla quale indirizzare l’utente che fa clic sul messaggio. Per ulteriori informazioni, vedi [Destinazioni](/help/using/acquisition-main/c-create-destinations.md).

      >[!TIP]
      >
      >I tipi di destinazione * **[!UICONTROL Collegamento web]** o **[!UICONTROL Collegamento personalizzato]** non vengono tracciati. Solo i **[!UICONTROL collegamenti profondi]** vengono tracciati.

## Requisiti per le notifiche push potenziate

Di seguito sono riportati i requisiti per l’invio di notifiche push potenziate:

* **Versioni supportate**

   Le notifiche push potenziate sono supportate nelle seguenti versioni:
   * Android 4.1.0 o versione successiva
   * iOS 10 o versione successiva

      >[!IMPORTANT]
      >
      >Considerazioni da ricordare:
      >* I messaggi push potenziati inviati a versioni precedenti vengono comunque inviati, ma risulterà visibile solo il testo.
      >* Al momento, gli orologi non sono supportati.


* **Formati di file**

   Di seguito sono elencati i formati di file supportati:
   * Immagini: JPG e PNG
   * Animazioni (solo iOS): GIF
   * Video (solo iOS): MP4

* **Formati URL**
   * Solo HTTPS

* **Ridimensionamento**
   * Le immagini devono essere in formato 2:1, altrimenti verranno ritagliate.

Per ulteriori informazioni sulla configurazione delle notifiche push potenziate, vedi:

* [Ricevere notifiche push in Android](/help/android/messaging-main/push-messaging/c-set-up-rich-push-notif-android.md)
* [Ricevere notifiche push potenziate in iOS](/help/ios/messaging-main/push-messaging/c-set-up-rich-push-notif-ios.md)

Per configurare un messaggio push nella pagina Esperienza:

1. (**Facoltativo**) Fai clic sul collegamento **[!UICONTROL Mostra opzioni avanzate]** per configurare altre opzioni:

   * **[!UICONTROL Payload: Dati]**

      Specifica un payload push personalizzato in JSON da inviare all’app tramite una notifica push o locale. Il limite per Android e iOS è di 4 KB.

   * **[!UICONTROL Opzioni Apple: Categoria]**

      Specifica una categoria per le notifiche push e locali. Per maggiori informazioni, consulta [Managing Your App’s Notification Support](https://developer.apple.com/library/content/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/SupportingNotificationsinYourApp.html#//apple_ref/doc/uid/TP40008194-CH4-SW9) nella *iOS Developer Library*.

   * **[!UICONTROL Opzioni Apple: Suono]**

      Specifica il nome del file audio da riprodurre nel pacchetto dell’app. Se non viene impostato, viene utilizzato un avviso sonoro predefinito. Per maggiori informazioni, consulta [Managing Your App’s Notification Support](https://developer.apple.com/library/content/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/SupportingNotificationsinYourApp.html#//apple_ref/doc/uid/TP40008194-CH4-SW10) nella *iOS Developer Library*.

   * **[!UICONTROL Opzioni Apple: Contenuto disponibile]**

      Seleziona questa opzione affinché, all’arrivo del messaggio, iOS riattivi l’app in background e le consenta di eseguire un codice in base al payload del messaggio. Per maggiori informazioni, consulta [Apple Push Notification Service](https://developer.apple.com/library/content/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/APNSOverview.html#//apple_ref/doc/uid/TP40008194-CH8-SW1) nella *iOS Developer Library*.

1. (Facoltativo) Per verificare il layout del messaggio, fai clic sulle icone seguenti:

   * **[!UICONTROL x Riepilogo]**

      Nasconde il riquadro di anteprima. Fai clic su ![Anteprima](assets/icon_preview.png) per visualizzare nuovamente il riquadro di anteprima.

   * **[!UICONTROL Modificare l’orientamento]**

      Per cambiare l’orientamento dell’anteprima da verticale a orizzontale, fai clic su ![orientamento](assets/icon_orientation.png). Per gli orologi, l’orientamento cambia da quadrante rotondo a quadrante quadrato.

   * **[!UICONTROL Anteprima sull’orologio di un utente]**

      Per visualizzare l’anteprima del messaggio così come verrà visualizzata sugli orologi degli utenti, fai clic sull’icona dell’![orologio](assets/icon_watch.png).

   * **[!UICONTROL Anteprima sul cellulare di un utente]**

      Per visualizzare l’anteprima del messaggio così come verrà visualizzata sul telefono cellulare di un utente, fai clic sull’icona del ![telefono](assets/icon_phone.png).

   * **[!UICONTROL Anteprima sul tablet di un utente]**

      Per visualizzare l’anteprima del messaggio sul tablet di un utente, fai clic sull’icona del ![tablet](assets/icon_tablet.png).
   Nella parte inferiore del riquadro di anteprima puoi visualizzare una descrizione del pubblico che hai selezionato nel passaggio precedente.

1. (**Facoltativo**) Fai clic su **[!UICONTROL Prova]** per inviare in push il messaggio a dispositivi specifici a scopo di test.
1. Seleziona il servizio e digita i token push per almeno un dispositivo al quale vuoi inviare il messaggio push.

   Per inviare il messaggio push a più dispositivi, specifica i token in un elenco di voci separate da virgola.

1. Configura le opzioni di pianificazione per il messaggio.

   Per ulteriori informazioni, consulta [Pianificazione: messaggio push](/help/using/in-app-messaging/t-create-push-message/c-schedule-push-message.md).
