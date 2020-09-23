---
description: 'null'
keywords: Unity
seo-description: 'null'
seo-title: Creazione del progetto
solution: Experience Cloud
title: Creazione del progetto
uuid: 5550a394-6f3f-4b87-b840-89621d8a0c1e
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '162'
ht-degree: 20%

---


# Creazione del progetto{#building-your-project}

## iOS

Quando create per iOS, viene creato un progetto Xcode. Per impostazione predefinita, i file `ADBMobileWrapper.mm` e `AdobeMobileLibrary.a` saranno inclusi nel gruppo Librerie del nuovo progetto. Per creare l&#39;app, eseguite i seguenti passaggi manuali:

1. Aggiungi il file `ADBMobileConfig.json` al progetto.

   Assicurarsi che sia membro della build tutte le destinazioni necessarie.

1. Nella scheda Fasi **** build del progetto, aggiungi un collegamento alle seguenti librerie:

   * `SystemConfiguration.framework`
Questa libreria potrebbe essere già collegata.

   * `libsqlite3.0.dylib`

>[!TIP]
>
>Per utilizzare i messaggi in-app delle notifiche locali dall’SDK, devi chiamare `ADBMobile.EnableLocalNotifications();` dal metodo Start nella prima Unity Scene.

## Android

Quando create per Android, il `apk` file include già il `ADBMobileConfig.json` file nella posizione corretta. Per impostazione predefinita, viene utilizzato anche il `AndroidManifest.xml` file nella `/Plugins/Android` cartella.

Se devi usare un file manifesto personalizzato, devi aggiungere le seguenti modifiche.

Aggiungi le autorizzazioni per:

* `INTERNET`
* `ACCESS_NETWORK_STATE`

```java
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

Se utilizzi la messaggistica in-app, aggiungi l’attività e il ricevitore seguenti:

```java
<activity android:name="com.adobe.mobile.MessageFullScreenActivity"  
android:theme="@android:style/Theme.Translucent.NoTitleBar" />
<receiver android:name="com.adobe.mobile.MessageNotificationHandler" />
```
