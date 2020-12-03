---
description: Puoi usare l’SDK di Adobe per raccogliere informazioni personali (PII) e inviarle a un endpoint di terze parti.
seo-description: Puoi usare l’SDK di Adobe per raccogliere informazioni personali (PII) e inviarle a un endpoint di terze parti.
seo-title: Postback PII
title: Postback PII
uuid: 08f76a52-75dd-4fc1-b4cc-4f5eef93d0f7
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e
workflow-type: tm+mt
source-wordcount: '178'
ht-degree: 88%

---


# Postback PII {#pii-postbacks}

Puoi usare l’SDK di Adobe per raccogliere informazioni personali (PII) e inviarle a un endpoint di terze parti.

Se desideri usare l’SDK di Adobe per raccogliere PII, invia una chiamata di tracciamento PII. Anche se l’utilizzo di questa chiamata abilita la raccolta di dati PII, l’SDK non invia automaticamente i dati ad alcun endpoint  Adobe. È necessario configurare un postback di tipo PII con l’endpoint appropriato.

>[!TIP]
>
>Per usare il tipo di postback PII, occorre un endpoint che supporta HTTPS.

## Tracciamento dei postback PII {#section_36B967B888CF467EACCDEF61DFA0B12B}

1. Aggiungi la libreria al tuo progetto e implementa le funzioni di ciclo di vita (lifecycle).

   Per ulteriori informazioni, consulta *Aggiungere l’SDK e il file di configurazione al progetto* in [Implementazione e ciclo di vita di base](/help/ios/getting-started/dev-qs.md).
1. Importa la libreria:

   ```objective-c
   #import "ADBMobile.h"
   ```

1. Quando sei pronto a catturare PII, chiama `trackPII` per inviare un hit per questa azione, evento o visualizzazione:

   ```objective-c
   [ADBMobile collectPII data:nil];
   ```

