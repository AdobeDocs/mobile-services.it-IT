---
description: Puoi usare Adobe SDK per raccogliere informazioni di identificazione personale (PII) e inviarle a un endpoint di terze parti.
seo-description: Puoi usare Adobe SDK per raccogliere informazioni di identificazione personale (PII) e inviarle a un endpoint di terze parti.
seo-title: Postback PII
title: Postback PII
uuid: 8d1f1fb8-6842-478b-a164-e7f727755bd9
translation-type: tm+mt
source-git-commit: 70ac08c74e11a68d94d3f10ed6d7fc133d34149d

---


# PII postbacks {#pii-postbacks}

Puoi usare Adobe SDK per raccogliere informazioni di identificazione personale (PII) e inviarle a un endpoint di terze parti.

Se desideri utilizzare Adobe SDK per raccogliere PII, invia una chiamata PII di tracciamento. Anche se l'utilizzo di questa chiamata abilita la raccolta di dati PII, l'SDK non invia automaticamente i dati a un endpoint Adobe. Un postback di tipo PII deve essere configurato con l'endpoint appropriato.

>[!TIP]
>
>Per utilizzare il tipo di postback PII è necessario un endpoint che supporta HTTPS.

## Tracking PII postbacks {#section_36B967B888CF467EACCDEF61DFA0B12B}

1. Add [the library to your project and implement lifecycle.

   For more information, see Add the SDK and Config File to your IntelliJ IDEA or Eclipse Project in Core implementation and lifecycle.**[](/help/android/getting-started/dev-qs.md)

1. Importa la libreria:

   ```java
   #import "ADBMobile.h"
   ```

1. Quando sei pronto a catturare PII, chiama `trackPII` per inviare un hit per questa azione, evento o visualizzazione:

   ```java
   Config.collectPII(new HashMap<String, Object>(){{
     put("key","value");
   }});
   ```

