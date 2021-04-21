---
description: Creazione di progetti iOS
keywords: Unity
solution: Experience Cloud
title: Creazione del progetto
uuid: 5550a394-6f3f-4b87-b840-89621d8a0c1e
exl-id: 9da99392-b34e-4e36-b255-f3787e26015c
translation-type: tm+mt
source-git-commit: b9ee49ba26d4726b1f97ef36f5c2e9923361b1ee
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 18%

---

# Creazione del progetto{#building-your-project}

## iOS

Quando crei per iOS, viene creato un progetto Xcode. Per impostazione predefinita, i file `ADBMobileWrapper.mm` e `AdobeMobileLibrary.a` si troveranno nel gruppo Librerie del nuovo progetto. Esegui i seguenti passaggi manuali necessari per creare l’app:

1. Aggiungi il file `ADBMobileConfig.json` al progetto.

   Assicurati che sia membro della build tutte le destinazioni necessarie.

1. Nella scheda **[!UICONTROL Fasi build]** del progetto, aggiungi un collegamento alle seguenti librerie:

   * `SystemConfiguration.framework`
Questa libreria potrebbe essere già collegata.

   * `libsqlite3.0.dylib`

>[!TIP]
>
>Per utilizzare i messaggi in-app di notifica locale dall&#39;SDK, devi chiamare `ADBMobile.EnableLocalNotifications();` dal metodo Start nella tua prima Unity Scene.

## Android

Quando si crea per Android, il file `apk` include già il file `ADBMobileConfig.json` nella posizione corretta. Per impostazione predefinita, viene utilizzato anche il file `AndroidManifest.xml` nella cartella `/Plugins/Android`.

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
