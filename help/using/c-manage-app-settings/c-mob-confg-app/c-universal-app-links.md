---
description: Universal Links (iOS) and App Links (Android) allow you to connect to deep links in your iOS or Android apps.
keywords: dispositivi mobili
seo-description: Universal Links (iOS) and App Links (Android) allow you to connect to deep links in your iOS or Android apps.
seo-title: Apple Universal Links and Android App Links
solution: Marketing Cloud,Analytics
title: Apple Universal Links and Android App Links
topic: Metrics (Metriche)
uuid: 8d6441dc-4307-4454-95ea-d77ec796f918
translation-type: tm+mt
source-git-commit: e65add089499f728827321e96e439f04ebb19a73

---


# Collegamenti universali Apple e collegamenti app Android{#universal-links-and-app-links}

Universal Links (iOS) and App Links (Android) allow you to connect to deep links in your iOS or Android apps.

>[!IMPORTANT]
>
>Starting with iOS 9.2, deep linking is not supported. You must use Apple Universal Links for deep linking to your app or website.

## Universal Links {#section_F8147944679A42E59CF4FD8814E5EF12}

Universal Links allow you to connect to deep links in your iOS app and are supported in iOS 9.2 or later. When a Universal Link is accessed, iOS redirects the link directly to the deeplink in your app. If your app is not installed, it opens a URL for your website in a browser instead. Per ulteriori informazioni sui collegamenti universali, consulta [Supporto dei collegamenti](https://developer.apple.com/library/content/documentation/General/Conceptual/AppSearch/UniversalLinks.html)universali.

## Collegamenti app

App Links allow you to connect to deep links in your Android app and is supported in Android 6.0 or later. Quando si accede a un collegamento app, Android reindirizzerà il collegamento direttamente al collegamento profondo nell'app. If your app is not installed, it opens a URL for your website in a browser instead. For more information about App Links, see the [Handling Android App Links](https://developer.android.com/training/app-links/index.html).

## Creare un collegamento di marketing utilizzando un collegamento universale o collegamento app {#section_609ADEFFB9B441C4A8C45E936D0DC859}

Potete creare un collegamento di marketing che utilizza un collegamento universale o un collegamento app.

### Configurare un collegamento universale

1. Per impostare i collegamenti universali nell'app iOS, passate a [Gestione dei collegamenti universali in Apple](https://developer.apple.com/documentation/uikit/inter-process_communication/allowing_apps_and_websites_to_link_to_your_content/handling_universal_links).

2. In Adobe Mobile Services, configura i documenti di associazione del sito:

   a. Nella home page di Mobile Services, seleziona l'app per la quale vuoi impostare i collegamenti universali.

   b. Click **[!UICONTROL Manage App Settings]**.

   c. Accertati che l’app iOS che gestisce i collegamenti universali sia aggiunta alla sezione **[!UICONTROL Aggiungi app]** per app store.

   >[!TIP]
   >
   >Se la sezione **[!UICONTROL Aggiungi app]** per app store non viene visualizzata, fai clic sul collegamento **[!UICONTROL Aggiungi app]** per app store.

   d. Nella sezione Opzioni **[!UICONTROL collegamenti]** universali e collegamenti app, seleziona un'app iOS e digita ID app.

   f.Fate clic su **[!UICONTROL Salva]**.

   Devi fornire almeno una selezione di app iOS e un ID app, altrimenti riceverai un errore.

   >[!IMPORTANT]
   >
   >Per aggiornare i documenti, fai clic su Aggiorna nella sezione delle opzioni dei collegamenti universali e collegamenti app. However, when you click **[!UICONTROL Update]**, a warning notifies you that all Universal Links or App Links that you created in the past will be affected.

### Usa collegamento universale

1. In Adobe Mobile Services, crea un collegamento marketing che utilizza i collegamenti universali:

   a. Select the app from the Mobile Services home page, click **[!UICONTROL Acquisition]** &gt; **[!UICONTROL Marketing Link Builder]**.

   b. Fate clic su **[!UICONTROL Crea nuovo]**.

   c. Under **[!UICONTROL Marketing Link Options]**, select **[!UICONTROL Use Universal Links or App Links]**.

   d. Se hai configurato i documenti di associazione del sito nella sezione *Impostazione dei documenti di associazione del sito nella sezione Adobe Mobile Services* precedente, questa opzione è selezionata per impostazione predefinita.

   Se non avete configurato i documenti, l’opzione **[!UICONTROL Usa collegamenti universali o collegamenti]** app è disabilitata e l’opzione **[!UICONTROL Usa interstiziali]** è selezionata per impostazione predefinita.

   e. Se è selezionata l’opzione **[!UICONTROL Usa collegamenti universali o collegamenti]** app, viene visualizzato il campo Percorso **** personalizzato.

   che permette agli utenti di definire l'URL dopo il dominio con eventuali parametri di query. Ad esempio, se immetti L' `my/universal/link?os=9.2`URL completo del collegamento marketing diventa `https://[marketing link domain]/my/universal/link?[AMS default query parameters]&os=9.2`.

   f. Fai clic sulla scheda **[!UICONTROL Decisioni]** e configura la struttura decisionale.

   h. Se l'app iOS è installata, l'app gestisce il collegamento profondo con la relativa logica. La destinazione finale funge solo da fallback quando l'app non è installata. Poiché l'app non è installata, la destinazione finale può essere solo un collegamento Web o un app store.

   i.Fate clic su **[!UICONTROL Salva]**.

>[!TIP]
>
>Una volta salvato il collegamento marketing, le opzioni di collegamento marketing non possono essere modificate. Questo perché non desiderate modificare il comportamento dei collegamenti marketing che potrebbero essere già stati distribuiti.


### Configurare un collegamento app

1. Per impostare i collegamenti app nell'app Android, accedi a [Aggiungi collegamenti](https://developer.android.com/studio/write/app-link-indexing)app Android.

1. In Adobe Mobile Services, configura i documenti di associazione del sito:

   a. Nella home page di Mobile Services, seleziona l'app per la quale vuoi impostare i collegamenti app.

   b. Click **[!UICONTROL Manage App Settings]**.

   c. Accertati che l’app Android che gestisce i collegamenti universali o i collegamenti app sia aggiunta alla sezione **[!UICONTROL Aggiungi app]** per app store.

   >[!TIP]
   >
   >If this section does not display, click the **[!UICONTROL Add App Store App]** link.

   d. Scorri fino alla sezione Opzioni **** collegamenti universali e collegamenti app.

   e. Click the App Links (Android) tab.****

   f. Selezionate un'app Android e digitate un'impronta di certificato SHA-256.

   g. Click Save.****

   Devi fornire almeno una selezione di app Android e un certificato SHA-256, altrimenti riceverai un errore.

   >[!IMPORTANT]
   >
   >Per aggiornare i documenti, fai clic su **[!UICONTROL Aggiorna]** nella sezione delle **opzioni dei collegamenti universali e collegamenti app[!UICONTROL .]** However, when you click **[!UICONTROL Update]**, a warning notifies you that all Universal Links or App Links that you created in the past will be affected.

### Use an App Link

1. In Adobe Mobile Services, create a Marketing Link that uses App Links:

   a. Select the app from the Mobile Services home page, click **[!UICONTROL Acquisition]** &gt; **[!UICONTROL Marketing Link Builder]**.

   b. Click Create New.****

   c. In the Marketing Link Options section, select Use Universal Links or App Links.********

   d. Se avete configurato i documenti di associazione del sito dal passaggio 2, questa opzione è selezionata per impostazione predefinita.

   If not, the **[!UICONTROL Use Universal Links or App Links]** option is disabled, and **[!UICONTROL Use Interstitials]** is selected by default.

   e. If Use Universal Links or App Links is selected, the Custom Path field is displayed.********

   che permette agli utenti di definire l'URL dopo il dominio con eventuali parametri di query. Ad esempio, se immetti , your full Marketing Link URL becomes .`my/app/link?os=6.0``https://[marketing link domain]/my/app/link?[AMS default query parameters]&os=6.0`

   f. Fai clic sulla scheda **[!UICONTROL Decisioni]** e configura la struttura decisionale.

   g. If the Android app is installed, the app handles the deeplink with its logic.

   The final destination serves only as the fallback case for when the app is not installed. Since the app is not installed, the final destination can only be a web link or app store.

   h.Fate clic su **[!UICONTROL Salva]**.

>[!TIP]
>
>After a Marketing Link is saved, the **[!UICONTROL Marketing Links Options]** cannot be altered. Questo perché non desiderate modificare il comportamento dei collegamenti marketing che potrebbero essere già stati distribuiti.

## Utilizzo dei collegamenti di marketing

Ora puoi usare questi collegamenti di marketing nei messaggi e in altre aree dell'app.

>[!IMPORTANT]
>
>I conteggi di monitoraggio dei clic non saranno visualizzati con collegamenti universali o collegamenti app e non sarà possibile utilizzare gli interstiziali.

