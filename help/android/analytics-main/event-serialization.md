---
description: La serializzazione degli eventi non è supportata dalle regole di elaborazione. Nell’SDK di Mobile devi usare una sintassi particolare nel parametro dei dati contestuali per impostare gli eventi serializzati nella chiamata al server.
keywords: android,libreria,mobile,sdk
seo-description: La serializzazione degli eventi non è supportata dalle regole di elaborazione. Nell’SDK di Mobile devi usare una sintassi particolare nel parametro dei dati contestuali per impostare gli eventi serializzati nella chiamata al server.
seo-title: Serializzazione degli eventi
solution: Experience Cloud,Analytics
title: Serializzazione degli eventi
topic-fix: Developer and implementation
uuid: acdeda16-ab83-4cfc-907d-33448b801b31
exl-id: 03556912-fdcc-402e-b1de-233771f4e719
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '108'
ht-degree: 100%

---

# Serializzazione degli eventi {#event-serialization}

La serializzazione degli eventi non è supportata dalle regole di elaborazione. Nell’SDK di Mobile devi usare una sintassi particolare nel parametro dei dati contestuali per impostare gli eventi serializzati nella chiamata al server.

```java
cdata.put("&&events", "event1:12341234");
```

Ad esempio:

```java
//create a context data dictionary 
HashMap cdata = new HashMap<String, Object>(); 
 
// add events 
cdata.put("&&events", "event1:12341234"); 
 
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
Analytics.trackAction("action", cdata); 
// trackState example: 
Analytics.trackState("State Name", cdata);
```
