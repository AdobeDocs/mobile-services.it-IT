---
description: Questa sezione descrive come migrare dalla versione 3.x di un precedente SDK Windows Mobile all’SDK 4.x della piattaforma UWP (Universal Windows Platform) per le soluzioni Experience Cloud.
solution: Experience Cloud,Analytics
title: Migrare a 4.x
topic-fix: Developer and implementation
uuid: bdd6c5cd-3892-4e99-b69e-77105ad66e25
exl-id: 68de505b-dcff-4a78-9f01-b1d103846281
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '675'
ht-degree: 27%

---

# Migrazione agli SDK 4.x{#migrate-to-x}

Questa sezione descrive come migrare dalla versione 3.x dell’SDK per dispositivi mobili Windows all’SDK 4.x della piattaforma UWP (Universal Windows Platform) per le soluzioni Experience Cloud.

Con il passaggio alla versione 4.x, tutte le funzionalità sono ora accessibili tramite metodi statici. Non è più necessario tenere traccia dei propri oggetti.

Nelle sezioni seguenti viene descritta la procedura di migrazione dalla versione 3.x alla versione 4.x.

## Rimuovere le proprietà non utilizzate {#section_145222EAA20F4CC2977DD883FDDBBFC5}

Probabilmente hai notato un nuovo file `ADBMobileConfig.json` incluso nel download. Questo file contiene impostazioni globali specifiche per le applicazioni e sostituisce la maggior parte delle variabili di configurazione utilizzate nelle versioni precedenti.

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

Nella tabella seguente sono elencate le variabili di configurazione che devi spostare al file di configurazione. Sposta il set di valori per la variabile della prima colonna alla variabile della seconda colonna, quindi rimuovi la vecchia variabile di configurazione dal codice.

### Migrazione da 3.x

La tabella seguente fornisce un elenco di variabili negli SDK 3.x e il nuovo nome negli SDK 4.x:

| Variabile/metodo di configurazione | Variabile nel file `ADBMobileConfig.json`. |
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

Invece di utilizzare le chiamate incentrate sul web `Track` e `TrackLink` , la versione 4 dell&#39;SDK utilizza due metodi che hanno un senso un po&#39; più nel mondo mobile:

* `TrackState` Gli stati sono le visualizzazioni disponibili nell&#39;app, ad esempio &quot;dashboard iniziale&quot;, &quot;impostazioni app&quot;, &quot;carrello&quot; e così via. Questi stati sono simili alle pagine di un sito Web e le chiamate `trackState` incrementano le visualizzazioni di pagina.

* `TrackAction` Le azioni sono gli eventi che avvengono nell’app e che desideri misurare, come &quot;accessi&quot;, &quot;tap sui banner&quot;, &quot;abbonamenti ai feed&quot; e altre metriche. Queste chiamate non incrementano le visualizzazioni di pagina.

Il parametro `contextData` di entrambi questi metodi contiene coppie nome-valore che vengono inviate come dati contestuali.

### Eventi, prop, eVar

Se hai esaminato i [metodi SDK](/help/universal-windows/c-configuration/methods.md), probabilmente ti stai chiedendo dove impostare eventi, eVar, prop, eredi ed elenchi. Nella versione 4, non puoi più assegnare direttamente nell’app questi tipi di variabili. L’SDK utilizza invece i dati contestuali e le regole di elaborazione per mappare i dati dell’app sulle variabili di Analytics a scopo di reportistica.

Le regole di elaborazione offrono i seguenti vantaggi:

* Puoi modificare la mappatura dei dati senza inviare un aggiornamento all’App Store.
* Puoi assegnare ai dati dei nomi significativi invece di impostare variabili specifiche per una suite di rapporti.
* L’invio di dati aggiuntivi ha un impatto minimo. Questi valori verranno visualizzati nei rapporti solo dopo che saranno stati mappati utilizzando delle regole di elaborazione.

Per ulteriori informazioni, consulta la sezione *Regole di elaborazione* in [Panoramica di Analytics](/help/universal-windows/analytics/analytics.md).

Eventuali valori che venivano assegnati direttamente alle variabili ora dovranno essere aggiunti ai dati contestuali. È quindi necessario rimuovere tutte le chiamate a `SetProp`, `SetEvar` e le assegnazioni a dati contestuali persistenti; i relativi valori devono essere aggiunti ai dati contestuali.

### AppSection/Server, GeoZip, transaction ID, Campaign e altre variabili standard

Eventuali altri dati che precedentemente impostavi sull&#39;oggetto di misurazione, comprese le variabili elencate qui sopra, devono essere aggiunti invece ai dati contestuali. In altre parole, gli unici dati inviati con una chiamata `TrackState` o `TrackAction` sono il payload nel parametro `data` .

**Sostituire le chiamate di tracciamento**

In tutto il codice, sostituisci i metodi seguenti con una chiamata a `trackState` o `trackAction`:

**Migrazione da 3.x:**

* TrackAppState (TrackState)
* TrackEvents (TrackAction)
* Track (TrackAction)
* TrackLinkURL (TrackAction)

## Servizio ID personalizzato {#section_2CF930C13BA64F04959846E578B608F3}

Sostituisci la variabile `visitorID` con una chiamata a `setUserIdentifier`.

## Tracciamento offline {#section_5D4CD8CD1BE041A79A8657E31C0D24C6}

Il tracciamento offline è abilitato nel file `ADBMobileConfig.json` . Tutte le altre configurazioni offline vengono eseguite automaticamente.

In tutto il codice, rimuovi le chiamate ai seguenti metodi:

**Migrazione da 3.x:**

* SetOnline
* SetOffline

## Variabile &quot;products&quot;  {#section_AFBA36F3718C44D29AF81B9E1056A1B4}

Poiché la variabile &quot;products&quot; non è disponibile nelle regole di elaborazione, puoi usare la sintassi seguente per impostare `products`products:

```js
// create a processing rule to set the corresponding product event. 
// for example, set the Product Views event when context data a.action = "product view" 
var cdata = new Windows.Foundation.Collections.PropertySet(); 
cdata["&&products"] = ";Cool Shoe"; 
ADB.Analytics.trackAction("product view", cdata);
```

![](assets/prod-view.png)

Il valore di `"&&products"` (in questo esempio, il valore è `";Cool Shoe`&quot;) deve seguire la sintassi della stringa dei prodotti per il tipo di evento di cui si sta eseguendo il tracciamento.
