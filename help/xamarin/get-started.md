---
description: Questo argomento descrive come iniziare a utilizzare i componenti Xamarin per l’SDK 4.x delle soluzioni Mobile.
keywords: Xamarina
solution: Experience Cloud Services
title: Componenti Xamarin per l’SDK 4.x delle soluzioni Experience Cloud
uuid: e7a48107-bd0e-47d6-b49c-dfdae189ac37
exl-id: 39628548-5787-4022-8792-86b78214a1c0
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '177'
ht-degree: 99%

---

# Componenti Xamarin per l’SDK 4.x delle soluzioni Experience Cloud {#xamarin-components-for-experience-cloud-solutions-x-sdk}

Questo argomento descrive come iniziare a utilizzare i componenti Xamarin per l’SDK 4.x delle soluzioni Mobile.

Ultimo aggiornamento: **10 gennaio 2019**

## Introduzione {#section_59D434C30C8F4765A7DEFE877D5268D0}

>[!IMPORTANT]
>
>L’SDK di Adobe Mobile non è più disponibile nello store dei componenti di Xamarin o nella raccolta NuGet. Per scaricare i componenti Xamarin, vai su [GitHub](https://github.com/Adobe-Marketing-Cloud/mobile-services).

## Android {#section_9CAE1BFD359242568D8288C12A4B7A7D}

Importa il componente ADBMobile nel progetto Xamarin.Android:

1. Apri il progetto Xamarin
1. Apri la finestra di dialogo **[!UICONTROL Riferimenti]** e fai clic sulla scheda **[!UICONTROL .Net Assembly]**.
1. Seleziona `ADBMobile.XamarinAndroidBinding.dll` dalla cartella **[!UICONTROL lib/Android]**.
1. Aggiungi il file `ADBMobileConfig.json` alla cartella **[!UICONTROL Risorse]** del progetto.
1. Aggiungi le autorizzazioni per:

   * `INTERNET`
   * `ACCESS_NETWORK_STATE`

   ```java
    <uses-permission android:name="android.permission.INTERNET" />
    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
   ```

1. Se utilizzi la messaggistica in-app, aggiungi l’attività e il ricevitore seguenti:

   ```java
    <activity 
    android:name="com.adobe.mobile.MessageFullScreenActivity" 
    android:theme="@android:style/Theme.Translucent.NoTitleBar" />
    <receiver android:name="com.adobe.mobile.MessageNotificationHandler" />
   ```

1. Se stai utilizzando l’acquisizione, aggiungi il ricevitore seguente:

   ```java
    <receiver android:name="com.your.package.name.GPBroadcastReceiver" android:exported="true">
    <intent-filter>
        <action android:name="com.android.vending.INSTALL_REFERRER" />
    </intent-filter>
    </receiver>
   ```

## iOS {#section_1531928DDE904D769B3987BF927D0E02}

Importa il componente ADBMobile nel progetto Xamarin.iOS:

1. Apri il progetto Xamarin.
1. Apri la finestra di dialogo **[!UICONTROL Riferimenti]** e fai clic sulla scheda **[!UICONTROL .Net Assembly]**.
1. Seleziona `ADBMobile.XamarinIOSBinding.dll` dalla cartella **[!UICONTROL lib/ios-unified]**.
1. Aggiungi il file `ADBMobileConfig.json` al progetto.
