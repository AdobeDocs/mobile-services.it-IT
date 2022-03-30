---
description: Le istruzioni seguenti sono utili per eseguire un ciclo completo per la verifica di una campagna di acquisizione con un collegamento di marketing basato sull'impronta digitale di un dispositivo.
keywords: android,libreria,mobile,sdk
solution: Experience Cloud Services,Analytics
title: Verifica dell’acquisizione da collegamenti marketing
topic-fix: Developer and implementation
uuid: 69503e01-182d-44c6-b0fb-e1c012ffa3bd
exl-id: 2fb02b36-172e-4c16-9ef9-13f8288ab8a4
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '542'
ht-degree: 100%

---

# Verifica dell’acquisizione da collegamenti marketing {#testing-marketing-link-acquisition}

Le istruzioni seguenti sono utili per eseguire un ciclo completo per la verifica di una campagna di acquisizione con un collegamento di marketing basato sull&#39;impronta digitale di un dispositivo.

1. Completa le attività preliminari descritte nella sezione [Acquisizione da app mobile](/help/ios/acquisition-main/acquisition.md).
1. Nell&#39;interfaccia utente di Adobe Mobile Services, fai clic su **[!UICONTROL Marketing Links Builder]** e genera un URL per un collegamento di acquisizione marketing, con l&#39;App Store impostato come destinazione per i dispositivi iOS.

   Ad esempio:

   ```
   https://c00.adobe.com/v3/da120731d6c09658b82d8fac78da1d5fc2d09c48e21b3a55f9e2d7344e08425d/start?a_dl=57477650072932ec6d3a470f
   ```

   Per ulteriori informazioni, consulta [Marketing Links Builder](/help/using/acquisition-main/c-marketing-links-builder/c-marketing-links-builder.md).


1. Sul dispositivo iOS, apri il collegamento generato e la pagina `https://c00.adobe.com/v3/<appid>/end`.

   Nella risposta JSON dovresti trovare i dati contestuali contextData:

   ```js
   {"fingerprint":"bae91bb778f0ad52e37f0892961d06ac6a5c935b","endCallbacks":["***"],"timestamp":1464301217,"appguid":"da120731d6c09658b82d8fac78da1d5fc2d09c48e21b3a55f9e2d7344e08425d","contextData":
   {"a.launch.campaign.trackingcode":"twdf4546","a.referrer.campaign.name":"iOS Demo","a.referrer.campaign.trackingcode":"twdf4546"}
   ,"adobeData":{"unique_id":"8c14098d7c79e8a180c15e4b2403549d3cc21ea8","deeplinkid":"57477650072932ec6d3a470f"}}
   ```

1. Verifica che le seguenti impostazioni nel file di configurazione siano corrette:

   | Impostazione | Valore |
   |--- |--- |
   | acquisizione | Il server dovrebbe essere `c00.adobe.com` e `appid` dovrebbe corrispondere a *`appid`* nel collegamento di acquisizione. |
   | analytics | `referrerTimeout` dovrebbe essere un valore maggiore di 0. |

1. (Condizionale) Se l&#39;impostazione SSL nel file di configurazione dell&#39;app è `false`, aggiorna il collegamento di acquisizione, impostandolo per l&#39;utilizzo del protocollo HTTP anziché HTTPS.
1. Dal dispositivo mobile sul quale desideri installare l&#39;app, fai clic sul collegamento generato.

   I server di Adobe (`c00.adobe.com`) memorizzano l&#39;impronta digitale ed eseguono il reindirizzamento all&#39;App Store. Non è necessario scaricare l&#39;app per eseguire la verifica.
1. Sullo stesso dispositivo mobile utilizzato al punto 6, avvia l&#39;applicazione per la prima volta.

   Se necessario, elimina e installa di nuovo l&#39;app.
1. (Facoltativo) Per ottenere informazioni aggiuntive, abilita la registrazione di debug dell&#39;SDK.

   Se tutto funziona correttamente, nel registro dovresti trovare le seguenti voci:

   `"Analytics - Trying to fetch referrer data from <acquisition end url>"`
   `"Analytics - Received Referrer Data(<Json Object>)"`

   In caso contrario, assicurati di aver completato i passaggi 4 e 5.

   Seguono alcune informazioni su possibili errori:

   * `Analytics - Unable to retrieve acquisition service response (<error message>)`

      (Impossibile recuperare la risposta del servizio di acquisizione) - Si è verificato un errore di rete.

   * `Analytics - Unable to parse acquisition service response (<error message>)`

      (Impossibile analizzare la risposta del servizio di acquisizione) - La risposta non è nel formato corretto.

   * `Analytics - Unable to parse acquisition service response (no contextData parameter in response)`

      Nela risposta non è presente il parametro `contextData`.

   * `Analytics - Acquisition referrer data was not complete, ignoring`

      `a.referrer.campaign.name` non è incluso in `contextData`.

   * `Analytics - Acquisition referrer timed out`

      (Timeout del referente acquisizione) - Impossibile ricevere la risposta entro l&#39;intervallo di tempo definito da `referrerTimeout`. Aumenta questo valore e riprova. Accertati inoltre di aver aperto il collegamento di acquisizione prima di installare l’app, e di utilizzare la stessa rete quando fai clic sull’URL e apri l’app.

Considerazioni da ricordare:

* Il server di acquisizione fornisce una corrispondenza di attribuzione basata sull&#39;indirizzo IP e sulle informazioni dell&#39;agente utente registrate al momento del clic sul collegamento (passaggio 6) e all&#39;avvio dell&#39;app (passaggio 7).

   Il clic sull&#39;URL e l&#39;avvio dell&#39;app devono avvenire dalla stessa rete.

* Utilizzando strumenti di monitoraggio HTTP, è possibile monitorare gli hit inviati dall&#39;app per fornire elementi utili alla verifica dell&#39;attribuzione dell&#39;acquisizione.

   Dovresti trovare una richiesta `/v3/<appid>/start` e una richiesta `/v3/<appid>/end`, entrambe inviate al server di acquisizione.

* Eventuali varianti nell&#39;agente utente inviato potrebbero provocare errori di attribuzione.

   Assicurati che `https://c00.adobe.com/v3/<appid>/start` e `https://c00.adobe.com/v3/<appid>/end` abbiano gli stessi valori agente utente.

* Il collegamento di acquisizione e l&#39;hit dell&#39;SDK dovrebbero usare lo stesso protocollo, HTTP o HTTPS.

   Se il collegamento e l&#39;hit usano protocolli diversi, ad esempio, HTTP per il collegamento e HTTPS per l&#39;SDK, l&#39;indirizzo IP potrebbe risultare diverso nelle due richieste per alcuni gestori. In tal caso l&#39;attribuzione potrebbe non riuscire.

* I collegamenti marketing sono memorizzati nella cache lato server con un tempo di scadenza di 10 minuti.

   Se devi apportare delle modifiche ai collegamenti marketing, attendi circa 10 minuti prima di usare i nuovi collegamenti.
