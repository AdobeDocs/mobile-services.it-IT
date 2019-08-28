---
description: 'Puoi definire e configurare le opzioni relative al pubblico per i messaggi push: intervalli di date, segmenti di Analytics e segmenti personalizzati.'
keywords: dispositivi mobili
seo-description: 'Puoi definire e configurare le opzioni relative al pubblico per i messaggi push: intervalli di date, segmenti di Analytics e segmenti personalizzati.'
seo-title: Audience Definire e configurare i segmenti di pubblico per i messaggi push
solution: Marketing Cloud, Analytics
title: Audience Definire e configurare i segmenti di pubblico per i messaggi push
topic: Metrics (Metriche)
uuid: efd 410 e 7-3 b 6 c -4 cf 4-a 26 f-b 11688 adc 491
translation-type: tm+mt
source-git-commit: f28ea0db13b8d8f209d7521d1f61f1c290e688aa

---


# Pubblico: messaggi push{#audience-define-and-configure-audience-segments-for-push-messages}

Puoi definire e configurare le opzioni relative al pubblico per i messaggi push: intervalli di date, segmenti di Analytics e segmenti personalizzati.

## Define audience segments {#section_7C4D2393CF7441959FE2381A02867CAC}

Quando si crea un segmento di pubblico per i messaggi push, esso può includere utenti di una o più app perché le suite di rapporti o le suite di rapporti virtuali potrebbero contenere dati provenienti da una o più app. Per maggiori informazioni sulle suite di rapporti virtuali, vedi [Suite di rapporti virtuali](/help/using/manage-apps/c-mob-vrs.md).

In Adobe Mobile Services, gli addetti al marketing possono inviare dati push a una sola app per piattaforma. Se tentano di inviare dati a segmenti che contengono utenti di più app, un avviso segnala che se procedono si possono verificare seri errori di push e il potenziale inserimento in blacklist degli utenti. Se incontri un errore di invio push, vedi *Risoluzione degli errori di invio push* in [Risoluzione dei problemi dei messaggi push](/help/using/in-app-messaging/t-create-push-message/c-schedule-push-message.md).

