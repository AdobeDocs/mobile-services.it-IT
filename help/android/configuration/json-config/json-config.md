---
description: Queste informazioni sono utili per usare il file di configurazione ADBMobile.json.
seo-description: Queste informazioni sono utili per usare il file di configurazione ADBMobile.json.
seo-title: File di configurazione ADBMobile JSON
solution: Marketing Cloud,Analytics
title: File di configurazione ADBMobile JSON
topic: Sviluppatore e implementazione
uuid: 1decf605-7bc3-4e73-ad52-1ecd5821599e
translation-type: tm+mt
source-git-commit: 19264af3f4a675add6f61c27f4cdaf20033b9bb7

---


# ADBMobile JSON config file {#adbmobile-json-config}

Queste informazioni sono utili per comprendere le variabili presenti nel file di configurazione ADBMobile.json.

## `ADBMobileConfig.json` riferimento del file di configurazione {#section_5AD4EDF87E304980B4AC4A5657FDA8B9}

Lo stesso file di configurazione può essere utilizzato per l'app su più piattaforme:

>[!TIP]
>
>In **Android**, the `ADBMobileConfig.json` file must be placed in the `assets` folder.

Elenco delle variabili nel file JSON e della versione SDK minima necessaria per ciascuna variabile:

* **acquisizione**
   * Versione SDK minima: 4.1
   * Abilita l'acquisizione dell'app mobile.
      * `server`, server di acquisizione controllato all'avvio iniziale per individuare un referente di acquisizione.
      * `appid`, ID generato che identifica l'app in modo univoco sul server di acquisizione.
   Se manca questa sezione, abilita l'acquisizione da app mobile e scarica di nuovo il file di configurazione dell'SDK. Per ulteriori informazioni, vedi *referrerTimeout* in questo elenco di variabili.

* **analyticsForwardingEnabled**
   * La versione SDK minima è 4.8.0.
   * Il valore predefinito è `false`.

      Proprietà nell'oggetto `audienceManager`. Se Audience Manager è configurato e `analyticsForwardingEnabled` è impostato su `true`, anch tutto il traffico Analytics viene inoltrato ad Audience Manager.

* **backdateSessionInfo**
   * Versione SDK minima: 4.6.
   * Abilita/disabilita la possibilità di Adobe SDK di retrodatare gli hit di informazioni delle sessioni.

      Gli hit di informazioni della sessione consistono attualmente in crash e durata e possono essere abilitati o disabilitati.

      **Abilitazione o disabilitazione degli hit**

      * Impostando il valore su `false`, gli hit vengono **disabilitati**. L'SDK ritorna al suo comportamento pre-4.1, che consiste nell'accorpare le informazioni della sessione precedente al primo hit della sessione successiva. L'SDK di Adobe allega anche le informazioni della sessione al ciclo di vita corrente, evitando così la creazione di una visita gonfiata. In seguito alla mancata creazione di visite gonfiate, si verifica un calo immediato del numero di visite.

      * Se non fornisci un valore, il valore predefinito è `true`, e gli hit sono **abilitati**. Se è abilitata, Adobe SDK retrodaterà l'hit di informazioni della sessione a 1 secondo dopo l'ultimo hit della sessione precedente. Gli arresti anomali e i dati delle sessioni saranno quindi correlati alla data corretta in cui si sono verificati. Un effetto collaterale è che l'SDK potrebbe creare una visita per l'hit retrodatato. Viene retrodatato un hit per ogni nuovo avvio dell'applicazione.

         >[!IMPORTANT]
         >
         >Backdated session hit information is sent in a session info server call and additional server calls might apply.

* **batchLimit**
   * Versione SDK minima: 4.1
   * Soglia per il numero di hit da inviare in chiamate consecutive.

      Ad esempio, se `batchLimit` è impostato su 10, ogni hit prima del decimo viene memorizzato nella coda. Quando arriva il 10° hit, tutti i 10 hit in coda vengono inviati consecutivamente.

      Considerazioni da ricordare:

      * Il valore predefinito è `0` e indica che la gestione degli hit in batch non è abilitata.
      * Richiede `offlineEnabled = true`.

