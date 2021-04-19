---
description: È possibile caricare un diverso file di configurazione ADBMobile JSON all'avvio dell'applicazione.
seo-description: È possibile caricare un diverso file di configurazione ADBMobile JSON all'avvio dell'applicazione.
seo-title: Escludere il percorso del file di configurazione ADBMobile JSON
solution: Experience Cloud,Analytics
title: Escludere il percorso del file di configurazione ADBMobile JSON
topic-fix: Developer and implementation
uuid: 0d1be674-c634-4a48-aa31-5701681911b9
exl-id: 3a191e9c-905f-4bea-8a6f-5ccf5ea02aff
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '120'
ht-degree: 100%

---

# Escludere il percorso del file di configurazione ADBMobile JSON {#override-the-adbmobile-json-config-path}

È possibile caricare un diverso file di configurazione ADBMobile JSON all&#39;avvio dell&#39;applicazione.

Il metodo `ADBMobile overrideConfigPath:filePath` consente di specificare il percorso di un file di configurazione `ADBMobile.json` diverso all&#39;avvio dell&#39;applicazione. Questo metodo deve essere chiamato nel metodo `applicationDidFinishLaunchingWithOptions` e la chiamata deve essere eseguita prima di qualsiasi altra chiamata Experience Cloud SDK, ad esempio `collectLifecycleData`.

Quando invochi questo metodo con un percorso diverso, si esclude una tantum il file di configurazione, fino alla chiusura dell&#39;applicazione.

Ad esempio:

```objective-c
NSString *filePath = [[NSBundle mainBundle] pathForResource:@"ExampleJSONFile" ofType:@"json"]; 
[ADBMobile overrideConfigPath:filePath];
```
