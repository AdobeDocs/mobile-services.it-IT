---
description: Le istruzioni seguenti ti aiutano a esplorare una campagna di acquisizione con un collegamento marketing basato sull'impronta digitale di un dispositivo.
keywords: android; libreria; mobile; sdk
seo-description: Le istruzioni seguenti ti aiutano a esplorare una campagna di acquisizione con un collegamento marketing basato sull'impronta digitale di un dispositivo.
seo-title: Test acquisizione collegamento marketing
solution: Marketing Cloud, Analytics
title: Test acquisizione collegamento marketing
topic: Sviluppatore e implementazione
uuid: 69503 e 01-182 d -44 c 6-b 0 fb-e 1 c 012 ffa 3 bd
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Testing Marketing Link acquisition {#testing-marketing-link-acquisition}

Le istruzioni seguenti ti aiutano a esplorare una campagna di acquisizione con un collegamento marketing basato sull'impronta digitale di un dispositivo.

1. Completa le attività preliminari in [Acquisizione app mobile](/help/ios/acquisition-main/acquisition.md).
1. In the Adobe Mobile Services UI, click **[!UICONTROL Marketing Links Builder]** and generate an acquisition Marketing Link URL that sets the App Store as the destination for iOS devices.

   Ad esempio:

   ```
   https://c00.adobe.com/v3/da120731d6c09658b82d8fac78da1d5fc2d09c48e21b3a55f9e2d7344e08425d/start?a_dl=57477650072932ec6d3a470f
   ```

   Per ulteriori informazioni, consulta [Marketing Links Builder](/help/using/acquisition-main/c-marketing-links-builder/c-marketing-links-builder.md).


1. Open the generated link on the iOS device and open `https://c00.adobe.com/v3/<appid>/end`.

   Nella risposta JSON dovresti trovare i dati contestuali contextData:

   ```js{"fingerprint":"bae91bb778f0ad52e37f0892961d06ac6a5c935b","endCallbacks":["***"],"timestamp":1464301217,"appguid":"da120731d6c09658b82d8fac78da1d5fc2d09c48e21b3a55f9e2d7344e08425d","contextData":
   {"a.launch.campaign.trackingcode":"twdf4546","a.referrer.campaign.name":"iOS Demo","a.referrer.campaign.trackingcode":"twdf4546"}
   ,"adobeData":{"unique_id":"8c14098d7c79e8a180c15e4b2403549d3cc21ea8","deeplinkid":"57477650072932ec6d3a470f"}}
   ```

1. Verifica che le seguenti impostazioni nel file di configurazione siano corrette:

   | Impostazione | Valore |
   |--- |--- |
   | acquisition | The server should be  `c00.adobe.com`. `appid` deve corrispondere al *`appid`* collegamento di acquisizione. |
   | analytics | `referrerTimeout` dovrebbe essere un valore maggiore di 0. |

1. (Condizionale) Se l'impostazione SSL nel file di configurazione dell'app è `false`, aggiorna il collegamento di acquisizione, impostandolo per l'utilizzo del protocollo HTTP anziché HTTPS.
1. Dal dispositivo mobile sul quale desideri installare l'app, fai clic sul collegamento generato.

   I server di Adobe (`c00.adobe.com`) memorizzano l'impronta digitale ed eseguono il reindirizzamento all'App Store. Non è necessario scaricare l'app per eseguire la verifica.
1. Sullo stesso dispositivo mobile utilizzato al punto 6, avvia l'applicazione per la prima volta.

   Se necessario, elimina e installa di nuovo l'app.
1. (Facoltativo) Per ottenere informazioni aggiuntive, abilita la registrazione di debug dell'SDK.

   Se tutto funziona correttamente, nel registro dovresti trovare le seguenti voci:

   `"Analytics - Trying to fetch referrer data from <acquisition end url>"`
   `"Analytics - Received Referrer Data(<Json Object>)"`

   Se non trovi questi registri, verifica di aver completato i passaggi 4 e 5.

   Seguono alcune informazioni su possibili errori:

   * `Analytics - Unable to retrieve acquisition service response (<error message>)`:

      (Impossibile recuperare la risposta del servizio di acquisizione) - Si è verificato un errore di rete.

   * `Analytics - Unable to parse acquisition service response (<error message>)`

      (Impossibile analizzare la risposta del servizio di acquisizione) - La risposta non è nel formato corretto.

   * `Analytics - Unable to parse acquisition service response (no contextData parameter in response)`

      Nela risposta non è presente il parametro `contextData`.

   * `Analytics - Acquisition referrer data was not complete, ignoring`

      `a.referrer.campaign.name` non è incluso `contextData`.

   * `Analytics - Acquisition referrer timed out`

      (Timeout del referente acquisizione) - Impossibile ricevere la risposta entro l'intervallo di tempo definito da `referrerTimeout`. Aumenta questo valore e riprova. Controlla anche di aver aperto il collegamento di acquisizione prima di installare l'app e di usare la stessa rete sia per fare clic sull'URL che per aprire l'app.

Considerazioni da ricordare:

* Il server di acquisizione fornisce una corrispondenza di attribuzione basata sull'indirizzo IP e sulle informazioni dell'agente utente registrate al momento del clic sul collegamento (passaggio 6) e all'avvio dell'app (passaggio 7).

   Il clic sull'URL e l'avvio dell'app devono avvenire dalla stessa rete.

* Utilizzando strumenti di monitoraggio HTTP, è possibile monitorare gli hit inviati dall'app per fornire elementi utili alla verifica dell'attribuzione dell'acquisizione.

   You should see one `/v3/<appid>/start` request and one `/v3/<appid>/end` request that are sent to the acquisition server.

* Eventuali varianti nell'agente utente inviato potrebbero provocare errori di attribuzione.

   Assicuratevi che `https://c00.adobe.com/v3/<appid>/start` e `https://c00.adobe.com/v3/<appid>/end` abbiano gli stessi valori agente utente.

* Il collegamento di acquisizione e l'hit dell'SDK dovrebbero usare lo stesso protocollo, HTTP o HTTPS.

   Se il collegamento e l'hit utilizzano protocolli diversi, dove ad esempio il collegamento utilizza HTTP e l'SDK usa HTTPS, l'indirizzo IP potrebbe risultare diverso in alcuni gestori per ogni richiesta. In tal caso l'attribuzione potrebbe non riuscire.

* I collegamenti di marketing sono memorizzati nella cache sul lato server con una scadenza di dieci minuti.

   Quando apportate modifiche ai collegamenti di marketing, attendete circa 10 minuti prima di utilizzare i collegamenti.