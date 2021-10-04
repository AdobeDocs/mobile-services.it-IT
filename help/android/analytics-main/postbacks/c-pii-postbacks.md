---
description: Puoi usare l’SDK di Adobe per raccogliere informazioni personali (PII) e inviarle a un endpoint di terze parti.
title: Postback PII
uuid: 8d1f1fb8-6842-478b-a164-e7f727755bd9
exl-id: 9f0b9d7b-e51d-477b-ae04-72ab09fbc6fd
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 100%

---

# Postback PII {#pii-postbacks}

Puoi usare l’SDK di Adobe per raccogliere informazioni personali (PII) e inviarle a un endpoint di terze parti.

Se desideri usare l’SDK di Adobe per raccogliere PII, invia una chiamata di tracciamento PII. L’utilizzo di questa chiamata abilita la raccolta di dati PII, tuttavia l’SDK non invia automaticamente i dati a un endpoint di Adobe. È necessario configurare un postback di tipo PII con l’endpoint appropriato.

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
