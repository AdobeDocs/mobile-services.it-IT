---
description: Queste informazioni sono utili per eseguire un ciclo completo di verifica per il collegamento di una campagna di acquisizione V3 basata sull'impronta digitale di un dispositivo.
seo-description: Queste informazioni sono utili per eseguire un ciclo completo di verifica per il collegamento di una campagna di acquisizione V3 basata sull'impronta digitale di un dispositivo.
seo-title: Verifica dell'acquisizione V3
solution: Marketing Cloud,Analytics
title: Verifica dell'acquisizione V3
uuid: 89137ccf-4839-4b37-926e-303cf8e511a5
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Testing V3 acquisition{#testing-v-acquisition}

Queste informazioni sono utili per eseguire un ciclo completo di verifica per il collegamento di una campagna di acquisizione V3 basata sull'impronta digitale di un dispositivo.

>[!IMPORTANT]
>
> per "acquisizione V3" si intendono i collegamenti di acquisizione creati con Acquisition Builder nell'interfaccia utente di Adobe Mobile Services. Per utilizzare questa funzione, devi passare alla versione SDK 4.6.0 o successiva per iOS.

Se l'app per dispositivi mobili non è ancora disponibile nell'App Store, seleziona una qualsiasi app mobile da usare come destinazione al momento di creare il collegamento della campagna. Questo incide solo sull'app alla quale il server di acquisizione ti reindirizzerà quando fai clic sul collegamento di acquisizione, e non sulla capacità di verificare il funzionamento del collegamento.

1. Completa le attività preliminari descritte nella sezione [Acquisizione da app mobile](/help/ios/acquisition-main/acquisition.md).
1. Passa ad **[!UICONTROL Acquisition Builder]nell'interfaccia utente di Adobe Mobile Services e genera un URL per una campagna di acquisizione.**

   Ad esempio:

   ```
   https://c00.adobe.com/v3/<appid>/start?a_i_id=iostestapp&a_g_id=com.adobe.android&a_dd=i&ctxa.referrer.campaign.name=name&ctxa.referrer.campaign.trackingcode=trackingcode
   ```


   Se il collegamento di acquisizione fa riferimento a un'app per iOS e una per Android, usa Apple Store come store predefinito.
1. Apri il collegamento generato in un browser desktop e passa a `https://c00.adobe.com/v3/<appid>/end`.

   Nella risposta JSON dovresti trovare i dati contestuali `contextData`:

   ```js
   {"fingerprint":"228d7e6058b1d731dc7a8b8bd0c15e1d78242f31","timestamp":1457989293,"appguid":"","contextData":{"a.referrer.campaign.name":"name","a.referrer.campaign.trackingcode":"trackingcode"}}.
   ```

   If you do not see `contextData`, or some of it is missing, ensure that the acquisition URL follows the format that is specified in [Create Acquisition Link Manually](/help/using/acquisition-main/c-marketing-links-builder/acquisition-link-manual.md).
1. Verifica che le seguenti impostazioni nel file di configurazione siano corrette:

   | Impostazione | Valore |
   |--- |--- |
   | acquisizione | The server should be  `c00.adobe.com`. *`appid`* should equal the *`appid`* in your acquisition link. |
   | analytics | `referrerTimeout` dovrebbe essere un valore maggiore di 0. |


1. (Condizionale) Se l'impostazione `ssl` nel file di configurazione dell'app è "true", aggiorna il collegamento di acquisizione, impostandolo per l'utilizzo del protocollo HTTPS.
1. Fate clic sul collegamento generato dal dispositivo mobile sul quale intendete installare l'app.

   I server di Adobe (`c00.adobe.com`) memorizzano l'impronta digitale ed eseguono il reindirizzamento all'App Store. Non è necessario scaricare l'app per eseguire la verifica.
1. Sullo stesso dispositivo mobile utilizzato al punto 6, avvia l'applicazione per la prima volta.

   Se necessario, elimina e installa di nuovo l'app.
1. (Facoltativo) Per ottenere informazioni aggiuntive, puoi abilitare la registrazione di debug dell'SDK.

   Se tutto funziona correttamente, nel registro dovresti trovare le seguenti voci:

   `"Analytics - Trying to fetch referrer data from <acquisition end url>"`
   `"Analytics - Received Referrer Data(<Json Object>)"`

   In caso contrario, assicurati di aver completato i passaggi 4 e 5.

   Here is some information about possible errors:

   * `Analytics - Unable to retrieve acquisition service response (<error message>)`(Impossibile recuperare la risposta del servizio di acquisizione) - Si è verificato un errore di rete.

   * `Analytics - Unable to parse acquisition service response (<error message>)`

      (Impossibile analizzare la risposta del servizio di acquisizione) - La risposta non è nel formato corretto.

   * `Analytics - Unable to parse acquisition service response (no contextData parameter in response)`

      Nela risposta non è presente il parametro `contextData`.

   * `Analytics - Acquisition referrer data was not complete, ignoring`

      `a.referrer.campaign.name` is not included in .`contextData`

   * `Analytics - Acquisition referrer timed out`

      (Timeout del referente acquisizione) - Impossibile ricevere la risposta entro l'intervallo di tempo definito da `referrerTimeout`. Aumenta questo valore e riprova. Controlla anche di aver aperto il collegamento di acquisizione prima di installare l'app e di usare la stessa rete sia per fare clic sull'URL che per aprire l'app.

      Considerazioni da ricordare:

      * Il server di acquisizione fornisce una corrispondenza di attribuzione basata sull'indirizzo IP e sulle informazioni dell'agente utente registrate al momento del clic sul collegamento (passaggio 6) e all'avvio dell'app (passaggio 7).

         Il clic sull'URL e l'avvio dell'app devono avvenire dalla stessa rete.

      * Utilizzando strumenti di monitoraggio HTTP, è possibile monitorare gli hit inviati dall'app per fornire elementi utili alla verifica dell'attribuzione dell'acquisizione.

         Dovresti trovare una richiesta `/v3/<appid>/start` e una richiesta `/v3/<appid>/end`, entrambe inviate al server di acquisizione. Eventuali varianti nell'agente utente inviato potrebbero provocare errori di attribuzione.

         >[!TIP]
         >
         >Accertatevi che `https://c00.adobe.com/v3/<appid>/start` e `https://c00.adobe.com/v3/<appid>/end` abbiate gli stessi valori agente utente.

      * Il collegamento di acquisizione e l'hit dell'SDK dovrebbero usare lo stesso protocollo, HTTP o HTTPS.

         Se il collegamento e l'hit usano protocolli diversi (ad esempio, HTTP per il collegamento e HTTPS per l'SDK), l'indirizzo IP potrebbe risultare diverso nelle due richieste (per alcuni gestori) e l'attribuzione potrebbe non riuscire.
