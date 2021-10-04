---
description: La serializzazione degli eventi non è supportata dalle regole di elaborazione. Nell’SDK di Mobile devi usare una sintassi particolare nel parametro dei dati contestuali per impostare gli eventi serializzati direttamente nella chiamata al server.
solution: Experience Cloud,Analytics
title: Serializzazione degli eventi
topic-fix: Developer and implementation
uuid: a5966d05-e218-446f-9f19-8664a84b74cd
exl-id: 42ea5e0f-a69e-44ab-aa4e-bbec27815cc8
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '70'
ht-degree: 31%

---

# Serializzazione degli eventi{#event-serialization}

La serializzazione degli eventi non è supportata dalle regole di elaborazione. Nell’SDK di Mobile devi usare una sintassi particolare nel parametro dei dati contestuali per impostare gli eventi serializzati direttamente nella chiamata al server.

```js
cdata["&&events"] = "event1:12341234";
```

Esempio:

```js
//create a context data dictionary 
var cdata = new Windows.Foundation.Collections.PropertySet(); 
 
// add events 
cdata["&&events"] = "event1:12341234"; 
 
var ADB = ADBMobile; 
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
ADB.Analytics.trackAction("action", cdata); 
// trackState example: 
ADB.Analytics.trackState("State Name", cdata);
```
