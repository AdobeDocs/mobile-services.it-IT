---
description: È possibile caricare un diverso file di configurazione ADBMobile JSON all'avvio dell'applicazione.
seo-description: È possibile caricare un diverso file di configurazione ADBMobile JSON all'avvio dell'applicazione.
seo-title: Ignorare il percorso di configurazione adbmobile JSON
solution: Marketing Cloud, Analytics
title: Ignorare il percorso di configurazione adbmobile JSON
topic: Sviluppatore e implementazione
uuid: 0 d 1 be 674-c 634-4 a 48-aa 31-5701681911 b 9
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Override the ADBMobile JSON config path {#override-the-adbmobile-json-config-path}

È possibile caricare un diverso file di configurazione ADBMobile JSON all'avvio dell'applicazione.

The `ADBMobile overrideConfigPath:filePath` method allows you to specify the path to a different `ADBMobile.json` configuration file when the application starts. Questo metodo deve essere chiamato nel metodo `applicationDidFinishLaunchingWithOptions` e la chiamata deve essere eseguita prima di qualsiasi altra chiamata Experience Cloud SDK, ad esempio `collectLifecycleData`.

Quando si chiama questo metodo con un percorso diverso, si verifica una sostituzione una tantum del file di configurazione fino alla chiusura dell'applicazione.

Ad esempio:

```objective-c
NSString *filePath = [[NSBundle mainBundle] pathForResource:@"ExampleJSONFile" ofType:@"json"]; 
[ADBMobile overrideConfigPath:filePath];
```

