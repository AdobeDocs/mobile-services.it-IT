---
description: Queste informazioni sono utili per usare il file di configurazione ADBMobile.json.
seo-description: Queste informazioni sono utili per usare il file di configurazione ADBMobile.json.
seo-title: Configurazione ADBMobile JSON
solution: Marketing Cloud,Analytics
title: Configurazione ADBMobile JSON
topic: Sviluppatore e implementazione
uuid: d9708d59-e30a-4f6c-ab1b-d9499855d0c2
translation-type: tm+mt
source-git-commit: 19264af3f4a675add6f61c27f4cdaf20033b9bb7

---


# ADBMobile JSON config {#adbmobile-json-config}

Queste informazioni sono utili per usare il file di configurazione `ADBMobile.json`.

## ADBMobileConfig.json config file reference {#section_5AD4EDF87E304980B4AC4A5657FDA8B9}

Lo stesso file di configurazione può essere utilizzato per l'app su più piattaforme:

>[!TIP]
>
>Su **iOS**, il file `ADBMobileConfig.json` può trovarsi ovunque possa essere accessibile nel pacchetto.

* **acquisizione**

   Abilita l'acquisizione dell'app mobile.

   Se manca questa sezione, abilita l'acquisizione da app mobile e scarica di nuovo il file di configurazione dell'SDK. Per ulteriori informazioni, consulta *referrerTimeout*, di seguito.

   * `server`: server di acquisizione controllato all'avvio iniziale per individuare un referente di acquisizione.
   * `appid`: ID generato che identifica l'app in modo univoco sul server di acquisizione.
   * Versione SDK minima: 4.1

* **analyticsForwardingEnabled**

   Proprietà nell'oggetto `audienceManager`. If `Audience Manager` is configured and `analyticsForwardingEnabled` is set to `true`, all Analytics traffic is also forwarded to Audience Manager. Il valore predefinito è `false`.

   * Versione SDK minima: 4.8.0

* **backdateSessionInfo**

   Abilita/disabilita la possibilità di Adobe SDK di retrodatare gli hit di informazioni delle sessioni.

   Gli hit di informazioni della sessione consistono attualmente in crash e durata e possono essere abilitati o disabilitati.

   * Impostando il valore su `false`, gli hit vengono **disabilitati**.

      L'SDK ritorna al suo comportamento pre-4.1, che consiste nell'accorpare le informazioni della sessione precedente al primo hit della sessione successiva. L'SDK di Adobe allega anche le informazioni della sessione al ciclo di vita corrente, evitando così la creazione di una visita gonfiata. In seguito alla mancata creazione di visite gonfiate, si verifica un calo immediato del numero di visite.

   * Se non fornisci un valore, il valore predefinito è `true`, e gli hit sono **abilitati**.

      Se è abilitata, Adobe SDK retrodaterà l'hit di informazioni della sessione a 1 secondo dopo l'ultimo hit della sessione precedente. Gli arresti anomali e i dati delle sessioni saranno quindi correlati alla data corretta in cui si sono verificati. Un effetto collaterale è che l'SDK potrebbe creare una visita per l'hit retrodatato. Viene retrodatato un hit per ogni nuovo avvio dell'applicazione.

   * Versione SDK minima: 4.6
   >[!IMPORTANT]
   >
   >Backdated session hit information is sent in a session info server call, and additional server calls might apply.


* **batchLimit**

   Soglia per il numero di hit da inviare in chiamate consecutive. Ad esempio, se `batchLimit` è impostato su 10, ogni hit prima del decimo viene memorizzato nella coda. Quando arriva il 10° hit, tutti i 10 hit in coda vengono inviati consecutivamente.

   * Default value is `0`, which means that batching is not enabled.
   * Richiede `offlineEnabled = true`.
   * Versione SDK minima: 4.1

* **charset**

   Definisce il set di caratteri utilizzato per i dati inviati ad Analytics. Il set di caratteri serve per convertire i dati in entrata in UTF-8 per l'archiviazione e la generazione di rapporti. For more information, see [s.charSet](https://marketing.adobe.com/resources/help/en_US/sc/implement/charset.html).

   * Versione SDK minima: 4.0

* **clientCode**

   Codice cliente assegnato.

   >[!IMPORTANT]
   >
   >Questa variabile è obbligatoria per Target.

   * Versione SDK minima: 4.0

