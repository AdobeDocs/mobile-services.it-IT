---
description: Dopo aver aggiunto la libreria al progetto, puoi effettuare una qualsiasi chiamata dei metodi di Analytics ovunque nell'app.
solution: Experience Cloud,Analytics
title: Analytics
topic-fix: Developer and implementation
uuid: fa0ef6c4-c04d-4695-9eb4-ada4e9920e6c
exl-id: 1a7b32b8-731d-4ae3-9feb-dafbb7495590
translation-type: tm+mt
source-git-commit: b9ee49ba26d4726b1f97ef36f5c2e9923361b1ee
workflow-type: tm+mt
source-wordcount: '961'
ht-degree: 20%

---

# Analytics {#analytics}

Dopo aver aggiunto la libreria al progetto, puoi effettuare una qualsiasi chiamata dei metodi di Analytics ovunque nell&#39;app.

>[!TIP]
>
>Assicurati di importare `ADBMobile.h` nella classe.

## Abilitare i rapporti sulle applicazioni mobili in Analytics {#section_F2F9234009184F20BA36B5CDE872B424}

Prima di aggiungere il codice, chiedi all’amministratore di Analytics di completare quanto segue per abilitare il tracciamento del ciclo di vita delle app mobili. In questo modo la suite di rapporti è pronta per acquisire le metriche all’inizio dello sviluppo.

1. Apri **[!UICONTROL Strumenti di amministrazione]** > **[!UICONTROL Suite di rapporti]** e seleziona le suite di rapporti mobili.
1. Fai clic su **[!UICONTROL Modifica impostazioni]** > **[!UICONTROL Gestione mobile]** > **[!UICONTROL Generazione rapporti applicazioni mobili]**.

   ![](assets/mobile-settings.png)

1. Fai clic su **[!UICONTROL Abilita rapporti app più recenti]**.

   Facoltativamente, puoi anche fare clic su **[!UICONTROL Abilita tracciamento posizione mobile]** e **[!UICONTROL Abilita rapporti legacy e attribuzione per hit di background]**.

   ![](assets/enable-lifecycle.png)

Le metriche del ciclo di vita sono ora pronte per essere acquisite e i rapporti sulle applicazioni mobili vengono visualizzati nel menu **[!UICONTROL Report]** nell’interfaccia dei rapporti di marketing.


### Nuove versioni

Periodicamente vengono rilasciate nuove versioni dei rapporti sulle applicazioni mobili. Le nuove versioni non vengono applicate automaticamente alla suite di rapporti, devi ripetere questi passaggi per eseguire l’aggiornamento. Ogni volta che aggiungi nuove funzionalità di Experience Cloud all’app, ti consigliamo di ripetere questi passaggi per assicurarti di disporre della configurazione più recente.


## Metriche del ciclo di vita {#section_532702562A7A43809407C9A2CBA80E1E}

