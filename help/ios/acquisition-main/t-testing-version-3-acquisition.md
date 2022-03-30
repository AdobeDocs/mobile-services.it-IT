---
description: Queste informazioni sono utili per eseguire un ciclo completo di verifica per il collegamento di una campagna di acquisizione V3 basata sull'impronta digitale di un dispositivo.
solution: Experience Cloud Services,Analytics
title: Verifica dell’acquisizione V3
uuid: 89137ccf-4839-4b37-926e-303cf8e511a5
exl-id: 3cf66802-1f2c-428f-86ef-a9afc57e3470
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '602'
ht-degree: 100%

---

# Verifica dell’acquisizione V3 {#testing-v-acquisition}

Queste informazioni sono utili per eseguire un ciclo completo di verifica per il collegamento di una campagna di acquisizione V3 basata sull&#39;impronta digitale di un dispositivo.

>[!IMPORTANT]
>
>per &quot;acquisizione V3&quot; si intendono i collegamenti di acquisizione creati con Acquisition Builder nell&#39;interfaccia utente di Adobe Mobile Services. Per utilizzare questa funzione, devi passare alla versione SDK 4.6.0 o successiva per iOS.

Se l&#39;app per dispositivi mobili non è ancora disponibile nell&#39;App Store, seleziona una qualsiasi app mobile da usare come destinazione al momento di creare il collegamento della campagna. Questo incide solo sull&#39;app alla quale il server di acquisizione ti reindirizzerà quando fai clic sul collegamento di acquisizione, e non sulla capacità di verificare il funzionamento del collegamento.

1. Completa le attività preliminari descritte nella sezione [Acquisizione da app mobile](/help/ios/acquisition-main/acquisition.md).
1. Passa ad **[!UICONTROL Acquisition Builder]** nell&#39;interfaccia utente di Adobe Mobile Services e genera un URL per una campagna di acquisizione.

   Ad esempio:

   ```
   https://c00.adobe.com/v3/<appid>/start?a_i_id=iostestapp&a_g_id=com.adobe.android&a_dd=i&ctxa.referrer.campaign.name=name&ctxa.referrer.campaign.trackingcode=trackingcode
   ```


   Se il collegamento di acquisizione fa riferimento a un&#39;app per iOS e una per Android, usa Apple Store come store predefinito.
1. Apri il collegamento generato in un browser desktop e passa a `https://c00.adobe.com/v3/<appid>/end`.

   Nella risposta JSON dovresti trovare i dati contestuali `contextData`:

   ```js
   {"fingerprint":"228d7e6058b1d731dc7a8b8bd0c15e1d78242f31","timestamp":1457989293,"appguid":"","contextData":{"a.referrer.campaign.name":"name","a.referrer.campaign.trackingcode":"trackingcode"}}.
   ```

   Se non visualizzi `contextData`, o se ne mancano alcuni, accertati che l&#39;URL di acquisizione segua il formato specificato in [Creare manualmente i collegamenti di acquisizione](/help/using/acquisition-main/c-marketing-links-builder/acquisition-link-manual.md).
1. Verifica che le seguenti impostazioni nel file di configurazione siano corrette:

   | Impostazione | Valore |
   |--- |--- |
   | acquisizione | Il server dovrebbe essere `c00.adobe.com` e *`appid`* dovrebbe corrispondere a *`appid`* nel collegamento di acquisizione. |
   | analytics | `referrerTimeout` dovrebbe essere un valore maggiore di 0. |


1. (Condizionale) Se l&#39;impostazione `ssl` nel file di configurazione dell&#39;app è &quot;true&quot;, aggiorna il collegamento di acquisizione, impostandolo per l&#39;utilizzo del protocollo HTTPS.
1. Dal dispositivo mobile sul quale intendi installare l&#39;app, fai clic sul collegamento generato.

   I server di Adobe (`c00.adobe.com`) memorizzano l&#39;impronta digitale ed eseguono il reindirizzamento all&#39;App Store. Non è necessario scaricare l&#39;app per eseguire la verifica.
1. Sullo stesso dispositivo mobile utilizzato al punto 6, avvia l&#39;applicazione per la prima volta.

   Se necessario, elimina e installa di nuovo l&#39;app.
1. (Facoltativo) Per ottenere informazioni aggiuntive, puoi abilitare la registrazione di debug dell&#39;SDK.

   Se tutto funziona correttamente, nel registro dovresti trovare le seguenti voci:

   `"Analytics - Trying to fetch referrer data from <acquisition end url>"`
   `"Analytics - Received Referrer Data(<Json Object>)"`

   In caso contrario, assicurati di aver completato i passaggi 4 e 5.

   Seguono alcune informazioni su possibili errori:

   * `Analytics - Unable to retrieve acquisition service response (<error message>)`(Impossibile recuperare la risposta del servizio di acquisizione) - Si è verificato un errore di rete.

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

         Dovresti trovare una richiesta `/v3/<appid>/start` e una richiesta `/v3/<appid>/end`, entrambe inviate al server di acquisizione. Eventuali varianti nell&#39;agente utente inviato potrebbero provocare errori di attribuzione.

         >[!TIP]
         >
         >Assicurati che `https://c00.adobe.com/v3/<appid>/start` e `https://c00.adobe.com/v3/<appid>/end` abbiano gli stessi valori agente utente.

      * Il collegamento di acquisizione e l&#39;hit dell&#39;SDK dovrebbero usare lo stesso protocollo, HTTP o HTTPS.

         Se il collegamento e l&#39;hit usano protocolli diversi (ad esempio, HTTP per il collegamento e HTTPS per l&#39;SDK), l&#39;indirizzo IP potrebbe risultare diverso nelle due richieste (per alcuni gestori) e l&#39;attribuzione potrebbe non riuscire.