* **charset**
   * Versione SDK minima: 4.0
   * Definisce il set di caratteri utilizzato per i dati inviati ad Analytics.

      Il set di caratteri serve per convertire i dati in entrata in UTF-8 per l'archiviazione e la generazione di rapporti.

* **clientCode**
   * Versione SDK minima: 4.0
   * Codice cliente assegnato.

      >[!IMPORTANT]
      >
      >Questa variabile è obbligatoria per Target.

* **coopUnsafe**
   * Versione SDK minima: 4.16.1
   * The Boolean property of the `marketingCloud` object that, when set to `true`, causes the device to be opted-out of the Experience Cloud's Device Co-Op.
   * Il valore predefinito è `false`.
   * Questa impostazione è utilizzata **solo** per i clienti abilitati per Device Co-op.
   I membri Device Co-op che necessitano tale valore impostato su `true` devono rivolgersi al team Co-op e richiedere un flag blacklist sul proprio account Device Co-op. Non esiste alcun percorso self-service per l'attivazione di questi flag.

   Considerazioni da ricordare:

   * When `coopUnsafe` is set to `true`, `coop_unsafe=1` will always be appended to Audience Manager and Visitor ID hits.
   * If you enable Analytics server-side forwarding to Audience Manager, you will also see `coop_unsafe=1` Analytics hits.


* **environmentId**
   * Versione SDK minima: 4.14
   * ID dell’ambiente da usare.

      Puoi specificare un ID valido (`environmentId=8`); se `environmentId` non è incluso, viene usato l’ambiente predefinito Produzione.

* **lifecycleTimeout**
   * Versione SDK minima: 4.0
   * Il valore predefinito è 300 secondi.

      Specifica l'intervallo di tempo, in secondi, che deve trascorrere tra il momento in cui viene avviata l'app e quando tale avvio debba essere considerato come una nuova sessione. Il timeout viene applicato anche quando l'applicazione viene lasciata in background e poi riattivata.

      Il tempo durante il quale l'app rimane in background non viene incluso nella durata della sessione.

* **messages**

   * Versione SDK minima: 4.2
   * Generata automaticamente da Adobe Mobile Services, definisce le impostazioni per i messaggi in-app. Per ulteriori informazioni, consulta *Descrizione dei messaggi*.

* **offlineEnabled**

   * Versione SDK minima: 4.0
   * Quando è disabilitata, gli hit vengono messi in coda mentre il dispositivo è offline e inviati non appena torna online.

      Per poter usare il tracciamento offline, nella suite di rapporti devono essere abilitate le marche temporali.

      Il valore predefinito è `false`.

      >[!IMPORTANT]
      >
      >If timestamps are enabled on your report suite, your `offlineEnabled` configuration property **must** be true. Se le marche temporali non sono abilitate nella suite di rapporti, la proprietà di configurazione `offlineEnabled` **deve** essere false.
      >
      >Se questo non viene configurato correttamente, i dati andranno perduti. Se non sei sicuro se le marche temporali sono abilitate o meno nella suite di rapporti contatta l'Assistenza clienti o scarica il file di configurazione da Adobe Mobile Services.

      Se i dati AppMeasurement vengono inviati a una suite di rapporti che raccoglie anche dati da JavaScript, potrebbe essere necessario impostare una suite di rapporti distinta per i dati mobile o includere una marca temporale personalizzata in tutti gli hit JavaScript che usano la variabile `s.timestamp`.

* **org**

   * Versione SDK minima: 4.3
   * Specifica l'ID organizzazione di Experience Cloud per il servizio ID.

