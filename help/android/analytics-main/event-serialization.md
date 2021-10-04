---
description: La serializzazione degli eventi non è supportata dalle regole di elaborazione. Nell’SDK di Mobile devi usare una sintassi particolare nel parametro dei dati contestuali per impostare gli eventi serializzati nella chiamata al server.
keywords: android,libreria,mobile,sdk
solution: Experience Cloud,Analytics
title: Serializzazione degli eventi
topic-fix: Developer and implementation
uuid: acdeda16-ab83-4cfc-907d-33448b801b31
exl-id: 03556912-fdcc-402e-b1de-233771f4e719
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '74'
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
