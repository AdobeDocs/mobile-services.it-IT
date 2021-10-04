---
description: Il servizio Adobe Experience Platform Identity fornisce un ID visitatore universale per le soluzioni Experience Cloud. Il servizio ID è richiesto da Analytics per Target, heartbeat video e integrazioni future di Experience Cloud.
solution: Experience Cloud,Analytics
title: Experience Cloud ID
topic-fix: Developer and implementation
uuid: 13628ea8-3cd4-4cfc-8ff6-722c33f7813a
exl-id: aa7db365-ad21-431f-bff6-2a6da212dd0c
source-git-commit: d1ebb2bbc4742f5288f90a90e977d252f3f30aa3
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 91%

---

# ID Experience Cloud {#experience-cloud-id}

Il servizio Adobe Experience Platform Identity fornisce un ID visitatore universale per le soluzioni Experience Cloud. Il servizio ID è richiesto da Analytics per Target, heartbeat video e integrazioni future di Experience Cloud.

>[!TIP]
>
>Devi compilare l&#39;Experience Cloud ID solo se utilizzi il servizio Adobe Experience Platform Identity. Per ulteriori informazioni, consulta la documentazione [Servizio Adobe Experience Platform Identity](https://experienceleague.adobe.com/docs/id-service/using/home.html?lang=it) .

## Attivare l&#39;Experience Cloud ID {#section_79F984271C3B4366B7B04F864F4FF8C2}

Questi passaggi richiedono una versione SDK 4.3 o successiva.

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
