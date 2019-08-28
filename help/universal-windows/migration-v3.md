---
description: Questa sezione descrive come migrare dalla versione 3.x di un SDK Windows Mobile precedente all’SDK 4.x della piattaforma UWP (Universal Windows Platform) per soluzioni Experience Cloud.
seo-description: Questa sezione descrive come migrare dalla versione 3.x di un SDK Windows Mobile precedente all’SDK 4.x della piattaforma UWP (Universal Windows Platform) per soluzioni Experience Cloud.
seo-title: Migrazione a 4. x
solution: Marketing Cloud, Analytics
title: Migrazione a 4. x
topic: Sviluppatore e implementazione
uuid: bdd 6 c 5 cd -3892-4 e 99-b 69 e -77105 ad 66 e 25
translation-type: tm+mt
source-git-commit: 68bc21f1c6dba2faeed332495592114af90c8f61

---


# Migrazione agli SDK 4. x{#migrate-to-x}

Questa sezione descrive come migrare dalla versione 3. x dell'SDK di Windows Mobile all'SDK 4. x della piattaforma UWP (Universal Windows Platform) per soluzioni Experience Cloud.

Con il passaggio alla versione 4. x, tutte le funzionalità sono ora accessibili tramite metodi statici. Non è più necessario tenere traccia dei propri oggetti.

Le sezioni seguenti illustrano la procedura per migrare dalla versione 3.x alla versione 4.x.

## Remove unused properties {#section_145222EAA20F4CC2977DD883FDDBBFC5}

Avrai probabilmente notato il nuovo file `ADBMobileConfig.json` incluso nel download. Questo file contiene impostazioni globali specifiche per le applicazioni e sostituisce la maggior parte delle variabili di configurazione utilizzate nelle versioni precedenti.

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

Nella tabella seguente sono elencate le variabili di configurazione che devi spostare al file di configurazione. Sposta il set di valori della variabile nella prima colonna alla variabile nella seconda colonna, quindi elimina la variabile di configurazione precedente dal codice.

### Migrazione da 3. x

La tabella seguente fornisce un elenco delle variabili negli SDK 3. x e il nuovo nome negli SDK 4. x:

| Variabile/Metodo di configurazione | Variable in the `ADBMobileConfig.json` file. |
|--- |--- |
| offlineTrackingEnabled | "offlineEnabled" |
| reportSuiteIDs | "rsids" |
| trackingServer | "server" |
| charSet | "charset" |
| currencyCode | "currency" |
| ssl | "ssl" |
| setOfflineHitLimit | Rimuovi, non è più utilizzata. |
| linkTrackVars | Rimuovi, non è più utilizzata. |
| linkTrackEvents | Rimuovi, non è più utilizzata. |

## Update track calls and tracking variables {#section_96E7D9B3CDAC444789503B7E7F139AB9}

Invece di utilizzare le chiamate `Track` e `TrackLink`, l’SDK della versione 4 utilizza due metodi che hanno più senso nel mondo dei dispositivi mobili:

* `TrackState` Gli stati sono le visualizzazioni disponibili nell'app, ad esempio “dashboard iniziale”, “impostazioni dell'app”, “carrello” e così via. Questi stati sono simili alle pagine di un sito Web e le chiamate `trackState` incrementano le visualizzazioni di pagina.

* `TrackAction` Le azioni sono gli eventi che avvengono nell’applicazione e che desideri misurare, come “accessi”, “tap sui banner”, “abbonamenti ai feed” e altre metriche. Tali chiamate non incrementano le visualizzazioni di pagina.

Il parametro `contextData` di entrambi questi metodi contiene coppie nome-valore che vengono inviate come dati contestuali.

### Eventi, prop, evar

Se hai esaminato i metodi [SDK](/help/universal-windows/c-configuration/methods.md), ti chiederai probabilmente dove impostare eventi, evar, prop, eredi ed elenchi. Nella versione 4, non è più possibile assegnare direttamente nell'app questi tipi di variabili. L'SDK utilizza invece i dati contestuali e le regole di elaborazione per mappare i dati dell'app sulle variabili di Analytics a scopo di reportistica.

Le regole di elaborazione offrono i seguenti vantaggi:

* È possibile cambiare la mappatura dei dati senza dover inviare un aggiornamento all'App Store.
* Invece di impostare variabili specifiche per una suite di rapporti, è possibile assegnare ai dati dei nomi significativi.
* L’impatto dell’invio di dati aggiuntivi è limitato. Questi valori compariranno nei rapporti solo dopo che questi saranno stati mappati utilizzando delle regole di elaborazione.

Per ulteriori informazioni, consulta la *sezione Regole* di elaborazione nella [panoramica di Analytics](/help/universal-windows/analytics/analytics.md).

Eventuali valori che venivano assegnati direttamente alle variabili ora dovranno essere aggiunti ai dati contestuali. This means that calls to `SetProp`, `SetEvar`, and assignments to persistent context data should all be removed and the values added to context data.

### Appsection/Server, geozip, transaction ID, Campaign e altre variabili standard

Tutti gli altri dati che precedentemente impostavi sull’oggetto di misurazione, comprese le variabili elencate qui sopra, devono essere aggiunti invece ai dati contestuali. Ovvero, gli unici dati inviati con una `TrackState` chiamata o `TrackAction` chiamano il payload nel `data` parametro.

**Sostituire le chiamate di tracciamento**

Nell’intero codice, sostituisci i metodi seguenti con una chiamata a `trackState` o `trackAction`:

**Migrazione dalla versione 3.x**

* TrackAppState (TrackState)
* TrackEvents (TrackAction)
* Track (TrackAction)
* TrackLinkURL (TrackAction)

## Servizio ID personale {#section_2CF930C13BA64F04959846E578B608F3}

Replace the `visitorID` variable with a call to `setUserIdentifier`.

## Offline tracking {#section_5D4CD8CD1BE041A79A8657E31C0D24C6}

Il tracciamento offline è attivato nel `ADBMobileConfig.json` file. Tutte le altre configurazioni offline vengono eseguite automaticamente.

Nell’intero codice, devi rimuovere le chiamate ai seguenti metodi:

**Migrazione dalla versione 3.x**

* SetOnline
* SetOffline

## Products variable {#section_AFBA36F3718C44D29AF81B9E1056A1B4}

Poiché la variabile "" non è disponibile nelle regole di elaborazione, puoi usare la sintassi seguente per impostare `products`products:

```js
// create a processing rule to set the corresponding product event. 
// for example, set the Product Views event when context data a.action = "product view" 
var cdata = new Windows.Foundation.Collections.PropertySet(); 
cdata["&&products"] = ";Cool Shoe"; 
ADB.Analytics.trackAction("product view", cdata);
```

![](assets/prod-view.png)

The value of `"&&products"` (in this example, the value is `";Cool Shoe`") should follow the products string syntax for the type of event that you are tracking.
