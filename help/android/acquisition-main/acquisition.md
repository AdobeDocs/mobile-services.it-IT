---
description: In Adobe Mobile Services è possibile generare collegamenti di acquisizione con codici di tracciamento univoci. Quando un utente scarica ed esegue un'app dall'App Store dopo aver fatto clic sul collegamento generato, l'SDK raccoglie e invia automaticamente i dati di acquisizione ad Adobe Mobile Services.
keywords: android; libreria; mobile; sdk
seo-description: In Adobe Mobile Services è possibile generare collegamenti di acquisizione con codici di tracciamento univoci. Quando un utente scarica ed esegue un'app dall'App Store dopo aver fatto clic sul collegamento generato, l'SDK raccoglie e invia automaticamente i dati di acquisizione ad Adobe Mobile Services.
seo-title: Acquisizione da app mobile
solution: Marketing Cloud, Analytics
title: Acquisizione da app mobile
topic: Sviluppatore e implementazione
uuid: 4 d 32 eae 9-e 856-4 e 40-8 a 29-2 b 5 bfiel__ent_numeric e 0
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Mobile app acquisition {#mobile-app-acquisition}

In Adobe Mobile Services è possibile generare collegamenti di acquisizione con codici di tracciamento univoci. Quando un utente scarica ed esegue un'app dall'App Store dopo aver fatto clic sul collegamento generato, l'SDK raccoglie e invia automaticamente i dati di acquisizione ad Adobe Mobile Services.

## Nuova versione di Adobe Experience Cloud SDK

Stai cercando informazioni e documentazione sull’SDK per dispositivi mobili di Adobe Experience Platform? Fai clic [qui](https://aep-sdks.gitbook.io/docs/) per la documentazione più recente.

A settembre 2018 è stata rilasciata una nuova versione principale dell’SDK. Questi nuovi SDK per dispositivi mobili di Adobe Experience Platform sono configurabili tramite [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* Per iniziare, passa ad [Launch](https://launch.adobe.com/).
* Per visualizzare cosa è compreso negli archivi Experience Platform SDK, passa a [Github: SDK di Adobe Experience Platform](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

>[!IMPORTANT]
>
> If you are using the Adobe Experience Platform Mobile SDKs with Adobe Launch, you **must** also install the Adobe Analytics Mobile Services extension to use Adobe Mobile Services features such as Acquisition links. Per ulteriori informazioni, consulta [Adobe Analytics - Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services). For more information about using Acquisition and Marketing Links with the Experience Cloud SDKs, see [Acquisition and Marketing Links](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services#acquisition-and-marketing-links).

>[!IMPORTANT]
>
>Per usare Acquisition, **devi** disporre della versione SDK 4.1 o successiva.

I collegamenti di acquisizione devono essere creati in Adobe Mobile Services. For more information, see [Acquisition](/help/using/acquisition-main/acquisition-main.md).

**Nelle versioni SDK 4.13.1 e successive**:

Se non sei in grado di utilizzare i collegamenti di acquisizione creati in Adobe Mobile Services, i dati di acquisizione possono comunque essere raccolti e inviati dall'SDK mediante Google Play Acquisition.

Per raccogliere dati di acquisizione da una campagna Google Play Acquisition standard:

* Usa il metodo di acquisizione standard di Google Play Store.

   I dati di acquisizione personalizzati possono essere utilizzati con le coppie chiave-valore standard di Google Play Acquisition.

* Quando l'utente scarica ed esegue un'app in seguito all'acquisizione da Google Play Store, i dati del riferimento saranno raccolti e inviati ad Adobe Mobile Services.

   * The data is stored and available in the `AdobeDataCallback` instance that was registered earlier with the SDK.

      Per ulteriori informazioni, consulta [Metodi di configurazione](/help/android/configuration/methods.md).

   * Il tipo `MobileDataEvent.MOBILE_EVENT_ACQUISITION_INSTALL` o il tipo `MobileDataEvent.MOBILE_EVENT_ACQUISITION_LAUNCH` di evento viene utilizzato.

   * Le chiavi personalizzate che facevano parte dei dati di acquisizione di Google Play avranno nomi separati con spazi con " `a.acquisition.custom.`"

Se usi i collegamenti di acquisizione creati su Adobe Mobile Services, aggiungi dati personalizzati al collegamento di acquisizione completando le seguenti attività:

1. Aggiungi il prefisso "`adb`" a una variabile di acquisizione.

   When the SDK receives the acquisition data from Adobe Mobile Services (on first launch), that data will be stored and also available in the `AdobeDataCallback` instance registered earlier with the SDK, as mentioned in [Configuration Methods](/help/android/configuration/methods.md).

1. Viene utilizzato il `MobileDataEvent.MOBILE_EVENT_ACQUISITION_INSTALL` tipo di `MobileDataEvent.MOBILE_EVENT_ACQUISITION_LAUNCH` evento.

1. Le chiavi dati personalizzate hanno il prefisso "`a.acquisition.custom.`

>[!TIP]
>
>Se invii dati a più suite di rapporti, usa i dati di acquisizione dell'app associata alla prima suite di rapporti nell'elenco degli ID delle suite di rapporti.

Gli aggiornamenti in questa sezione consentono all'SDK di inviare dati di acquisizione da un collegamento di acquisizione.

## Tracking mobile acquisition {#section_CEA30C652AC8470784B8054E299B80FA}

1. Aggiungi la libreria [nel progetto e implementa il ciclo di vita.

   Per ulteriori informazioni, vedi *Aggiungere l'SDK e il file di configurazione al progetto intellij IDEA o Eclipse* nell'implementazione [e nel ciclo di vita principali](/help/android/getting-started/dev-qs.md).

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

1. Verify that the `ADBMobileConfig.json` file contains the required acquisition settings:

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
   >Se invii dati a più suite di rapporti, usa le impostazioni di acquisizione (server di acquisizione e appid) dall'app associata alla prima suite di rapporti nell'elenco degli ID suite di rapporti.

   `acquisition` Le impostazioni sono generate da Adobe Mobile Services e non devono essere modificate. For more information about how to download a customized `ADBMobileConfig.json` file with the `acquisition` settings pre-configured, see [Before You Start](/help/android/getting-started/requirements.md).

Dopo aver abilitato queste impostazioni, dopo il primo avvio dell'app, i dati di acquisizione vengono inviati automaticamente con la chiamata del ciclo di vita iniziale.

>[!CAUTION]
>
>`referrerTimeout` devono essere impostati su un valore maggiore di 0 per abilitare l'acquisizione da app.
