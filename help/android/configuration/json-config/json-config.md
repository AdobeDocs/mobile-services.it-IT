---
description: Queste informazioni sono utili per usare il file di configurazione ADBMobile.json.
seo-description: Queste informazioni sono utili per usare il file di configurazione ADBMobile.json.
seo-title: File di configurazione ADBMobile JSON
solution: Experience Cloud,Analytics
title: File di configurazione ADBMobile JSON
topic: Developer and implementation
uuid: 1decf605-7bc3-4e73-ad52-1ecd5821599e
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '1678'
ht-degree: 100%

---


# File di configurazione ADBMobile JSON {#adbmobile-json-config}

Queste informazioni sono utili per comprendere le variabili presenti nel file di configurazione ADBMobile.json.

## `ADBMobileConfig.json` Guida di riferimento per il file di configurazione {#section_5AD4EDF87E304980B4AC4A5657FDA8B9}

Lo stesso file di configurazione può essere utilizzato per l&#39;app su più piattaforme:

>[!TIP]
>
>Su **Android**, il file `ADBMobileConfig.json` deve trovarsi nella cartella `assets`.

Elenco delle variabili nel file JSON e della versione SDK minima necessaria per ciascuna variabile:

* **acquisizione**
   * Versione SDK minima: 4.1
   * Abilita l&#39;acquisizione dell&#39;app mobile.
      * `server`, server di acquisizione controllato all&#39;avvio iniziale per individuare un referente di acquisizione.
      * `appid`, ID generato che identifica l&#39;app in modo univoco sul server di acquisizione.

   Se manca questa sezione, abilita l&#39;acquisizione da app mobile e scarica di nuovo il file di configurazione dell&#39;SDK. Per ulteriori informazioni, vedi *referrerTimeout* in questo elenco di variabili.

* **analyticsForwardingEnabled**
   * La versione SDK minima è 4.8.0.
   * Il valore predefinito è `false`.

      Proprietà nell&#39;oggetto `audienceManager`. Se Audience Manager è configurato e `analyticsForwardingEnabled` è impostato su `true`, anche tutto il traffico Analytics viene inoltrato ad Audience Manager.

* **backdateSessionInfo**
   * Versione SDK minima: 4.6.
   * Abilita/disabilita la possibilità di Adobe SDK di retrodatare gli hit di informazioni delle sessioni.

      Gli hit di informazioni delle sessioni sono attualmente costituiti da arresti anomali e dalla lunghezza di sessione e possono essere attivati o disattivati.

      **Abilitazione o disabilitazione degli hit**

      * Impostando il valore su `false`, gli hit vengono **disabilitati**. L’SDK torna al suo comportamento precedente alla versione 4.1, ossia il raggruppamento delle informazioni sulla sessione precedente con il primo hit della sessione successiva. L’SDK di Adobe associa anche le informazioni sulla sessione al ciclo di vita corrente, evitando così la creazione di visite in eccesso. Poiché non vengono più create visite in eccesso, si verifica un calo immediato del numero di visite.

      * Se non fornisci un valore, il valore predefinito è `true`, e gli hit sono **abilitati**. Quando gli hit sono attivati, l’SDK di Adobe retrodaterà l’hit di informazioni delle sessioni a 1 secondo dopo l’hit finale nella sessione precedente. Ciò significa che i dati di arresto anomalo e di sessione saranno correlati alla data corretta in cui si sono verificati. Un effetto collaterale è che l’SDK potrebbe creare una visita per l’hit retrodatato. Viene retrodatato un hit per ogni nuovo avvio dell&#39;applicazione.

         >[!IMPORTANT]
         >
         >Le informazioni sugli hit di sessione retrodatate vengono inviate in una chiamata al server per informazioni sulle sessioni, e potrebbero essere applicabili chiamate server aggiuntive.

