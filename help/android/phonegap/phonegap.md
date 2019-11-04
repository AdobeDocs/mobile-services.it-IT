---
description: Questo plug-in consente di inviare chiamate Android AppMeasurement dal progetto PhoneGap.
keywords: android,libreria,mobile,sdk
seo-description: Questo plug-in consente di inviare chiamate Android AppMeasurement dal progetto PhoneGap.
seo-title: Panoramica del plug-in PhoneGap
solution: Experience Cloud,Analytics
title: Panoramica del plug-in PhoneGap
topic: Sviluppatore e implementazione
uuid: c5c32357-d8df-458a-b0e8-e0c56040241d
translation-type: ht
source-git-commit: 1c387b063eedb41a52e044dc824df6a51f173ad2

---


# Panoramica del plug-in PhoneGap {#phonegap-plug-in}

Questo plug-in consente di inviare chiamate Android AppMeasurement dal progetto PhoneGap. Per creare un progetto PhoneGap, consulta [PhoneGap](https://helpx.adobe.com/it/experience-manager/6-4/mobile/using/phonegap.html).

## Nuova versione dell'SDK per dispositivi mobili di Adobe Experience Platform

Stai cercando informazioni e documentazione sull’SDK per dispositivi mobili di Adobe Experience Platform? Fai clic [qui](https://aep-sdks.gitbook.io/docs/) per la documentazione più recente.

A settembre 2018 è stata rilasciata una nuova versione principale dell'SDK. Questi nuovi SDK per dispositivi mobili di Adobe Experience Platform sono configurabili tramite [Experience Platform Launch](https://www.adobe.com/it/experience-platform/launch.html).

* Per iniziare, vai su Adobe Experience Platform Launch.
* Per visualizzare cosa è compreso negli archivi Experience Platform SDK, passa a [Github: SDK di Adobe Experience Platform](https://github.com/Adobe-Marketing-Cloud/acp-sdks).


## Installare il plug-in utilizzando npm {#section_43229E57C16944C0B51531CB92089189}

Esegui il comando seguente:

```java
cordova plugin add adobe-mobile-services
```

## Installare il plug-in manualmente  {#section_EA1FD59C484D44878AB509954DEE6037}

## Includere il plug-in

1. Trascina il file `ADBMobile_PhoneGap.java` nella cartella `src`.

   Per spostare questo file, fai clic su **[!UICONTROL OK]**.

1. Trascina il file `ADB_Helper.js` nella cartella che contiene il file `index.html`

   Per spostare questo file, fai clic su **[!UICONTROL OK]**.

1. Nella cartella `res/xml`, apri il file `config.xml` e registra un nuovo plug-in aggiungendo gli elementi seguenti:

   ```xml
   <feature name="ADBMobile_PhoneGap"> 
     <param name="android-package" value="[YOUR_PACKAGE_NAME].ADBMobile_PhoneGap" /> 
   </feature>
   ```

   Ad esempio, se il pacchetto si chiama `com.example.phonegaptest`, il valore `android-package` è il seguente:

   ```xml
   <param name="android-package" value="com.example.phonegaptest.ADBMobile_PhoneGap" />
   ```

## Includere la libreria AppMeasurement

1. Per scaricare la libreria AppMeasurement, vedi [Ottenere l'SDK](/help/android/getting-started/dev-qs.md).
1. Trascina il file `adobeMobileLibrary.jar` nella cartella `src`.

   Per spostare questo file, fai clic su **[!UICONTROL OK]**.

1. Fai clic con il pulsante destro del mouse sul file adobeMobileLibrary.jar e seleziona **[!UICONTROL Aggiungi come libreria]**.
1. In base ai requisiti del progetto, inserisci nome, livello e posizione della libreria.
1. Trascina il file `ADBMobileConfig.json` nella cartella `assets` della radice dell'applicazione.
1. Accertati di aver selezionato l'applicazione radice e **non** un'applicazione in un'applicazione.

   Per spostare questo file, fai clic su **[!UICONTROL OK]**.

## Aggiungere le autorizzazioni dell'app

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

## Implementare il tracciamento personalizzato {#section_FD102B3CDAA4492FB04E56BF17E28663}

Nei file `html`, aggiungi quanto segue al tag `<head>` in cui desideri usare il tracciamento:

```
<script type="text/javascript" charset="utf-8" src="ADB_Helper.js"></script>
```

