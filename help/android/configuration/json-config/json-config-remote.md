---
description: È possibile caricare un diverso file di configurazione ADBMobile JSON all'avvio dell'applicazione.
seo-description: È possibile caricare un diverso file di configurazione ADBMobile JSON all'avvio dell'applicazione.
seo-title: Escludere il percorso del file di configurazione ADBMobile JSON
solution: Experience Cloud,Analytics
title: Escludere il percorso del file di configurazione ADBMobile JSON
topic-fix: Developer and implementation
uuid: 6872a5d7-0c5a-4fdc-b7bf-ad1534763a6a
exl-id: 6ca8e264-af79-4734-aeb9-824582980953
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '116'
ht-degree: 100%

---

# Escludere il percorso del file di configurazione ADBMobile JSON {#override-the-adbmobile-json-config-path}

È possibile caricare un diverso file di configurazione ADBMobile JSON all&#39;avvio dell&#39;applicazione.

Il metodo `Config.overrideConfigStream(configInput)` consente di specificare il percorso di un file di configurazione `ADBMobile.json` diverso all&#39;avvio dell&#39;applicazione. Questo metodo deve essere chiamato prima di qualsiasi altra chiamata Experience Cloud SDK (prima di `Config.collectLifecycleData()` ), generalmente nel metodo `onCreate` della prima attività caricata.

Se si invoca questo metodo con un percorso diverso, si esclude una tantum il file di configurazione, fino alla chiusura dell&#39;applicazione.

```java
 try { 
   InputStream configInput = getAssets().open("ExampleJSONFile.json"); 
   Config.overrideConfigStream(configInput); 
   } catch (IOException ex) { 
   // do something with the exception if needed 
}
```
