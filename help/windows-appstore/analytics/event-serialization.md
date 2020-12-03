---
description: La serializzazione degli eventi non è supportata dalle regole di elaborazione. Nell’SDK di Mobile devi usare una sintassi particolare nel parametro dei dati contestuali per impostare gli eventi serializzati direttamente nella chiamata al server.
seo-description: La serializzazione degli eventi non è supportata dalle regole di elaborazione. Nell’SDK di Mobile devi usare una sintassi particolare nel parametro dei dati contestuali per impostare gli eventi serializzati direttamente nella chiamata al server.
seo-title: Serializzazione degli eventi
solution: Experience Cloud,Analytics
title: Serializzazione degli eventi
topic: Developer and implementation
uuid: a5966d05-e218-446f-9f19-8664a84b74cd
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 30%

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

