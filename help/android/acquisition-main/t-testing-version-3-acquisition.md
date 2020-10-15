---
description: Queste informazioni consentono di esplorare un collegamento di campagna di acquisizione versione 3 su un dispositivo Android.
keywords: android;library;mobile;sdk
seo-description: Queste informazioni consentono di esplorare un collegamento di campagna di acquisizione versione 3 su un dispositivo Android.
seo-title: Verifica dell’acquisizione dalla versione 3
solution: Experience Cloud,Analytics
title: Verifica dell’acquisizione dalla versione 3
topic: Developer and implementation
uuid: 5e38b43d-389e-4412-99e5-3e6223b6ad28
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '820'
ht-degree: 100%

---


# Verifica dell’acquisizione V3 {#testing-version-acquisition}

Queste informazioni consentono di esplorare un collegamento di campagna di acquisizione versione 3 su un dispositivo Android.

>[!IMPORTANT]
>
>Acquisizione in V3 si riferisce ai collegamenti di acquisizione creati con Builder nell&#39;interfaccia utente di Adobe Mobile Services. Per utilizzare questa funzione, devi passare a SDK 4.x per Android per le soluzioni Experience Cloud 4.6.0 o versione successiva.

Se l’app per dispositivi mobili non è ancora disponibile in Google Play, seleziona una qualsiasi app mobile da usare come destinazione al momento di creare il collegamento della campagna. Questo incide solo sull&#39;app alla quale il server di acquisizione ti reindirizzerà quando fai clic sul collegamento di acquisizione, e non sulla capacità di verificare il funzionamento del collegamento. I parametri della stringa di query vengono passati a Google Play Store, e quindi passati all’app al momento dell’installazione come parte di una trasmissione della campagna. Il test del ciclo completo di acquisizione da app mobile richiede la simulazione di questo tipo di trasmissione.

>[!IMPORTANT]
>
>Se stai implementando tramite le API di riferimento per l’installazione di Google Play, non potrai testare l’acquisizione prima che l’app sia nello store di Google Play.

L’app deve essere stata appena installata oppure i dati devono essere eliminati nelle **[!UICONTROL Impostazioni]** tutte le volte che si esegue un test. In questo modo le metriche del ciclo di vita iniziali associate ai parametri di stringa della query della campagna vengono inviate al primo avvio dell&#39;app.

1. Completa le attività preliminari descritte nella sezione [Acquisizione da app mobile](/help/android/acquisition-main/acquisition.md) e assicurati di aver implementato correttamente il destinatario della trasmissione per `INSTALL_REFERRER`.

1. Nell’interfaccia utente di Adobe Mobile Services, fai clic su **[!UICONTROL Acquisizione]** > **[!UICONTROL Marketing Links Builder]** e genera l’URL di un collegamento marketing di acquisizione che imposti Google Play come destinazione per i dispositivi Android.

   Per ulteriori informazioni, consulta [Marketing Links Builder](/help/using/acquisition-main/c-marketing-links-builder/c-marketing-links-builder.md).

   Ad esempio, `https://c00.adobe.com/v3/<appid>/start?a_i_id=iostestapp&a_g_id=com.adobe.android&a_dd=g&ctxa.referrer.campaign.name=name&ctxa.referrer.campaign.trackingcode=trackingcode`.

   >[!TIP]
   >
   >Se nel collegamento di acquisizione fai riferimento sia ad app Android che iOS, usa Google Play come store predefinito.

1. Apri il collegamento generato in un browser desktop.

   Dovresti essere reindirizzato a una pagina con un URL simile al seguente esempio:
   `https://play.google.com/store/apps/details?id=com.adobe.android&referrer=utm_campaign%3Dadb_acq_v3%26utm_source%3Dadb_acq_v3%26utm_content%3D91b52ce097b1464b9b47cb2995c493cc6ab2c3a3`

1. Copia l&#39;ID univoco dopo `utm_content%3D`.

   Nell’esempio precedente, l’ID è `91b52ce097b1464b9b47cb2995c493cc6ab2c3a3`.

1. Crea il collegamento di acquisizione finale usando l&#39;ID univoco del passaggio 3, nel seguente formato:

   `https://c00.adobe.com/v3/<appid>/end?a_ugid=<unique id>`.

   Ad esempio, `https://c00.adobe.com/v3/<appid>/end?a_ugid=91b52ce097b1464b9b47cb2995c493cc6ab2c3a3`.

1. Apri il collegamento in un browser desktop.

   Dovresti vedere `contextData` nella risposta JSON:

   `{"fingerprint":"228d7e6058b1d731dc7a8b8bd0c15e1d78242f31","timestamp":1457989293,"appguid":"","contextData":{"a.referrer.campaign.name":"name","a.referrer.campaign.trackingcode":"trackingcode"}}.`

   Se non vedi `contextData` oppure se manca parte della stringa, accertati che l&#39;URL di acquisizione segua il formato indicato in [Creazione manuale del collegamento di acquisizione](/help/using/acquisition-main/c-marketing-links-builder/acquisition-link-manual.md).
