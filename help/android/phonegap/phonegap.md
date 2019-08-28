---
description: Questo plug-in consente di inviare chiamate Android AppMeasurement dal progetto PhoneGap.
keywords: android; libreria; mobile; sdk
seo-description: Questo plug-in consente di inviare chiamate Android AppMeasurement dal progetto PhoneGap.
seo-title: Panoramica del plug-in phonegap
solution: Marketing Cloud, Analytics
title: Panoramica del plug-in phonegap
topic: Sviluppatore e implementazione
uuid: c 5 c 32357-d 8 df -458 a-b 0 e 8-e 0 c 56040241 d
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Panoramica del plug-in phonegap {#phonegap-plug-in}

Questo plug-in consente di inviare chiamate Android AppMeasurement dal progetto PhoneGap. To create a PhoneGap project, see [PhoneGap](https://helpx.adobe.com/experience-manager/6-4/mobile/using/phonegap.html).

## Nuova versione di Adobe Experience Cloud SDK

Stai cercando informazioni e documentazione sull’SDK per dispositivi mobili di Adobe Experience Platform? Fai clic [qui](https://aep-sdks.gitbook.io/docs/) per la documentazione più recente.

>[!IMPORTANT]
>
>A settembre 2018 è stata rilasciata una nuova versione principale dell’SDK. Questi nuovi SDK per dispositivi mobili di Adobe Experience Platform sono configurabili tramite [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* Per iniziare, passa ad [Launch](https://launch.adobe.com/).
* Per visualizzare cosa è compreso negli archivi Experience Platform SDK, passa a [Github: SDK di Adobe Experience Platform](https://github.com/Adobe-Marketing-Cloud/acp-sdks).


## Installare il plug-in utilizzando npm {#section_43229E57C16944C0B51531CB92089189}

Esegui il comando seguente:

```java
cordova plugin add adobe-mobile-services
```

## Installare il plug-in manualmente {#section_EA1FD59C484D44878AB509954DEE6037}

## Includere il plug-in

1. Trascinate il `ADBMobile_PhoneGap.java` file nella `src` cartella.

   Per spostare questo file, fai clic su **[!UICONTROL OK]**.

1. Trascinare il `ADB_Helper.js` file nella cartella contenente il `index.html` file

   Per spostare questo file, fai clic su **[!UICONTROL OK]**.

1. In the `res/xml` folder, open the `config.xml` file and register an new plugin by adding the following:

   ```xml
   <feature name="ADBMobile_PhoneGap"> 
     <param name="android-package" value="[YOUR_PACKAGE_NAME].ADBMobile_PhoneGap" /> 
   </feature>
   ```

   Ad esempio, se il pacchetto si chiama `com.example.phonegaptest`, il valore `android-package` è il seguente:

   ```xml
   <param name="android-package" value="com.example.phonegaptest.ADBMobile_PhoneGap" />
   ```

## Includere la libreria appmeasurement

1. To download the AppMeasurement library, see [Get the SDK](/help/android/getting-started/dev-qs.md).
1. Trascinate il `adobeMobileLibrary.jar` file nella `src` cartella.

   Per spostare questo file, fai clic su **[!UICONTROL OK]**.

1. Right-click the `adobeMobileLibrary.jar file and select **[!UICONTROL Add as Library]**.
1. In base ai requisiti del progetto, inserisci nome, livello e posizione della libreria.
1. Drag the `ADBMobileConfig.json` file to your `assets` folder in the application root.
1. Accertati di aver selezionato l'applicazione radice e **non** un'applicazione in un'applicazione.

   Per spostare questo file, fai clic su **[!UICONTROL OK]**.

## Aggiungere autorizzazioni per l'app

La libreria AppMeasurement richiede le seguenti autorizzazioni per inviare dati e registrare le chiamate di tracciamento offline:

* `INTERNET`
* `ACCESS_NETWORK_STATE`

Per aggiungere queste autorizzazioni, aggiungi le seguenti righe al file `AndroidManifest.xml`, che si trova nella directory di progetto dell'applicazione:

```xml
<uses-permission android:name="android.permission.INTERNET" /> 
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

Per abilitare i messaggi in-app:

Aggiorna AndroidManifest.xml per dichiarare l'attività a schermo intero e abilita il gestore di notifica dei messaggi:

```java
<activity  
android:name="com.adobe.mobile.MessageFullScreenActivity"  
android:theme="@android:style/Theme.Translucent.NoTitleBar" /> 
<receiver android:name="com.adobe.mobile.MessageNotificationHandler" />
```

Se selezioni il layout modale quando crei un messaggio in Adobe Mobile Services, seleziona uno dei seguenti temi:

* `Theme.Translucent.NoTitleBar.Fullscreen`
* `Theme.Translucent.NoTitleBar`
* `Theme.Translucent`

Ad esempio:

```java
<activity 
android:name="com.adobe.mobile.MessageFullScreenActivity" 
android:theme="@android:style/Theme.Translucent.NoTitleBar.Fullscreen" 
android:windowSoftInputMode="adjustUnspecified|stateHidden" /> 
<receiver android:name="com.adobe.mobile.MessageNotificationHandler" />
```

## Implement custom tracking {#section_FD102B3CDAA4492FB04E56BF17E28663}

In `html` files, add the following to the `<head>` tag where you want to use tracking:

```
<script type="text/javascript" charset="utf-8" src="ADB_Helper.js"></script>
```

