---
description: L'SDK di Adobe Mobile per iOS può essere integrato direttamente in un progetto Swift mediante la funzione "Mix and Match" della iOS Developer Library.
seo-description: L'SDK di Adobe Mobile per iOS può essere integrato direttamente in un progetto Swift mediante la funzione "Mix and Match" della iOS Developer Library.
seo-title: Integrazione Swift
solution: Experience Cloud,Analytics
title: Integrazione Swift
topic: Developer and implementation
uuid: 5fb77b57-cbf9-4bcf-8b41-65a933bf9336
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '129'
ht-degree: 100%

---


# Integrazione Swift {#swift-integration}

L&#39;SDK di Adobe Mobile per iOS può essere integrato direttamente in un progetto Swift mediante la funzione &quot;Mix and Match&quot; della iOS Developer Library.

Per ulteriori informazioni, consulta [Interoperabilità lingua](https://developer.apple.com/documentation/swift#2984801.html).

Ad esempio, utilizzando il metodo bridging header descritto nella documentazione, puoi importare il file di intestazione dell’SDK Adobe Mobile per iOS:

```
#import “ADBMobile.h”
```

Per accedere ai metodi dell’SDK nei file Swift, usa il formato seguente:

```
ADBMobile.{methodname}
```

