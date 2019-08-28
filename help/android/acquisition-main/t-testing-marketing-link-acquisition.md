---
description: Le istruzioni seguenti ti aiutano a esplorare una campagna di acquisizione con un collegamento marketing su un dispositivo Android.
keywords: android; libreria; mobile; sdk
seo-description: Le istruzioni seguenti ti aiutano a esplorare una campagna di acquisizione con un collegamento marketing su un dispositivo Android.
seo-title: Verifica dell'acquisizione da collegamenti marketing
solution: Marketing Cloud, Analytics
title: Verifica dell'acquisizione da collegamenti marketing
topic: Sviluppatore e implementazione
uuid: d 0933 dcc -8 fc 3-4 f 60-987 f -7 a 54559 aacf 5
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Testing Marketing Link acquisition {#testing-marketing-link-acquisition}

Le istruzioni seguenti ti aiutano a esplorare una campagna di acquisizione con un collegamento marketing su un dispositivo Android.

Se la tua app mobile non è ancora disponibile in Google Play, puoi selezionare qualsiasi app mobile come destinazione quando crei il collegamento marketing. Questo incide solo sull'app alla quale il server di acquisizione ti reindirizzerà quando fai clic sul collegamento di acquisizione, e non sulla capacità di verificare il funzionamento del collegamento di acquisizione. I parametri della stringa di query vengono passati a Google Play Store e quindi all'app al momento dell'installazione, nell'ambito della trasmissione della campagna. Il test dell'acquisizione da app mobile richiede la simulazione di questo tipo di trasmissione.

The app must be freshly installed, or have data cleared in **[!UICONTROL Settings]**, each time a test is run. In questo modo le metriche del ciclo di vita iniziali associate ai parametri di stringa della query della campagna vengono inviate al primo avvio dell'app.

1. Completa le attività preliminari nell'acquisizione da app [mobile](/help/android/acquisition-main/acquisition.md) e accertati di aver implementato correttamente il destinatario della trasmissione.`INSTALL_REFERRER`
1. In the Adobe Mobile Services] UI, click  **[!UICONTROL Acquisition]** &gt; **[!UICONTROL Marketing Links Builder]** and generate an Acquisition Marketing Link URL that sets Google Play as the destination for Android devices.

   Per ulteriori informazioni, consulta [Marketing Links Builder](/help/using/acquisition-main/c-marketing-links-builder/c-marketing-links-builder.md).

   Ad esempio:

   `https://c00.adobe.com/v3/da120731d6c09658b82d8fac78da1d5fc2d09c48e21b3a55f9e2d7344e08425d/start?a_dl=573e5bb3248a501360c2890b`

1. Apri il collegamento generato sul dispositivo Android.

   Dovresti essere reindirizzato a una pagina con un URL simile al seguente esempio:

   `https://play.google.com/store/apps/details?id=com.adobe.android&referrer=utm_campaign%3Dadb_acq_v3%26utm_source%3Dadb_acq_v3%26utm_content%3D91b52ce097b1464b9b47cb2995c493cc6ab2c3a3`

1. Copy the unique ID after `utm_content%3D`.

   Nell'esempio precedente, l'ID `91b52ce097b1464b9b47cb2995c493cc6ab2c3a3`è.

   Se non riesci a ottenere l'ID univoco sul dispositivo, esegui il seguente comando `CURL` sul desktop per ottenere l'ID univoco dalla stringa di risposta.

   `curl -A "Mozilla/5.0 (Linux; Android 5.0.2; SAMSUNG SM-T815Y Build/LRX22G) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/44.0.2403.133 Safari/537.36" <Your Marketing Link>`

   Ad esempio:

   `curl -A "Mozilla/5.0 (Linux; Android 5.0.2; SAMSUNG SM-T815Y Build/LRX22G) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/44.0.2403.133 Safari/537.36" https://c00.adobe.com/v3/da120731d6c09658b82d8fac78da1d5fc2d09c48e21b3a55f9e2d7344e08425d/start?a_dl=573e5bb3248a501360c2890b`

1. Crea il collegamento di acquisizione finale usando l'ID univoco del passaggio 3, nel seguente formato:

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
   | acquisition | Il server dovrebbe essere `c00.adobe.com`e *`appid`* deve corrispondere al `appid` collegamento di acquisizione. |
   | analytics | A fini di test, imposta il timeout di riferimento in modo tale da fornire il tempo necessario (almeno 60 secondi) per inviare manualmente la trasmissione. Puoi ripristinare l'impostazione di timeout originale dopo il test. |

