---
description: Questo argomento descrive come iniziare a utilizzare i componenti Xamarin per l’SDK 4.x delle soluzioni mobili.
keywords: Xamarin
seo-description: Questo argomento descrive come iniziare a utilizzare i componenti Xamarin per l’SDK 4.x delle soluzioni mobili.
seo-title: Componenti Xamarin per l’SDK per soluzioni  Experience Cloud 4.x
solution: Marketing Cloud,Developer
title: Componenti Xamarin per l’SDK per soluzioni  Experience Cloud 4.x
uuid: e7a48107-bd0e-47d6-b49c-dfdae189ac37
translation-type: tm+mt
source-git-commit: c198ae57b05f8965a8e27191443ee2cd552d6c50
workflow-type: tm+mt
source-wordcount: '199'
ht-degree: 3%

---


# Xamarin components for Experience Cloud Solutions 4.x SDK {#xamarin-components-for-experience-cloud-solutions-x-sdk}

Questo argomento descrive come iniziare a utilizzare i componenti Xamarin per l’SDK 4.x delle soluzioni mobili.

Last Updated: **January 10, 2019**

## Introduzione {#section_59D434C30C8F4765A7DEFE877D5268D0}

>[!IMPORTANT]
>
> SDK Mobile di Adobe non è più disponibile nello store componenti di Xamarin o nella raccolta NuGet. Per scaricare i componenti Xamarin, andate a [GitHub](https://github.com/Adobe-Marketing-Cloud/mobile-services).

## Android {#section_9CAE1BFD359242568D8288C12A4B7A7D}

Importa il componente ADBMobile nel progetto Xamarin.Android:

1. Apri il progetto Xamarin
1. Aprite la finestra di dialogo **[!UICONTROL Riferimenti]** e fate clic sulla scheda Assembly **** .Net.
1. Selezionate `ADBMobile.XamarinAndroidBinding.dll` dalla cartella **[!UICONTROL lib/Android]** .
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

1. Se utilizzi l&#39;acquisizione, aggiungi il ricevitore seguente:

   ```java
    <receiver android:name="com.your.package.name.GPBroadcastReceiver" android:exported="true">
    <intent-filter>
        <action android:name="com.android.vending.INSTALL_REFERRER" />
    </intent-filter>
    </receiver>
   ```

## iOS {#section_1531928DDE904D769B3987BF927D0E02}

Importa il componente ADBMobile nel progetto Xamarin.iOS:

1. Apri il tuo progetto Xamarin.
1. Aprite la finestra di dialogo **[!UICONTROL Riferimenti]** e fate clic sulla scheda Assembly **** .Net.
1. Selezionate `ADBMobile.XamarinIOSBinding.dll` dalla cartella **[!UICONTROL lib/ios-unified]** .
1. Aggiungete il `ADBMobileConfig.json` file al progetto.
