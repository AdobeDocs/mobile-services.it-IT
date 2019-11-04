---
description: È possibile caricare un diverso file di configurazione ADBMobile JSON all'avvio dell'applicazione.
seo-description: È possibile caricare un diverso file di configurazione ADBMobile JSON all'avvio dell'applicazione.
seo-title: Escludere il percorso del file di configurazione ADBMobile JSON
solution: Experience Cloud,Analytics
title: Escludere il percorso del file di configurazione ADBMobile JSON
topic: Sviluppatore e implementazione
uuid: 6872a5d7-0c5a-4fdc-b7bf-ad1534763a6a
translation-type: ht
source-git-commit: bf076aa8e59d5c3e634fc4ae21f0de0d4541a83f

---


# Escludere il percorso del file di configurazione ADBMobile JSON {#override-the-adbmobile-json-config-path}

È possibile caricare un diverso file di configurazione ADBMobile JSON all'avvio dell'applicazione.

Il metodo `Config.overrideConfigStream(configInput)` consente di specificare il percorso di un file di configurazione `ADBMobile.json` diverso all'avvio dell'applicazione. Questo metodo deve essere chiamato prima di qualsiasi altra chiamata Experience Cloud SDK (prima di `Config.collectLifecycleData()` ), generalmente nel metodo `onCreate` della prima attività caricata.

Se si invoca questo metodo con un percorso diverso, si esclude una tantum il file di configurazione, fino alla chiusura dell'applicazione.

```java
 try { 
   InputStream configInput = getAssets().open("ExampleJSONFile.json"); 
   Config.overrideConfigStream(configInput); 
   } catch (IOException ex) { 
   // do something with the exception if needed 
}
```

