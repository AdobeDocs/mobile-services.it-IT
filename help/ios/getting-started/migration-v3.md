---
description: Queste informazioni sono utili per passare dalle versioni 3.x o 2.x della libreria iOS alla versione 4.x.
seo-description: Queste informazioni sono utili per passare dalle versioni 3.x o 2.x della libreria iOS alla versione 4.x.
seo-title: Migrazione alla libreria iOS 4.x
solution: Experience Cloud,Analytics
title: Migrazione alla libreria iOS 4.x
topic: Developer and implementation
uuid: 5668972b-f355-4e03-9df0-8c82ddf6809b
translation-type: tm+mt
source-git-commit: aab04abeb5edb6be886002e27ef1c5340b0a8f0d
workflow-type: tm+mt
source-wordcount: '895'
ht-degree: 100%

---


# Migrazione alla libreria iOS 4.x {#migrating-to-the-x-ios-library}

Queste informazioni sono utili per passare dalle versioni 3.x o 2.x della libreria iOS alla versione 4.x.

>[!IMPORTANT]
>
>L’SDK utilizza `NSUserDefaults` per memorizzare i dati che sono necessari per calcolare gli utenti univoci, le metriche del ciclo di vita e altri dati relativi alle funzionalità SDK di base. Se modifichi o rimuovi i valori di `NSUserDefaults` che sono attesi dall’SDK, si potrebbe determinare un comportamento imprevisto con conseguente incoerenza dei dati.

Nella versione 4.x della libreria SDK iOS, i metodi pubblici sono consolidati in un’unica intestazione. Inoltre, le funzionalità sono ora accessibili tramite metodi di livello di classe; pertanto, non è più necessario tenere traccia di puntatori, istanze o singleton.

## Eventi, prop ed eVar {#section_76EA6F5611184C5CAE6E62956D84D7B6}

Nella versione 4, non è più possibile assegnare direttamente nell’app variabili quali eventi, eVar, prop, eredi ed elenchi. L’SDK utilizza invece i dati contestuali e le regole di elaborazione per mappare i dati dell’app sulle variabili di Analytics a scopo di reportistica.

Le regole di elaborazione offrono i seguenti vantaggi:

* Puoi modificare la mappatura dei dati senza inviare un aggiornamento all’App Store.
* Puoi assegnare ai dati dei nomi significativi invece di impostare variabili specifiche per una suite di rapporti.
* L’invio di dati aggiuntivi ha un impatto minimo.

   Questi valori verranno inclusi nei rapporti solo dopo che saranno stati mappati mediante le regole di elaborazione.

>[!TIP]
>
>I valori che venivano assegnati direttamente alle variabili ora dovranno essere aggiunti al dizionario NSDictionary `data`.

## Rimuovere le proprietà non utilizzate {#section_145222EAA20F4CC2977DD883FDDBBFC5}

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
1. Rimuovi dal codice la recedente variabile di configurazione.

### Informazioni sulla migrazione

Nella tabella seguente sono elencate le variabili di configurazione che devi spostare al file di configurazione.

#### Migrazione dalla versione 3.x

Sposta il valore riportato nella prima colonna alla variabile della seconda colonna.

| Variabile di configurazione | Variabile nel file `ADBMobileConfig.json` |
|--- |--- |
| offlineTrackingEnabled | &quot;offlineEnabled&quot; |
| offlineHitLimit | &quot;batchLimit&quot; |
| reportSuiteIDs | &quot;rsids&quot; |
| trackingServer | &quot;server&quot; |
| charSet | &quot;charset&quot; |
| currencyCode | &quot;currency&quot; |
| ssl | &quot;ssl&quot; |
| linkTrackVars | Rimuovi, non più in uso. |
| linkTrackEvents | Rimuovi, non più in uso. |


#### Migrazione dalla versione 2.x

Sposta il valore riportato nella prima colonna alla variabile della seconda colonna.

