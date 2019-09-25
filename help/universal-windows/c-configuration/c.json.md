---
description: Informazioni utili per l’utilizzo del file di configurazione ADBMobile JSON.
seo-description: Informazioni utili per l’utilizzo del file di configurazione ADBMobile JSON.
seo-title: Configurazione ADBMobileConfig.json
solution: Marketing Cloud,Analytics
title: Configurazione ADBMobileConfig.json
topic: Sviluppatore e implementazione
uuid: cbcb54a3-4b8f-4651-8ce9-2731ac988545
translation-type: tm+mt
source-git-commit: 19264af3f4a675add6f61c27f4cdaf20033b9bb7

---


# File di configurazione ADBMobileConfig.json {#adbmobileconfig-json-config}

Informazioni utili per l’utilizzo del file di configurazione ADBMobile JSON.

Al momento l’SDK dispone di supporto per più Soluzioni Adobe Experience Cloud, tra cui Analytics, Target e Audience Manager. Ai metodi è applicato il prefisso della relativa soluzione. I metodi di configurazione hanno il prefisso "Config".

* **rsids**

   (**Required by Analytics**) One or more report suites to receive Analytics data. Nel caso di più suite di rapporti, i rispettivi ID devono essere separati da una virgola, senza spazio.

   * Di seguito è riportata la sintassi per questo metodo:

      ```js
      "rsids" : "rsid"
      ```

      ```js
      "rsids" : "rsid1,rsid2"
      ```

* **server**

   (**Richiesto da Analytics e Gestione dell’audience**). Server di Analytics o Gestione dell’audience, in base al nodo principale. This variable should be populated with the server domain, without an `"https://"` or `"https://"` protocol prefix. Il prefisso del protocollo viene gestito automaticamente dalla libreria, in base alla variabile `ssl`.

   Se `ssl` è `true`, viene eseguita una connessione sicura al server. Se `ssl` è `false`, viene eseguita una connessione non sicura.

* **charset**

   Definisce il set di caratteri utilizzato per i dati inviati ad Analytics. Il set di caratteri serve per convertire i dati in entrata in UTF-8 per l’archiviazione e la generazione di rapporti. For more information, see [s.charSet](https://marketing.adobe.com/resources/help/en_US/sc/implement/charset.html).

* **ssl**

   Enables (`true`) or disables (`false`) sending measurement data via SSL (`HTTPS`). Il valore predefinito è `false`.

* **offlineEnabled**

   When enabled (`true`), hits are queued while the device is offline and sent later when the device is online. Per poter usare il tracciamento offline, nella suite di rapporti devono essere abilitate le marche temporali.

   If time stamps are enabled on your report suite, your `offlineEnabled` configuration property *must* be `true`. Se le marche temporali non sono abilitate nella suite di rapporti, la proprietà di configurazione `offlineEnabled` *deve* essere `false`.

   Se questo non viene configurato correttamente, i dati andranno perduti. If you are unsure whether a report suite is timestamp enabled, contact Customer Care. If you are currently reporting AppMeasurement data to a report suite that also collects data from JavaScript, you might need to set up a separate report suite for mobile data or include a custom timestamp on all JavaScript hits using the `s.timestamp` variable.

   Il valore predefinito è `false`.

* **lifecycleTimeout**

   Specifica l’intervallo di tempo, in secondi, che deve trascorrere tra un avvio dell’app e quello successivo affinché questo sia considerato come una nuova sessione. Il timeout viene applicato anche quando l’applicazione viene lasciata in background e poi riattivata. Il tempo durante il quale l’app rimane in background non viene incluso nella durata della sessione.

   Il valore predefinito è 300 secondi.

* **batchLimit**

   Invia gli hit in batch 

   For example, if set to `50`, hits are queued until 50 are stored, then all queued hits are sent. Richiede `offlineEnabled=true`e il valore predefinito è `0` (nessun invio in batch).

* **privacyDefault**

   Le opzioni sono:

   * `optedin` - gli hit vengono inviati immediatamente.
   * `optedout` - gli hit vengono scartati.
   * Per `optunknown`, se le marche temporali sono abilitate nella suite di rapporti, gli hit vengono salvati fino alla modifica dello stato di privacy, quando l’utente acconsente (optedin, gli hit vengono inviati) o rinuncia (optedout, gli hit vengono eliminati). Se le marche temporali non sono abilitate nella suite di rapporti, gli hit vengono eliminati fino alla modifica dello stato di privacy, quando l’utente acconsente (optedin).

      Questo imposta solo il valore predefinito. Se questo valore è impostato o modificato nel codice, il valore impostato dal codice viene salvato nello spazio di archiviazione locale e utilizzato fino a quando non viene modificato o l’app non viene disinstallata e reinstallata.

      Il valore predefinito è `optedin`.

* **poi**

   Ogni array POI contiene il nome, la latitudine, la longitudine e il raggio (in metri) dell'area di interesse. Il nome POI può essere una qualsiasi stringa. Quando viene inviata una chiamata `trackLocation`, se le coordinate correnti si trovano in un POI definito, una variabile di dati di contesto viene compilata e inviata insieme alla chiamata `trackLocation`.

   * Here is the code sample for this variable:

      ```js
       "poi" [ 
                ["san francisco",37.757144,-122.44812,7000], 
                ["santa cruz",36.972935,-122.01725,600] 
             ]
      ```

* **clientCode**

   (**Required by Target**) Your assigned client code.

* **timeout**

   Determina per quanto tempo Target può aspettare di ricevere una risposta.

Di seguito viene indicato un esempio del file `ADBMobileConfig.json`:

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
  "timeout" : 1
 },
 "audienceManager" : {
  "server" : "myServer.demdex.com"
 }
}
```
