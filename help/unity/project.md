---
description: nulle
keywords: Unity
seo-description: nulle
seo-title: Building your project
solution: Marketing Cloud,Developer
title: Creazione del progetto
uuid: 5550a394-6f3f-4b87-b840-89621d8a0c1e
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Building your project{#building-your-project}

## iOS

Quando si sviluppa per iOS, viene creato un progetto Xcode. Per impostazione predefinita, i file `ADBMobileWrapper.mm` e `AdobeMobileLibrary.a` saranno inclusi nel gruppo Librerie del nuovo progetto. Esegui le seguenti operazioni manuali necessarie per creare l'app:

1. Aggiungi il file `ADBMobileConfig.json` al progetto.

   Assicurati che ogni destinazione necessaria faccia parte della build.

1. In the **[!UICONTROL Build Phases]** tab of your project, add a link to the following libraries:

   * `SystemConfiguration.framework`
(This library might be linked already.)

   * `libsqlite3.0.dylib`

>[!TIP]
>
>To use Local Notification In-App messages from the SDK, you must call `ADBMobile.EnableLocalNotifications();` from the Start method in your first Unity Scene.

## Android

Quando si sviluppa per Android, il file `apk` include già il file `ADBMobileConfig.json` nella posizione corretta. By default, the `AndroidManifest.xml` file in your `/Plugins/Android` folder is also used.

Per utilizzare un file di manifesto personalizzato è necessario aggiungere le seguenti modifiche.

Aggiungi le autorizzazioni per:

* `INTERNET`
* `ACCESS_NETWORK_STATE`

```java
<uses-permission android:name="android.permission.INTERNET" /> 
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

Se utilizzate la messaggistica in-app, aggiungete la seguente attività e il ricevitore:

```java
<activity android:name="com.adobe.mobile.MessageFullScreenActivity"  
android:theme="@android:style/Theme.Translucent.NoTitleBar" /> 
<receiver android:name="com.adobe.mobile.MessageNotificationHandler" /> 
```

Se utilizzi l’acquisizione, aggiungi il ricevitore seguente:

```java
<receiver android:name="com.your.package.name.GPBroadcastReceiver" android:exported="true"> 
   <intent-filter> 
      <action android:name="com.android.vending.INSTALL_REFERRER" /> 
   </intent-filter> 
</receiver>
```