1. Connetti il dispositivo a un computer e disinstalla e reinstalla l'app.
1. Avvia ADB Shell, quindi avvia l'applicazione sul dispositivo.

   ```
   adb shell
   ```

1. Invia una trasmissione usando il seguente comando `adb`: 

   ```
   am broadcast -a com.android.vending.INSTALL_REFERRER -n com.adobe.android/com.adobe.android.YourBroadcastReceiver --es "referrer" "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<unique id get on step 5>"
   ```

1. Sostituisci `com.adobe.android` con il nome del pacchetto dell'applicazione, aggiorna il riferimento del ricevitore con il riferimento della posizione del ricevitore di tracciamento della campagna nella tua app e sostituisci i valori associati con `utm_content`.

   Se la trasmissione è riuscita, la risposta sarà simile a quella nel seguente esempio:

   ```
   Broadcasting: Intent 
   { act=com.android.vending.INSTALL_REFERRER cmp=com.adobe.adms.tests/.ReferralReceiver (has extras) } 
   Broadcast completed: result=0 
   ```

1. (Facoltativo) Per ottenere informazioni aggiuntive, puoi abilitare la registrazione di debug dell'SDK.

   Se tutto funziona correttamente, nel registro dovresti trovare le seguenti voci:

   ```
   "Analytics - Received referrer information(<referrer content>)" 
   "Analytics - Trying to fetch referrer data from (acquisition end url)"; 
   "Analytics - Received Referrer Data(<A JSON Response>)"
   ```

   Se questi registri non compaiono, accertati di aver completato i passaggi da 6 a 10.

   La seguente tabella contiene informazioni aggiuntive sui possibili errori:

   | Errore | Descrizione |
   |--- |--- |
   | Analytics - Unable to decode response(`<string>`). | La risposta è formata in modo errato. |
   | Analytics - Unable to parse response (`a JSON Response`). | La stringa JSON è formata in modo errato. |
   | Analytics - Unable to parse acquisition service response (no `contextData` parameter in response). | La risposta non contiene il parametro `contextData`. |
   | Analytics - Acquisition referrer data was not complete (no `a.referrer.campaign.name` in context data), ignoring. | `a.referrer.campaign.name` non è incluso in contextdata. |
   | Analytics - Acquisition referrer timed out. | Impossibile ottenere la risposta nell'intervallo temporale definito in `referrerTimeout`. Aumenta questo valore e riprova.  Devi accertarti anche di aver aperto il collegamento di acquisizione prima di installare l'app. |

Considerazioni da ricordare:

* Gli hit che vengono inviati dall'app possono essere monitorati mediante gli strumenti di monitoraggio HTTP per verificare l'attribuzione di acquisizione.
* Per ulteriori informazioni sulle modalità di trasmissione di `INSTALL_REFERRER`, vedi [Testare la misurazione delle campagne Google Play](https://developers.google.com/analytics/solutions/testing-play-campaigns) nella guida per gli sviluppatori di Google .
* Puoi usare lo strumento Java `acquisitionTest.jar` fornito per ottenere l'ID univoco e il riferimento di installazione della trasmissione, per ottenere quindi le informazioni nei passaggi 3-10.

**Installare lo strumento Java**

Per installare lo strumento Java:

1. Download the [`acquistionTester.zip`](../assets/acquisitionTester.zip) file.
1. Estrai il file .jar.

   Puoi eseguire il file .jar sulla riga di comando.

Ad esempio:

```
java -jar acquisitionTester.jar -a com.adobe.test -r com.adobe.test.ReferrerReceiver -l "https://c00.adobe.com/v3/appid/start?a_i_id=123456&a_g_id=com.adobe.test&a_dd=i&ctxa.referrer.campaign.name=name&ctxa.referrer.campaign.trackingcode=1234
```

I collegamenti di marketing sono memorizzati nella cache sul lato server con una scadenza di dieci minuti. Quando apporti modifiche ai collegamenti di marketing, attendi 10 minuti prima di riutilizzarli, per accertarti che le modifiche siano state applicate.
