---
description: In Adobe Mobile Services è possibile generare collegamenti di acquisizione con codici di tracciamento univoci. Quando un utente scarica ed esegue un'app dall'app store dopo aver fatto clic sul collegamento generato, l'SDK raccoglie e invia automaticamente i dati di acquisizione ad Adobe Mobile Services.
keywords: android,libreria,mobile,sdk
seo-description: In Adobe Mobile Services è possibile generare collegamenti di acquisizione con codici di tracciamento univoci. Quando un utente scarica ed esegue un'app dall'app store dopo aver fatto clic sul collegamento generato, l'SDK raccoglie e invia automaticamente i dati di acquisizione ad Adobe Mobile Services.
seo-title: Acquisizione da app mobile
solution: Experience Cloud,Analytics
title: Acquisizione da app mobile
topic: Sviluppatore e implementazione
uuid: 4d32eae9-e856-4e40-8a29-2b5bccd106e0
translation-type: ht
source-git-commit: b690ec677cf5aedfb2673b707f82716af1851124

---


# Acquisizione da app mobile {#mobile-app-acquisition}

In Adobe Mobile Services è possibile generare collegamenti di acquisizione con codici di tracciamento univoci. Quando un utente scarica ed esegue un'app dall'app store dopo aver fatto clic sul collegamento generato, l'SDK raccoglie e invia automaticamente i dati di acquisizione ad Adobe Mobile Services.

## Nuova versione dell'SDK per dispositivi mobili di Adobe Experience Platform

Stai cercando informazioni e documentazione sull’SDK per dispositivi mobili di Adobe Experience Platform? Fai clic [qui](https://aep-sdks.gitbook.io/docs/) per la documentazione più recente.

A settembre 2018 è stata rilasciata una nuova versione principale dell'SDK. Questi nuovi SDK per dispositivi mobili di Adobe Experience Platform sono configurabili tramite [Experience Platform Launch](https://www.adobe.com/it/experience-platform/launch.html).

* Per iniziare, vai su Adobe Experience Platform Launch.
* Per visualizzare cosa è compreso negli archivi Experience Platform SDK, passa a [Github: SDK di Adobe Experience Platform](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

>[!IMPORTANT]
>
>Per usare Acquisition, **devi** disporre della versione SDK 4.1 o successiva.

I collegamenti di acquisizione devono essere creati in Adobe Mobile Services. Per ulteriori informazioni, vedi [Acquisizione](/help/using/acquisition-main/acquisition-main.md).

**Nelle versioni SDK 4.13.1 e successive**:

Se non sei in grado di utilizzare i collegamenti di acquisizione creati in Adobe Mobile Services, i dati di acquisizione possono comunque essere raccolti e inviati dall'SDK mediante Google Play Acquisition.

Per raccogliere dati di acquisizione da una campagna Google Play Acquisition standard:

* Usa il metodo di acquisizione standard di Google Play Store.

   I dati di acquisizione personalizzati possono essere utilizzati con le coppie chiave-valore standard di Google Play Acquisition.

* Quando l'utente scarica ed esegue un'app in seguito all'acquisizione da Google Play Store, i dati del riferimento saranno raccolti e inviati ad Adobe Mobile Services.

   * I dati sono memorizzati e disponibili nell'istanza `AdobeDataCallback` registrata in precedenza con l'SDK.

      Per ulteriori informazioni, consulta [Metodi di configurazione](/help/android/configuration/methods.md).

   * Viene utilizzato il `MobileDataEvent.MOBILE_EVENT_ACQUISITION_INSTALL` o il tipo di evento `MobileDataEvent.MOBILE_EVENT_ACQUISITION_LAUNCH`.

   * Le chiavi personalizzate che facevano parte dei dati di acquisizione di Google Play avranno nomi separati con spazi con " `a.acquisition.custom.`"

Se usi i collegamenti di acquisizione creati su Adobe Mobile Services, aggiungi dati personalizzati al collegamento di acquisizione completando le seguenti attività:

1. Aggiungi il prefisso "`adb`" a una variabile di acquisizione.

   Quando l'SDK riceve i dati di acquisizione da Adobe Mobile Services (al primo avvio), questi saranno memorizzati e disponibili nell'istanza `AdobeDataCallback` registrata in precedenza con l'SDK, come indicato in [Metodi di configurazione](/help/android/configuration/methods.md).

1. Sarà utilizzato il `MobileDataEvent.MOBILE_EVENT_ACQUISITION_INSTALL` o il tipo di evento `MobileDataEvent.MOBILE_EVENT_ACQUISITION_LAUNCH`.

1. Le chiavi di dati personalizzate hanno il prefisso "`a.acquisition.custom.`"

>[!TIP]
>
>Se invii dati a suite di rapporti multiple, usa i dati di acquisizione dell'app associata alla prima suite di rapporti nell'elenco degli ID della suite di rapporti.

Gli aggiornamenti in questa sezione consentono all'SDK di inviare dati di acquisizione da un collegamento di acquisizione.

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
   >se invii dati a suite di rapporti multiple, usa le impostazioni di acquisizione (server di acquisizione e appid) dell'app associata alla prima suite di rapporti nell'elenco degli ID di suite di rapporti.

   Le impostazioni `acquisition` sono generate da Adobe Mobile Services e non devono essere modificate. Per ulteriori informazioni sul download di un file `ADBMobileConfig.json` personalizzato con le impostazioni `acquisition` pre-configurate, vedi [Prima di iniziare](/help/android/getting-started/requirements.md).

Dopo aver abilitato queste impostazioni, dopo il primo avvio dell'app, i dati di acquisizione vengono inviati automaticamente con la chiamata del ciclo di vita iniziale.

>[!CAUTION]
>
>`referrerTimeout` deve essere impostato su un valore maggiore di 0 per abilitare l'acquisizione da parte dell'app.
