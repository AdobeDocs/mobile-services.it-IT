---
description: L'SDK di Adobe Mobile per iOS può essere integrato direttamente in un progetto Swift mediante la funzione "Mix and Match" della iOS Developer Library.
seo-description: L'SDK di Adobe Mobile per iOS può essere integrato direttamente in un progetto Swift mediante la funzione "Mix and Match" della iOS Developer Library.
seo-title: Integrazione Swift
solution: Experience Cloud,Analytics
title: Integrazione Swift
topic-fix: Developer and implementation
uuid: 5fb77b57-cbf9-4bcf-8b41-65a933bf9336
exl-id: 3c1a2e28-53b0-4128-a5d9-d2403885098d
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
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
