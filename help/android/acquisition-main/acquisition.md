---
description: In Adobe Mobile Services è possibile generare collegamenti di acquisizione con codici di tracciamento univoci. Quando un utente scarica ed esegue un'app dall'app store dopo aver fatto clic sul collegamento generato, l'SDK raccoglie e invia automaticamente i dati di acquisizione ad Adobe Mobile Services.
keywords: android,libreria,mobile,sdk
solution: Experience Cloud Services,Analytics
title: Acquisizione da app mobile
topic-fix: Developer and implementation
uuid: 4d32eae9-e856-4e40-8a29-2b5bccd106e0
exl-id: 266f0266-38f5-410b-ae14-92874fb0e7ce
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '833'
ht-degree: 100%

---

# Acquisizione da app mobile {#mobile-app-acquisition}

In Adobe Mobile Services è possibile generare collegamenti di acquisizione con codici di tracciamento univoci. Quando un utente scarica ed esegue un&#39;app dall&#39;app store dopo aver fatto clic sul collegamento generato, l&#39;SDK raccoglie e invia automaticamente i dati di acquisizione ad Adobe Mobile Services.

## Nuova versione dell&#39;SDK per dispositivi mobili di Adobe Experience Platform

Hai bisogno di informazioni e documentazione relative all’SDK per dispositivi mobili di Adobe Experience Platform? Fai clic [qui](https://aep-sdks.gitbook.io/docs/) per la documentazione più recente.

A settembre 2018 è stata rilasciata una nuova versione principale dell&#39;SDK. Questi nuovi SDK per dispositivi mobili di Adobe Experience Platform sono configurabili tramite [Experience Platform Launch](https://www.adobe.com/it/experience-platform/launch.html).

* Per iniziare, vai su Adobe Experience Platform Launch.
* Per visualizzare cosa è compreso negli archivi Experience Platform SDK, passa a [Github: SDK di Adobe Experience Platform](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

>[!IMPORTANT]
>
>Per usare la funzione Acquisizione, **è necessario** disporre della versione SDK 4.1 o successiva.

I collegamenti di acquisizione devono essere creati in Adobe Mobile Services. Per ulteriori informazioni, vedi [Acquisizione](/help/using/acquisition-main/acquisition-main.md).

**Nelle versioni SDK 4.18.0 e successive**:

A partire dal 1 marzo 2020, Google ha dichiarerà obsoleto il meccanismo di intent broadcast install_referrer. Per ulteriori informazioni, consulta [Still Using InstallBroadcast? Passa all’API Play Referrer entro il 1 marzo 2020](https://android-developers.googleblog.com/2019/11/still-using-installbroadcast-switch-to.html). Per continuare a raccogliere le informazioni sul referente di installazione da Google Play Store, aggiorna l’applicazione per utilizzare la versione SDK 4.18.0 o successiva.

Con questa opzione, invece di creare un `BroadcastReceiver`, devi raccogliere l’URL del referente per l’installazione da una nuova API Google e passare l’URL risultante all’SDK.

1. Aggiungi il pacchetto Google Play Install Referrer alle dipendenze del file di gradle:

   `implementation 'com.android.installreferrer:installreferrer:1.1'`

1. Per recuperare l’URL del referente dall’API di riferimento di installazione, completa i passaggi descritti in [Ottenere il referente](https://developer.android.com/google/play/installreferrer/library#install-referrer) di installazione.

1. Passa l’URL del referente all’SDK:

   `Analytics.processGooglePlayInstallReferrerUrl(referrerUrl);`

>[!IMPORTANT]
>
>Per evitare chiamate alla API non necessarie nell’app, Google consiglia di richiamare l’API solo una volta immediatamente dopo l’installazione.

Per scegliere il modo migliore per utilizzare le API di riferimento di Google Play Install nell’app, consulta la documentazione di Google. Di seguito è riportato un esempio di come utilizzare l’SDK di Adobe con le API di riferimento per l’installazione di Google Play:

```java
void handleGooglePlayReferrer() {
    // Google recommends only calling this API the first time you need it:
    // https://developer.android.com/google/play/installreferrer/library#install-referrer

    // Store a boolean in SharedPreferences to ensure we only call it once.
    final SharedPreferences prefs = getSharedPreferences("acquisition", 0);
    if (prefs != null) {
        if (prefs.getBoolean("referrerHasBeenProcessed", false)) {
            return;
        }
    }

    final InstallReferrerClient referrerClient = InstallReferrerClient.newBuilder(getApplicationContext()).build();
    referrerClient.startConnection(new InstallReferrerStateListener() {
        private boolean complete = false;

        @Override
        public void onInstallReferrerSetupFinished(int responseCode) {
            switch (responseCode) {
                case InstallReferrerClient.InstallReferrerResponse.OK:
                    // connection is established
                    complete();
                    try {
                        final ReferrerDetails details = referrerClient.getInstallReferrer();                        

                        // pass the install referrer url to the SDK
                        Analytics.processGooglePlayInstallReferrerUrl(details.getInstallReferrer());

                    } catch (final RemoteException ex) {
                        Log.w("Acquisition - RemoteException while retrieving referrer information (%s)", ex.getLocalizedMessage() == null ? "unknown" : ex.getLocalizedMessage());
                    } finally {
                        referrerClient.endConnection();
                    }
                    break;
                case InstallReferrerClient.InstallReferrerResponse.FEATURE_NOT_SUPPORTED:
                case InstallReferrerClient.InstallReferrerResponse.SERVICE_UNAVAILABLE:
                default:
                    // API not available in the Play Store app - nothing to do here
                    complete();
                    referrerClient.endConnection();
                    break;
            }
        }

        @Override
        public void onInstallReferrerServiceDisconnected() {
            if (!complete) {
                // something went wrong trying to get a connection, try again
                referrerClient.startConnection(this);
            }
        }

        void complete() {
            complete = true;
            SharedPreferences.Editor editor = getSharedPreferences("acquisition", 0).edit();
            editor.putBoolean("referrerHasBeenProcessed", true);
            editor.apply();
        }
    });
}
```

**Nelle versioni SDK 4.13.1 e successive**:

Se non sei in grado di utilizzare i collegamenti di acquisizione creati in Adobe Mobile Services, i dati di acquisizione possono comunque essere raccolti e inviati dall&#39;SDK mediante Google Play Acquisition.

Per raccogliere dati di acquisizione da una campagna Google Play Acquisition standard:

* Usa il metodo di acquisizione standard di Google Play Store.

   I dati di acquisizione personalizzati possono essere utilizzati con le coppie chiave-valore standard di Google Play Acquisition.

* Quando l&#39;utente scarica ed esegue un&#39;app in seguito all&#39;acquisizione da Google Play Store, i dati del riferimento saranno raccolti e inviati ad Adobe Mobile Services.

   * I dati sono memorizzati e disponibili nell&#39;istanza `AdobeDataCallback` registrata in precedenza con l&#39;SDK.

      Per ulteriori informazioni, consulta [Metodi di configurazione](/help/android/configuration/methods.md).

   * Viene utilizzato il `MobileDataEvent.MOBILE_EVENT_ACQUISITION_INSTALL` o il tipo di evento `MobileDataEvent.MOBILE_EVENT_ACQUISITION_LAUNCH`.

   * Le chiavi personalizzate che facevano parte dei dati di acquisizione di Google Play avranno nomi separati con spazi con &quot; `a.acquisition.custom.`&quot;

Se usi i collegamenti di acquisizione creati su Adobe Mobile Services, aggiungi dati personalizzati al collegamento di acquisizione completando le seguenti attività:

1. Aggiungi il prefisso &quot;`adb`&quot; a una variabile di acquisizione.

   Quando l’SDK riceve i dati di acquisizione da Adobe Mobile Services al primo avvio, i dati vengono memorizzati e sono disponibili nell’`AdobeDataCallback`istanza registrata in precedenza con l’SDK. Per ulteriori informazioni, consulta [Metodi di configurazione](/help/android/configuration/methods.md).

1. Sarà utilizzato il `MobileDataEvent.MOBILE_EVENT_ACQUISITION_INSTALL` o il tipo di evento `MobileDataEvent.MOBILE_EVENT_ACQUISITION_LAUNCH`.

1. Le chiavi di dati personalizzate hanno il prefisso &quot;`a.acquisition.custom.`&quot;

>[!TIP]
>
>Se invii dati a suite di rapporti multiple, usa i dati di acquisizione dell&#39;app associata alla prima suite di rapporti nell&#39;elenco degli ID della suite di rapporti.

Gli aggiornamenti in questa sezione consentono all&#39;SDK di inviare dati di acquisizione da un collegamento di acquisizione.

## Tracciamento acquisizione mobile {#section_CEA30C652AC8470784B8054E299B80FA}

1. Aggiungi la libreria al tuo progetto e implementa le funzioni di ciclo di vita (lifecycle).

   Per ulteriori informazioni, consulta *Aggiungere l’SDK e il file di configurazione al progetto IntelliJ IDEA o Eclipse* in [Implementazione e ciclo di vita di base](/help/android/getting-started/dev-qs.md).

1. Importa la libreria:

   ```java
   import com.adobe.mobile.*;
   ```

1. Implementa il `BroadcastReceiver` per il referente:

   ```java
   package com.your.package.name;  // replace with your app package name
   
   import android.content.BroadcastReceiver;
   import android.content.Context;
   import android.content.Intent;
   
   public class GPBroadcastReceiver extends BroadcastReceiver {
     @Override
     public void onReceive(Context c, Intent i) {
      com.adobe.mobile.Analytics.processReferrer(c, i);
     }
   }
   ```

1. Aggiorna `AndroidManifest.xml` per abilitare il `BroadcastReceiver` creato nel passaggio precedente:

   ```xml
   <receiver android:name="com.your.package.name.GPBroadcastReceiver" android:exported="true">
    <intent-filter>
     <action android:name="com.android.vending.INSTALL_REFERRER" />
    </intent-filter>
   </receiver>
   ```

1. Verifica che il file `ADBMobileConfig.json` contenga le impostazioni di acquisizione necessarie:

   ```xml
   "acquisition": {
      "server": "c00.adobe.com",
      "appid": "0652024f-adcd-49f9-9bd7-2552a4565d2f"
   },
   "analytics": {
     "referrerTimeout": 5,
     ...
   ```

   >[!IMPORTANT]
   >
   >se invii dati a suite di rapporti multiple, usa le impostazioni di acquisizione (server di acquisizione e appid) dell&#39;app associata alla prima suite di rapporti nell&#39;elenco degli ID di suite di rapporti.

   Le impostazioni `acquisition` sono generate da Adobe Mobile Services e non devono essere modificate. Per ulteriori informazioni sul download di un file `ADBMobileConfig.json` personalizzato con le impostazioni `acquisition` pre-configurate, vedi [Prima di iniziare](/help/android/getting-started/requirements.md).

Dopo aver abilitato queste impostazioni, dopo il primo avvio dell&#39;app, i dati di acquisizione vengono inviati automaticamente con la chiamata del ciclo di vita iniziale.

>[!CAUTION]
>
>`referrerTimeout` deve essere impostato su un valore maggiore di 0 per abilitare l&#39;acquisizione da parte dell&#39;app.
