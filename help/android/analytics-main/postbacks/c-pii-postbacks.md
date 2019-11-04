---
description: Puoi usare Adobe SDK per raccogliere informazioni di identificazione personale (PII) e inviarle a un endpoint di terze parti.
seo-description: Puoi usare Adobe SDK per raccogliere informazioni di identificazione personale (PII) e inviarle a un endpoint di terze parti.
seo-title: Postback PII
title: Postback PII
uuid: 8d1f1fb8-6842-478b-a164-e7f727755bd9
translation-type: ht
source-git-commit: 70ac08c74e11a68d94d3f10ed6d7fc133d34149d

---


# Postback PII {#pii-postbacks}

Puoi usare Adobe SDK per raccogliere informazioni di identificazione personale (PII) e inviarle a un endpoint di terze parti.

Se desideri utilizzare Adobe SDK per raccogliere PII, invia una chiamata PII di tracciamento. Anche se l'utilizzo di questa chiamata abilita la raccolta di dati PII, l'SDK non invia automaticamente i dati a un endpoint Adobe. Un postback di tipo PII deve essere configurato con l'endpoint appropriato.

>[!TIP]
>
>Per usare il tipo di postback PII, occorre un endpoint che supporta HTTPS.

## Tracciamento dei postback PII {#section_36B967B888CF467EACCDEF61DFA0B12B}

1. Aggiungi la libreria al tuo progetto e implementa le funzioni di ciclo di vita (lifecycle).

   Per ulteriori informazioni, consulta *Aggiungere l’SDK e il file di configurazione al progetto IntelliJ IDEA o Eclipse* in [Implementazione e ciclo di vita di base](/help/android/getting-started/dev-qs.md).

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