* **batchLimit**
   * Versione SDK minima: 4.1
   * Soglia per il numero di hit da inviare in chiamate consecutive.

      Ad esempio, se `batchLimit` è impostato su 10, ogni hit prima del decimo viene memorizzato nella coda. All’arrivo del decimo hit, tutti i 10 hit in coda vengono inviati consecutivamente.

      Considerazioni da ricordare:

      * Il valore predefinito è `0` e indica che la gestione degli hit in batch non è abilitata.
      * Richiede `offlineEnabled = true`.

* **charset**
   * Versione SDK minima: 4.0
   * Definisce il set di caratteri utilizzato per i dati inviati ad Analytics.

      Il set di caratteri serve per convertire i dati in entrata in UTF-8 per l&#39;archiviazione e la generazione di rapporti.

* **clientCode**
   * Versione SDK minima: 4.0
   * Codice cliente assegnato.

      >[!IMPORTANT]
      >
      >Questa variabile è obbligatoria per Target.

* **coopUnsafe**
   * Versione SDK minima: 4.16.1
   * Proprietà booleana dell’oggetto `marketingCloud` che, se impostata su `true`, determina il rifiuto di partecipazione a Experience Cloud Device Co-op.
   * Il valore predefinito è `false`.
   * Questa impostazione è utilizzata **solo** per i clienti abilitati per Device Co-op.

   Per i membri Device Co-op che richiedono che questo valore sia impostato come `true`, è necessario collaborare con il team Co-op per richiedere un flag di blocklist per l’account Device Co-op. Non esiste alcun percorso self-service per l&#39;attivazione di questi flag.

   Considerazioni da ricordare:

   * Quando `coopUnsafe` è impostato su `true`, `coop_unsafe=1` agli hit di Audience Manager e del servizio ID visitatori verrà sempre aggiunto.
   * Se abiliti l’inoltro lato server da Analytics ad Audience Manager, troverai l’hit di Analytics `coop_unsafe=1`.


* **environmentId**
   * Versione SDK minima: 4.14
   * ID dell’ambiente da usare.

      Puoi specificare un ID valido (`environmentId=8`); se `environmentId` non è incluso, viene usato l’ambiente predefinito Produzione.

* **lifecycleTimeout**
   * Versione SDK minima: 4.0
   * Il valore predefinito è 300 secondi.

      Specifica il tempo, in secondi, che deve trascorrere tra il momento in cui l’app viene avviata e quello in cui l’avvio viene considerato come una nuova sessione. Questo timeout si applica anche quando l’applicazione viene messa in background e riattivata.

      Il tempo trascorso in background dall’app non viene incluso nella durata della sessione.

* **messages**

   * Versione SDK minima: 4.2
   * Generato automaticamente da Adobe Mobile Services, definisce le impostazioni per la messaggistica in-app. Per ulteriori informazioni, consulta la sezione *Descrizione dei messaggi* di seguito.

* **offlineEnabled**

   * Versione SDK minima: 4.0
   * Quando è disabilitata, gli hit vengono messi in coda mentre il dispositivo è offline e inviati non appena torna online.

      Per poter usare il tracciamento offline, nella suite di rapporti devono essere abilitate le marche temporali.

      Il valore predefinito è `false`.

      >[!IMPORTANT]
      >
      >Se le marche temporali sono abilitate nella suite di rapporti, la proprietà di configurazione `offlineEnabled` **deve** essere true. Se le marche temporali non sono abilitate nella suite di rapporti, la proprietà di configurazione `offlineEnabled` **deve** essere false.
      >
      >Se questo non viene configurato correttamente, i dati andranno perduti. Se non sei sicuro se le marche temporali sono abilitate o meno nella suite di rapporti  contatta l&#39;Assistenza clienti o scarica il file di configurazione da Adobe Mobile Services.

      Se i dati AppMeasurement vengono inviati a una suite di rapporti che raccoglie anche dati da JavaScript, potrebbe essere necessario impostare una suite di rapporti distinta per i dati mobile o includere una marca temporale personalizzata in tutti gli hit JavaScript che usano la variabile `s.timestamp`.

