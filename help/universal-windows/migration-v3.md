---
description: Questa sezione descrive come migrare dalla versione 3.x di un precedente SDK Windows Mobile all’SDK 4.x della piattaforma UWP (Universal Windows Platform) per  soluzioni di Experience Cloud.
seo-description: Questa sezione descrive come migrare dalla versione 3.x di un precedente SDK Windows Mobile all’SDK 4.x della piattaforma UWP (Universal Windows Platform) per  soluzioni di Experience Cloud.
seo-title: Migrare a 4.x
solution: Experience Cloud,Analytics
title: Migrare a 4.x
topic: Developer and implementation
uuid: bdd6c5cd-3892-4e99-b69e-77105ad66e25
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '705'
ht-degree: 26%

---


# Migrazione agli SDK 4.x{#migrate-to-x}

Questa sezione descrive come migrare dalla versione 3.x dell’SDK di Windows Mobile all’SDK 4.x della piattaforma UWP (Universal Windows Platform) per  soluzioni di Experience Cloud.

Con il passaggio alla versione 4.x, tutte le funzionalità ora sono accessibili tramite metodi statici. Non è più necessario tenere traccia dei propri oggetti.

Nelle sezioni seguenti viene descritta la migrazione dalla versione 3.x alla versione 4.x.

## Rimuovere le proprietà non utilizzate {#section_145222EAA20F4CC2977DD883FDDBBFC5}

Probabilmente avete notato un nuovo `ADBMobileConfig.json` file incluso nel download. Questo file contiene impostazioni globali specifiche per le applicazioni e sostituisce la maggior parte delle variabili di configurazione utilizzate nelle versioni precedenti.

Ecco un esempio di file `ADBMobileConfig.json`:

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

### Migrazione da 3.x

La tabella seguente fornisce un elenco di variabili negli SDK 3.x e il nuovo nome negli SDK 4.x:

| Variabile/Metodo di configurazione | Variable in the `ADBMobileConfig.json` file. |
|--- |--- |
| offlineTrackingEnabled | &quot;offlineEnabled&quot; |
| reportSuiteIDs | &quot;rsids&quot; |
| trackingServer | &quot;server&quot; |
| charSet | &quot;charset&quot; |
| currencyCode | &quot;currency&quot; |
| ssl | &quot;ssl&quot; |
| setOfflineHitLimit | Rimuovi, non più in uso. |
| linkTrackVars | Rimuovi, non più in uso. |
| linkTrackEvents | Rimuovi, non più in uso. |

## Aggiornare le chiamate e le variabili di tracciamento {#section_96E7D9B3CDAC444789503B7E7F139AB9}

Invece di utilizzare le `Track` chiamate e `TrackLink` gli SDK versione 4 incentrati sul Web, l&#39;SDK usa due metodi che hanno un senso nel mondo dei dispositivi mobili:

* `TrackState` Gli stati sono le visualizzazioni disponibili nell’app, ad esempio &quot;dashboard iniziale&quot;, &quot;impostazioni dell’app&quot;, &quot;carrello&quot; e così via. Questi stati sono simili alle pagine di un sito Web e le chiamate `trackState` incrementano le visualizzazioni di pagina.

* `TrackAction` Le azioni sono gli eventi che avvengono nell’app e che desideri misurare, come &quot;accessi&quot;, &quot;tap sui banner&quot;, &quot;abbonamenti ai feed&quot; e altre metriche. Queste chiamate non incrementano le visualizzazioni di pagina.

The `contextData` parameter for both of these methods contains name-value pairs that are sent as context data.

### Eventi, prop, eVar

Se hai esaminato i metodi [](/help/universal-windows/c-configuration/methods.md)SDK, probabilmente ti chiederai dove impostare eventi, eVar, prop, eredi ed elenchi. Nella versione 4, non è più possibile assegnare questi tipi di variabili direttamente nell&#39;app. L’SDK utilizza invece i dati contestuali e le regole di elaborazione per mappare i dati dell’app sulle variabili di Analytics a scopo di reportistica.

Le regole di elaborazione offrono i seguenti vantaggi:

* Puoi modificare la mappatura dei dati senza inviare un aggiornamento all’App Store.
* Puoi assegnare ai dati dei nomi significativi invece di impostare variabili specifiche per una suite di rapporti.
* L’invio di dati aggiuntivi ha un impatto minimo. Questi valori verranno visualizzati nei rapporti solo dopo che saranno stati mappati utilizzando delle regole di elaborazione.

Per ulteriori informazioni, consulta la sezione *Regole* di elaborazione nella panoramica [di](/help/universal-windows/analytics/analytics.md)Analytics.

Eventuali valori che venivano assegnati direttamente alle variabili ora dovranno essere aggiunti ai dati contestuali. This means that calls to `SetProp`, `SetEvar`, and assignments to persistent context data should all be removed and the values added to context data.

### AppSection/Server, GeoZip, transaction ID, Campaign e altre variabili standard

Tutti gli altri dati che precedentemente impostavi sull’oggetto di misurazione, comprese le variabili elencate sopra, devono essere aggiunti invece ai dati contestuali. In altre parole, gli unici dati inviati con una `TrackState` chiamata o `TrackAction` chiamata sono il payload nel `data` parametro.

**Sostituire le chiamate di tracciamento**

Throughout your code, replace the following methods with a call to `trackState` or `trackAction`:

**Migrazione da 3.x:**

* TrackAppState (TrackState)
* TrackEvents (TrackAction)
* Track (TrackAction)
* TrackLinkURL (TrackAction)

## Servizio ID personalizzato {#section_2CF930C13BA64F04959846E578B608F3}

Sostituisci la variabile `visitorID` con una chiamata a `setUserIdentifier`.

## Tracciamento offline {#section_5D4CD8CD1BE041A79A8657E31C0D24C6}

Offline tracking is enabled in the `ADBMobileConfig.json` file. All other offline configuration is done automatically.

In tutto il codice, devi rimuovere le chiamate ai seguenti metodi:

**Migrazione da 3.x:**

* SetOnline
* SetOffline

## Variabile &quot;products&quot; {#section_AFBA36F3718C44D29AF81B9E1056A1B4}

Poiché la variabile &quot;products&quot; non è disponibile nelle regole di elaborazione, puoi usare la sintassi seguente per impostare `products`products:

```js
// create a processing rule to set the corresponding product event. 
// for example, set the Product Views event when context data a.action = "product view" 
var cdata = new Windows.Foundation.Collections.PropertySet(); 
cdata["&&products"] = ";Cool Shoe"; 
ADB.Analytics.trackAction("product view", cdata);
```

![](assets/prod-view.png)

Il valore di `"&&products"` (in questo esempio, il valore è `";Cool Shoe`&quot;) deve seguire la sintassi della stringa products per il tipo di evento che si sta monitorando.
