---
description: Queste informazioni consentono di esplorare un collegamento di campagna di acquisizione versione 3 su un dispositivo Android.
keywords: android;libreria;mobile;sdk
seo-description: Queste informazioni consentono di esplorare un collegamento di campagna di acquisizione versione 3 su un dispositivo Android.
seo-title: Verifica dell'acquisizione dalla versione 3
solution: Marketing Cloud,Analytics
title: Verifica dell'acquisizione dalla versione 3
topic: Sviluppatore e implementazione
uuid: 5e38b43d-389e-4412-99e5-3e6223b6ad28
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Testing V3 acquisition {#testing-version-acquisition}

Queste informazioni consentono di esplorare un collegamento di campagna di acquisizione versione 3 su un dispositivo Android.

>[!IMPORTANT]
>
>Per "acquisizione in V3" si intendono i collegamenti di acquisizione creati con Acquisition Builder nell’interfaccia utente di Adobe Mobile Services. Per utilizzare questa funzionalità, devi eseguire l'aggiornamento alla versione 4.x dell'SDK per Android per soluzioni Experience Cloud 4.6.0 o versioni successive.

Se l'app mobile non è ancora disponibile in Google Play, quando crei il collegamento della campagna puoi selezionare come destinazione qualsiasi app mobile. Questo incide solo sull'app alla quale il server di acquisizione ti reindirizzerà quando fai clic sul collegamento di acquisizione, e non sulla capacità di verificare il funzionamento del collegamento. I parametri della stringa di query vengono passati a Google Play Store e quindi all'app al momento dell'installazione, nell'ambito della trasmissione della campagna. Il test dell'acquisizione da app mobile richiede la simulazione di questo tipo di trasmissione.

The app must be freshly installed, or have data cleared in **[!UICONTROL Settings]**, each time a test is run. In questo modo le metriche del ciclo di vita iniziali associate ai parametri di stringa della query della campagna vengono inviate al primo avvio dell'app.

1. Complete the prerequisite tasks in [Mobile App Acquisition](/help/android/acquisition-main/acquisition.md) and ensure that you have correctly implemented the broadcast receiver for `INSTALL_REFERRER`.
1. In the Adobe Mobile Services UI, click  **[!UICONTROL Acquisition]** &gt; **[!UICONTROL Marketing Links Builder]** and generate an Acquisition Marketing Link URL that sets Google Play as the destination for Android devices.

   Per ulteriori informazioni, consulta [Marketing Links Builder](/help/using/acquisition-main/c-marketing-links-builder/c-marketing-links-builder.md).

   Ad esempio, `https://c00.adobe.com/v3/<appid>/start?a_i_id=iostestapp&a_g_id=com.adobe.android&a_dd=g&ctxa.referrer.campaign.name=name&ctxa.referrer.campaign.trackingcode=trackingcode`.

   >[!TIP]
   >
   >Se nel collegamento di acquisizione fate riferimento sia alle app Android che iOS, utilizzate Google Play come store predefinito.

1. Apri il collegamento generato in un browser desktop.

   Dovresti essere reindirizzato a una pagina con un URL simile al seguente esempio:
   `https://play.google.com/store/apps/details?id=com.adobe.android&referrer=utm_campaign%3Dadb_acq_v3%26utm_source%3Dadb_acq_v3%26utm_content%3D91b52ce097b1464b9b47cb2995c493cc6ab2c3a3`

1. Copy the unique ID after `utm_content%3D`.

   In the previous example, the ID is .`91b52ce097b1464b9b47cb2995c493cc6ab2c3a3`

1. Crea il collegamento di acquisizione finale usando l'ID univoco del passaggio 3, nel seguente formato:

   `https://c00.adobe.com/v3/<appid>/end?a_ugid=<unique id>`.

   Ad esempio, `https://c00.adobe.com/v3/<appid>/end?a_ugid=91b52ce097b1464b9b47cb2995c493cc6ab2c3a3`.

1. Apri il collegamento in un browser desktop.

   Dovresti vedere `contextData` nella risposta JSON:

   `{"fingerprint":"228d7e6058b1d731dc7a8b8bd0c15e1d78242f31","timestamp":1457989293,"appguid":"","contextData":{"a.referrer.campaign.name":"name","a.referrer.campaign.trackingcode":"trackingcode"}}.`

   Se non vedi `contextData` oppure se manca parte della stringa, accertati che l'URL di acquisizione segua il formato indicato in [Creazione manuale del collegamento di acquisizione](/help/using/acquisition-main/c-marketing-links-builder/acquisition-link-manual.md).
1. Per ottenere un nuovo ID univoco, ripeti il passaggio 3.
1. Verifica che le seguenti impostazioni nel file di configurazione siano corrette:

   | Impostazione | Valore |
   |--- |--- |
   | acquisizione | The server should be `c00.adobe.com`.   *`appid`*  should equal the `appid`  in your acquisition link. |
   | analytics | A fini di test, imposta il timeout di riferimento in modo tale da fornire il tempo necessario (almeno 60 secondi) per inviare manualmente la trasmissione. Puoi ripristinare l'impostazione di timeout originale dopo il test. |

1. Connetti il dispositivo a un computer e disinstalla e reinstalla l'app.
1. Avvia ADB Shell, quindi avvia l'applicazione sul dispositivo.
1. Invia una trasmissione usando il seguente comando `adb`: 

   `am broadcast -a com.android.vending.INSTALL_REFERRER -n com.adobe.android/com.adobe.android.YourBroadcastReceiver --es "referrer" "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<unique id get on step 5>"`

1. Completa i seguenti passaggi:
   1. Sostituisci `com.adobe.android` con il nome del pacchetto dell'applicazione.
   1.  Aggiorna il riferimento del ricevitore con quello della posizione del ricevitore di tracciamento della campagna nella tua app. 
   1. Replace values that are associated with `utm_content`.
   Se la trasmissione è riuscita, la risposta sarà simile a quella nel seguente esempio:

   `Broadcasting: Intent 
{ act=com.android.vending.INSTALL_REFERRER cmp=com.adobe.adms.tests/.ReferralReceiver (has extras) } 
Broadcast completed: result=0`

1. (Facoltativo) Per ottenere informazioni aggiuntive, puoi abilitare la registrazione di debug dell'SDK.

   Se tutto funziona correttamente, nel registro dovresti trovare le seguenti voci:

`"Analytics - Received referrer information(<referrer content>)"   "Analytics - Trying to fetch referrer data from (acquisition end url)"; "Analytics - Received Referrer Data(<A JSON Response>)"`

In caso contrario, assicurati di aver completato i passaggi da 6 a 12.

La seguente tabella contiene informazioni aggiuntive sui possibili errori:

| Errore | Descrizione |
|--- |--- |
| Analytics - Unable to decode response(*String*). | La risposta è formata in modo errato. |
| Analytics - Unable to parse response (*a JSON Response*). | La stringa JSON è formata in modo errato. |
| Analytics - Unable to parse acquisition service response (no contextData parameter in response). | La risposta non contiene il parametro contextData. |
| Analytics - Acquisition referrer data was not complete (no `a.referrer.campaign.name` in context data), ignoring. | `a.referrer.campaign.name`  non è incluso in contextData. |
| Analytics - Acquisition referrer timed out. | Impossibile ottenere la risposta nell'intervallo temporale definito in `referrerTimeout`. Aumenta questo valore e riprova.  Devi accertarti anche di aver aperto il collegamento di acquisizione prima di installare l'app. |

Considerazioni da ricordare:

* Gli hit inviati dall'app possono essere monitorati mediante gli strumenti di monitoraggio HTTP per verificare l'attribuzione di acquisizione.
* Per ulteriori informazioni sulle modalità di trasmissione di `INSTALL_REFERRER`, vedi [Testare la misurazione delle campagne Google Play](https://developers.google.com/analytics/solutions/testing-play-campaigns) nella guida per gli sviluppatori di Google.

* In Android 4.8.2 è stata rilasciata una correzione di bug per l'acquisizione.

   Prima di eseguire il test, aggiorna l'SDK alla versione più recente.

* Puoi usare lo strumento Java `acquisitionTest.jar` fornito per ottenere l'ID univoco e il riferimento di installazione della trasmissione, per ottenere quindi le informazioni nei passaggi 3-12.

   **Installare lo strumento Java**

Per installare lo strumento Java:

1. Download the [`acquisitionTester.zip`](/help/android/assets/acquisitionTester.zip) file.

1. Estrai il file .jar.

   Puoi eseguire il file sulla riga di comando.

   Ad esempio:

   ```java
   java -jar acquisitionTester.jar -a com.adobe.test -r com.adobe.test.ReferrerReceiver -l "https://c00.adobe.com/v3/appid/start?a_i_id=123456&a_g_id=com.adobe.test&a_dd=i&ctxa.referrer.campaign.name=name&ctxa.referrer.campaign.trackingcode=1234
   ```
