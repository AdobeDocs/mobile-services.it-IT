---
description: L'SDK di Adobe Mobile per iOS può essere integrato direttamente in un progetto Swift mediante la funzione "Mix and Match" della iOS Developer Library.
seo-description: L'SDK di Adobe Mobile per iOS può essere integrato direttamente in un progetto Swift mediante la funzione "Mix and Match" della iOS Developer Library.
seo-title: Integrazione Swift
solution: Experience Cloud,Analytics
title: Integrazione Swift
topic: Sviluppatore e implementazione
uuid: 5fb77b57-cbf9-4bcf-8b41-65a933bf9336
translation-type: ht
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Integrazione Swift {#swift-integration}

L'SDK di Adobe Mobile per iOS può essere integrato direttamente in un progetto Swift mediante la funzione "Mix and Match" della iOS Developer Library.

Per ulteriori informazioni, consulta [Interoperabilità lingua](https://developer.apple.com/documentation/swift#2984801.html).

Ad esempio, utilizzando il metodo "bridging header" descritto nella documentazione citata qui sopra, puoi importare il file header dell'SDK di Adobe Mobile per iOS:

```
#import “ADBMobile.h”
```

Per accedere ai metodi dell'SDK nei file Swift, utilizza il seguente formato:

```
ADBMobile.{methodname}
```

