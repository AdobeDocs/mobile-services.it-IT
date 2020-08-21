---
description: Le seguenti istruzioni consentono di esplorare una campagna di acquisizione con un collegamento di marketing su un dispositivo Android.
keywords: android;library;mobile;sdk
seo-description: Le seguenti istruzioni consentono di esplorare una campagna di acquisizione con un collegamento di marketing su un dispositivo Android.
seo-title: Verifica dell'acquisizione da collegamenti marketing
solution: Marketing Cloud,Analytics
title: Verifica dell'acquisizione da collegamenti marketing
topic: Developer and implementation
uuid: d0933dcc-8fc3-4f60-987f-7a54559aacf5
translation-type: tm+mt
source-git-commit: 7ae626be4d71641c6efb127cf5b1d3e18fccb907
workflow-type: tm+mt
source-wordcount: '763'
ht-degree: 78%

---


# Verifica dell&#39;acquisizione da collegamenti marketing {#testing-marketing-link-acquisition}

Le seguenti istruzioni consentono di esplorare una campagna di acquisizione con un collegamento di marketing su un dispositivo Android.

Se la tua app mobile non è ancora disponibile in Google Play, durante la creazione del collegamento di marketing puoi selezionare come destinazione qualsiasi app mobile. Questo incide solo sull’app alla quale il server di acquisizione ti reindirizzerà, dopo aver fatto clic sul collegamento di acquisizione, e non sulla capacità di verificare il collegamento di acquisizione. I parametri della stringa di query vengono passati a Google Play Store, che vengono passati all&#39;app al momento dell&#39;installazione come parte di una trasmissione della campagna. Il test di acquisizione da app mobile richiede la simulazione di questo tipo di trasmissione.

L’app deve essere stata appena installata oppure i dati devono essere eliminati nelle **[!UICONTROL Impostazioni]** tutte le volte che si esegue un test. In questo modo le metriche del ciclo di vita iniziali associate ai parametri di stringa della query della campagna vengono inviate al primo avvio dell&#39;app.

1. Completa le attività preliminari descritte nella sezione [Acquisizione da app mobile](/help/android/acquisition-main/acquisition.md) e assicurati di aver implementato correttamente il destinatario della trasmissione per `INSTALL_REFERRER`.
1. Nell’interfaccia utente di Adobe Mobile Services, fai clic su **[!UICONTROL Acquisizione]** > **[!UICONTROL Marketing Links Builder]** e genera l’URL di un collegamento marketing di acquisizione che imposti Google Play come destinazione per i dispositivi Android.

   Per ulteriori informazioni, consulta [Marketing Links Builder](/help/using/acquisition-main/c-marketing-links-builder/c-marketing-links-builder.md).

   Ad esempio:

   `https://c00.adobe.com/v3/da120731d6c09658b82d8fac78da1d5fc2d09c48e21b3a55f9e2d7344e08425d/start?a_dl=573e5bb3248a501360c2890b`

1. Apri il collegamento generato sul dispositivo Android.

   Dovresti essere reindirizzato a una pagina con un URL simile al seguente esempio:

   `https://play.google.com/store/apps/details?id=com.adobe.android&referrer=utm_campaign%3Dadb_acq_v3%26utm_source%3Dadb_acq_v3%26utm_content%3D91b52ce097b1464b9b47cb2995c493cc6ab2c3a3`

1. Copia l&#39;ID univoco dopo `utm_content%3D`.

   Nell’esempio precedente, l’ID è `91b52ce097b1464b9b47cb2995c493cc6ab2c3a3`.

   Se non riesci a ottenere l&#39;ID univoco sul dispositivo, esegui il seguente comando `CURL` sul desktop per ottenere l&#39;ID univoco dalla stringa di risposta.

   `curl -A "Mozilla/5.0 (Linux; Android 5.0.2; SAMSUNG SM-T815Y Build/LRX22G) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/44.0.2403.133 Safari/537.36" <Your Marketing Link>`

   Ad esempio:

   `curl -A "Mozilla/5.0 (Linux; Android 5.0.2; SAMSUNG SM-T815Y Build/LRX22G) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/44.0.2403.133 Safari/537.36" https://c00.adobe.com/v3/da120731d6c09658b82d8fac78da1d5fc2d09c48e21b3a55f9e2d7344e08425d/start?a_dl=573e5bb3248a501360c2890b`

1. Crea il collegamento di acquisizione finale usando l&#39;ID univoco del passaggio 3, nel seguente formato:

   `https://c00.adobe.com/v3/<appid>/end?a_ugid=<unique id>`

   Ad esempio, `https://c00.adobe.com/v3/<appid>/end?a_ugid=91b52ce097b1464b9b47cb2995c493cc6ab2c3a3`