* **org**

   * Versione SDK minima: 4.3
   * Specifica l&#39;ID organizzazione di Experience Cloud per il servizio ID.

* **poi**
   * Versione SDK minima: 4.0
   * Ogni array di punto di interesse (POI) contiene il nome, la latitudine, la longitudine e il raggio in metri dell&#39;area di interesse.

      Il nome POI può essere una qualsiasi stringa. Quando viene inviata una chiamata `trackLocation`, se le coordinate correnti si trovano in un POI definito, una variabile di dati di contesto viene compilata e inviata insieme alla chiamata `trackLocation`.

      ```javascript
      "poi": [
                 ["san francisco",37.757144,-122.44812,7000]
                 ["santa cruz",36.972935,-122.01725,600]
             ]
      ```

      A partire dalla versione 4.2, i punti di interesse (POI) sono definiti nell&#39;interfaccia di Adobe Mobile e sincronizzati dinamicamente con il file di configurazione dell&#39;app. Tale sincronizzazione richiede un&#39;impostazione `analytics.poi`:

      ```javascript
        “analytics.poi“: `https://assets.adobedtm.com/`
      …/yourfile.json”`,
      ```

      Se non è configurata, devi aggiornare il file `ADBMobile.json` affinché contenga questa riga. Per scaricare un file di configurazione aggiornato, vedi [Prima di iniziare](/help/android/getting-started/requirements.md).

* **postback**
   * Versione SDK minima: 4.6
   * Di seguito viene illustrata la definizione del modello di messaggio &quot;callback&quot;:

      ```javascript
      "payload":{
        "templateurl":"", //required will be token-expanded prior to being sent
        "templatebody":"", //optional - if this length > 0 POST will be used as transport method. This is a base64 encoded blob, which will be decoded and token-expanded prior to being sent.
        "contenttype": "", // optional - if this is length > 0 and POST type is selected this will be set as the Content-Type header.  if this is not supplied for a POST request, the default will be "application/x-www-form-urlencoded"
        "timeout": 0 // optional - number of seconds to wait before timing out.  Default is 2.}
      ```

      L&#39;oggetto `payload` nel codice è un payload di esempio per la definizione di un messaggio da inserire nel file `ADBMobileConfig.json`. Per ulteriori informazioni, vedi [Postback](/help/android/analytics-main/postbacks/postbacks.md).

* **privacyDefault**
   * Versione SDK minima: 4.0
   * Il valore predefinito è `optedin`.
      * Per `optedin`, gli hit vengono inviati immediatamente.
      * Per `optedout`, gli hit vengono scartati.
      * Per `optunknown`, se le marche temporali sono abilitate nella suite di rapporti, gli hit vengono salvati fino a quando lo stato di privacy non cambia in optedin (gli hit vengono inviati) o in optedout (gli hit vengono scartati).

      Se le marche temporali non sono abilitate nella suite di rapporti, gli hit vengono scartati fino a quando lo stato di privacy non cambia in `optedin`.  Questo imposta solo il valore iniziale. Se questo valore viene impostato o modificato nel codice, il nuovo valore viene usato finché non viene nuovamente modificato oppure finché l&#39;app non viene disinstallata e reinstallata.


* **referrerTimeout**
   * Versione SDK minima: 4.1
   * Numero di secondi in cui l’SDK attende i dati del referente di acquisizione all’avvio iniziale, prima che venga eseguito il timeout. Se utilizzi l’acquisizione, consigliamo un timeout di 5 secondi.

      >[!IMPORTANT]
      >
      >Questa variabile è obbligatoria per la funzione Acquisizione. Se la variabile è impostata su `0` o non è inclusa, l&#39;SDK non attende i dati di acquisizione e la metrica di acquisizione non può essere tracciata.

