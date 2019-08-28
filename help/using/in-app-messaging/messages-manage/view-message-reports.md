---
description: Puoi visualizzare i rapporti sui messaggi in-app e push.
keywords: dispositivi mobili
seo-description: Puoi visualizzare i rapporti sui messaggi in-app e push.
seo-title: Visualizzazione dei rapporti sui messaggi
solution: Marketing Cloud, Analytics
title: Visualizzazione dei rapporti sui messaggi
topic: Metrics (Metriche)
uuid: 0 ac 73 a 81-388 f -4 dfd -84 d 5-21 b 8 db 4 b 8 c 83
translation-type: tm+mt
source-git-commit: 44f531ad140827d563255fad197811185c5337c9

---


# View message reports{#view-message-reports}

Puoi visualizzare i rapporti sui messaggi in-app e push.

1. Click ![report icon](assets/icon_report.png) in the **[!UICONTROL Report]** column for a message.
1. **(Facoltativo**) Crea un filtro fisso per il rapporto o cambia il periodo di tempo facendo clic sull'icona **[!UICONTROL Calendario]** .

   Per ulteriori informazioni sulla creazione di un filtro fisso, consultate [Aggiungere un filtro fisso](/help/using/usage/reports-customize/t-sticky-filter.md).

>[!TIP]
>
>A seconda del tipo di messaggio visualizzato, il rapporto potrebbe variare.

## Messaggi in-app {#section_90B79BA58E8141F78538C187EB1BF8C7}

Se visualizzi i rapporti relativi a un messaggio in-app, il rapporto è simile a quello dell'illustrazione seguente:

![report, messaggio](assets/report_message.png)

### Metriche dei messaggi in-app

Elenco delle metriche disponibili per i messaggi in-app:

* **[!UICONTROL Impression]**, quando viene attivato un messaggio.

* **[!UICONTROL Fate clic su di esso]** quando un utente preme il **[!UICONTROL pulsante Click-through]** su un avviso o su un messaggio a schermo intero e quando un utente apre l'app da una notifica locale.

* **[!UICONTROL Annulla]**, quando un utente preme **[!UICONTROL il]** pulsante Annulla su un avviso o su un messaggio a schermo intero.

* **[!UICONTROL Tasso di coinvolgimento]**, una metrica calcolata da Adobe Analytics ed è il risultato del numero di click-through diviso per il numero di impression.

## Push messages {#section_BEAFD858CA194185B6F88903446058E9}

Se visualizzi i rapporti relativi a un messaggio push, il rapporto è simile a quello dell'illustrazione seguente:

![messaggio push](assets/report_message_push.png)

Il grafico in alto mostra il numero di utenti che hanno aperto il messaggio.

### Metriche dei messaggi push

Elenco delle metriche disponibili per i messaggi push:

* **[!UICONTROL Tempo]**

   L'ora in cui il messaggio è stato inviato ai dispositivi da Mobile Services.

* **[!UICONTROL Stato]**

   Lo stato del messaggio e gli stati disponibili sono:

   * **[!UICONTROL Annullato]**
   * **[!UICONTROL Pianificato]**
   * **[!UICONTROL Esecuzione]**
   * **[!UICONTROL Eseguito]**

* **[!UICONTROL Pubblicato]**

   Il numero di token dispositivo inviati con successo ad Apple Push Notification Service/Firebase Cloud Messaging (APNS/FCM) per l'invio del messaggio ai dispositivi degli utenti.

* **[!UICONTROL Non riuscito]**

   Il numero di token dispositivo non inviati con successo a APNS/FCM. Alcuni motivi possibili per gli errori:

   * Un pushID non valido

   * La piattaforma push (APNS, FCM, ecc.) specificata come destinazione del push non esiste per l'applicazione del processo. Ad esempio, la piattaforma potrebbe raccogliere token di push iOS senza che sia stato configurato il servizio APNS.

   * Il mancato invio di un messaggio può essere dovuto alla configurazione non corretta del servizio push o alla temporanea indisponibilità del sistema Mobile Services.
   >[!IMPORTANT]
   >
   >Se si verificano numerosi tentativi non riusciti, controlla la configurazione dei servizi push. Se sembrano configurati correttamente, contatta l'assistenza clienti Adobe.

* **[!UICONTROL In lista nera]**

   Il numero di token dispositivo che non sono più validi per l'invio a APNS o FCM. Solitamente indicano che l'app è stata disinstallata dal dispositivo oppure che l'utente ha modificato le proprie opzioni di consenso alla ricezione dei messaggi. Android e iOS si comportano diversamente quando dei token vengono considerati in lista nera. I token Android figurano immediatamente nel conteggio dei token in lista nera. I token iOS inizialmente vengono visualizzati come pubblicati ma, in base al feedback ricevuto da APNS, vengono poi indicati come in lista nera nei messaggi successivi.
