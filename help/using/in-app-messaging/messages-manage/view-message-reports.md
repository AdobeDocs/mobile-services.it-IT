---
description: Puoi visualizzare i rapporti sui messaggi in-app e push.
keywords: dispositivi mobili
seo-description: Puoi visualizzare i rapporti sui messaggi in-app e push.
seo-title: Visualizzare i rapporti sui messaggi
solution: Marketing Cloud,Analytics
title: Visualizzare i rapporti sui messaggi
topic: Metrics (Metriche)
uuid: 0ac73a81-388f-4dfd-84d5-21b8db4b8c83
translation-type: tm+mt
source-git-commit: 44f531ad140827d563255fad197811185c5337c9

---


# View message reports{#view-message-reports}

Puoi visualizzare i rapporti sui messaggi in-app e push.

1. Click ![report icon](assets/icon_report.png) in the **[!UICONTROL Report]** column for a message.
1. (**Optional**) Create a sticky filter for the report or change the time period by clicking the **[!UICONTROL Calendar]** icon.

   For more information about creating a sticky filter, see Add a sticky filter.[](/help/using/usage/reports-customize/t-sticky-filter.md)

>[!TIP]
>
>Depending on the type of message you are viewing, the report might vary.

## Messaggi in-app {#section_90B79BA58E8141F78538C187EB1BF8C7}

Se visualizzi i rapporti relativi a un messaggio in-app, il rapporto è simile a quello dell'illustrazione seguente:

![report message](assets/report_message.png)

### In-app message metrics

Elenco delle metriche disponibili per i messaggi in-app:

* **[!UICONTROL Impression, when a message is triggered.]**

* **[!UICONTROL Fate clic]** per passare il mouse, quando un utente preme il pulsante **[!UICONTROL Click Through]** su un avviso o un messaggio a schermo intero e quando un utente apre l'app da una notifica locale.

* **[!UICONTROL Annulla]**, quando un utente preme il pulsante **[!UICONTROL Annulla]** su un avviso o un messaggio a schermo intero.

* **[!UICONTROL Engagement Rate, a calculated metric from Adobe Analytics and is the result of the number of click throughs divided by the number of impressions.]**

## Push messages {#section_BEAFD858CA194185B6F88903446058E9}

Se visualizzi i rapporti relativi a un messaggio push, il rapporto è simile a quello dell'illustrazione seguente:

![messaggio push](assets/report_message_push.png)

Il grafico in alto mostra il numero di utenti che hanno aperto il messaggio.

### Metriche messaggio push

Segue un elenco delle metriche disponibili per i messaggi push:

* **[!UICONTROL Tempo]**

   L'ora in cui il messaggio è stato inviato ai dispositivi da Mobile Services.

* **[!UICONTROL Stato]**

   Lo stato del messaggio e gli stati disponibili sono:

   * **[!UICONTROL Annullato]**
   * **[!UICONTROL Scheduled]**
   * **[!UICONTROL Executing]**
   * **[!UICONTROL Eseguito]**

* **[!UICONTROL Pubblicato]**

   Il numero di token dispositivo che sono stati inviati correttamente a Apple Push Notification Service/Firebase Cloud Messaging (APNS/FCM) per l'invio del messaggio ai dispositivi degli utenti.

* **[!UICONTROL Non riuscito]**

   Numero di token dispositivo non inviati correttamente a APNS/FCM. Alcuni possibili motivi di errore:

   * Un pushID non valido

   * La piattaforma push (APNS, FCM e così via) fornita per il push non esiste per l'applicazione del processo. Ad esempio, la piattaforma potrebbe raccogliere token di push iOS senza che sia stato configurato il servizio APNS.

   * Il mancato invio di un messaggio può essere dovuto alla configurazione non corretta del servizio push o alla temporanea indisponibilità del sistema Mobile Services.
   >[!IMPORTANT]
   >
   >Se si verificano numerosi tentativi non riusciti, controlla la configurazione dei servizi push. Se sembrano configurati correttamente, contatta l'assistenza clienti Adobe.

* **[!UICONTROL In lista nera]**

   Il numero di token dispositivo che non sono più validi da inviare a APNS o FCM. Solitamente indicano che l'app è stata disinstallata dal dispositivo oppure che l'utente ha modificato le proprie opzioni di consenso alla ricezione dei messaggi. Android e iOS si comportano diversamente quando dei token vengono considerati in lista nera. I token Android figurano immediatamente nel conteggio dei token in lista nera. I token iOS inizialmente vengono visualizzati come pubblicati ma, in base al feedback ricevuto da APNS, vengono poi indicati come in lista nera nei messaggi successivi.