* **remotes**
   * Versione SDK minima: 4.2
   * Configurata automaticamente, definisce gli endpoint gestiti da Adobe per i file di configurazione dinamici.

      Ad ogni avvio, l&#39;ora dell&#39;ultimo aggiornamento di ogni file di configurazione viene verificato rispetto alla versione corrente, e gli aggiornamenti vengono scaricati e salvati.
      * `analytics.poi` è l&#39;endpoint per la configurazione dei punti di interesse in hosting.
      * `messages` è l&#39;endpoint per la configurazione dei messaggi in-app.

* **rsids**
   * Versione SDK minima: 4.0
   * Una o più suite di rapporti che riceva i dati di Analytics. Gli ID suite di rapporti multipli devono essere separati da virgole senza spazi intermedi.

      ```javascript
        "rsids" "rsid"
      ```

      ```javascript
        "rsids" "rsid1,rsid2"
      ```

      >[!IMPORTANT]
      >
      >Questa variabile è obbligatoria per Analytics.

* **server**
   * Versione SDK minima: 4.0
   * Server di Analytics o Gestione dell&#39;audience, in base al nodo principale. Questa variabile deve essere compilata con il dominio del server, senza il prefisso del protocollo `https://` o `https://`. Il prefisso viene gestito automaticamente dalla libreria, in base alla variabile `ssl`. Se `ssl` è `true`, viene eseguita una connessione sicura al server. Se `ssl` è `false`, viene eseguita una connessione non sicura.

* **ssl**
   * Versione SDK minima: 4.0
   * Il valore predefinito è `false`.

      Abilita (`true`) o disabilita (`false`) l&#39;invio dei dati di misurazione tramite SSL (HTTPS).

      Di seguito viene illustrata la definizione del modello di messaggio &quot;callback&quot;:

      ```javascript
      "payload": {
          "templateurl":"",//required-will be token-expanded prior to being sent 
          "templatebody": "", //optional - if this length >  0 POST will be used& as transport method. This is a base64 encoded blob, which will be  decoded and token-expanded prior to being sent.
          "contenttype": "" // optional - if this is length > 0 POST type is selected this will be set as the Content-Type header. if this is not supplied for a POST request, the default will be "application/x-www-form-urlencoded"
          "timeout": 0 // optional - number of seconds to wait before timing& out. Default is 2.}
      ```

* **timeout**
   * Versione SDK minima: 4.0
   * Determina per quanto tempo Target può aspettare di ricevere una risposta.


## File di esempio `ADBMobileConfig.json` {#section_4655EF79744649E5A5AE19E3224C472C}

Ecco un esempio di file `ADBMobileConfig.json`:

```js
 { 
    "version": "2014-08-05T19:18:28.169Z", 
    "marketingCloud" : { 
        "org": "016D5C175213CCA80A490D05@AdobeOrg", 
        "coopUnsafe": false 
    }, 
    "target": { 
        "clientCode": "", 
        "timeout": 5, 
        "environmentId": 8 
    }, 
    "audienceManager": { 
        "server": "", 
        "analyticsForwardingEnabled": false 
    }, 
    "acquisition": { 
        "server": "c00.adobe.com", 
        "appid": "10a77a60192fbb628376e1b1daeeb65debf934e2c807e067ceb2963a41b165ee" 
    }, 
    "analytics": { 
        "rsids": "coolApp", 
        "server": "my.CoolApp.com", 
        "ssl": true, 
        "offlineEnabled": true, 
        "charset": "UTF-8", 
        "lifecycleTimeout": 300, 
        "privacyDefault": "optedin", 
        "batchLimit": 0, 
        "referrerTimeout": 5, 
        "poi": [ 
            ["san francisco",37.757144,-122.44812,7000],  
            ["santa cruz",36.972935,-122.01725,600] 
        ] 
    }, 
    "messages": [ 
        { 
            "messageId": "cb426565-a563-497a-a889-9dbeb451f8ae", 
            "template": "fullscreen", 
            "payload": { 
                 "html": "<!DOCTYPE html><html><head><meta charset=\"utf-8\" /><title></title><style></style></head><body><iframe src=\"https://www.adobe.com/\" frameborder=\"0\"></iframe></body></html>" 
            }, 
            "showOffline": false, 
            "showRule": "always", 
            "endDate": 2524730400, 
            "startDate": 0, 
            "audiences": [], 
            "triggers": [ 
                { 
                    "key": "pev2", 
                    "matches": "eq", 
                    "values": [ 
                        "AMACTION:custom" 
                    ] 
                } 
            ] 
        } 
    ], 
    "remotes": { 
        "analytics.poi": "https://assets.adobedtm.com/staging/42a6fc9b77cd9f29082cf19b787bae75b7d1f9ca/scripts/satellite-53e0faadc2f9ed92bc00003b.json", 
        "messages": "https://assets.adobedtm.com/staging/42a6fc9b77cd9f29082cf19b787bae75b7d1f9ca/scripts/satellite-53e0f9e2c2f9ed92bc000032.json" 
    } 
}
```

