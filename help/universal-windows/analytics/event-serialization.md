---
description: La serializzazione degli eventi non è supportata dalle regole di elaborazione. Nell’SDK di Mobile devi usare una sintassi particolare nel parametro dei dati contestuali per impostare gli eventi serializzati direttamente nella chiamata al server.
seo-description: La serializzazione degli eventi non è supportata dalle regole di elaborazione. Nell’SDK di Mobile devi usare una sintassi particolare nel parametro dei dati contestuali per impostare gli eventi serializzati direttamente nella chiamata al server.
seo-title: Serializzazione degli eventi
solution: Marketing Cloud, Analytics
title: Serializzazione degli eventi
topic: Sviluppatore e implementazione
uuid: 7220 a 001-1174-4013-91 ff-e 8603 d 8 ab 265
translation-type: tm+mt
source-git-commit: f5ba33fe805c502b8ae91ddafcaa0b57e68704b8

---


# Event serialization {#event-serialization}

La serializzazione degli eventi non è supportata dalle regole di elaborazione. Nell'SDK di Mobile devi usare una sintassi particolare nel parametro dei dati contestuali per impostare gli eventi serializzati direttamente nella chiamata al server.

```js
cdata["&&events"] = "event1:12341234";
```

Ad esempio:

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

