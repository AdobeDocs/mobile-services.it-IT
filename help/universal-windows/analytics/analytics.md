---
description: nulle
seo-description: nulle
seo-title: Analytics
solution: Marketing Cloud,Analytics
title: Analytics
topic: Sviluppatore e implementazione
uuid: c2cef3d3-77a7-4a8e-bbe4-3db10a77996a
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Analytics {#analytics}

After you add the library to your project, you can make any of the Analytics method calls anywhere in your app.

>[!TIP]
>
>Accertatevi di importare `ADBMobile.h` nella classe.

## Enable mobile application reports in Analytics {#section_F2F9234009184F20BA36B5CDE872B424}

Prima di aggiungere il codice, chiedi all’amministratore di Analytics di completare le seguenti operazioni in modo da abilitare il tracciamento del ciclo di vita dell’app per dispositivi mobili. Ciò assicura che la suite di rapporti sia pronta ad acquisire le metriche quando inizi lo sviluppo.

1. Open **[!UICONTROL Admin Tools]** &gt; **[!UICONTROL Report Suites]** and select your mobile report suite(s).

1. Click **[!UICONTROL Edit Settings]** &gt; **[!UICONTROL Mobile Management]** &gt; **[!UICONTROL Mobile Application Reporting]**.

   ![](assets/mobile-settings.png)

1. Click **[!UICONTROL Enable Latest App Reports]**.

   Optionally, you can also click **[!UICONTROL Enable Mobile Location Tracking]** or **[!UICONTROL Enable Legacy Reporting and Attribution for background hits]**.

   ![](assets/enable-lifecycle.png)

Le metriche del ciclo di vita sono ora pronte per essere acquisite e la voce Rapporti per applicazioni mobili è disponibile nel menu **Rapporti** nell’interfaccia per i rapporti di marketing.

### Nuove versioni

Periodicamente, vengono rilasciate nuove versioni dei rapporti delle applicazioni mobili. Le nuove versioni non vengono applicate alla suite di rapporti automaticamente, è necessario ripetere questi passaggi per eseguire l’aggiornamento. Ogni volta che aggiungi nuove funzionalità di Experience Cloud all’app, si consiglia di ripetere questi passaggi per assicurarti di disporre della configurazione più recente.

## Lifecycle metrics {#section_532702562A7A43809407C9A2CBA80E1E}

Per raccogliere metriche del ciclo di vita nell’app, aggiungi chiamate a quando l’applicazione viene attivata, come illustrato negli esempi seguenti.

### WinJS in default.js

```js
app.onactivated = function (args) { 
  if (args.detail.kind === activation.ActivationKind.launch) { 
   ... 
   // launched and resumed stuff  
   ADBMobile.Config.collectLifecycleData(); 
  } 
}; 
app.oncheckpoint = function (args) { 
  ADBMobile.Config.pauseCollectingLifecycleData(); 
}
```

### C# in App.xaml.cs

```js
public App() 
{ 
    this.InitializeComponent(); 
    this.Resuming += OnResuming; 
    this.Suspending += OnSuspending; 
} 
protected override void OnLaunched(LaunchActivatedEventArgs e) 
{   ... 
    ADBMobile.Config.CollectLifecycleData(); 
    ... 
} 
private void OnResuming(object sender, object e) 
{ 
    ... 
    ADBMobile.Config.CollectLifecycleData(); 
    ... 
} 
private void OnSuspending(object sender, SuspendingEventArgs e) 
{ 
    ... 
    ADBMobile.Config.PauseCollectingLifecycleData(); 
    ... 
}
```

### C++/CX in App.xaml.cpp

```js
App::App() 
{ 
 InitializeComponent(); 
 Resuming += ref new EventHandler<Object ^>(this, &App::OnResuming); 
 Suspending += ref new SuspendingEventHandler(this, &App::OnSuspending); 
} 
void App::OnResuming(Object ^sender, Object ^args) 
{ 
 ... 
 ADBMobile::Config::CollectLifecycleData(); 
 ... 
} 
void App::OnSuspending(Object^ sender, SuspendingEventArgs^ e) 
{ 
 ... 
 ADBMobile::Config::PauseCollectingLifecycleData(); 
 ... 
} 
void App::OnLaunched(Windows::ApplicationModel::Activation::LaunchActivatedEventArgs^ e) 
{ 
 ... 
 ADBMobile::Config::CollectLifecycleData(); 
 ... 
}
```

If `CollectLifecycleData()` is called twice in the same session, your application reports a crash on every call after the first. L'SDK imposta un flag quando l'applicazione viene chiusa, per indicare una chiusura corretta. If this flag is not set, `CollectLifecyleData()` reports a crash.

## Events, props, and eVars {#section_76EA6F5611184C5CAE6E62956D84D7B6}

If you've looked at [SDK methods](/help/universal-windows/c-configuration/methods.md), you are probably wondering where to set events, eVars, props, heirs, and lists. Nella versione 4, non è più possibile assegnare direttamente nell'app questi tipi di variabili. L’SDK utilizza invece i dati contestuali e le regole di elaborazione per mappare i dati dell’app sulle variabili di Analytics a scopo di reportistica.

L’elaborazione di regole offre diversi vantaggi:

* È possibile cambiare la mappatura dei dati senza dover inviare un aggiornamento all’App Store.
* Invece di impostare variabili specifiche per una suite di rapporti, è possibile assegnare ai dati dei nomi significativi.
* L’impatto dell’invio di dati aggiuntivi è limitato. Questi valori compariranno nei rapporti solo dopo che questi saranno stati mappati utilizzando delle regole di elaborazione.

Eventuali valori che venivano assegnati direttamente alle variabili ora dovranno essere aggiunti ai dati contestuali.

## Regole di elaborazione {#section_66EE762EEA5E4728864166201617DEBF}

L’elaborazione delle regole viene usata per copiare i dati inviati in variabili di dati di contesto a elementi evar, prop e ad altre variabili a scopo di reportistica.

[Formazione sulle regole di elaborazione](https://tv.adobe.com/embed/1181/16506/) @ Summit 2013

[Guida sulle regole di elaborazione](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules.html)

[Ottenere l’autorizzazione all’utilizzo delle regole di elaborazione](https://helpx.adobe.com/analytics/kb/processing-rules-authorization.html)

Si consiglia di raggruppare le variabili di dati di contesto utilizzando "spazi nome", in quanto aiuta a mantenere un ordine logico. Ad esempio, se desideri raccogliere informazioni su un prodotto, puoi definire le seguenti variabili:

```javascript
"product.type":"hat" 
"product.team":"mariners" 
"product.color":"blue"
```

Le variabili di dati di contesto sono riportate in ordine alfabetico nell’interfaccia delle regole di elaborazione, così utilizzando i namespace puoi vedere rapidamente le variabili di uno stesso namespace.

Inoltre, alcuni programmatori hanno l’abitudine di denominare le chiavi dei dati di contesto utilizzando il numero evar o prop:

```js
"eVar1":"jimbo"
```

Anche se tali numeri possono facilitare *leggermente* un lavoro di mappatura una tantum nelle regole di elaborazione, potrebbe rendere il codice meno leggibile durante le attività di debug e complicare gli aggiornamenti del codice futuri. Piuttosto, consigliamo vivamente di assegnare a chiavi e valori dei nomi descrittivi:

```js
"username":"jimbo"
```

Imposta variabili contestuali che definiscono gli eventi del contatore su un valore di "1":

```js
"logon":"1"
```

Le variabili dei dati di contesto che definiscono gli eventi dell’incrementatore possono avere il valore da incrementare:

```js
"levels completed":"6"
```

>[!TIP]
>
>Adobe riserva lo spazio dei nomi `a.`. Other than this restriction, context data variables just need to be unique in your login company to avoid collisions.

## Products variable {#section_AFBA36F3718C44D29AF81B9E1056A1B4}

Per impostare *`products`* nell’SDK di Mobile, devi usare una sintassi particolare. Per ulteriori informazioni, vedi [Variabile](/help/universal-windows/analytics/products.md)Prodotti.

## (Optional) Enable offline tracking {#section_955B2A03EB854742BDFC4A0A3C287009}

To store hits when the device is offline, you can enable offline tracking in the [SDK methods](/help/universal-windows/c-configuration/methods.md) file. Pay close attention to the timestamp requirements described in the config file reference before you enable offline tracking.

## Geo-location and points of interest {#section_BAD34A8DD013454DB355121316BD7FD4}

La geolocalizzazione consente di misurare i dati della posizione (latitudine/longitudine) e i punti di interesse (POI) predefiniti. Each `TrackLocation` call sends:

* Latitudine/longitudine, e POI (se all’interno di un POI definito nel file di configurazione `ADBMobileConfig.json`). 

   Questi dati vengono passati alle variabili della soluzione mobile per la generazione automatica di rapporti.

* Distanza dal centro e precisione passate come dati contestuali.

   Acquisisci utilizzando una regola di elaborazione.

Per tenere traccia di una posizione:

```js
var ADB = ADBMobile; 
ADB.Analytics.trackLocation(37.75345, -122.33207, null);
```

Se il seguente POI è definito nel file di configurazione `ADBMobileConfig.json`:

```js
"poi" : [ 
            ["San Francisco",37.757144,-122.44812,7000], 
        ]
```

When the device location is determined to be within a 7000 meter radius of the defined point, an `a.loc.poi` context data variable with the value `San Francisco` is sent in with the `TrackLocation` hit. Viene inviata la variabile di dati di contesto `a.loc.dist`, con la distanza (in metri) dalle coordinate definite.

## Lifetime value {#section_D2C6971545BA4D639FBE07F13EF08895}

Il valore "lifetime" permette di misurare e impostare come destinazione un valore del ciclo di vita per ogni utente. Ogni volta che viene inviato un valore con `TrackLifetimeValueIncrease`, tale valore viene aggiunto a quello esistente. Il valore "lifetime" del ciclo di vita è memorizzato nel dispositivo e può essere recuperato in qualsiasi momento con una chiamata `GetLifetimeValue`. È utile per memorizzare gli acquisti, le visualizzazioni di annunci, la visione completa di un video, le condivisioni social, i caricamenti di foto, ecc. nel corso del ciclo di vita.

```js
// Lifetime Value Example 
var ADB = ADBMobile; 
var purchasePrice = 39.95; 
var cdata = new Windows.Foundation.Collections.PropertySet(); 
cdata["ItemPurchaseEvent"] = "ItemPurchaseEvent"; 
cdata["PurchaseItem"] = "Item453"; 
cdata["PurchasePrice"] = purchasePrice; 
ADB.Analytics.trackLifetimeValueIncrease(purchasePrice, cdata);
```

## Timed actions {#section_7FF8B6A913A0460EAA4CAE835E32D8C1}

Le azioni temporizzate consentono di misurare il tempo trascorso all’interno dell’app e il tempo totale dall’inizio alla fine di un’azione. L’SDK calcola il tempo necessario a completare l’azione nella sessione e complessivamente in più sessioni. Questo può essere utilizzato per definire i segmenti da confrontare riguardo a tempo dell’acquisto, livello passaggio, flusso di cassa e così via.

* Numero totale di secondi trascorsi nell'app tra avvio e fine, attraverso sessioni diverse
* Numero totale di secondi tra avvio e fine (tempo effettivo)

```js
// Timed Action Start Example 
var ADB = ADBMobile; 
var cdata = new Windows.Foundation.Collections.PropertySet(); 
cdata["ExperienceName"] = experience; 
ADB.Analytics.trackTimedActionStart("TimeUntilPurchase", cdata);
```

```js
// Timed Action Update Example 
var ADB = ADBMobile; 
var cdataUpdate = new Windows.Foundation.Collections.PropertySet(); 
cdataUpdate["ImageLiked"] = imageName; 
ADB.Analytics.trackTimedActionStart("TimeUntilPurchase", cdata); 
```

```js
// Timed Action End Example 
var ADB = ADBMobile; 
ADB.Analytics.trackTimedActionEnd("TimeUntilPurchase");
```