1. Per ottenere un nuovo ID univoco, ripeti il passaggio 3.
1. Verifica che le seguenti impostazioni nel file di configurazione siano corrette:

   | Impostazione | Valore |
   |--- |--- |
   | acquisizione | Il server dovrebbe essere `c00.adobe.com` e *`appid`* dovrebbe corrispondere a `appid` nel collegamento di acquisizione. |
   | analytics | A scopo di test, imposta il timeout del referente in modo da concedere un tempo sufficiente (almeno 60 secondi) per inviare manualmente la trasmissione. Dopo il test potrai ripristinare l’impostazione di timeout originale. |

1. Connetti il dispositivo a un computer e disinstalla e reinstalla l&#39;app.
1. Avvia ADB Shell, quindi avvia l&#39;applicazione sul dispositivo.
1. Invia una trasmissione usando il seguente comando `adb`:

   `am broadcast -a com.android.vending.INSTALL_REFERRER -n com.adobe.android/com.adobe.android.YourBroadcastReceiver --es "referrer" "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<unique id get on step 5>"`

1. Completa i seguenti passaggi:
   1. Sostituisci `com.adobe.android` con il nome del pacchetto dell&#39;applicazione.
   1. Aggiorna il riferimento del ricevitore con quello della posizione del ricevitore di tracciamento della campagna nella tua app.
   1. Sostituisci i valori associati con `utm_content`.

   Se la trasmissione è riuscita, la risposta sarà simile a quella nel seguente esempio:

   `Broadcasting: Intent
{ act=com.android.vending.INSTALL_REFERRER cmp=com.adobe.adms.tests/.ReferralReceiver (has extras) }
Broadcast completed: result=0`

1. (Facoltativo) Per ottenere informazioni aggiuntive, puoi abilitare la registrazione di debug dell&#39;SDK.

   Se tutto funziona correttamente, nel registro dovresti trovare le seguenti voci:

`"Analytics - Received referrer information(<referrer content>)"   "Analytics - Trying to fetch referrer data from (acquisition end url)"; "Analytics - Received Referrer Data(<A JSON Response>)"`

In caso contrario, assicurati di aver completato i passaggi da 6 a 12.

La tabella seguente contiene informazioni aggiuntive sui possibili errori:

| Errore | Descrizione |
|--- |--- |
| Analytics - Unable to decode response(*String*). | La risposta è formata in modo errato. |
| Analytics - Unable to parse response (*a JSON Response*). | La stringa JSON è formata in modo errato. |
| Analytics - Unable to parse acquisition service response (no contextData parameter in response). | La risposta non contiene il parametro contextData. |
| Analytics - Acquisition referrer data was not complete (no `a.referrer.campaign.name` in context data), ignoring. | `a.referrer.campaign.name`  non è incluso in contextData. |
| Analytics - Acquisition referrer timed out. | Impossibile ottenere la risposta nell&#39;intervallo temporale definito in `referrerTimeout`. Aumenta questo valore e riprova.  Assicurati anche di aver aperto il collegamento di acquisizione prima di installare l’app. |

Considerazioni da ricordare:

* Gli hit inviati dall’app possono essere monitorati mediante strumenti di monitoraggio HTTP per verificare l’attribuzione di acquisizione.
* Per ulteriori informazioni sulle modalità di trasmissione di `INSTALL_REFERRER`, consulta [Testare la misurazione delle campagne Google Play](https://developers.google.com/analytics/solutions/testing-play-campaigns) nella guida per gli sviluppatori di Google.

* È stata rilasciata una correzione di bug per l’acquisizione su Android 4.8.2.

   Prima di eseguire il test, aggiorna l’SDK alla versione più recente.

* Puoi usare lo strumento Java `acquisitionTest.jar` fornito per ottenere l&#39;ID univoco e il riferimento di installazione della trasmissione, per ottenere quindi le informazioni nei passaggi 3-12.

   **Installare lo strumento Java**

Per installare lo strumento Java:

1. Scarica il file [`acquisitionTester.zip`](/help/android/assets/acquisitionTester.zip).

1. Estrai il file .jar.

   Puoi eseguire il file dalla riga di comando.

   Ad esempio:

   ```java
   java -jar acquisitionTester.jar -a com.adobe.test -r com.adobe.test.ReferrerReceiver -l "https://c00.adobe.com/v3/appid/start?a_i_id=123456&a_g_id=com.adobe.test&a_dd=i&ctxa.referrer.campaign.name=name&ctxa.referrer.campaign.trackingcode=1234
   ```