* **coopUnsafe**

   I membri Device Co-op che necessitano tale valore impostato su `true` devono rivolgersi al team Co-op e richiedere un flag blacklist sul proprio account Device Co-op. Non esiste alcun percorso self-service per l'attivazione di questi flag.

   Considerazioni da ricordare:

   * When `coopUnsafe` is set to `true`, `coop_unsafe=1` will always be appended to Audience Manager and Visitor ID hits.
   * Se abiliti l’inoltro lato server da Analytics ad Audience Manager, negli hit di Analytics troverai `coop_unsafe=1`.
   Seguono alcune informazioni aggiuntive:

   * Versione SDK minima: 4.16.1
   * The Boolean property of the `marketingCloud` object that, when set to `true`, causes the device to be opted-out of the Experience Cloud's Device Co-Op.
   * Il valore predefinito è `false`.
   * Questa impostazione è utilizzata **solo** per i clienti abilitati per Device Co-op.



* **environmentId**

   ID dell’ambiente da usare. Puoi specificare un ID valido (`environmentId=8`); se `environmentId` non è incluso, viene usato l’ambiente predefinito Produzione.

   * Versione SDK minima: 4.14

* **lifecycleTimeout**

   Il valore predefinito è 300 secondi.

   Specifica l'intervallo di tempo, in secondi, che deve trascorrere tra il momento in cui viene avviata l'app e quando tale avvio debba essere considerato come una nuova sessione. Il timeout viene applicato anche quando l’applicazione viene lasciata in background e poi riattivata. Il tempo durante il quale l’app rimane in background non viene incluso nella durata della sessione.

   * Versione SDK minima: 4.0

* **messages**

   Generata automaticamente da Adobe Mobile Services, definisce le impostazioni per i messaggi in-app. Per ulteriori informazioni, consulta *Descrizione dei messaggi*.

   * Versione SDK minima: 4.2

* **offlineEnabled**

   Quando è disabilitata, gli hit vengono messi in coda mentre il dispositivo è offline e inviati non appena torna online. Per poter usare il tracciamento offline, nella suite di rapporti devono essere abilitate le marche temporali. Il valore predefinito è `false`.

   Seguono alcune informazioni importanti:

   * If timestamps are enabled on your report suite, your `offlineEnabled` configuration property *must* be true.
   * If your report suite is not timestamp enabled, your `offlineEnabled` configuration property *must* be false.

      Se questo non viene configurato correttamente, i dati andranno perduti. Se non sei sicuro se le marche temporali sono abilitate o meno nella suite di rapporti, contatta l'Assistenza clienti o scarica il file di configurazione da Adobe Mobile Services. Se i dati AppMeasurement vengono inviati a una suite di rapporti che raccoglie anche dati da JavaScript, potrebbe essere necessario impostare una suite di rapporti distinta per i dati mobile o includere una marca temporale personalizzata in tutti gli hit JavaScript che usano la variabile `s.timestamp`.

   * Versione SDK minima: 4.0

* **org**

   Specifica l’ID organizzazione di Experience Cloud per il servizio di identità della piattaforma Adobe Experience Cloud.

   * Versione SDK minima: 4.3