Per raccogliere le metriche del ciclo di vita nell&#39;app, aggiungi chiamate a quando l&#39;applicazione viene attivata, come mostrato negli esempi seguenti.


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
    this.Resuming *= OnResuming; 
    this.Suspending *= OnSuspending; 
} 
protected override void OnLaunched(LaunchActivatedEventArgs e) 
{ 
    ... 
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

### C/CX in App.xaml.cpp

```js
App::App() 
{ 
 InitializeComponent(); 
 Resuming *= ref new EventHandler<Object ^>(this, &App::OnResuming); 
 Suspending *= ref new SuspendingEventHandler(this, &App::OnSuspending); 
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

Se `CollectLifecycleData()` viene chiamato due volte nella stessa sessione, l&#39;applicazione segnalerà un arresto anomalo per ogni chiamata successiva alla prima. L&#39;SDK imposta un flag quando l&#39;applicazione viene chiusa che indica una corretta uscita. Se questo flag non è impostato, `CollectLifecyleData()` segnala un arresto anomalo.


## Eventi, prop ed eVar {#section_76EA6F5611184C5CAE6E62956D84D7B6}


Se hai esaminato la [Guida di riferimento delle classi e dei metodi ADBMobile](/help/windows-appstore/c-configuration/methods.md), probabilmente ti chiederai dove impostare eventi, eVar, prop, eredi ed elenchi. Nella versione 4, non puoi più assegnare direttamente nell’app questi tipi di variabili. L’SDK utilizza invece i dati contestuali e le regole di elaborazione per mappare i dati dell’app sulle variabili di Analytics a scopo di reportistica.

Le regole di elaborazione offrono diversi vantaggi:

* Puoi modificare la mappatura dei dati senza inviare un aggiornamento all’App Store.
* Puoi assegnare ai dati dei nomi significativi invece di impostare variabili specifiche per una suite di rapporti.
* L’invio di dati aggiuntivi ha un impatto minimo. Questi valori verranno visualizzati nei rapporti solo dopo che saranno stati mappati utilizzando delle regole di elaborazione.

Eventuali valori che venivano assegnati direttamente alle variabili ora dovranno essere aggiunti ai dati contestuali.


## Regole di elaborazione {#section_66EE762EEA5E4728864166201617DEBF}

Le regole di elaborazione vengono utilizzate per copiare i dati inviati in variabili di dati di contesto a eVar, prop e ad altre variabili a scopo di reportistica.

[Formazione sulle regole di elaborazione](https://tv.adobe.com/embed/1181/16506/) @ Summit 2013

[Panoramica sulle regole di elaborazione](https://docs.adobe.com/content/help/it-IT/analytics/admin/admin-tools/processing-rules/processing-rules.html)

[Ottenere l&#39;autorizzazione all&#39;utilizzo delle regole di elaborazione](https://helpx.adobe.com/analytics/kb/processing-rules-authorization.html)

Consigliamo di raggruppare le variabili di dati di contesto utilizzando &quot;namespace&quot;, in quanto consente di mantenere un ordine logico. Ad esempio, se desideri raccogliere informazioni su un prodotto, puoi definire le seguenti variabili:

```js
"product.type":"hat" 
"product.team":"mariners" 
"product.color":"blue"
```

Le variabili di dati di contesto sono ordinate alfabeticamente nell’interfaccia delle regole di elaborazione, pertanto gli spazi dei nomi consentono di vedere rapidamente le variabili che si trovano nello stesso spazio dei nomi.

Inoltre, abbiamo sentito che alcuni di voi stanno denominando le chiavi dei dati di contesto utilizzando il numero evar o prop:

```js
"eVar1":"jimbo"
```

Questo potrebbe semplificare leggermente *la mappatura una tantum nelle regole di elaborazione, a scapito però della leggibilità durante il debug e complicando gli aggiornamenti futuri del codice.* Consigliamo piuttosto di utilizzare nomi descrittivi per chiavi e valori:

```js
"username":"jimbo"
```

Imposta le variabili di contesto che definiscono eventi contatore su un valore di &quot;1&quot;:

```js
"logon":"1"
```

Le variabili di dati di contesto che definiscono eventi di incremento possono avere il valore da incrementare:

```js
"levels completed":"6"
```

>[!NOTE]
>
>Adobe riserva lo spazio dei nomi `a.`. A parte questa piccola restrizione, le variabili di dati di contesto devono essere univoche nella società di accesso per evitare conflitti.

## Variabile &quot;products&quot; {#section_AFBA36F3718C44D29AF81B9E1056A1B4}

Per impostare *`products`* nell’SDK di Mobile, devi usare una sintassi particolare. Vedere [Variabile &quot;products&quot;](/help/windows-appstore/analytics/products/products.md).

## (Facoltativo) Abilita il tracciamento offline {#section_955B2A03EB854742BDFC4A0A3C287009}

Per memorizzare gli hit quando il dispositivo è offline, puoi abilitare il tracciamento offline nella [configurazione ADBMobileConfig.json](/help/windows-appstore/c-configuration/methods.md). Prima di abilitare il tracciamento offline, fai attenzione ai requisiti di marca temporale descritti nel riferimento al file di configurazione.

## Geolocalizzazione e punti di interesse {#section_BAD34A8DD013454DB355121316BD7FD4}

La geolocalizzazione consente di misurare i dati sulla posizione (latitudine/longitudine) e i punti di interesse predefiniti. Ogni chiamata `TrackLocation` invia:

* Latitudine/longitudine e POI (se all’interno di un POI definito nel file di configurazione `ADBMobileConfig.json`). Questi vengono passati alle variabili della soluzione mobile per il reporting automatico.
* Distanza dal centro e precisione passate come dati contestuali. Acquisisci utilizzando una regola di elaborazione.

Per tracciare una posizione:

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

Quando la posizione del dispositivo è determinata entro un raggio di 7000 metri dal punto definito, viene inviata una variabile di dati di contesto `a.loc.poi` con il valore &quot;San Francisco&quot; con l&#39;hit `TrackLocation` . Viene inviata una variabile di contesto `a.loc.dist` con la distanza in metri dalle coordinate definite.

## Valore del ciclo di vita {#section_D2C6971545BA4D639FBE07F13EF08895}

Il valore &quot;lifetime&quot; permette di misurare e impostare come destinazione un valore del ciclo di vita per ogni utente. Ogni volta che viene inviato un valore con `TrackLifetimeValueIncrease`, tale valore viene aggiunto a quello esistente. Il valore &quot;lifetime&quot; del ciclo di vita è memorizzato nel dispositivo e può essere recuperato in qualsiasi momento con una chiamata `GetLifetimeValue`. È utile per memorizzare gli acquisti, le visualizzazioni di annunci, la visione completa di un video, le condivisioni social, i caricamenti di foto, ecc. nel corso del ciclo di vita.

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

## Azioni temporizzate {#section_7FF8B6A913A0460EAA4CAE835E32D8C1}

Le azioni temporizzate consentono di misurare il tempo trascorso in-app e il tempo totale dall’inizio alla fine di un’azione. L’SDK calcola il tempo di sessione e il tempo totale (per più sessioni) necessario per completare l’azione. Può essere utilizzato per definire i segmenti da confrontare in base al tempo di acquisto, al livello di passaggio, al flusso di cassa e così via.

* Numero totale di secondi trascorsi nell’app dall’inizio alla fine, per più sessioni
* Numero totale di secondi dall’inizio alla fine (in base all’ora effettiva)

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
