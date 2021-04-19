---
description: Queste informazioni sono utili per passare dalla versione 3.x o 2.x della libreria Android alla versione 4.x.
keywords: android,libreria,mobile,sdk
seo-description: Queste informazioni sono utili per passare dalla versione 3.x o 2.x della libreria Android alla versione 4.x.
seo-title: Migrazione alla libreria Android 4.x
solution: Experience Cloud,Analytics
title: Migrazione alla libreria Android 4.x
topic-fix: Developer and implementation
uuid: 906e83bb-2faf-4aa2-ac9b-3fba6b833c7e
exl-id: 8061c1ab-aaaf-4d4c-9bd5-b2f80b6b06a3
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '884'
ht-degree: 100%

---

# Migrazione alla libreria Android 4.x {#migrating-to-the-android-x-library}

Informazioni utili per passare dalla versione 3.x o 2.x della libreria Android alla versione 4.x.

>[!IMPORTANT]
>
>L’SDK utilizza `SharedPreferences` per memorizzare i dati che sono necessari per calcolare gli utenti univoci, le metriche del ciclo di vita e altri dati relativi alle funzionalità SDK di base.  Se modifichi o rimuovi i valori di `SharedPreferences` che sono attesi dall’SDK, si potrebbe determinare un comportamento imprevisto con conseguente incoerenza dei dati.

Nella versione 4.x della libreria, i metodi pubblici sono consolidati in un’unica intestazione. Inoltre, tutte le funzionalità sono ora accessibili tramite metodi di livello di classe; pertanto, non è più necessario tenere traccia di puntatori, istanze o singleton.

## Eventi, prop ed eVar {#section_76EA6F5611184C5CAE6E62956D84D7B6}

Nella versione 4, non è più possibile assegnare nell’app variabili quali eventi, eVar, prop, eredi ed elenchi. L’SDK utilizza invece i dati contestuali e le regole di elaborazione per mappare i dati dell’app sulle variabili di Analytics a scopo di reportistica.

Le regole di elaborazione offrono i seguenti vantaggi:

* Puoi modificare la mappatura dei dati senza inviare un aggiornamento all’App Store.
* Puoi assegnare ai dati dei nomi significativi invece di impostare variabili specifiche per una suite di rapporti.
* L’invio di dati aggiuntivi ha un impatto minimo.

   Questi valori verranno inclusi nei rapporti solo dopo che saranno stati mappati mediante le regole di elaborazione.

>[!TIP]
>
>Eventuali valori che venivano assegnati direttamente alle variabili ora dovranno essere aggiunti all&#39;HashMap `data`.

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

## Spostamento del file di configurazione e migrazione alla versione 4 {#section_0B844235E0B04DD4B36976A73DB28FB5}

Nella tabella seguente sono elencate le variabili di configurazione che devi spostare al file di configurazione.

### Spostare il file di configurazione

1. Sposta il valore impostato per la variabile della prima colonna alla variabile della seconda colonna.
1. Rimuovi dal codice la recedente variabile di configurazione.

### Migrazione dalla versione 3.x

Per eseguire la migrazione dalla versione 3.x alla versione 4, sposta la variabile di configurazione/il valore del metodo nella variabile `ADBMobileConfig.json`.

| Variabile o metodo di configurazione | Variabile nel file `ADBMobileConfig.json` |
|--- |--- |
| setOfflineTrackingEnabled | &quot;offlineEnabled&quot; |
| setOfflineHitLimit | &quot;batchLimit&quot; |
| reportSuiteIDs | &quot;rsids&quot; |
| trackingServer | &quot;server&quot; |
| charSet | &quot;charset&quot; |
| currencyCode | &quot;currency&quot; |
| ssl | &quot;ssl&quot; |
| linkTrackVars | Rimuovi, non più in uso. |
| linkTrackEvents | Rimuovi, non più in uso. |

### Migrazione dalla versione 2.x

Per migrare dalla versione 2.x alla versione 4, sposta il valore riportato nella prima colonna alla variabile della seconda colonna.

| Variabile di configurazione | Variabile nel file `ADBMobileConfig.json` |
| --- |--- |
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
| useBestPractices, tutte le chiamate alla misurazione churn (getChurnInstance) | Rimuovi, sostituito dalle metriche del ciclo di vita. |

## Aggiornare le chiamate e le variabili di tracciamento {#section_96E7D9B3CDAC444789503B7E7F139AB9}

Invece di usare le chiamate `track` e `trackLink` incentrate sul web, la versione 4 dell&#39;SDK usa i metodi seguenti:

* `trackState`, che sono le visualizzazioni disponibili nell&#39;app, ad esempio `home dashboard`, `app settings`, `cart` e così via.

   Questi stati sono simili alle pagine di un sito Web e le chiamate `trackState` incrementano le visualizzazioni di pagina.

* Azioni `trackAction`, come `logons`, `banner taps`, `feed subscriptions` e altre che si verificano nell&#39;app e che desideri misurare.

Il parametro `contextData` di entrambi questi metodi è un `HashMap<String, Object>`, contenente le coppie nome-valore che vengono inviate come dati contestuali.

## Eventi, prop ed eVar

Nella versione 4, non è più possibile assegnare direttamente nell’app variabili quali eventi, eVar, prop, eredi ed elenchi. L’SDK ora utilizza i dati contestuali e le regole di elaborazione per mappare i dati dell’app sulle variabili di Analytics a scopo di reportistica.

Le regole di elaborazione offrono i seguenti vantaggi:

* Puoi modificare la mappatura dei dati senza inviare un aggiornamento all’app store.
* Puoi assegnare ai dati dei nomi significativi invece di impostare variabili specifiche per una suite di rapporti.
* L’invio di dati aggiuntivi ha un impatto minimo.

   Questi valori verranno inclusi nei rapporti solo dopo che saranno stati mappati mediante le regole di elaborazione. Per ulteriori informazioni, consulta [Regole di elaborazione e dati contestuali](/help/android/getting-started/proc-rules.md).

Eventuali valori che venivano assegnati direttamente alle variabili ora dovranno essere aggiunti all&#39;HashMap `data`. È quindi necessario rimuovere tutte le chiamate a `setProp`, `setEvar` e le assegnazioni a dati contestuali persistenti; i relativi valori devono essere aggiunti al parametro `data`.

## AppSection/server, GeoZip, transaction ID, Campaign e altre variabili standard

I dati che precedentemente impostavi sull&#39;oggetto di misurazione, comprese le variabili elencate qui sopra, devono essere aggiunti all&#39;HashMap `data`. L&#39;unico dato che viene inviato con una chiamata `trackState` o `trackAction` è il payload nel parametro `data`.

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

## ID visitatore personalizzato {#section_2CF930C13BA64F04959846E578B608F3}

Sostituisci la variabile `visitorID` con una chiamata a `setUserIdentifier`.

## Tracciamento offline {#section_5D4CD8CD1BE041A79A8657E31C0D24C6}

Il tracciamento offline è abilitato nel file `ADBMobileConfig.json` e tutte le altre configurazioni offline vengono eseguite in automatico.

Rimuovi le chiamate ai seguenti metodi:

**Versione 3.x**

* `setOnline`
* `setOffline`

**Versione 2.x**

* `forceOffline`
* `forceOnline`

## Variabile &quot;products&quot; {#section_AFBA36F3718C44D29AF81B9E1056A1B4}

Per ulteriori informazioni sulla variabile &quot;products&quot;, vedi [Variabile &quot;products&quot;](/help/android/analytics-main/products/products.md).
