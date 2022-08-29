---
description: Queste informazioni sono utili per usare il file di configurazione ADBMobile.json.
solution: Experience Cloud Services,Analytics
title: File di configurazione ADBMobile JSON
topic-fix: Developer and implementation
uuid: d9708d59-e30a-4f6c-ab1b-d9499855d0c2
exl-id: e3515de3-3aec-4dd0-996d-9c561ad1b1de
source-git-commit: 78b7a623a7811cf0ede789c74b3ca7a80372c9f4
workflow-type: tm+mt
source-wordcount: '1591'
ht-degree: 99%

---

# File di configurazione ADBMobile JSON {#adbmobile-json-config}

Queste informazioni sono utili per usare il file di configurazione `ADBMobile.json`.

## Riferimento per il file di configurazione ADBMobileConfig.json {#section_5AD4EDF87E304980B4AC4A5657FDA8B9}

Lo stesso file di configurazione può essere utilizzato per l&#39;app su più piattaforme:

>[!TIP]
>
>Su **iOS**, il file `ADBMobileConfig.json` può trovarsi ovunque possa essere accessibile nel pacchetto.

* **acquisizione**

   Abilita l&#39;acquisizione dell&#39;app mobile.

   Se manca questa sezione, abilita l&#39;acquisizione da app mobile e scarica di nuovo il file di configurazione dell&#39;SDK. Per ulteriori informazioni, vedi *referrerTimeout* di seguito.

   * `server`: server di acquisizione controllato all&#39;avvio iniziale per individuare un referente di acquisizione.
   * `appid`: ID generato che identifica l&#39;app in modo univoco sul server di acquisizione.
   * Versione SDK minima: 4.1

* **analyticsForwardingEnabled**

   Proprietà nell&#39;oggetto `audienceManager`. Se `Audience Manager` è configurato e `analyticsForwardingEnabled` è impostato su `true`, anche tutto il traffico Analytics viene inoltrato ad Audience Manager. Il valore predefinito è `false`.

   * Versione SDK minima: 4.8.0

* **backdateSessionInfo**

   Abilita/disabilita la possibilità di Adobe SDK di retrodatare gli hit di informazioni delle sessioni.

   Gli hit di informazioni delle sessioni sono attualmente costituiti da arresti anomali e dalla lunghezza di sessione e possono essere attivati o disattivati.

   * Impostando il valore su `false`, gli hit vengono **disabilitati**.

      L’SDK torna al suo comportamento precedente alla versione 4.1, ossia il raggruppamento delle informazioni sulla sessione precedente con il primo hit della sessione successiva. L’SDK di Adobe associa anche le informazioni sulla sessione al ciclo di vita corrente, evitando così la creazione di visite in eccesso. Poiché non vengono più create visite in eccesso, si verifica un calo immediato del numero di visite.

   * Se non fornisci un valore, il valore predefinito è `true`, e gli hit sono **abilitati**.

      Quando gli hit sono attivati, l’SDK di Adobe retrodaterà l’hit di informazioni delle sessioni a 1 secondo dopo l’hit finale nella sessione precedente. Ciò significa che i dati di arresto anomalo e di sessione saranno correlati alla data corretta in cui si sono verificati. Un effetto collaterale è che l’SDK potrebbe creare una visita per l’hit retrodatato. Viene retrodatato un hit per ogni nuovo avvio dell&#39;applicazione.

   * Versione SDK minima: 4.6
   >[!IMPORTANT]
   >
   >Le informazioni di hit di sessione retrodatate vengono inviate in una chiamata al server per informazioni sulle sessioni, e potrebbero essere applicabili chiamate server aggiuntive.


* **batchLimit**

   Soglia per il numero di hit da inviare in chiamate consecutive. Ad esempio, se `batchLimit` è impostato su 10, ogni hit prima del decimo viene memorizzato nella coda. Quando arriva il 10° hit, tutti i 10 hit in coda vengono inviati consecutivamente.

   * Il valore predefinito è `0` e indica che la gestione degli hit in batch non è abilitata.
   * Richiede `offlineEnabled = true`.
   * Versione SDK minima: 4.1

* **charset**

   Definisce il set di caratteri utilizzato per i dati inviati ad Analytics. Il set di caratteri serve per convertire i dati in entrata in UTF-8 per l&#39;archiviazione e la generazione di rapporti. Per ulteriori informazioni, consulta la sezione [charSet](https://experienceleague.adobe.com/docs/analytics/implementation/vars/config-vars/charset.html?lang=it) nella documentazione di Adobe Analytics.

   * Versione SDK minima: 4.0

* **clientCode**

   Codice cliente assegnato.

   >[!IMPORTANT]
   >
   >Questa variabile è obbligatoria per Target.

   * Versione SDK minima: 4.0

* **environmentId**

   ID dell’ambiente da usare. Puoi specificare un ID valido (`environmentId=8`); se `environmentId` non è incluso, viene usato l’ambiente predefinito Produzione.

   * Versione SDK minima: 4.14

