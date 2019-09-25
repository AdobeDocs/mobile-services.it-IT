---
description: Queste informazioni sono utili per passare dalla versione 3.x o 2.x della libreria Android alla versione 4.x.
keywords: android;libreria;mobile;sdk
seo-description: Queste informazioni sono utili per passare dalla versione 3.x o 2.x della libreria Android alla versione 4.x.
seo-title: Migrazione alla libreria Android 4.x
solution: Marketing Cloud,Analytics
title: Migrazione alla libreria Android 4.x
topic: Sviluppatore e implementazione
uuid: 906e83bb-2faf-4aa2-ac9b-3fba6b833c7e
translation-type: tm+mt
source-git-commit: 68bc21f1c6dba2faeed332495592114af90c8f61

---


# Migrating to the Android 4.x library {#migrating-to-the-android-x-library}

Queste informazioni sono utili per passare dalla versione 3.x o 2.x della libreria Android alla versione 4.x.

>[!IMPORTANT]
>
>The SDK uses `SharedPreferences` to store data that is needed to calculate unique users, lifecycle metrics, and other data related to core SDK functionality.  Se modifichi o rimuovi i valori di `SharedPreferences` che sono attesi dall’SDK, si potrebbe determinare un comportamento imprevisto con conseguente incoerenza dei dati.

Nella versione 4.x della libreria SDK, tutti i metodi pubblici sono consolidati in un unico header. Inoltre, tutte le funzionalità sono ora accessibili tramite metodi di livello di classe; pertanto, non è più necessario tenere traccia di puntatori, istanze o singleton.

## Events, props, and eVars {#section_76EA6F5611184C5CAE6E62956D84D7B6}

Nella versione 4, non è più possibile assegnare direttamente nell'app variabili quali eventi, eVar, prop, eredi ed elenchi. L'SDK utilizza invece i dati contestuali e le regole di elaborazione per mappare i dati dell'app sulle variabili di Analytics a scopo di reportistica.

Le regole di elaborazione offrono i seguenti vantaggi:

* È possibile cambiare la mappatura dei dati senza dover inviare un aggiornamento all'App Store.
* Invece di impostare variabili specifiche per una suite di rapporti, è possibile assegnare ai dati dei nomi significativi.
* L'impatto dell'invio di dati aggiuntivi è limitato.

   Questi valori compariranno nei rapporti solo dopo che saranno stati mappati utilizzando delle regole di elaborazione.

>[!TIP]
>
>Values that you assigned directly to variables should be added to the `data` HashMap.

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

## Moving the configuration file and migrating to version 4 {#section_0B844235E0B04DD4B36976A73DB28FB5}

Nella tabella seguente sono elencate le variabili di configurazione che devi spostare al file di configurazione.

### Spostare il file di configurazione

1. Sposta il valore impostato per la variabile della prima colonna alla variabile della seconda colonna.
1. Rimuovi dal codice la precedente variabile di configurazione.

### Migrazione dalla versione 3.x

Per eseguire la migrazione dalla versione 3.x alla versione 4, spostare la variabile di configurazione/il valore del metodo nella `ADBMobileConfig.json` variabile.

| Configuration Variable or Method | Variable in the `ADBMobileConfig.json` file |
|--- |--- |
| setOfflineTrackingEnabled | "offlineEnabled" |
| setOfflineHitLimit | "batchLimit" |
| reportSuiteIDs | "rsids" |
| trackingServer | "server" |
| charSet | "charset" |
| currencyCode | "currency" |
| ssl | "ssl" |
| linkTrackVars | Rimuovi, non è più utilizzata. |
| linkTrackEvents | Rimuovi, non è più utilizzata. |

### Migrazione dalla versione 2.x

To migrate from version 2.x to version 4, move the value from the first column to the variable in the second column.

| Variabile di configurazione | Variable in the `ADBMobileConfig.json` file |
| --- |--- |
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
| useBestPractices  tutte le chiamate alla misurazione churn (getChurnInstance) | Rimuovi, sostituito da Metriche del ciclo di vita. |

## Update track calls and tracking variables {#section_96E7D9B3CDAC444789503B7E7F139AB9}

Invece di usare le chiamate `track` e `trackLink` incentrate sul web, la versione 4 dell'SDK usa i metodi seguenti:

* `trackState`, che sono le visualizzazioni disponibili nell'app, ad esempio `home dashboard`, `app settings`, `cart`e così via.

   Questi stati sono simili alle pagine di un sito Web e le chiamate `trackState` incrementano le visualizzazioni di pagina.

* `trackAction` azioni, come `logons`, `banner taps``feed subscriptions`, e così via, che si verificano nell'app e che desideri misurare.

The `contextData` parameter for both of these methods is a `HashMap<String, Object>`, which contains the name-value pairs that are sent as context data.

## Eventi, prop ed eVar

Nella versione 4, non è più possibile assegnare direttamente nell'app variabili quali eventi, eVar, prop, eredi ed elenchi. L'SDK utilizza ora i dati contestuali e le regole di elaborazione per mappare i dati dell'app sulle variabili di Analytics a scopo di reportistica.

Le regole di elaborazione offrono i seguenti vantaggi:

* È possibile cambiare la mappatura dei dati senza dover inviare un aggiornamento all'App Store.
* Invece di impostare variabili specifiche per una suite di rapporti, è possibile assegnare ai dati dei nomi significativi.
* L'impatto dell'invio di dati aggiuntivi è limitato.

   Questi valori compariranno nei rapporti solo dopo che saranno stati mappati utilizzando delle regole di elaborazione. Per ulteriori informazioni, vedere Regole di [elaborazione e dati](/help/android/getting-started/proc-rules.md)contestuali.

Eventuali valori che venivano assegnati direttamente alle variabili ora dovranno essere aggiunti all'HashMap `data`. This means that calls to `setProp`, `setEvar`, and assignments to persistent context data should be removed and the values be added to the `data` parameter.

## AppSection/server, GeoZip, ID transazione, Campaign e altre variabili standard

I dati che precedentemente impostavi sull'oggetto di misurazione, comprese le variabili elencate qui sopra, devono essere aggiunti all'HashMap `data`. L'unico dato che viene inviato con una chiamata `trackState` o `trackAction` è il payload nel parametro `data`.

### Sostituire le chiamate di tracciamento

Sostituisci i metodi seguenti con una chiamata a `trackState` o `trackAction`:

* **Migrazione dalla versione 3.x**

   * `trackAppState (trackState)`
   * `trackEvents (trackAction)`
   * `track (trackAction)`
   * `trackLinkURL (trackAction)`

* **Migrazione dalla versione 2.x**

   * `track (trackState)`
   * `trackLink (trackAction)`

## Custom visitor ID {#section_2CF930C13BA64F04959846E578B608F3}

Replace the `visitorID` variable with a call to `setUserIdentifier`.

## Offline tracking {#section_5D4CD8CD1BE041A79A8657E31C0D24C6}

Offline tracking is enabled in the `ADBMobileConfig.json` file, and all other offline configuration is done automatically.

Rimuovi le chiamate ai seguenti metodi:

**Versione 3.x**

* `setOnline`
* `setOffline`

**Versione 2.x**

* `forceOffline`
* `forceOnline`

## Products variable {#section_AFBA36F3718C44D29AF81B9E1056A1B4}

For more information about the products variable, see [Products variable](/help/android/analytics-main/products/products.md).

