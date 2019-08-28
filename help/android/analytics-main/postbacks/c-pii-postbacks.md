---
description: Puoi usare Adobe SDK per raccogliere informazioni di identificazione personale (PII) e inviarle a un endpoint di terze parti.
seo-description: Puoi usare Adobe SDK per raccogliere informazioni di identificazione personale (PII) e inviarle a un endpoint di terze parti.
seo-title: Postback PII
title: Postback PII
uuid: 8 d 1 f 1 fb 8-6842-478 b-a 164-e 7 f 727755 bd 9
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

1. Aggiungi [la libreria al progetto e implementa il ciclo di vita.

   Per ulteriori informazioni, vedi *Aggiungere l'SDK e il file di configurazione al progetto intellij IDEA o Eclipse* nell'implementazione [e nel ciclo di vita principali](/help/android/getting-started/dev-qs.md).

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

