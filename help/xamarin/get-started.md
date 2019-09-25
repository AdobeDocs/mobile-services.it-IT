---
description: Questo argomento descrive come iniziare a utilizzare i componenti di Xamarin per l'SDK 4.x delle soluzioni mobili.
keywords: Xamarin
seo-description: Questo argomento descrive come iniziare a utilizzare i componenti di Xamarin per l'SDK 4.x delle soluzioni mobili.
seo-title: Xamarin components for Experience Cloud Solutions 4.x SDK
solution: Marketing Cloud,Sviluppatore
title: Componenti Xamarin per l’SDK 4.x per soluzioni Experience Cloud
uuid: e7a48107-bd0e-47d6-b49c-dfdae189ac37
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Xamarin components for Experience Cloud Solutions 4.x SDK {#xamarin-components-for-experience-cloud-solutions-x-sdk}

Questo argomento descrive come iniziare a utilizzare i componenti di Xamarin per l'SDK 4.x delle soluzioni mobili.

Ultimo aggiornamento: **10 gennaio 2019**

## Introduzione {#section_59D434C30C8F4765A7DEFE877D5268D0}

>[!IMPORTANT]
>
>L’SDK di Adobe Mobile non è più disponibile nello store componenti Xamarin o nella raccolta NuGet. Per scaricare i componenti Xamarin, vai su [GitHub](https://github.com/Adobe-Marketing-Cloud/mobile-services).


## Android {#section_9CAE1BFD359242568D8288C12A4B7A7D}

Import the ADBMobile Component to your Xamarin.Android project:

1. Apri il progetto Xamarin

1. Open **[!UICONTROL References]** dialog and click the **[!UICONTROL .Net Assembly]** tab.

1. Select  from the lib/Android folder.`ADBMobile.XamarinAndroidBinding.dll`****

1. Add your `ADBMobileConfig.json` file to the **[!UICONTROL Assets]** folder of your project.

1. Aggiungi le autorizzazioni per:

   * `INTERNET`
   * `ACCESS_NETWORK_STATE`
   ```java
    <uses-permission android:name="android.permission.INTERNET" />
    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
   ```

1. Se utilizzi la messaggistica in-app, aggiungi la seguente attività e ricevitore:

   ```java
   <activity 
   android:name="com.adobe.mobile.MessageFullScreenActivity" 
   android:theme="@android:style/Theme.Translucent.NoTitleBar" />
   <receiver android:name="com.adobe.mobile.MessageNotificationHandler" />
   ```

1. Se utilizzi l'acquisizione, aggiungi il ricevitore seguente:

   ```java
   <receiver android:name="com.your.package.name.GPBroadcastReceiver" android:exported="true">
   <intent-filter>
       <action android:name="com.android.vending.INSTALL_REFERRER" />
   </intent-filter>
   </receiver>
   ```

## iOS {#section_1531928DDE904D769B3987BF927D0E02}

Import the ADBMobile Component to your Xamarin.iOS project:

1. Apri il tuo progetto Xamarin.
1. Open **[!UICONTROL References]** dialog and click the **[!UICONTROL .Net Assembly]** tab.

1. Selezionate `ADBMobile.XamarinIOSBinding.dll` dalla cartella **[!UICONTROL lib/ios-unified]** .

1. Aggiungi il file `ADBMobileConfig.json` al progetto.


