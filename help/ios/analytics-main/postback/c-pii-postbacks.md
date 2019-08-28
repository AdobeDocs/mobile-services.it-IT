---
description: Puoi usare Adobe SDK per raccogliere informazioni di identificazione personale (PII) e inviarle a un endpoint di terze parti.
seo-description: Puoi usare Adobe SDK per raccogliere informazioni di identificazione personale (PII) e inviarle a un endpoint di terze parti.
seo-title: Postback PII
title: Postback PII
uuid: 08 f 76 a 52-75 dd -4 fc 1-b 4 cc -4 f 5 eef 93 d 0 f 7
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# PII postbacks {#pii-postbacks}

Puoi usare Adobe SDK per raccogliere informazioni di identificazione personale (PII) e inviarle a un endpoint di terze parti.

Se desideri utilizzare Adobe SDK per raccogliere PII, invia una chiamata PII di tracciamento. Anche se l'utilizzo di questa chiamata abilita la raccolta di dati PII, l'SDK non invia automaticamente i dati ad alcun endpoint Adobe. Un postback di tipo PII deve essere configurato con l'endpoint appropriato.

>[!TIP]
>
>Per utilizzare il tipo di postback PII è necessario un endpoint che supporta HTTPS.

## Tracking PII postbacks {#section_36B967B888CF467EACCDEF61DFA0B12B}

1. Aggiungi la libreria al tuo progetto e implementa le funzioni di ciclo di vita (lifecycle).

   Per ulteriori informazioni, vedi *Aggiungere l'SDK e il file di configurazione al progetto* in [Implementazione e ciclo di vita di base](/help/ios/getting-started/dev-qs.md).
1. Importa la libreria:

   ```objective-c
   #import "ADBMobile.h"
   ```

1. Quando sei pronto a catturare PII, chiama `trackPII` per inviare un hit per questa azione, evento o visualizzazione:

   ```objective-c
   [ADBMobile collectPII data:nil];
   ```

