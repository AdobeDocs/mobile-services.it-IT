---
description: L'SDK di Adobe Mobile per iOS può essere integrato direttamente in un progetto Swift mediante la funzione "Mix and Match" della iOS Developer Library.
seo-description: L'SDK di Adobe Mobile per iOS può essere integrato direttamente in un progetto Swift mediante la funzione "Mix and Match" della iOS Developer Library.
seo-title: Integrazione Swift
solution: Marketing Cloud, Analytics
title: Integrazione Swift
topic: Sviluppatore e implementazione
uuid: 5 fb 77 b 57-cbf 9-4 bcf -8 b 41-65 a 933 bf 9336
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Swift integration {#swift-integration}

L'SDK di Adobe Mobile per iOS può essere integrato direttamente in un progetto Swift mediante la funzione "Mix and Match" della iOS Developer Library.

Per ulteriori informazioni, vedere [Interoperabilità della lingua](https://developer.apple.com/documentation/swift#2984801.html).

Ad esempio, utilizzando il metodo "bridging header" descritto nella documentazione citata qui sopra, puoi importare il file header dell'SDK di Adobe Mobile per iOS:

```
#import “ADBMobile.h”
```

Per accedere ai metodi dell'SDK nei file Swift, utilizza il seguente formato:

```
ADBMobile.{methodname}
```

