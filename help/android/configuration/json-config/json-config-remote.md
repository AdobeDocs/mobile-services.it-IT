---
description: È possibile caricare un diverso file di configurazione ADBMobile JSON all'avvio dell'applicazione.
seo-description: È possibile caricare un diverso file di configurazione ADBMobile JSON all'avvio dell'applicazione.
seo-title: Escludere il percorso del file di configurazione ADBMobile JSON
solution: Marketing Cloud, Analytics
title: Escludere il percorso del file di configurazione ADBMobile JSON
topic: Sviluppatore e implementazione
uuid: 6872 a 5 d 7-0 c 5 a -4 fdc-b 7 bf-ad 1534763 a 6 a
translation-type: tm+mt
source-git-commit: bf076aa8e59d5c3e634fc4ae21f0de0d4541a83f

---


# Override the ADBMobile JSON config path {#override-the-adbmobile-json-config-path}

È possibile caricare un diverso file di configurazione ADBMobile JSON all'avvio dell'applicazione.

The `Config.overrideConfigStream(configInput)` method allows you to specify the path to a different `ADBMobile.json` configuration file when the application starts. This method must be called before any other Experience Cloud SDK call (before `Config.collectLifecycleData()` ), typically in the `onCreate` method of your first loaded activity.

Se si invoca questo metodo con un percorso diverso, si esclude una tantum il file di configurazione, fino alla chiusura dell'applicazione.

```java
 try { 
   InputStream configInput = getAssets().open("ExampleJSONFile.json"); 
   Config.overrideConfigStream(configInput); 
   } catch (IOException ex) { 
   // do something with the exception if needed 
}
```

