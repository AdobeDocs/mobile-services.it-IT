---
description: Il servizio Adobe Experience Platform Identity fornisce un ID visitatore universale per le soluzioni Experience Cloud. Il servizio ID è richiesto da Analytics per Target, heartbeat video e integrazioni future di Experience Cloud.
seo-description: Il servizio Adobe Experience Platform Identity fornisce un ID visitatore universale per le soluzioni Experience Cloud. Il servizio ID è richiesto da Analytics per Target, heartbeat video e integrazioni future di Experience Cloud.
seo-title: Experience Cloud ID
solution: Marketing Cloud,Analytics
title: Experience Cloud ID
topic: Developer and implementation
uuid: 13628ea8-3cd4-4cfc-8ff6-722c33f7813a
translation-type: ht
source-git-commit: 82b3dc38a0325b3aa733b491ddad9b59dbe84eaa
workflow-type: ht
source-wordcount: '261'
ht-degree: 100%

---


# Experience Cloud ID {#experience-cloud-id}

Il servizio Adobe Experience Platform Identity fornisce un ID visitatore universale per le soluzioni Experience Cloud. Il servizio ID è richiesto da Analytics per Target, heartbeat video e integrazioni future di Experience Cloud.

>[!TIP]
>
>Devi compilare l&#39;Experience Cloud ID solo se utilizzi il servizio Adobe Experience Platform Identity. Per ulteriori informazioni, consulta [Adobe Experience Platform Identity Service](https://docs.adobe.com/content/help/it-IT/id-service/using/home.html).

**Richiede SDK versione 4.3 o successiva**

## Attivare l&#39;Experience Cloud ID {#section_79F984271C3B4366B7B04F864F4FF8C2}

1. Aggiungi la libreria al tuo progetto e implementa le funzioni di ciclo di vita (lifecycle).

   Per ulteriori informazioni, consulta *Aggiungere l’SDK e il file di configurazione al progetto* in [Implementazione e ciclo di vita di base](/help/ios/getting-started/dev-qs.md).
1. Importa la libreria:

   ```objective-c
   #import "ADBMobile.h"
   ```

1. Verifica che i file `ADBMobileConfig.json` contengano `marketingCloud` `org`:

   ```js
   "marketingCloud" : { 
     "org": "YOUR-MCORG-ID" 
   }
   ```

   Gli ID organizzazione di Experience Cloud identificano in modo univoco ogni società cliente in Adobe Experience Cloud e hanno un valore simile al seguente: `016D5C175213CCA80A490D05@AdobeOrg`.

   >[!IMPORTANT]
   >
   >Devi includere `@AdobeOrg`.

   Se tali valori non sono presenti, scarica e aggiorna un file `ADBMobileConfig.json` aggiornato da Adobe Mobile Services. Per ulteriori informazioni, vedi [File di configurazione ADBMobile JSON](/help/ios/getting-started/requirements.md).

Dopo la configurazione, viene generato un Experience Cloud ID che viene incluso in tutti gli hit. Eventuali altri ID visitatore, ad esempio gli ID personalizzati o generati in automatico, continueranno a essere inviati con ogni hit.
