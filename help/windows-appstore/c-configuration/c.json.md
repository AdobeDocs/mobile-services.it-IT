---
description: Informazioni utili per l’utilizzo del file di configurazione ADBMobile JSON.
solution: Experience Cloud,Analytics
title: File di configurazione ADBMobileConfig.json
topic-fix: Developer and implementation
uuid: a45b91cc-982e-4d6c-a4e4-d2e4b4fa7556
exl-id: 520dffb8-ca47-444f-bbc9-f18413ddeb05
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '609'
ht-degree: 45%

---

# `ADBMobileConfig.json` file di configurazione {#adbmobileconfig-json-config}

Informazioni utili per usare il file di configurazione `ADBMobile.json`.

L&#39;SDK supporta attualmente più soluzioni Adobe Experience Cloud, tra cui Analytics, Target e Audience Manager. Ai metodi è applicato il prefisso della relativa soluzione. I metodi di configurazione hanno il prefisso &quot;Config&quot;.

* **rsids**

   (Richiesto da Analytics) Una o più suite di rapporti che deve ricevere i dati di Analytics. Gli ID suite di rapporti multipli devono essere separati da virgole senza spazi intermedi.

   * Di seguito sono riportati alcuni esempi di codice per questa variabile:

      ```js
      "rsids" : "rsid"
      ```

      ```js
      "rsids" : "rsid1,rsid2"
      ```

* **server**

   (Richiesto da Analytics e Gestione dell&#39;audience). Server di Analytics o Gestione dell&#39;audience, in base al nodo principale. Questa variabile deve essere compilata con il dominio del server, senza il prefisso del protocollo `https://` o `https://`. Il prefisso del protocollo viene gestito automaticamente dalla libreria in base alla variabile `ssl` .

   Se `ssl` è `true`, viene eseguita una connessione sicura al server. Se `ssl` è `false`, viene eseguita una connessione non sicura.

* **charset**

   Definisce il set di caratteri utilizzato per i dati inviati ad Analytics. Il set di caratteri serve per convertire i dati in entrata in UTF-8 per l&#39;archiviazione e la generazione di rapporti. Per ulteriori informazioni, consulta la variabile [charSet](https://experienceleague.adobe.com/docs/analytics/implementation/vars/config-vars/charset.html?lang=it) nella documentazione di Adobe Analytics.

* **ssl**

   Abilita (`true`) o disabilita (`false`) l&#39;invio dei dati di misurazione tramite SSL (HTTPS). Il valore predefinito è `false`.

* **offlineEnabled**

   Quando è abilitato (true), gli hit vengono messi in coda mentre il dispositivo è offline e inviati non appena torna online. Per poter usare il tracciamento offline, nella suite di rapporti devono essere abilitate le marche temporali.

   >[!IMPORTANT]
   >
   >Se le marche temporali sono abilitate nella suite di rapporti, la proprietà di configurazione `offlineEnabled` *deve essere true.* Se le marche temporali non sono abilitate nella suite di rapporti, la proprietà di configurazione `offlineEnabled` *deve* essere false. Se questo non viene configurato correttamente, i dati andranno perduti. Se non sei sicuro se le marche temporali sono abilitate o meno nella suite di rapporti,   contatta   Assistenza clienti. Se i dati AppMeasurement vengono inviati a una suite di rapporti che raccoglie anche dati da JavaScript, potrebbe essere necessario impostare una suite di rapporti distinta per i dati mobile o includere una marca temporale personalizzata in tutti gli hit JavaScript che utilizzano la variabile `s.timestamp` .

* **lifecycleTimeout**

   Specifica il tempo, in secondi, che deve trascorrere tra il momento in cui l’app viene avviata e quello in cui l’avvio viene considerato come una nuova sessione. Questo timeout si applica anche quando l’applicazione viene messa in background e riattivata. Il tempo trascorso in background dall’app non viene incluso nella durata della sessione. Il valore predefinito è 300 secondi.

* **batchLimit**

   Invia gli hit in batch. Ad esempio, se è impostato su 50, gli hit vengono messi in coda fino a memorizzarne 50, dopodiché tutti gli hit in coda vengono inviati. Richiede `offlineEnabled=true`. Il valore predefinito è `0` (nessun invio in batch).

* **privacyDefault**

   * `optedin` - gli hit vengono inviati immediatamente.
   * `optedout` - gli hit vengono eliminati.
   * `optunknown` - Se le marche temporali sono abilitate nella suite di rapporti, gli hit vengono salvati fino a quando lo stato di privacy non cambia in optedin (gli hit vengono inviati) o optedout (gli hit vengono scartati). Se le marche temporali non sono abilitate nella suite di rapporti, gli hit vengono eliminati fino alla modifica dello stato di privacy, quando l&#39;utente acconsente (optedin).

      Il valore predefinito è `optedin`.

      >[!TIP]
      >
      >Questo imposta solo il valore predefinito. Se questo valore viene impostato o modificato nel codice, il valore impostato dal codice viene salvato nell&#39;archivio locale e utilizzato fino a quando non viene modificato oppure finché l&#39;app non viene disinstallata e reinstallata.

* **poi**

   Ogni array POI contiene il nome, la latitudine, la longitudine e il raggio (in metri) dell&#39;area di interesse. Il nome POI può essere una qualsiasi stringa. Quando viene inviata una chiamata `trackLocation`, se le coordinate correnti si trovano in un POI definito, una variabile di dati di contesto viene compilata e inviata insieme alla chiamata `trackLocation`.

   * Di seguito è riportato un esempio di codice per questa variabile:

      ```js
      "poi": [
                  ["san francisco",37.757144,-122.44812,7000], 
                  ["santa cruz",36.972935,-122.01725,600] 
              ]
      ```

* **clientCode**

   (**Richiesto da Target**) Il codice client assegnato.

* **timeout**

   Determina per quanto tempo Target può aspettare di ricevere una risposta.

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