Per utilizzare i dati di Audience Manager nelle tue definizioni di segmenti, vedi [Audience Analytics](https://docs-author-stg.corp.adobe.com/content/help/en/analytics/integration/audience-analytics/mc-audiences-aam.html).

>[!IMPORTANT]
>
>If app users are blacklisted, marketers can **never** send push messages to those affected users again.

Se selezioni un segmento di pubblico che contiene utenti in più app, potresti visualizzare il seguente avviso:

![multiple app name](assets/multiple_appname.png)

The app name is based on the pared down version of the appId, which is automatically sent to Adobe Analytics by the Mobile Services SDK in the `<app name> <version number> (<bundle id>)` format.

>[!TIP]
>
>Il numero di versione è facoltativo.

Vengono rimossi fino a 6 serie di numeri dalla versione e fino a 5 serie di numeri dall'ID bundle.

Ad esempio:

* `Bea[rd]cons 1.0 (123)` apparirà come `Bea[rd]cons`
* `Bea[rd]cons 1.2 (1.2)` apparirà come `Bea[rd]cons`
* `Bea[rd]cons 1.2.3.4.5.6.7 (1111)` apparirà come `Bea[rd]cons .7`
* `Bea[rd]cons 1.2.3. (1.2.3.4.5.6)` apparirà come `Bea[rd]cons (.6)`

Per continuare a inviare il messaggio push alle app elencate, seleziona la casella di controllo **Sì, desidero procedere.** e fai clic su **[!UICONTROL Invia]**.

## Procedure consigliate

Seguono alcune best practice per ricordare:

* Per non fare confusione, **evita** di definire suite di rapporti virtuali per app mobili che contengono dati di più app.
* Utilizza un ID app univoco per un segmento di pubblico **ogni** volta che vuoi inviare un messaggio push.
In questo modo, le notifiche push vengono inviate a un segmento di pubblico che appartiene a **una sola** app.

### Esempi

Ecco alcuni esempi per aiutarti a comprendere come si definiscono correttamente i segmenti:

**Procedura corretta**: l'addetto al marketing fornisce dei certificati push per le versioni iOS e Android di un'app, ad esempio Adobe Photoshop. Potrebbe inviare una notifica push a un segmento di utenti di entrambe le piattaforme.

**Procedura non corretta**: l'addetto al marketing fornisce certificati push per le versioni iOS e Android di un'app, ad esempio Adobe Photoshop. Se crea e invia una notifica a un segmento di *tutti gli utenti attivi degli ultimi 30 giorni*, solo gli utenti dell'app Adobe Photoshop iOS e Android ricevono la notifica push, mentre tutti gli utenti dell'app Adobe Illustrator iOS e Android verranno inseriti in blacklist. Per un esempio più dettagliato, vedi *Risoluzione degli errori relativi ai messaggi push* in [Risoluzione dei problemi dei messaggi push](/help/using/in-app-messaging/t-create-push-message/c-troubleshooting-push-messaging.md).

## Configure audience segments {#section_A92C60885A30421B8150820EC1CCBF13}

1. Vai alla pagina Pubblico per un nuovo messaggio push.

   For more information, see [Create a push message](/help/using/in-app-messaging/t-create-push-message/t-create-push-message.md).

   As you configure the audience options, remember the following **important** information:

   * Il **[!UICONTROL Pubblico con consenso stimato]** rappresenta il numero di dispositivi che corrispondono al segmento di Adobe Analytics **e** al numero di dispositivi con consenso.

      Puoi anche visualizzare una stima del numero di utenti dei segmenti che hai selezionato che hanno acconsentito alla ricezione dei messaggi e quindi riceveranno il messaggio push. Sotto la stima viene indicato il numero totale di utenti dell'app, che abbiano prestato o meno il consenso.

   * Il **[!UICONTROL Totale]è il numero di dispositivi che corrispondono al segmento di Adobe Analytics.**

   * Push messages are sent to the devices that are part of a defined Adobe Analytics segment **and** that have opted-in for push messages.

      Questo significa che l'SDK ha inviato un valore `True` per l'eVar Messaggio push di consenso.

   * Anche se il dispositivo ha un token dispositivo valido, a meno che Adobe Analytics non abbia impostato il flag di questo tipo, il messaggio non viene inviato al dispositivo.

   * Per ulteriori informazioni sulla risoluzione dei problemi dei messaggi push, vedi:

      * [Messaggi push in iOS](https://docs.adobe.com/content/help/en/mobile-services/ios/messaging-ios/push-messaging/push-messaging.html)

      * [Messaggi push in Android](https://docs.adobe.com/content/help/en/mobile-services/android/messaging-android/push-messaging/push-messaging.html)

1. Digita le informazioni nei campi seguenti:

   * **[!UICONTROL Periodo]**

      Specifica l'intervallo di tempo da utilizzare per il pubblico stimato. Dall'elenco a discesa **[!UICONTROL Periodo], seleziona un'opzione:**

   * **[!UICONTROL Ultimo/i:]** seleziona un periodo di tempo relativo (ad esempio gli ultimi 7, 30 o 60 giorni) dal momento in cui è pianificato il push del messaggio.

      Per esempio, se selezioni gli ultimi 30 giorni e pianifichi l'invio in push del messaggio per il 31 ottobre, il pubblico stimato corrisponderebbe al numero di utenti che hanno acconsentito alla ricezione dei messaggi push nei 30 giorni precedenti al 31 ottobre.

   * **[!UICONTROL Intervallo statico:]** seleziona un intervallo di tempo statico scegliendo la data di inizio e la data di fine per il pubblico stimato.

      Rifacendoci all'esempio precedente, se selezioni un intervallo di date che va dal 1° al 15 ottobre ma pianifichi l'invio in push del messaggio per il 31 ottobre, il pubblico stimato corrisponderebbe al numero di utenti che hanno acconsentito alla ricezione dei messaggi push nell'intervallo di tempo statico specificato (dal 1° al 15 ottobre).

   * **[!UICONTROL Segmenti di Analytics]**

      Seleziona un segmento Adobe Analytics esistente dall'elenco a discesa. For more information, see [Build segments](https://docs.adobe.com/content/help/en/analytics/components/segmentation/segmentation-workflow/seg-build.html).

   * **[!UICONTROL Segmenti personalizzati]**

      Select a metric or variable from the drop-down list (for example, **[!UICONTROL Days Since Last Use]** or **[!UICONTROL Point of Interest]**) and configure the filter as desired. Ad esempio, il segmento personalizzato seguente ha come target gli utenti che hanno uno smartphone iOS e si trovano nell'area della California (Stati Uniti).
   >[!IMPORTANT]
   >
   >In the **[!UICONTROL Create Audience]** section, if you click **[!UICONTROL And]**, a dialog box appears that reminds you to ensure that each app that is listed **must** have a valid certificate. If you clicked **[!UICONTROL Or]**, the default dialog box appears. For more information about valid certificates and report suites, see [Virtual report suites](/help/using/manage-apps/c-mob-vrs.md).
