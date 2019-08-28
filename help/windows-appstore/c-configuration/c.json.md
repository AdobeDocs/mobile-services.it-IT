---
description: Informazioni utili per l’utilizzo del file di configurazione ADBMobile JSON.
seo-description: Informazioni utili per l’utilizzo del file di configurazione ADBMobile JSON.
seo-title: File di configurazione adbmobileconfig. json
solution: Marketing Cloud, Analytics
title: File di configurazione adbmobileconfig. json
topic: Sviluppatore e implementazione
uuid: a 45 b 91 cc -982 e -4 d 6 c-a 4 e 4-d 2 e 4 b 4 fa 7556
translation-type: tm+mt
source-git-commit: 1dbdb998228bd3b0ae41e774b6e9aa111d8dbe1c

---


# `ADBMobileConfig.json` file di configurazione {#adbmobileconfig-json-config}

Information to help you use the `ADBMobile.json` config file.

Al momento l’SDK dispone di supporto per più Soluzioni Adobe Experience Cloud, tra cui Analytics, Target e Audience Manager. Ai metodi è applicato il prefisso della relativa soluzione. I metodi di configurazione hanno il prefisso "Config".

* **rsids**

   (Richiesto da Analytics) Una o più suite di rapporti che riceveranno i dati di Analytics. Nel caso di più suite di rapporti, i rispettivi ID devono essere separati da una virgola, senza spazio.

   * Di seguito sono riportati gli esempi di codice per questa variabile:

      ```js
      "rsids" : "rsid"
      ```

      ```js
      "rsids" : "rsid1,rsid2"
      ```

* **server**

   (Richiesto da Analytics e Gestione dell’audience). Server di Analytics o Gestione dell’audience, in base al nodo principale. This variable should be populated with the server domain, without an `https://` or `https://` protocol prefix. Il prefisso del protocollo viene gestito automaticamente dalla libreria, in base alla variabile `ssl`.

   Se `ssl` è `true`, viene eseguita una connessione sicura al server. Se `ssl` è `false`, viene eseguita una connessione non sicura.

* **charset**

   Definisce il set di caratteri utilizzato per i dati inviati ad Analytics. Il set di caratteri serve per convertire i dati in entrata in UTF-8 per l’archiviazione e la generazione di rapporti. For more information, see [s.charSet](https://marketing.adobe.com/resources/help/en_US/sc/implement/charset.html).

* **ssl**

   Enables (`true`) or disables (`false`) sending measurement data via SSL (HTTPS). Il valore predefinito è `false`.

* **offlineEnabled**

   Quando è disabilitata (true ), gli hit vengono messi in coda mentre il dispositivo è offline e inviati non appena torna online. Per poter usare il tracciamento offline, nella suite di rapporti devono essere abilitate le marche temporali.

   >[!IMPORTANT]
   >
   >IIf time stamps are enabled on your report suite, your `offlineEnabled` configuration property *must* be true. Se le marche temporali non sono abilitate nella suite di rapporti, la proprietà di configurazione `offlineEnabled` *deve* essere false. Se questo non viene configurato correttamente, i dati andranno perduti. Se non sei sicuro se le marche temporali sono abilitate o meno nella suite di rapporti, contatta Assistenza clienti. Se i dati AppMeasurement vengono inviati a una suite di rapporti che raccoglie anche dati da JavaScript, potrebbe essere necessario impostare una suite di rapporti distinta per i dati mobile o includere una marca temporale personalizzata in tutti gli hit JavaScript che usano la variabile `s.timestamp`.

* **lifecycleTimeout**

   Specifica l’intervallo di tempo, in secondi, che deve trascorrere tra un avvio dell’app e quello successivo affinché questo sia considerato come una nuova sessione. Il timeout viene applicato anche quando l’applicazione viene lasciata in background e poi riattivata. Il tempo durante il quale l'app rimane in background non viene incluso nella durata della sessione. Il valore predefinito è 300 secondi.

* **batchLimit**

   Invia gli hit in batch Ad esempio, se il valore impostato è 50, gli hit sono messi in coda fino a memorizzarne 50, dopodiché tutti quelli in coda vengono inviati. `offlineEnabled=true`Richiede. Il valore predefinito è `0` (Nessuna gestione batch).

* **privacyDefault**

   * `optedin` - gli hit vengono inviati immediatamente.
   * `optedout` - gli hit vengono eliminati.
   * Per `optunknown`, se le marche temporali sono abilitate nella suite di rapporti, gli hit vengono salvati fino alla modifica dello stato di privacy, quando l’utente acconsente (optedin, gli hit vengono inviati) o rinuncia (optedout, gli hit vengono eliminati). Se le marche temporali non sono abilitate nella suite di rapporti, gli hit vengono eliminati fino alla modifica dello stato di privacy, quando l’utente acconsente (optedin).

      Il valore predefinito è `optedin`.

      >[!TIP]
      >
      >Questo imposta solo il valore predefinito. Se questo valore è impostato o modificato nel codice, il valore impostato dal codice viene salvato nello spazio di archiviazione locale e utilizzato fino a quando non viene modificato o l’app non viene disinstallata e reinstallata.

* **poi**

   Ogni array POI contiene il nome, la latitudine, la longitudine e il raggio (in metri) dell'area di interesse. Il nome POI può essere una qualsiasi stringa. Quando viene inviata una chiamata `trackLocation`, se le coordinate correnti si trovano in un POI definito, una variabile di dati di contesto viene compilata e inviata insieme alla chiamata `trackLocation`.

   * Ecco l'esempio di codice per questa variabile:

      ```js
      "poi": [
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

