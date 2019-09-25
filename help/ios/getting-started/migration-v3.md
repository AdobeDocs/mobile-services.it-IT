---
description: Queste informazioni sono utili per passare dalle versioni 3.x o 2.x della libreria iOS alla versione 4.x.
seo-description: Queste informazioni sono utili per passare dalle versioni 3.x o 2.x della libreria iOS alla versione 4.x.
seo-title: Migrating to the 4.x iOS library
solution: Marketing Cloud,Analytics
title: Migrazione alla libreria iOS 4.x
topic: Sviluppatore e implementazione
uuid: 5668972b-f355-4e03-9df0-8c82ddf6809b
translation-type: tm+mt
source-git-commit: 68bc21f1c6dba2faeed332495592114af90c8f61

---


# Migrating to the 4.x iOS library{#migrating-to-the-x-ios-library}

Queste informazioni sono utili per passare dalle versioni 3.x o 2.x della libreria iOS alla versione 4.x.

>[!IMPORTANT]
>
>The SDK uses `NSUserDefaults` to store data that is needed to calculate unique users, lifecycle metrics, and other data related to core SDK functionality.  Se modifichi o rimuovi i valori di `NSUserDefaults` che sono attesi dall’SDK, si potrebbe determinare un comportamento imprevisto con conseguente incoerenza dei dati.

Nella versione 4.x della libreria SDK iOS, i metodi pubblici sono consolidati in un unico header. Inoltre, la funzionalità ora è accessibile tramite metodi a livello di classe, pertanto non è necessario tenere traccia di puntatori, istanze o singleton.

## Events, props, and eVars {#section_76EA6F5611184C5CAE6E62956D84D7B6}

Nella versione 4, non è più possibile assegnare direttamente nell'app variabili quali eventi, eVar, prop, eredi ed elenchi. L'SDK utilizza invece i dati contestuali e le regole di elaborazione per mappare i dati dell'app sulle variabili di Analytics a scopo di reportistica.

Le regole di elaborazione offrono i seguenti vantaggi:

* È possibile cambiare la mappatura dei dati senza dover inviare un aggiornamento all'App Store.
* Invece di impostare variabili specifiche per una suite di rapporti, è possibile assegnare ai dati dei nomi significativi.
* L'impatto dell'invio di dati aggiuntivi è limitato.

   Questi valori compariranno nei rapporti solo dopo che saranno stati mappati utilizzando delle regole di elaborazione.

>[!TIP]
>
>Values that you were assigning directly to variables should now be added to the `data` NSDictionary.

## Remove unused properties {#section_145222EAA20F4CC2977DD883FDDBBFC5}

Il nuovo file `ADBMobileConfig.json` contiene impostazioni globali specifiche per le applicazioni e sostituisce la maggior parte delle variabili di configurazione utilizzate nelle versioni precedenti. Ecco un esempio di file `ADBMobileConfig.json`:

```js
{ 
    "version" : "1.0", 
    "analytics" : { 
        "rsids" : "coolApp", 
        "server" : "my.CoolApp.com", 
        "charset" : "UTF-8", 
        "ssl" : true, 
        "offlineEnabled" : true, 
        "lifecycleTimeout" : 5, 
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


### Spostare il file di configurazione

Per spostare il file di configurazione:

1. Sposta il valore impostato per la variabile della prima colonna alla variabile della seconda colonna.
1. Rimuovi dal codice la precedente variabile di configurazione.

### Informazioni sulla migrazione

Nella tabella seguente sono elencate le variabili di configurazione che devi spostare al file di configurazione.

#### Migrazione dalla versione 3.x

Sposta il valore riportato nella prima colonna alla variabile della seconda colonna.

| Variabile di configurazione | Variable in the `ADBMobileConfig.json` file |
|--- |--- |
| offlineTrackingEnabled | "offlineEnabled" |
| offlineHitLimit | "batchLimit" |
| reportSuiteIDs | "rsids" |
| trackingServer | "server" |
| charSet | "charset" |
| currencyCode | "currency" |
| ssl | "ssl" |
| linkTrackVars | Rimuovi, non è più utilizzata. |
| linkTrackEvents | Rimuovi, non è più utilizzata. |


#### Migrazione dalla versione 2.x

Sposta il valore riportato nella prima colonna alla variabile della seconda colonna.

| Variabile di configurazione | Variable in the `ADBMobileConfig.json` file |
|--- |--- |
| trackOffline | "offlineEnabled" |
| offlineLimit | "batchLimit" |
| account | "rsids" |
| trackingServer | "server", remove the `"https://"` prefix. Il prefisso del protocollo viene aggiunto in automatico in base all'impostazione "ssl". |
| trackingServerSecure | Rimuovi. Per connessioni sicure, definisci "server" e quindi abilita "ssl". |
| charSet | "charset" |
| currencyCode | "currency" |
| ssl | "ssl" |
| linkTrackVars | Rimuovi, non è più utilizzata. |
| linkTrackEvents | Rimuovi, non è più utilizzata. |
| timestamp | Rimuovi, non è più configurabile. |
| dc | Rimuovi, non è più utilizzata. |
| userAgent | Rimuovi, non è più configurabile. |
| dynamicVariablePrefix | Rimuovi, non è più utilizzata. |
| visitorNamespace | Rimuovi, non è più utilizzata. |
| usePlugins | Rimuovi, non è più utilizzata. |
| useBestPractices  tutte le chiamate alla misurazione churn (getChurnInstance ) | Remove, replaced by lifecycle metrics. Per ulteriori informazioni, vedi [Metriche del ciclo di vita](//help/ios/metrics.md). |


## Update track calls and tracking variables {#section_96E7D9B3CDAC444789503B7E7F139AB9}

Invece di usare le chiamate `track` e `trackLink` incentrate sul web, la versione 4 dell'SDK usa i metodi seguenti:

* `trackState:data:` states are the views that are available in your app, such as , , , and so on.`home dashboard``app settings``cart`

   Questi stati sono simili alle pagine di un sito Web e le chiamate `trackState` incrementano le visualizzazioni di pagina.

* `trackAction:data:` actions , such as , , , and other metrics that occur in your app and that you want to measure.`logons``banner taps``feed subscriptions`

Il parametro `data` di entrambi questi metodi è un dizionario `NSDictionary` contenente coppie nome-valore che vengono inviate come dati contestuali.

### Eventi, prop, eVar

Nella versione 4, non è più possibile assegnare direttamente nell'app variabili quali eventi, eVar, prop, eredi ed elenchi. L'SDK utilizza ora i dati contestuali e le regole di elaborazione per mappare i dati dell'app sulle variabili di Analytics a scopo di reportistica.

Le regole di elaborazione offrono i seguenti vantaggi:

* È possibile cambiare la mappatura dei dati senza dover inviare un aggiornamento all'App Store.
* Invece di impostare variabili specifiche per una suite di rapporti, è possibile assegnare ai dati dei nomi significativi.
* L'impatto dell'invio di dati aggiuntivi è limitato.

   Questi valori compariranno nei rapporti solo dopo che saranno stati mappati utilizzando delle regole di elaborazione. Per ulteriori informazioni, consulta [Regole di elaborazione e dati contestuali](/help/ios/getting-started/proc-rules.md).

Eventuali valori che venivano assegnati direttamente alle variabili ora dovranno essere aggiunti al dizionario   `data``NSDictionary`. This means that calls to `setProp`, `setEvar`, and assignments to persistent context data should all be removed and the values be added to the `data` parameter.

### AppSection/Server, GeoZip, transaction ID, Campaign, and other standard variables

I dati che precedentemente impostavi sull'oggetto di misurazione, comprese le variabili elencate qui sopra, devono essere aggiunti al dizionario `data``NSDictionary` . L'unico dato che viene inviato con una chiamata `trackState` o `trackAction` è il payload nel parametro `data`.

### Sostituire le chiamate di tracciamento

Nel codice, sostituisci i metodi seguenti con una chiamata a `trackState` o `trackAction`:

#### Migrazione dalla versione 3.x

* `trackAppState (trackState)`
* `trackEvents (trackAction)`
* `track (trackAction)`
* `trackWithContextData (trackAction)`
* `trackLinkURL (trackAction)`

#### Migrazione dalla versione 2.x

* `track (trackState)`
* `trackLink (trackAction)`

## Custom visitor ID {#section_2CF930C13BA64F04959846E578B608F3}

Replace the `visitorID` variable with a call to `setUserIdentifier:`.

## Offline tracking {#section_5D4CD8CD1BE041A79A8657E31C0D24C6}

Offline tracking is enabled in the `ADBMobileConfig.json` file, and all other offline configuration is done automatically.

Nel codice, devi rimuovere le chiamate ai seguenti metodi:

### Versione 3.x

* `setOnline`
* `setOffline`

### Versione 2.x

* `forceOffline`
* `forceOnline`

## Products variable {#section_AFBA36F3718C44D29AF81B9E1056A1B4}

Poiché la variabile "" non è disponibile nelle regole di elaborazione, puoi usare la sintassi seguente per impostare `products`products:

```objective-c
//create a processing rule to set the corresponding product event. 
// for example, set prodView event when context data a.action = "product view" 
[ADBMobile trackAction:@"LikeButtonClicked"  
                  data:@{@"&&products" : @";Cool Shoe"}];
```

![](assets/prod-view.png)