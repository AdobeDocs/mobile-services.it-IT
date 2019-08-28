---
description: La serializzazione degli eventi non è supportata dalle regole di elaborazione. Nell'SDK di Mobile devi usare una sintassi particolare nel parametro dei dati contestuali per impostare gli eventi serializzati direttamente nella chiamata al server.
seo-description: La serializzazione degli eventi non è supportata dalle regole di elaborazione. Nell'SDK di Mobile devi usare una sintassi particolare nel parametro dei dati contestuali per impostare gli eventi serializzati direttamente nella chiamata al server.
seo-title: Serializzazione degli eventi
solution: Marketing Cloud, Analytics
title: Serializzazione degli eventi
topic: Sviluppatore e implementazione
uuid: 19 a 27 df 4-0998-403 d -800 c -26 ff 61149208
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Event serialization {#event-serialization}

La serializzazione degli eventi non è supportata dalle regole di elaborazione. Nell'SDK di Mobile devi usare una sintassi particolare nel parametro dei dati contestuali per impostare gli eventi serializzati direttamente nella chiamata al server.

```objective-c
[contextData setObject:@"eventN:serial number" forKey:@"&&events"];
```

Ad esempio:

```objective-c
//create a context data dictionary 
NSMutableDictionary *contextData = [NSMutableDictionary dictionary]; 
 
// add events 
[contextData setObject:@"event1:12341234" forKey:@"&&events"]; 
 
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
[ADBMobile trackAction:@"action" data:contextData]; 
// trackState example: 
[ADBMobile trackState:@"State Name" data:contextData]; 
```