* **lifecycleTimeout**

   Il valore predefinito è 300 secondi.

   Specifica il tempo, in secondi, che deve trascorrere tra il momento in cui l’app viene avviata e quello in cui l’avvio viene considerato come una nuova sessione. Questo timeout si applica anche quando l’applicazione viene messa in background e riattivata. Il tempo trascorso in background dall’app non viene incluso nella durata della sessione.

   * Versione SDK minima: 4.0

* **messages**

   Generato automaticamente da Adobe Mobile Services, definisce le impostazioni per la messaggistica in-app. Per ulteriori informazioni, consulta la sezione *Descrizione dei messaggi* di seguito.

   * Versione SDK minima: 4.2

* **offlineEnabled**

   Quando è disabilitata, gli hit vengono messi in coda mentre il dispositivo è offline e inviati non appena torna online. Per poter usare il tracciamento offline, nella suite di rapporti devono essere abilitate le marche temporali. Il valore predefinito è `false`.

   Seguono alcune importanti informazioni:

   * Se le marche temporali sono abilitate nella suite di rapporti, la proprietà di configurazione `offlineEnabled` *deve* essere true.
   * Se le marche temporali non sono abilitate nella suite di rapporti, la proprietà di configurazione `offlineEnabled` *deve* essere false.

      Se questo non viene configurato correttamente, i dati andranno perduti. Se non sei sicuro se le marche temporali sono abilitate o meno nella suite di rapporti,   contatta   l&#39;Assistenza clienti o scarica il file di configurazione da Adobe Mobile Services. Se i dati AppMeasurement vengono inviati a una suite di rapporti che raccoglie anche dati da JavaScript, potrebbe essere necessario impostare una suite di rapporti distinta per i dati mobile o includere una marca temporale personalizzata in tutti gli hit JavaScript che usano la variabile `s.timestamp`.

   * Versione SDK minima: 4.0

* **org**

   Specifica l&#39;ID organizzazione di Experience Cloud per il servizio Adobe Experience Platform.

   * Versione SDK minima: 4.3