## Descrizione dei messaggi {#section_B97D654BA92149CE91F525268D7AD71F}

Il nodo dei messaggi viene generato automaticamente da Adobe Mobile Services e in genere non è necessario modificarlo manualmente. La seguente descrizione è fornita per la risoluzione di problemi:

* “messageId”
* ID generato, obbligatorio
* “template”
   * “alert”, “fullscreen” o “local”
   * obbligatorio

* “showOffline”
   * true o false
   * il valore predefinito è false

* “showRule”
   * “always”, “once” o “untilClick”
   * obbligatorio

* “endDate”
   * numero di secondi dal 1° gennaio 1970
   * Il valore predefinito è 2524730400

* “startDate”
   * numero di secondi dal 1° gennaio 1970
   * Il valore predefinito è 0

* “payload”
   * “html”
      * solo modello a schermo intero, obbligatorio
      * html che definisce il messaggio
   * “image”
      * solo a schermo intero, facoltativo
      * URL dell’immagine da utilizzare per un’immagine a schermo intero
   * “altImage”
      * solo a schermo intero, facoltativo
      * nome dell’immagine nel bundle da utilizzare se l’URL specificato in
         * immagine
         * non è accessibile
   * “title”
      * a schermo intero e avviso, obbligatorio
      * testo del titolo per un messaggio di avviso o a schermo intero
   * “content”
      * notifica di avviso e locale, obbligatorio
      * sottotesto per un messaggio di avviso o testo di notifica per un messaggio di notifica locale
   * “confirm”
      * avviso, facoltativo
      * testo utilizzato nel pulsante di conferma
   * “cancel”
      * avviso, obbligatorio
      * testo utilizzato nel pulsante di annullamento
   * “url”
      * avviso, facoltativo
      * azione URL da caricare se si fa clic sul pulsante di conferma
   * “wait”
      * notifica locale, obbligatorio
      * tempo di attesa (in secondi) per la pubblicazione della notifica locale dopo che i criteri sono stati soddisfatti



* &quot;audiences&quot;
   * array di oggetti che definisce come deve essere visualizzato il messaggio
   * &quot;key&quot;
      * nome della variabile da cercare nell’hit, obbligatorio
* &quot;matches&quot;
   * tipo di matcher utilizzato per il confronto
   * eq = equals (uguale a)
   * ne = does not equal (non uguale a)
   * co = contains (contiene)
   * nc = does not contain (non contiene)
   * sw = starts with (inizia con)
   * ew = ends with (termina con)
   * ex = exists (esiste)
   * nx = does not exist (non esiste)
   * lt = less than (minore di)
   * le = less than or equals (minore o uguale a)
   * gt = greater than (maggiore di)
   * ge = greater than or equals (maggiore o uguale a)
* &quot;values&quot;
   * array di valori utilizzati per eseguire il confronto rispetto al valore della variabile denominata
      * key
      * con il tipo di corrispondenza in
      * matches
* &quot;triggers&quot;
   * simile a audience, ma per l’azione anziché per il pubblico
   * &quot;key&quot;
   * &quot;matches&quot;
   * &quot;values&quot;
