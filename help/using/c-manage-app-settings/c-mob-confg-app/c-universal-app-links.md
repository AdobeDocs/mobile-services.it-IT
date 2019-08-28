---
description: Collegamenti universali (iOS) e collegamenti app (Android) consentono di connettersi ai collegamenti profondi nelle app iOS o Android.
keywords: dispositivi mobili
seo-description: Collegamenti universali (iOS) e collegamenti app (Android) consentono di connettersi ai collegamenti profondi nelle app iOS o Android.
seo-title: Collegamenti universali Apple e collegamenti app Android
solution: Marketing Cloud, Analytics
title: Collegamenti universali Apple e collegamenti app Android
topic: Metrics (Metriche)
uuid: 8 d 6441 dc -4307-4454-95 ea-d 77 ec 796 f 918
translation-type: tm+mt
source-git-commit: e65add089499f728827321e96e439f04ebb19a73

---


# Collegamenti universali Apple e collegamenti app Android{#universal-links-and-app-links}

Collegamenti universali (iOS) e collegamenti app (Android) consentono di connettersi ai collegamenti profondi nelle app iOS o Android.

>[!IMPORTANT]
>
>A partire da iOS 9.2, il collegamento diretto non è supportato. Devi usare i collegamenti universali Apple per collegamenti profondi all'app o al sito Web.

## Universal Links {#section_F8147944679A42E59CF4FD8814E5EF12}

I collegamenti universali consentono di connettersi a collegamenti profondi nell'app iOS e sono supportati in iOS 9.2 o versione successiva. Quando si accede a un collegamento universale, iOS reindirizza il collegamento direttamente al collegamento di deeplink nell'app. Se l'app non è installata, viene aperto un URL per il sito Web in un browser. Per ulteriori informazioni sui collegamenti universali, consulta [Supporto dei collegamenti universali](https://developer.apple.com/library/content/documentation/General/Conceptual/AppSearch/UniversalLinks.html).

## Collegamenti app

I collegamenti app consentono di connettersi a collegamenti profondi nella tua app Android ed è supportato in Android 6.0 o versione successiva. Quando si accede a un collegamento app, Android reindirizza il collegamento direttamente al collegamento di deeplink nell'app. Se l'app non è installata, viene aperto un URL per il sito Web in un browser. For more information about App Links, see the [Handling Android App Links](https://developer.android.com/training/app-links/index.html).

## Creare un collegamento di marketing utilizzando un collegamento universale o app {#section_609ADEFFB9B441C4A8C45E936D0DC859}

Puoi creare un collegamento marketing che usa un collegamento universale o app.

### Configurare un collegamento universale

1. Per configurare i collegamenti universali nell'app iOS, vai alla [gestione dei collegamenti universali in Apple](https://developer.apple.com/documentation/uikit/inter-process_communication/allowing_apps_and_websites_to_link_to_your_content/handling_universal_links).

2. In Adobe Mobile Services, imposta i documenti di associazione dei siti:

   a. Nella home page di Mobile Services, seleziona l'app per la quale vuoi impostare i collegamenti universali.

   b. Click **[!UICONTROL Manage App Settings]**.

   c. Assicurati che l'app iOS che gestisce i collegamenti universali sia aggiunta alla **[!UICONTROL sezione Aggiungi app]** App store.

   >[!TIP]
   >
   >Se la **[!UICONTROL sezione Aggiungi app]** App store non viene visualizzata, fai clic sul **[!UICONTROL collegamento Aggiungi app]** App store.

   d. Nella sezione Opzioni collegamenti **[!UICONTROL universali e]** collegamenti app, seleziona un'app iOS e digita l'ID app.

   f. Fate clic **[!UICONTROL su Salva]**.

   Devi fornire almeno una selezione app iOS e un ID app, oppure riceverai un errore.

   >[!IMPORTANT]
   >
   >Per aggiornare i documenti, fai clic su Aggiorna nella sezione delle opzioni dei collegamenti universali e collegamenti app. However, when you click **[!UICONTROL Update]**, a warning notifies you that all Universal Links or App Links that you created in the past will be affected.

### Usare un collegamento universale

1. In Adobe Mobile Services, crea un collegamento marketing che usa collegamenti universali:

   a. Select the app from the Mobile Services home page, click **[!UICONTROL Acquisition]** &gt; **[!UICONTROL Marketing Link Builder]**.

   b. Fai clic su **[!UICONTROL Crea nuovo]**.

   c. Under **[!UICONTROL Marketing Link Options]**, select **[!UICONTROL Use Universal Links or App Links]**.

   d. Se hai configurato i documenti associazione siti nella sezione *Configurazione dei documenti associazione siti nella sezione Adobe Mobile Services* qui sopra, questa opzione è selezionata per impostazione predefinita.

   Se non hai configurato i documenti, l'opzione **[!UICONTROL Usa collegamenti universali o collegamenti]** app è disabilitata e **[!UICONTROL l'opzione Usa interstiziali]** è selezionata per impostazione predefinita.

   e. Se è selezionata l'opzione **[!UICONTROL Usa collegamenti universali o collegamenti]** app, viene **[!UICONTROL visualizzato]** il campo Percorso personalizzato.

   che permette agli utenti di definire l'URL dopo il dominio con eventuali parametri di query. Ad esempio, se immetti `my/universal/link?os=9.2`, diventa l'URL completo collegamento marketing `https://[marketing link domain]/my/universal/link?[AMS default query parameters]&os=9.2`.

   f. Fai clic sulla scheda **[!UICONTROL Decisioni]** e configura la struttura decisionale.

   h. Se l'app iOS è installata, l'app gestisce il collegamento profondo con la sua logica. La destinazione finale funge solo da fallback quando l'app non è installata. Poiché l'app non è installata, la destinazione finale può essere solo un collegamento Web o un app store.

   i. Fai clic **[!UICONTROL su Salva]**.