1. Apri il collegamento in un browser.

   Dovresti vedere `contextData` nella risposta JSON:

   ```
   {"fingerprint":"44b2f88a062df7e727c047f006deb9971304617b","endCallbacks":["***"],"timestamp":1464301282,"appguid":"da120731d6c09658b82d8fac78da1d5fc2d09c48e21b3a55f9e2d7344e08425d","contextData": 
   {"a.launch.campaign.trackingcode":"trymttvm","a.referrer.campaign.name":"Android Demo","a.referrer.campaign.trackingcode":"trymttvm"} 
   ,"adobeData":{"unique_id":"9a2be52764a8db125c29a8c10f3b1b3d5d8ed915","deeplinkid":"57476c26072932ec6d3a470b"}}.
   ```

1. Per ottenere un nuovo ID univoco, ripeti il passaggio 3.
1. Verifica che le seguenti impostazioni nel file di configurazione siano corrette:

   | Impostazione | Valore |
   |--- |--- |
   | acquisizione | Il server dovrebbe essere `c00.adobe.com` e *`appid`* dovrebbe corrispondere a `appid` nel collegamento di acquisizione. |
   | analytics | A scopo di test, impostate il timeout del referente in modo da concedere un tempo sufficiente (almeno 60 secondi) per inviare manualmente la trasmissione. Puoi ripristinare l’impostazione di timeout originale dopo il test. |

1. Connetti il dispositivo a un computer e disinstalla e reinstalla l&#39;app.
1. Avvia ADB Shell, quindi avvia l&#39;applicazione sul dispositivo.

   ```
   adb shell
   ```

1. Invia una trasmissione usando il seguente comando `adb`:

   ```
   am broadcast -a com.android.vending.INSTALL_REFERRER -n com.adobe.android/com.adobe.android.YourBroadcastReceiver --es "referrer" "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<unique id get on step 5>"
   ```

1. Sostituisci `com.adobe.android` con il nome del pacchetto dell&#39;applicazione, aggiorna il riferimento del ricevitore con il riferimento della posizione del ricevitore di tracciamento della campagna nella tua app e sostituisci i valori associati con `utm_content`.

   Se la trasmissione è riuscita, la risposta sarà simile a quella nel seguente esempio:

   ```
   Broadcasting: Intent 
   { act=com.android.vending.INSTALL_REFERRER cmp=com.adobe.adms.tests/.ReferralReceiver (has extras) } 
   Broadcast completed: result=0 
   ```

1. (Facoltativo) Per ottenere informazioni aggiuntive, puoi abilitare la registrazione di debug dell&#39;SDK.

   Se tutto funziona correttamente, nel registro dovresti trovare le seguenti voci:

   ```
   "Analytics - Received referrer information(<referrer content>)" 
   "Analytics - Trying to fetch referrer data from (acquisition end url)"; 
   "Analytics - Received Referrer Data(<A JSON Response>)"
   ```

   Se questi registri non compaiono, verifica di aver completato i passaggi da 6 a 10.

   La tabella seguente contiene informazioni aggiuntive sui possibili errori:

   | Errore | Descrizione |
   |--- |--- |
   | Analytics - Unable to decode response(`<string>`). | La risposta è formata in modo errato. |
   | Analytics - Unable to parse response (`a JSON Response`). | La stringa JSON è formata in modo errato. |
   | Analytics - Unable to parse acquisition service response (no `contextData` parameter in response). | La risposta non contiene il parametro `contextData`. |
   | Analytics - Acquisition referrer data was not complete (no `a.referrer.campaign.name` in context data), ignoring. | `a.referrer.campaign.name` non è incluso in contextData. |
   | Analytics - Acquisition referrer timed out. | Impossibile ottenere la risposta nell&#39;intervallo temporale definito in `referrerTimeout`. Aumenta questo valore e riprova.  Devi accertarti anche di aver aperto il collegamento di acquisizione prima di installare l’app. |

Considerazioni da ricordare:

* Gli hit inviati dall’app possono essere monitorati mediante gli strumenti di monitoraggio HTTP per verificare l’attribuzione di acquisizione.
* Per ulteriori informazioni sulle modalità di trasmissione di `INSTALL_REFERRER`, consulta [Testare la misurazione delle campagne Google Play](https://developers.google.com/analytics/solutions/testing-play-campaigns) nella guida per gli sviluppatori di Google.
* Puoi usare lo strumento Java `acquisitionTest.jar` fornito per ottenere l&#39;ID univoco e il riferimento di installazione della trasmissione, per ottenere quindi le informazioni nei passaggi 3-10.

**Installare lo strumento Java**

Per installare lo strumento Java:

1. Scarica il file [`acquistionTester.zip`](../assets/acquisitionTester.zip).
1. Estraete il file .jar.

   Potete eseguire il file .jar sulla riga di comando.

Ad esempio:

```
java -jar acquisitionTester.jar -a com.adobe.test -r com.adobe.test.ReferrerReceiver -l "https://c00.adobe.com/v3/appid/start?a_i_id=123456&a_g_id=com.adobe.test&a_dd=i&ctxa.referrer.campaign.name=name&ctxa.referrer.campaign.trackingcode=1234
```

I collegamenti marketing sono memorizzati nella cache lato server con un tempo di scadenza di 10 minuti. Quando apporti modifiche ai collegamenti di marketing, attendi 10 minuti prima di riutilizzarli, per accertarti che le modifiche siano state applicate.