* **poi**

   Ogni array POI contiene il nome, la latitudine, la longitudine e il raggio (in metri) dell'area di interesse. Il nome POI può essere una qualsiasi stringa. Quando viene inviata una chiamata `trackLocation`, se le coordinate correnti si trovano in un POI definito, una variabile di dati di contesto viene compilata e inviata insieme alla chiamata `trackLocation`.

   * Versione SDK minima: 4.0
   ```js
   "poi" [ 
           ["sanfrancisco",37.757144,-122.44812,7000]
           ["santacruz",36.972935,-122.01725,600]
         ] 
   ```

   >[!TIP]
   >
   >A partire dalla versione 4.2, i punti di interesse (POI) sono definiti nell'interfaccia di Adobe Mobile e sincronizzati dinamicamente con il file di configurazione dell'app. Tale sincronizzazione richiede un'impostazione `analytics.poi`:

   ```js
   “analytics.poi”: “`https://assets.adobedtm.com/…/yourfile.json`”,
   ```

   Se non è configurata, devi aggiornare il file `ADBMobile.json` affinché contenga questa riga. Per scaricare un file di configurazione aggiornato, vedi [Prima di iniziare](/help/ios/getting-started/requirements.md).

* **postback**

   Di seguito viene illustrata la definizione del modello di messaggio "callback":

   ```js
   "payload":{
       "templateurl":"",//required- will be token-expanded prior to being sent
       "templatebody":"", //optional-if this length > 0 POST will be used as transport method. This is a base-64 encoded blob,which will be decoded and token-expanded prior to being sent.
       "contenttype":"", //optional-if this is length > 0 and POST type is selected, this will be set as the Content-Typeheader. if this is not supplied for a POST request,the default will be "application/x-www-form-urlencoded"
       "timeout": 0 //optional-number of seconds to wait before timingout.Defaultis2.}
   ```

   The `payload` object in the code is an example payload for a message definition that would go in the `ADBMobileConfig.json` file. For more information, see [Postbacks](/help/ios/analytics-main/postback/postback.md).

   * Versione SDK minima: 4.6

* **privacyDefault**

   * Per `optedin`, gli hit vengono inviati immediatamente.
   * Per `optedout`, gli hit vengono scartati.
   * Per `optunknown`, se le marche temporali sono abilitate nella suite di rapporti, gli hit vengono salvati fino a quando lo stato di privacy non cambia in optedin (gli hit vengono inviati) o in optedout (gli hit vengono scartati).

      Se le marche temporali non sono abilitate nella suite di rapporti, gli hit vengono scartati fino a quando lo stato di privacy non cambia in optedin.

      Questo imposta solo il valore iniziale. Se questo valore viene impostato o modificato nel codice, il nuovo valore viene usato finché non viene nuovamente modificato oppure finché l'app non viene disinstallata e reinstallata. Il valore predefinito è `optedin`.

   * Versione SDK minima: 4.0

* **referrerTimeout**

   Tempo di attesa, in secondi, affinché l'SDK possa ricevere i dati del referente dell'acquisizione all'avvio iniziale, prima che si verifichi un timeout. Se usi la funzione di acquisizione, consigliamo un timeout di 5 secondi.

   >[!IMPORTANT]
   >
   >Questa variabile è obbligatoria per Acquisizione. If the variable is set to `0`, or is not included, the SDK does not wait for acquisition data, and acquisition metrics are not tracked.

   * Versione SDK minima: 4.1

* **remotes**

   Configurata automaticamente, definisce gli endpoint gestiti da Adobe per i file di configurazione dinamici. Ad ogni avvio, l'ora dell'ultimo aggiornamento di ogni file di configurazione viene verificato rispetto alla versione corrente, e gli aggiornamenti vengono scaricati e salvati.

   * `analytics.poi` è l'endpoint per la configurazione dei punti di interesse in hosting.

   * `messages` è l'endpoint per la configurazione dei messaggi in-app.

   * Versione SDK minima: 4.2

* **rsids**

   Una o più suite di rapporti che dovrà ricevere i dati Analytics. Nel caso di più suite di rapporti, i rispettivi ID devono essere separati da una virgola, senza spazio.

   ```js
   "rsids": "rsid"
   ```

   ```js
   "rsids" : "rsid1,rsid2" 
   ```

   >[!IMPORTANT]
   >
   >This variable is required by Analytics.

   * Versione SDK minima: 4.0

* **server**

   Server di Analytics o Gestione dell'audience, in base al nodo principale.

   This variable should be populated with the server domain, without an `https://` or `https://` protocol prefix. Il prefisso viene gestito automaticamente dalla libreria, in base alla variabile `ssl`.

   Se `ssl` è `true`, viene eseguita una connessione sicura al server. Se `ssl` è `false`, viene eseguita una connessione non sicura.

   >[!IMPORTANT]
   >
   >This variable is required by Analytics and/or Audience Management.

   * Versione SDK minima: 4.0

* **ssl**

   Il valore predefinito è `false`. Abilita (`true`) o disabilita (`false`) l'invio dei dati di misurazione tramite SSL (HTTPS).

   Di seguito viene illustrata la definizione del modello di messaggio "callback":

   ```js
   "payload":{
       "templateurl":"",//required-will be token-expanded prior to being sent
       "templatebody":"",//optional-if this length > 0, POST will be used as transport method. This is a base64 encoded blob,which will be decoded and token-expanded prior to being sent.
       "contenttype":"",//optional-if this is length > 0 and POST type is selected this will be set as the Content-Typeheader. if this is not supplied for a POST request,the default will be "application/x-www-form-urlencoded"
       "timeout":0//optional-numberofsecondstowaitbeforetimingout.Defaultis2.} 
   ```

   The `payload` object in the code is an sample payload for a message definition that goes in the `ADBMobileConfig.json` file. For more information, see [Postbacks](/help/ios/analytics-main/postback/postback.md).

   * Versione SDK minima: 4.0

* **timeout**

   Determina per quanto tempo Target può aspettare di ricevere una risposta.

   * Versione SDK minima: 4.0


## Sample `ADBMobileConfig.json` file {#section_52FA7C71A99147AFA9BE08D2177D8DA7}

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
         `image` non è accessibile
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

* "audiences"

   Array di oggetti che definisce come deve essere visualizzato il messaggio:

   * "key"

      Nome della variabile da cercare nell’hit; obbligatorio.

   * "matches"

      Tipo di corrispondenza utilizzato per il confronto:

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

      Array di valori utilizzati per eseguire il confronto rispetto al valore della variabile denominata in:

      * key
      * con il tipo di corrispondenza definito in
      * matches


* "triggers"

   Simile a audience, ma per le azioni anziché per il pubblico:

   * "key"
   * "matches"
   * "values"
