---
description: In questa sezione viene descritto come migrare dalla versione 3.x di un precedente SDK Windows Mobile all’SDK 4.x per Windows 8.1 Universal App Store per  Soluzioni di Experience Cloud.
seo-description: In questa sezione viene descritto come migrare dalla versione 3.x di un precedente SDK Windows Mobile all’SDK 4.x per Windows 8.1 Universal App Store per  Soluzioni di Experience Cloud.
seo-title: Migrazione agli SDK 4.x
solution: Experience Cloud,Analytics
title: Migrazione agli SDK 4.x
topic: Developer and implementation
uuid: e0fe3b7b-cda5-4a91-834c-2c7e17a501a3
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '683'
ht-degree: 13%

---


# Migrazione agli SDK 4.x {#migrate-to-the-x-sdks}

In questa sezione viene descritto come migrare dalla versione 3.x di un precedente SDK Windows Mobile all’SDK 4.x per Windows 8.1 Universal App Store per  Soluzioni di Experience Cloud.

Con il passaggio alla versione 4.x, tutte le funzionalità sono ora accessibili tramite metodi statici, per cui non è più necessario tenere traccia dei propri oggetti.

Nelle sezioni seguenti viene descritta la migrazione dalla versione 3.x alla versione 4.x.

## Rimuovere le proprietà non utilizzate {#section_145222EAA20F4CC2977DD883FDDBBFC5}

Probabilmente avete notato un nuovo `ADBMobileConfig.json` file incluso nel download. Questo file contiene impostazioni globali specifiche per le applicazioni e sostituisce la maggior parte delle variabili di configurazione utilizzate nelle versioni precedenti. Ecco un esempio di file `ADBMobileConfig.json`:

```js
{ 
    "version" : "1.0", 
    "analytics" : { 
        "rsids" : "coolApp", 
        "server" : "my.CoolApp.com", 
        "charset" : "UTF-8", 
        "ssl" : true, 
        "offlineEnabled" : true, 
        "lifecycleTimeout" : 300, 
        "privacyDefault" : "optedin", 
        "poi" : [ 
                    ["san francisco",37.757144,-122.44812,7000], 
                    ["santa cruz",36.972935,-122.01725,600] 
                ] 
    }, 
 "target" : { 
  "clientCode" : "myTargetClientCode", 
  "timeout" : 5 
 }, 
 "audienceManager" : { 
  "server" : "myServer.demdex.com" 
 } 
}
```

Nella tabella seguente sono elencate le variabili di configurazione che devi spostare al file di configurazione. Sposta il valore impostato per la variabile della prima colonna alla variabile della seconda colonna, quindi rimuovi la vecchia variabile di configurazione dal codice.

## Migrazione da 3.x

| Variabile/Metodo di configurazione | Variable in the `ADBMobileConfig.json` file. |
|--- |--- |
| offlineTrackingEnabled | &quot;offlineEnabled&quot; |
| reportSuiteIDs | &quot;rsids&quot; |
| trackingServer | &quot;server&quot; |
| charSet | &quot;charset&quot; |
| currencyCode | &quot;currency&quot; |
| ssl | &quot;ssl&quot; |
| setOfflineHitLimit | Rimuovi, non più utilizzato. |
| linkTrackVars | Rimuovi, non più utilizzato. |
| linkTrackEvents | Rimuovi, non più utilizzato. |

## Aggiornare le chiamate e le variabili di tracciamento {#section_96E7D9B3CDAC444789503B7E7F139AB9}

Invece di utilizzare le `Track` chiamate e `TrackLink` gli SDK versione 4 incentrati sul Web, l&#39;SDK usa due metodi che hanno un senso nel mondo dei dispositivi mobili:

* `TrackState` Gli stati sono le visualizzazioni disponibili nell’app, ad esempio &quot;dashboard iniziale&quot;, &quot;impostazioni dell’app&quot;, &quot;carrello&quot; e così via. Questi stati sono simili alle pagine di un sito Web e le chiamate `trackState` incrementano le visualizzazioni di pagina.

* `TrackAction` Le azioni sono gli eventi che avvengono nell’app e che desideri misurare, come &quot;accessi&quot;, &quot;tap sui banner&quot;, &quot;abbonamenti ai feed&quot; e altre metriche. Queste chiamate non incrementano le visualizzazioni di pagina.

The `contextData` parameter for both of these methods contains name-value pairs that are sent as context data.

## Eventi, prop, eVar

Se hai esaminato i metodi [](/help/windows-appstore/c-configuration/methods.md)SDK, probabilmente ti chiederai dove impostare eventi, eVar, prop, eredi ed elenchi. Nella versione 4, non è più possibile assegnare questi tipi di variabili direttamente nell&#39;app. Al contrario, l&#39;SDK utilizza i dati contestuali e le regole di elaborazione per mappare i dati dell&#39;app sulle variabili Analytics a scopo di reportistica.

Le regole di elaborazione offrono diversi vantaggi:

* Potete modificare la mappatura dei dati senza inviare un aggiornamento all&#39;App Store.
* Puoi utilizzare nomi significativi per i dati invece di impostare variabili specifiche per una suite di rapporti.
* L&#39;impatto sull&#39;invio di dati aggiuntivi è limitato. Questi valori verranno visualizzati nei rapporti solo dopo che saranno stati mappati utilizzando delle regole di elaborazione.

For more information, see *Processing Rules* in [Analytics](/help/windows-appstore/analytics/analytics.md).

Eventuali valori che venivano assegnati direttamente alle variabili ora dovranno essere aggiunti ai dati contestuali. This means that calls to `SetProp`, `SetEvar`, and assignments to persistent context data should all be removed and the values added to context data.

**AppSection/Server, GeoZip, ID transazione, Campaign e altre variabili standard**

Tutti gli altri dati che precedentemente impostavi sull’oggetto di misurazione, comprese le variabili elencate sopra, devono essere aggiunti invece ai dati contestuali.

Per dirla semplicemente, gli unici dati inviati con una `TrackState` chiamata o `TrackAction` chiamata sono il payload nel `data` parametro.

### Sostituire le chiamate di tracciamento

Throughout your code, replace the following methods with a call to `trackState` or `trackAction`:

### Migrazione da 3.x

* `TrackAppState` (TrackState)
* `TrackEvents` (TrackAction)
* `Track` (TrackAction)
* `TrackLinkURL` (TrackAction)

## ID visitatore personalizzato {#section_2CF930C13BA64F04959846E578B608F3}

Sostituisci la variabile `visitorID` con una chiamata a `setUserIdentifier`.

## Tracciamento offline {#section_5D4CD8CD1BE041A79A8657E31C0D24C6}

Offline tracking is enabled in the `ADBMobileConfig.json` file. All other offline configuration is done automatically.

In tutto il codice, devi rimuovere le chiamate ai seguenti metodi:

### Migrazione da 3.x

* `SetOnline`
* `SetOffline`

## Variabile dei prodotti {#section_AFBA36F3718C44D29AF81B9E1056A1B4}

Poiché la variabile &quot;products&quot; non è disponibile nelle regole di elaborazione, puoi usare la sintassi seguente per impostare `products`products:

```js
// create a processing rule to set the corresponding product event. 
// for example, set the Product Views event when context data a.action = "product view" 
var cdata = new Windows.Foundation.Collections.PropertySet(); 
cdata["&&products"] = ";Cool Shoe"; 
ADB.Analytics.trackAction("product view", cdata);
```

![](assets/prod-view.png)

In questo esempio, il valore di `"&&products"` è `";Cool Shoe`&quot; e deve seguire la sintassi della stringa products per il tipo di evento che si sta monitorando.