---
description: Informazioni utili per l’utilizzo del file di configurazione ADBMobile JSON.
seo-description: Informazioni utili per l’utilizzo del file di configurazione ADBMobile JSON.
seo-title: Configurazione di ADBMobileConfig.json
solution: Experience Cloud,Analytics
title: Configurazione di ADBMobileConfig.json
topic-fix: Developer and implementation
uuid: cbcb54a3-4b8f-4651-8ce9-2731ac988545
exl-id: 57d50d30-651c-4943-835e-1cbce7467baf
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '620'
ht-degree: 44%

---

# File di configurazione ADBMobileConfig.json {#adbmobileconfig-json-config}

Informazioni utili per l’utilizzo del file di configurazione ADBMobile JSON.

L&#39;SDK supporta attualmente più soluzioni Adobe Experience Cloud, tra cui Analytics, Target e Audience Manager. Ai metodi è applicato il prefisso della relativa soluzione. I metodi di configurazione hanno il prefisso &quot;Config&quot;.

* **rsids**

   (**Richiesto da Analytics**) Una o più suite di rapporti che devono ricevere i dati di Analytics. Gli ID suite di rapporti multipli devono essere separati da virgole senza spazi intermedi.

   * Di seguito è riportata la sintassi per questo metodo:

      ```js
      "rsids" : "rsid"
      ```

      ```js
      "rsids" : "rsid1,rsid2"
      ```

* **server**

   (**Richiesto da Analytics e Gestione dell&#39;audience**). Server di Analytics o Gestione dell&#39;audience, in base al nodo principale. Questa variabile deve essere compilata con il dominio del server, senza il prefisso del protocollo `"https://"` o `"https://"`. Il prefisso del protocollo viene gestito automaticamente dalla libreria in base alla variabile `ssl` .

   Se `ssl` è `true`, viene eseguita una connessione sicura al server. Se `ssl` è `false`, viene eseguita una connessione non sicura.

* **charset**

   Definisce il set di caratteri utilizzato per i dati inviati ad Analytics. Il set di caratteri serve per convertire i dati in entrata in UTF-8 per l&#39;archiviazione e la generazione di rapporti. Per ulteriori informazioni, consulta [s.charSet](https://docs.adobe.com/content/help/it-IT/analytics/implementation/vars/config-vars/charset.html).

* **ssl**

   Abilita (`true`) o disabilita (`false`) l&#39;invio dei dati di misurazione tramite SSL (`HTTPS`). Il valore predefinito è `false`.

* **offlineEnabled**

   Quando è abilitato (`true`), gli hit vengono messi in coda mentre il dispositivo è offline e inviati non appena il dispositivo è online. Per poter usare il tracciamento offline, nella suite di rapporti devono essere abilitate le marche temporali.

   Se le marche temporali sono abilitate nella suite di rapporti, la proprietà di configurazione `offlineEnabled` *deve essere*. `true` Se le marche temporali non sono abilitate nella suite di rapporti, la proprietà di configurazione `offlineEnabled` *deve* essere `false`.

   Se questo non viene configurato correttamente, i dati andranno perduti. Se non sei sicuro se le marche temporali sono abilitate o meno nella suite di rapporti, contatta l’Assistenza clienti. Se i dati AppMeasurement vengono inviati a una suite di rapporti che raccoglie anche dati da JavaScript, potrebbe essere necessario impostare una suite di rapporti distinta per i dati mobile o includere una marca temporale personalizzata in tutti gli hit JavaScript che utilizzano la variabile `s.timestamp` .

   Il valore predefinito è `false`.

* **lifecycleTimeout**

   Specifica il tempo, in secondi, che deve trascorrere tra il momento in cui l’app viene avviata e quello in cui l’avvio viene considerato come una nuova sessione. Questo timeout si applica anche quando l’applicazione viene messa in background e riattivata. Il tempo trascorso in background dall’app non viene incluso nella durata della sessione.

   Il valore predefinito è 300 secondi.

* **batchLimit**

   Invia gli hit in batch.

   Ad esempio, se è impostato su `50`, gli hit vengono messi in coda fino a memorizzarne 50, dopodiché tutti gli hit in coda vengono inviati. Richiede `offlineEnabled=true` e il valore predefinito è `0` (nessun invio in batch).

* **privacyDefault**

   Le opzioni sono:

   * `optedin` - gli hit vengono inviati immediatamente.
   * `optedout` - gli hit vengono eliminati.
   * `optunknown` - Se le marche temporali sono abilitate nella suite di rapporti, gli hit vengono salvati fino a quando lo stato di privacy non cambia in optedin (gli hit vengono inviati) o optedout (gli hit vengono scartati). Se le marche temporali non sono abilitate nella suite di rapporti, gli hit vengono eliminati fino alla modifica dello stato di privacy, quando l&#39;utente acconsente (optedin).

      Questo imposta solo il valore predefinito. Se questo valore viene impostato o modificato nel codice, il valore impostato dal codice viene salvato nell&#39;archiviazione locale e utilizzato fino a quando non viene modificato oppure finché l&#39;app non viene disinstallata e reinstallata.

      Il valore predefinito è `optedin`.

* **poi**

   Ogni array POI contiene il nome, la latitudine, la longitudine e il raggio (in metri) dell&#39;area di interesse. Il nome POI può essere una qualsiasi stringa. Quando viene inviata una chiamata `trackLocation`, se le coordinate correnti si trovano in un POI definito, una variabile di dati di contesto viene compilata e inviata insieme alla chiamata `trackLocation`.

   * Di seguito è riportato un esempio di codice per questa variabile:

      ```js
       "poi" [ 
                ["san francisco",37.757144,-122.44812,7000], 
                ["santa cruz",36.972935,-122.01725,600] 
             ]
      ```

* **clientCode**

   (**Richiesto da Target**) Il codice client assegnato.

* **timeout**

   Determina per quanto tempo target attende una risposta.

Di seguito è riportato un esempio di file `ADBMobileConfig.json` :

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