* **poi**
   * Versione SDK minima: 4.0
   * Ogni array di punto di interesse (POI) contiene il nome, la latitudine, la longitudine e il raggio in metri dell'area di interesse.

      Il nome POI può essere una qualsiasi stringa. Quando viene inviata una chiamata `trackLocation`, se le coordinate correnti si trovano in un POI definito, una variabile di dati di contesto viene compilata e inviata insieme alla chiamata `trackLocation`.

      ```javascript
      "poi": [
                 ["san francisco",37.757144,-122.44812,7000]
                 ["santa cruz",36.972935,-122.01725,600]
             ]
      ```

      A partire dalla versione 4.2, i punti di interesse (POI) sono definiti nell'interfaccia di Adobe Mobile e sincronizzati dinamicamente con il file di configurazione dell'app. Tale sincronizzazione richiede un'impostazione `analytics.poi`:

      ```javascript
      “analytics.poi“: `https://assets.adobedtm.com/`
      …/yourfile.json”`,
      ```

      Se non è configurata, devi aggiornare il file `ADBMobile.json` affinché contenga questa riga. Per scaricare un file di configurazione aggiornato, vedi [Prima di iniziare](/help/android/getting-started/requirements.md).

* **postback**
   * Versione SDK minima: 4.6
   * Di seguito viene illustrata la definizione del modello di messaggio "callback":

      ```javascript
      "payload":{
        "templateurl":"", //required will be token-expanded prior to being sent
        "templatebody":"", //optional - if this length > 0 POST will be used as transport method. This is a base64 encoded blob, which will be decoded and token-expanded prior to being sent.
        "contenttype": "", // optional - if this is length > 0 and POST type is selected this will be set as the Content-Type header.  if this is not supplied for a POST request, the default will be "application/x-www-form-urlencoded"
        "timeout": 0 // optional - number of seconds to wait before timing out.  Default is 2.}
      ```

      The `payload` object in the code is a sample payload for a message definition that goes in the `ADBMobileConfig.json` file. For more information, see [Postbacks](/help/android/analytics-main/postbacks/postbacks.md).

* **privacyDefault**
   * Versione SDK minima: 4.0
   * Il valore predefinito è `optedin`.
      * Per `optedin`, gli hit vengono inviati immediatamente.
      * Per `optedout`, gli hit vengono scartati.
      * Per `optunknown`, se le marche temporali sono abilitate nella suite di rapporti, gli hit vengono salvati fino a quando lo stato di privacy non cambia in optedin (gli hit vengono inviati) o in optedout (gli hit vengono scartati).
      If your report suite is not timestamp-enabled, hits are discarded until the privacy status changes to `optedin`.  Questo imposta solo il valore iniziale. Se questo valore viene impostato o modificato nel codice, il nuovo valore viene usato finché non viene nuovamente modificato oppure finché l'app non viene disinstallata e reinstallata.


* **referrerTimeout**
   * Versione SDK minima: 4.1
   * Tempo di attesa, in secondi, affinché l'SDK possa ricevere i dati del referente dell'acquisizione all'avvio iniziale, prima che si verifichi un timeout. Se usi la funzione di acquisizione, consigliamo un timeout di 5 secondi.

      >[!IMPORTANT]
      >
      >Questa variabile è obbligatoria per Acquisizione. Se la variabile è impostata su `0` o non è inclusa, l'SDK non attende i dati di acquisizione e la metrica di acquisizione non può essere tracciata.

* **remotes**
   * Versione SDK minima: 4.2
   * Configurata automaticamente, definisce gli endpoint gestiti da Adobe per i file di configurazione dinamici.

      Ad ogni avvio, l'ora dell'ultimo aggiornamento di ogni file di configurazione viene verificato rispetto alla versione corrente, e gli aggiornamenti vengono scaricati e salvati.
      * `analytics.poi` è l'endpoint per la configurazione dei punti di interesse in hosting.
      * `messages` è l'endpoint per la configurazione dei messaggi in-app.

