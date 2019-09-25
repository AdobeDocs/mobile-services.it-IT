---
description: È possibile caricare un diverso file di configurazione ADBMobile JSON all'avvio dell'applicazione.
seo-description: È possibile caricare un diverso file di configurazione ADBMobile JSON all'avvio dell'applicazione.
seo-title: Escludere il percorso di configurazione ADBMobile JSON
solution: Marketing Cloud,Analytics
title: Escludere il percorso di configurazione ADBMobile JSON
topic: Sviluppatore e implementazione
uuid: 0d1be674-c634-4a48-aa31-5701681911b9
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Override the ADBMobile JSON config path {#override-the-adbmobile-json-config-path}

È possibile caricare un diverso file di configurazione ADBMobile JSON all'avvio dell'applicazione.

The `ADBMobile overrideConfigPath:filePath` method allows you to specify the path to a different `ADBMobile.json` configuration file when the application starts. Questo metodo deve essere chiamato nel metodo `applicationDidFinishLaunchingWithOptions` e la chiamata deve essere eseguita prima di qualsiasi altra chiamata Experience Cloud SDK, ad esempio `collectLifecycleData`.

When you call this method with a different path, a one-time override of the configuration file occurs until the application is closed.

Ad esempio:

```objective-c
NSString *filePath = [[NSBundle mainBundle] pathForResource:@"ExampleJSONFile" ofType:@"json"]; 
[ADBMobile overrideConfigPath:filePath];
```