| Variabile di configurazione | Variabile nel file `ADBMobileConfig.json` |
|--- |--- |
| trackOffline | &quot;offlineEnabled&quot; |
| offlineLimit | &quot;batchLimit&quot; |
| account | &quot;rsids&quot; |
| trackingServer | &quot;server&quot;, rimuovi il prefisso `"https://"`. Il prefisso del protocollo viene aggiunto automaticamente in base all’impostazione &quot;ssl&quot;. |
| trackingServerSecure | Rimuovi. Per le connessioni sicure, definisci &quot;server&quot; e quindi abilita &quot;ssl&quot;. |
| charSet | &quot;charset&quot; |
| currencyCode | &quot;currency&quot; |
| ssl | &quot;ssl&quot; |
| linkTrackVars | Rimuovi, non più in uso. |
| linkTrackEvents | Rimuovi, non più in uso. |
| timestamp | Rimuovi, non più configurabile. |
| dc | Rimuovi, non più in uso. |
| userAgent | Rimuovi, non più configurabile. |
| dynamicVariablePrefix | Rimuovi, non più in uso. |
| visitorNamespace | Rimuovi, non più in uso. |
| usePlugins | Rimuovi, non più in uso. |
| useBestPractices, tutte le chiamate alla misurazione churn (getChurnInstance) | Rimuovi, sostituito dalle metriche del ciclo di vita. Per ulteriori informazioni, vedi [Metriche del ciclo di vita](/help/ios/metrics.md). |


## Aggiornare le chiamate e le variabili di tracciamento {#section_96E7D9B3CDAC444789503B7E7F139AB9}

Invece di usare le chiamate `track` e `trackLink` incentrate sul web, la versione 4 dell&#39;SDK usa i metodi seguenti:

* Gli stati `trackState:data:` sono le visualizzazioni disponibili nell&#39;app, ad esempio `home dashboard`, `app settings`, `cart` e così via.

   Questi stati sono simili alle pagine di un sito Web e le chiamate `trackState` incrementano le visualizzazioni di pagina.

* Azioni `trackAction:data:`, come `logons`, `banner taps`, `feed subscriptions` e altre metriche che si verificano nell&#39;app e che desideri misurare.

Il parametro `data` di entrambi questi metodi è un dizionario `NSDictionary` contenente coppie nome-valore che vengono inviate come dati contestuali.

### Eventi, prop, eVar

Nella versione 4, non è più possibile assegnare direttamente nell’app variabili quali eventi, eVar, prop, eredi ed elenchi. L’SDK ora utilizza i dati contestuali e le regole di elaborazione per mappare i dati dell’app sulle variabili di Analytics a scopo di reportistica.

Le regole di elaborazione offrono i seguenti vantaggi:

* Puoi modificare la mappatura dei dati senza inviare un aggiornamento all’App Store.
* Puoi assegnare ai dati dei nomi significativi invece di impostare variabili specifiche per una suite di rapporti.
* L’invio di dati aggiuntivi ha un impatto minimo.

   Questi valori verranno inclusi nei rapporti solo dopo che saranno stati mappati mediante le regole di elaborazione. Per ulteriori informazioni, consulta [Regole di elaborazione e dati contestuali](/help/ios/getting-started/proc-rules.md).

Eventuali valori che venivano assegnati direttamente alle variabili ora dovranno essere aggiunti al dizionario `data` `NSDictionary`. È quindi necessario rimuovere tutte le chiamate a `setProp`, `setEvar` e le assegnazioni a dati contestuali persistenti; i relativi valori devono essere aggiunti al parametro `data`.

### AppSection/Server, GeoZip, transaction ID, Campaign e altre variabili standard

I dati che precedentemente impostavi sull&#39;oggetto di misurazione, comprese le variabili elencate qui sopra, devono essere aggiunti al dizionario `data` `NSDictionary`. L&#39;unico dato che viene inviato con una chiamata `trackState` o `trackAction` è il payload nel parametro `data`.

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

## ID visitatore personalizzato {#section_2CF930C13BA64F04959846E578B608F3}

Sostituisci la variabile `visitorID` con una chiamata a `setUserIdentifier:`.

## Tracciamento offline {#section_5D4CD8CD1BE041A79A8657E31C0D24C6}

Il tracciamento offline è abilitato nel file `ADBMobileConfig.json` e tutte le altre configurazioni offline vengono eseguite in automatico.

Nel codice, devi rimuovere le chiamate ai seguenti metodi:

### Versione 3.x

* `setOnline`
* `setOffline`

### Versione 2.x

* `forceOffline`
* `forceOnline`

## Variabile &quot;products&quot; {#section_AFBA36F3718C44D29AF81B9E1056A1B4}

Poiché la variabile &quot;products&quot; non è disponibile nelle regole di elaborazione, puoi usare la sintassi seguente per impostare `products`products:

```objective-c
//create a processing rule to set the corresponding product event. 
// for example, set prodView event when context data a.action = "product view" 
[ADBMobile trackAction:@"LikeButtonClicked"  
                  data:@{@"&&products" : @";Cool Shoe"}];
```

![](assets/prod-view.png)