* **rsids**
   * Versione SDK minima: 4.0
   * Una o più suite di rapporti che dovrà ricevere i dati Analytics. Nel caso di più suite di rapporti, i rispettivi ID devono essere separati da una virgola, senza spazio.

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
   * Server di Analytics o Gestione dell'audience, in base al nodo principale. This variable should be populated with the server domain, without an `https://` or `https://` protocol prefix. Il prefisso viene gestito automaticamente dalla libreria, in base alla variabile `ssl`. Se `ssl` è `true`, viene eseguita una connessione sicura al server. Se `ssl` è `false`, viene eseguita una connessione non sicura.

* **ssl**
   * Versione SDK minima: 4.0
   * Il valore predefinito è `false`.

      Abilita (`true`) o disabilita (`false`) l'invio dei dati di misurazione tramite SSL (HTTPS).

      Di seguito viene illustrata la definizione del modello di messaggio "callback":

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


## Sample `ADBMobileConfig.json` file {#section_4655EF79744649E5A5AE19E3224C472C}

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

Il nodo dei messaggi viene generato automaticamente da Adobe Mobile Services e generalmente non deve essere modificato manualmente. La descrizione seguente è utile per la risoluzione di eventuali problemi:

* "messageId"
* ID generato, obbligatorio
* "template"
   * "alert", "fullscreen" o "local"
   * obbligatorio

* "showOffline"
   * true o false
   * il valore predefinito è false

* "showRule"
   * "always", "once" o "untilClick"
   * obbligatorio

* "endDate"
   * numero di secondi dal 1° gennaio 1970
   * Il valore predefinito è 2524730400

* "startDate"
   * numero di secondi dal 1° gennaio 1970
   * Il valore predefinito è 0

* "payload"
   * "html"
      * solo per il modello fullscreen, obbligatorio
      * html che definisce il messaggio
   * "image"
      * solo fullscreen, facoltativo
      * url dell'immagine da usare come immagine a schermo intero
   * "altImage"
      * solo fullscreen, facoltativo
      * nome dell'immagine fornita nel pacchetto da usare se l'URL specificato in
         * image
         * non è accessibile
   * "title"
      * per fullscreen e alert, obbligatorio
      * testo del titolo di un messaggio fullscreen o alert
   * "content"
      * notifica alert e local, obbligatorio
      * sottotesto per un messaggio alert, o testo di notifica per un messaggio di notifica local
   * "confirm"
      * alert, facoltativo
      * testo usato per il pulsante di conferma
   * "cancel"
      * alert, obbligatorio
      * testo usato per il pulsante Annulla
   * "url"
      * alert, facoltativo
      * azione URL da caricare se si fa clic sul pulsante di conferma
   * "wait"
      * notifica local, obbligatorio
      * tempo (in secondi) che deve trascorrere prima di pubblicare la notifica local una volta soddisfatti i relativi criteri



* "audiences"
   * array di oggetti che definisce come dovrà essere visualizzato il messaggio
   * "key"
      * nome della variabile da cercare nell'hit, obbligatorio
* "matches"
   * tipo di corrispondenza usato nel confronto
   * eq = equals (uguale a)
   * ne = does not equal (non uguale a)
   * co = contains (contiene)
   * nc = does not contain (non contiene)
   * sw = starts with (inizia con)
   * ew = ends with (termina con)
   * ex = exists (esiste)
   * nx = does not exist (non esiste)
   * lt = less than (minore di)
   * le = less than or equals (minore di o uguale a)
   * gt = greater than (maggiore di)
   * ge = greater than or equals (maggiore di o uguale a)
* "values"
   * array di valori usati per determinare la corrispondenza rispetto al valore della variabile denominata in
      * key
      * con il tipo di corrispondenza definito in
      * matches
* "triggers"
   * come "audiences", ma si tratta dell'azione anziché del pubblico
   * "key"
   * "matches"
   * "values"