* **poi**

   Ogni array POI contiene il nome, la latitudine, la longitudine e il raggio (in metri) dell&#39;area di interesse. Il nome POI può essere una qualsiasi stringa. Quando viene inviata una chiamata `trackLocation`, se le coordinate correnti si trovano in un POI definito, una variabile di dati di contesto viene compilata e inviata insieme alla chiamata `trackLocation`.

   * Versione SDK minima: 4.0

   ```js
   "poi" [ 
           ["sanfrancisco",37.757144,-122.44812,7000]
           ["santacruz",36.972935,-122.01725,600]
         ] 
   ```

   >[!TIP]
   >
   >A partire dalla versione 4.2, i punti di interesse (POI) sono definiti nell&#39;interfaccia di Adobe Mobile e sincronizzati dinamicamente con il file di configurazione dell&#39;app. Tale sincronizzazione richiede un&#39;impostazione `analytics.poi`:

   ```js
   "analytics.poi": "`https://assets.adobedtm.com/…/yourfile.json`",
   ```

   Se non è configurata, devi aggiornare il file `ADBMobile.json` affinché contenga questa riga. Per scaricare un file di configurazione aggiornato, vedi [Prima di iniziare](/help/ios/getting-started/requirements.md).

* **postback**

   Di seguito viene illustrata la definizione del modello di messaggio &quot;callback&quot;:

   ```js
   "payload":{
       "templateurl":"",//required- will be token-expanded prior to being sent
       "templatebody":"", //optional-if this length > 0 POST will be used as transport method. This is a base-64 encoded blob,which will be decoded and token-expanded prior to being sent.
       "contenttype":"", //optional-if this is length > 0 and POST type is selected, this will be set as the Content-Typeheader. if this is not supplied for a POST request,the default will be "application/x-www-form-urlencoded"
       "timeout": 0 //optional-number of seconds to wait before timingout.Defaultis2.}
   ```

   L&#39;oggetto `payload` nel codice è un payload di esempio per la definizione di un messaggio da inserire nel file `ADBMobileConfig.json`. Per ulteriori informazioni, vedi [Postback](/help/ios/analytics-main/postback/postback.md).

   * Versione SDK minima: 4.6

* **privacyDefault**

   * Per `optedin`, gli hit vengono inviati immediatamente.
   * Per `optedout`, gli hit vengono scartati.
   * Per `optunknown`, se le marche temporali sono abilitate nella suite di rapporti, gli hit vengono salvati fino a quando lo stato di privacy non cambia in optedin (gli hit vengono inviati) o in optedout (gli hit vengono scartati).

      Se le marche temporali non sono abilitate nella suite di rapporti, gli hit vengono eliminati fino alla modifica dello stato di privacy, quando l&#39;utente acconsente (optedin).

      Questo imposta solo il valore iniziale. Se questo valore viene impostato o modificato nel codice, il nuovo valore viene usato finché non viene nuovamente modificato oppure finché l&#39;app non viene disinstallata e reinstallata. Il valore predefinito è `optedin`.

   * Versione SDK minima: 4.0

* **referrerTimeout**

   Numero di secondi in cui l’SDK attende i dati del referente di acquisizione all’avvio iniziale, prima che venga eseguito il timeout. Se utilizzi l’acquisizione, consigliamo un timeout di 5 secondi.

   >[!IMPORTANT]
   >
   >Questa variabile è obbligatoria per la funzione Acquisizione. Se la variabile è impostata su `0` o non è inclusa, l&#39;SDK non attende i dati di acquisizione e la metrica di acquisizione non può essere tracciata.

   * Versione SDK minima: 4.1

* **remotes**

   Configurata automaticamente, definisce gli endpoint gestiti da Adobe per i file di configurazione dinamici. Ad ogni avvio, l&#39;ora dell&#39;ultimo aggiornamento di ogni file di configurazione viene verificato rispetto alla versione corrente, e gli aggiornamenti vengono scaricati e salvati.

   * `analytics.poi` è l&#39;endpoint per la configurazione dei punti di interesse in hosting.

   * `messages` è l&#39;endpoint per la configurazione dei messaggi in-app.

   * Versione SDK minima: 4.2

* **rsids**

   Una o più suite di rapporti che riceva i dati di Analytics. Gli ID suite di rapporti multipli devono essere separati da virgole senza spazi intermedi.

   ```js
   "rsids": "rsid"
   ```

   ```js
   "rsids" : "rsid1,rsid2" 
   ```

   >[!IMPORTANT]
   >
   >Questa variabile è obbligatoria per Analytics.

   * Versione SDK minima: 4.0

* **server**

   Server di Analytics o Gestione dell&#39;audience, in base al nodo principale.

   Questa variabile deve essere compilata con il dominio del server, senza il prefisso del protocollo `https://` o `https://`. Il prefisso viene gestito automaticamente dalla libreria, in base alla variabile `ssl`.

   Se `ssl` è `true`, viene eseguita una connessione sicura al server. Se `ssl` è `false`, viene eseguita una connessione non sicura.

   >[!IMPORTANT]
   >
   >Questa variabile è obbligatoria per Analytics e/o Gestione dell&#39;audience.

   * Versione SDK minima: 4.0

* **ssl**

   >[!IMPORTANT]
   >
   > A partire dalla versione 4.10.0, l’impostazione predefinita SSL è autentica se il contrassegno non è impostato.

   Abilita (`true`) o disabilita (`false`) l&#39;invio dei dati di misurazione tramite SSL (HTTPS).

   Di seguito viene illustrata la definizione del modello di messaggio &quot;callback&quot;:

   ```js
   "payload":{
       "templateurl":"",//required-will be token-expanded prior to being sent
       "templatebody":"",//optional-if this length > 0, POST will be used as transport method. This is a base64 encoded blob,which will be decoded and token-expanded prior to being sent.
       "contenttype":"",//optional-if this is length > 0 and POST type is selected this will be set as the Content-Typeheader. if this is not supplied for a POST request,the default will be "application/x-www-form-urlencoded"
       "timeout":0//optional-numberofsecondstowaitbeforetimingout.Defaultis2.} 
   ```

   L&#39;oggetto `payload` nel codice è un payload di esempio per la definizione di un messaggio da inserire nel file `ADBMobileConfig.json`. Per ulteriori informazioni, vedi [Postback](/help/ios/analytics-main/postback/postback.md).

   * Versione SDK minima: 4.0

* **timeout**

   Determina per quanto tempo Target può aspettare di ricevere una risposta.

   * Versione SDK minima: 4.0

## File di esempio `ADBMobileConfig.json`  {#section_52FA7C71A99147AFA9BE08D2177D8DA7}

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
         `image` non è accessibile
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

* &quot;audiences&quot;

   Array di oggetti che definisce come deve essere visualizzato il messaggio:

   * &quot;key&quot;

      Nome della variabile da cercare nell’hit; obbligatorio.

   * &quot;matches&quot;

      Tipo di corrispondenza utilizzato per il confronto:

      * eq = equals
      * ne = does not equal
      * co = contains
      * nc = does not contain
      * sw = starts with
      * ew = ends with
      * ex = exists
      * nx = does not exist
      * lt = less than
      * le = less than or equals
      * gt = greater than
      * ge = greater than or equals
   * &quot;values&quot;

      Array di valori utilizzati per eseguire il confronto rispetto al valore della variabile denominata in:

      * key
      * con il tipo di corrispondenza in
      * matches


* &quot;triggers&quot;

   Simile a audience, ma per le azioni anziché per il pubblico:

   * &quot;key&quot;
   * &quot;corrisponde&quot;
   * &quot;values&quot;