>[!TIP]
>
>Una volta salvato il collegamento Marketing, le Opzioni collegamento marketing non possono essere modificate. poiché non desiderate modificare il comportamento dei collegamenti di marketing già distribuiti.


### Configurare un collegamento app

1. Per configurare i collegamenti app nella tua app Android, vai a [Aggiungi collegamenti app Android](https://developer.android.com/studio/write/app-link-indexing).

1. In Adobe Mobile Services, imposta i documenti di associazione dei siti:

   a. Nella home page di Mobile Services, seleziona l'app per la quale vuoi configurare i collegamenti app.

   b. Click **[!UICONTROL Manage App Settings]**.

   c. Assicurati che l'app Android che gestisce i collegamenti universali o i collegamenti app sia aggiunta alla **[!UICONTROL sezione Aggiungi app]** App store.

   >[!TIP]
   >
   >If this section does not display, click the **[!UICONTROL Add App Store App]** link.

   d. Scorri fino alla **[!UICONTROL sezione Opzioni]** collegamenti universali e collegamenti app.

   e. Fai clic sulla scheda Collegamenti **[!UICONTROL app (Android)]** .

   f. Seleziona un'app Android e digita un'impronta digitale SHA -256.

   g. Fate clic **[!UICONTROL su Salva]**.

   Devi fornire almeno una selezione app Android e un certificato SHA -256, oppure riceverai un errore.

   >[!IMPORTANT]
   >
   >Per aggiornare i documenti, fai clic su **[!UICONTROL Aggiorna]** nella sezione delle **opzioni dei collegamenti universali e collegamenti app[!UICONTROL .]** However, when you click **[!UICONTROL Update]**, a warning notifies you that all Universal Links or App Links that you created in the past will be affected.

### Usare un collegamento app

1. In Adobe Mobile Services, crea un collegamento marketing che usa collegamenti app:

   a. Select the app from the Mobile Services home page, click **[!UICONTROL Acquisition]** &gt; **[!UICONTROL Marketing Link Builder]**.

   b. Fai clic su **[!UICONTROL Crea nuovo]**.

   c. Nella **[!UICONTROL sezione Opzioni]** collegamento di marketing, seleziona **[!UICONTROL Usa collegamenti universali o collegamenti app]**.

   d. Se avete configurato i documenti associazione siti dal passaggio 2, questa opzione è selezionata per impostazione predefinita.

   If not, the **[!UICONTROL Use Universal Links or App Links]** option is disabled, and **[!UICONTROL Use Interstitials]** is selected by default.

   e. Se **[!UICONTROL è selezionata l'opzione Usa collegamenti universali o collegamenti]** app, viene **[!UICONTROL visualizzato]** il campo Percorso personalizzato.

   che permette agli utenti di definire l'URL dopo il dominio con eventuali parametri di query. Ad esempio, se immetti `my/app/link?os=6.0`, diventa l'URL completo collegamento marketing `https://[marketing link domain]/my/app/link?[AMS default query parameters]&os=6.0`.

   f. Fai clic sulla scheda **[!UICONTROL Decisioni]** e configura la struttura decisionale.

   g. Se l'app Android è installata, l'app gestisce il collegamento profondo con la sua logica.

   La destinazione finale viene usata solo come caso di fallback se l'app non è installata. Poiché l'app non è installata, la destinazione finale può essere solo un collegamento Web o un app store.

   h. Fate clic **[!UICONTROL su Salva]**.

>[!TIP]
>
>After a Marketing Link is saved, the **[!UICONTROL Marketing Links Options]** cannot be altered. poiché non desiderate modificare il comportamento dei collegamenti di marketing già distribuiti.

## Utilizzo dei collegamenti di marketing

Ora puoi utilizzare questi collegamenti di marketing nei messaggi e in altre aree dell'app.

>[!IMPORTANT]
>
>Non visualizzerai i conteggi di monitoraggio dei clic con collegamenti universali o collegamenti app e non puoi usare gli interstiziali.

