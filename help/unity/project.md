---
description: Creazione di progetti iOS
keywords: Unity
solution: Experience Cloud Services
title: Creazione del progetto
uuid: 5550a394-6f3f-4b87-b840-89621d8a0c1e
exl-id: 9da99392-b34e-4e36-b255-f3787e26015c
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 18%

---

# Creazione del progetto{#building-your-project}

## iOS

Quando si crea per iOS, viene creato un progetto Xcode. Per impostazione predefinita, la `ADBMobileWrapper.mm` e  `AdobeMobileLibrary.a` I file saranno inclusi nel gruppo Librerie del nuovo progetto. Esegui i seguenti passaggi manuali necessari per creare l’app:

1. Aggiungi il file `ADBMobileConfig.json` al progetto.

   Assicurati che sia membro della build tutte le destinazioni necessarie.

1. In **[!UICONTROL Fasi di creazione]** aggiungi un collegamento alle seguenti librerie nella scheda del progetto:

   * `SystemConfiguration.framework`
Questa libreria potrebbe essere già collegata.

   * `libsqlite3.0.dylib`

>[!TIP]
>
>Per utilizzare i messaggi in-app di notifica locale dall&#39;SDK, devi chiamare `ADBMobile.EnableLocalNotifications();` dal metodo Start nella prima Unity Scene.

## Android

Quando si crea per Android, la `apk` il file include già `ADBMobileConfig.json` nella posizione corretta. Per impostazione predefinita, la `AndroidManifest.xml` in `/Plugins/Android` viene utilizzata anche la cartella .

Se devi utilizzare un file manifesto personalizzato, devi aggiungere le seguenti modifiche.

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
