---
description: I collegamenti universali (iOS) e i collegamenti alle app (Android) consentono di connettersi ai collegamenti profondi nelle app iOS o Android.
keywords: mobile
seo-description: I collegamenti universali (iOS) e i collegamenti alle app (Android) consentono di connettersi ai collegamenti profondi nelle app iOS o Android.
seo-title: Collegamenti universali Apple e collegamenti app Android
solution: Experience Cloud,Analytics
title: Collegamenti universali Apple e collegamenti app Android
topic: Metrics
uuid: 8d6441dc-4307-4454-95ea-d77ec796f918
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '1142'
ht-degree: 100%

---


# Collegamenti universali Apple e collegamenti app Android {#universal-links-and-app-links}

I collegamenti universali (iOS) e i collegamenti alle app (Android) consentono di connettersi ai collegamenti profondi nelle app iOS o Android.

>[!IMPORTANT]
>
>A partire da iOS 9.2, i collegamenti diretti non sono supportati. È necessario utilizzare i collegamenti universali Apple per i collegamenti diretti alle app o al sito web.

## Collegamenti universali {#section_F8147944679A42E59CF4FD8814E5EF12}

I collegamenti universali consentono di connettersi ai collegamenti diretti nell’app iOS e sono supportati in iOS 9.2 o versione successiva. Quando si accede a un collegamento universale, iOS reindirizzerà il collegamento direttamente al collegamento diretto nell’app. Se l’app non è installata, viene invece aperto un URL per il sito web in un browser. Per ulteriori informazioni sui collegamenti universali, consulta [Supporto collegamenti universali](https://developer.apple.com/library/content/documentation/General/Conceptual/AppSearch/UniversalLinks.html).

## Collegamenti alle app

I collegamenti alle app consentono di connettersi ai collegamenti diretti nell’app Android ed è supportato in Android 6.0 o versione successiva. Quando si accede a un collegamento all’app, Android reindirizzerà il collegamento direttamente al collegamento diretto nell’app. Se l’app non è installata, viene invece aperto un URL per il sito web in un browser. Per ulteriori informazioni sui collegamenti alle app, consulta [Gestione del collegamento alle app Android](https://developer.android.com/training/app-links/index.html).

## Creare un collegamento di marketing utilizzando un collegamento universale o collegamento alle app {#section_609ADEFFB9B441C4A8C45E936D0DC859}

Puoi creare un collegamento di marketing che utilizza un collegamento universale o un collegamento alle app.

### Configurare un collegamento universale

1. Per impostare i collegamenti universali nell’app di iOS, vai a [Gestione dei collegamenti universali in Apple](https://developer.apple.com/documentation/uikit/inter-process_communication/allowing_apps_and_websites_to_link_to_your_content/handling_universal_links).

2. In Adobe Mobile Services, configura i documenti di associazione al sito:

   a. Nella home page di Mobile Services, scegli l’app per la quale vuoi impostare collegamenti universali o collegamenti alle app.

   b. Fai clic su **[!UICONTROL Gestione impostazioni app]**.

   c. Accertati che l’app iOS che gestisce i collegamenti universali sia aggiunta alla sezione **[!UICONTROL Aggiungi app per app store]**.

   >[!TIP]
   >
   >Se la sezione **[!UICONTROL Aggiungi app per app store]** non viene visualizzata, fai clic sul collegamento **[!UICONTROL Aggiungi app per app store]**.

   d. Nella sezione **[!UICONTROL Opzioni collegamenti universali e collegamenti alle app]**, seleziona un’app iOS e digita l’ID app.

   f. Fai clic su **[!UICONTROL Salva]**.

   Devi fornire almeno una selezione di app iOS e un ID app, altrimenti riceverai un errore.

   >[!IMPORTANT]
   >
   >Per aggiornare i documenti, fai clic su Aggiorna nella sezione Opzioni collegamenti universali e alle app. Tuttavia, quando fai clic su **[!UICONTROL Aggiorna]**, un avviso ti segnala che la modifica verrà applicata a tutti i collegamenti universali e ai collegamenti alle app già creati in passato.

### Usare un collegamento universale

1. In Adobe Mobile Services, crea un collegamento di marketing che utilizza i collegamenti universali:

   a. Seleziona l’app dalla home page di Mobile Services e fai clic su **[!UICONTROL Acquisizione]** > **[!UICONTROL Marketing Link Builder]**.

   b. Fai clic su **[!UICONTROL Crea nuovo]**.

   c. In **[!UICONTROL Opzioni collegamento di marketing]**, seleziona **[!UICONTROL Usa collegamenti universali o alle app]**.

   d. Se, nella precedente sezione sull’*impostazione dei documenti di associazione sito in Adobe Mobile Services*, avevi configurato i documenti di associazione sito, questa opzione è selezionata per impostazione predefinita.

   Se non hai configurato i documenti, l’opzione **[!UICONTROL Usa collegamenti universali o alle app]** è disabilitata e l’opzione **[!UICONTROL Usa interstiziali]** è selezionata per impostazione predefinita.

   e. Se è selezionata l’opzione **[!UICONTROL Usa collegamenti universali o alle app]**, viene visualizzato il campo **[!UICONTROL Percorso personalizzato]**

   che permette agli utenti di definire l’URL dopo il dominio con eventuali parametri di query. Ad esempio, se immetti   `my/universal/link?os=9.2`, l’URL completo del collegamento marketing diventa `https://[marketing link domain]/my/universal/link?[AMS default query parameters]&os=9.2`.

   f. Fai clic sulla scheda **[!UICONTROL Decisioni]** e configura la struttura decisionale.

   h. Se è installata l’app iOS, viene gestito il collegamento diretto con la relativa logica. La destinazione finale funge solo da fallback quando l’app non è installata. Poiché l’app non è installata, la destinazione finale può essere solo un collegamento web o un app store.

   i. Fai clic su **[!UICONTROL Salva]**.

>[!TIP]
>
>Una volta salvato il collegamento di marketing, non è più possibile modificare le Opzioni collegamento di marketing, per evitare che venga modificato il comportamento di eventuali collegamenti di marketing già distribuiti.


### Configurare un collegamento alle app

1. Per impostare i collegamenti alle app nell’app Android, passa a [Aggiungi collegamento alle app Android](https://developer.android.com/studio/write/app-link-indexing).

1. In Adobe Mobile Services, configura i documenti di associazione al sito:

   a. Nella home page di Mobile Services, scegli l’app per la quale vuoi impostare collegamenti alle app.

   b. Fai clic su **[!UICONTROL Gestione impostazioni app]**.

   c. Accertati che l’app Android che gestisce i collegamenti universali o i collegamenti alle app sia aggiunta alla sezione **[!UICONTROL Aggiungi app per app store]**.

   >[!TIP]
   >
   >Se questa sezione non è visibile, fai clic sul collegamento **[!UICONTROL Aggiungi app per app store]**.

   d. Scorri fino alla sezione **[!UICONTROL Opzioni collegamenti universali e collegamenti alle app]**.

   e. Fai clic sulla scheda **[!UICONTROL Collegamenti alle app (Android)]**.

   f. Per Android, scegli un’app Android e specifica la relativa impronta di certificazione SHA-256.

   g. Fai clic su **[!UICONTROL Salva]**.

   Devi fornire almeno una selezione di app Android e un certificato SHA-256, altrimenti riceverai un errore.

   >[!IMPORTANT]
   >
   >Per aggiornare i documenti, fai clic su **[!UICONTROL Aggiorna]** nella sezione **[!UICONTROL Opzioni collegamenti universali e alle app]**. Tuttavia, quando fai clic su **[!UICONTROL Aggiorna]**, un avviso ti segnala che la modifica verrà applicata a tutti i collegamenti universali e ai collegamenti alle app già creati in passato.

### Usare un collegamento alle app

1. In Adobe Mobile Services, crea un collegamento di marketing che utilizza i collegamenti alle app:

   a. Seleziona l’app dalla home page di Mobile Services e fai clic su **[!UICONTROL Acquisizione]** > **[!UICONTROL Marketing Link Builder]**.

   b. Fai clic su **[!UICONTROL Crea nuovo]**.

   c. Nella sezione **[!UICONTROL Opzioni collegamento di marketing]**, seleziona **[!UICONTROL Usa collegamenti universali o alle app]**.

   d. Se nella fase 2 hai impostato i documenti di associazione dei siti, questa opzione è selezionata per impostazione predefinita.

   In caso contrario, l’opzione **[!UICONTROL Usa collegamenti universali o alle app]** è disattivata ed è invece selezionata per impostazione predefinita l’opzione **[!UICONTROL Usa interstiziali]**.

   e. Se è selezionata l’opzione **[!UICONTROL Usa collegamenti universali o alle app]**, viene visualizzato il campo **[!UICONTROL Percorso personalizzato]**.

   che permette agli utenti di definire l’URL dopo il dominio con eventuali parametri di query. Ad esempio, se immetti   `my/app/link?os=6.0`, l’URL completo del collegamento marketing diventa `https://[marketing link domain]/my/app/link?[AMS default query parameters]&os=6.0`.

   f. Fai clic sulla scheda **[!UICONTROL Decisioni]** e configura la struttura decisionale.

   g. Se l’app Android è installata, l’app gestisce il collegamento diretto con la relativa logica.

   La destinazione finale funge solo da caso di fallback per i casi in cui l’app non è installata. Poiché l’app non è installata, la destinazione finale può essere solo un collegamento web o un app store.

   h. Fai clic su **[!UICONTROL Salva]**.

>[!TIP]
>
>Una volta salvato il collegamento di marketing, non è più possibile modificare le **[!UICONTROL Opzioni collegamento di marketing]** per evitare che venga modificato il comportamento di eventuali collegamenti di marketing già distribuiti.

## Utilizzo dei collegamenti di marketing

Puoi ora usare questi collegamenti di marketing nei messaggi e in altre aree dell’app.

>[!IMPORTANT]
>
>I conteggi di tracciamento dei clic non saranno visualizzati con collegamenti universali o collegamenti alle app e non sarà possibile utilizzare gli interstiziali.

