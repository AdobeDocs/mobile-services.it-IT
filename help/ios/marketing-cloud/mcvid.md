---
description: Adobe Experience Platform Identity Service fornisce un ID visitatore universale nelle soluzioni Experience Cloud. Il servizio ID è richiesto da Analytics per Target, heartbeat video e integrazioni future di Experience Cloud.
seo-description: Adobe Experience Platform Identity Service fornisce un ID visitatore universale nelle soluzioni Experience Cloud. Il servizio ID è richiesto da Analytics per Target, heartbeat video e integrazioni future di Experience Cloud.
seo-title: Experience Cloud ID
solution: Marketing Cloud, Analytics
title: Experience Cloud ID
topic: Sviluppatore e implementazione
uuid: 13628 ea 8-3 cd 4-4 cfc -8 ff 6-722 c 33 f 7813 a
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Experience Cloud ID {#experience-cloud-id}

Adobe Experience Platform Identity Service fornisce un ID visitatore universale nelle soluzioni Experience Cloud. Il servizio ID è richiesto da Analytics per Target, heartbeat video e integrazioni future di Experience Cloud.

>[!TIP]
>
>Non devi compilare l'ID di Experience Cloud a meno che non utilizzi il servizio Identità Adobe Experience Platform. For more information, see [Adobe Experience Platform Identity Service](https://marketing.adobe.com/resources/help/en_US/mcvid/).

**Richiede SDK versione 4.3 o successiva**

## Enable the Experience Cloud ID {#section_79F984271C3B4366B7B04F864F4FF8C2}

1. Aggiungi la libreria al tuo progetto e implementa le funzioni di ciclo di vita (lifecycle).

   Per ulteriori informazioni, vedi *Aggiungere l'SDK e il file di configurazione al progetto* in [Implementazione e ciclo di vita di base](/help/ios/getting-started/dev-qs.md).
1. Importa la libreria:

   ```objective-c
   #import "ADBMobile.h"
   ```

1. Verificate che `ADBMobileConfig.json` i file contengano `marketingCloud``org`i seguenti elementi:

   ```js
   "marketingCloud" : { 
     "org": "YOUR-MCORG-ID" 
   }
   ```

   Gli ID organizzazione di Experience Cloud identificano in modo univoco ogni società cliente in Adobe Experience Cloud e hanno un valore simile al seguente: `016D5C175213CCA80A490D05@AdobeOrg`.

   >[!IMPORTANT]
   >
   >È necessario includere `@AdobeOrg`.

   If these values are not present, download an updated `ADBMobileConfig.json` file from Adobe Mobile services. Per ulteriori informazioni, vedi [Configurazione adbmobile JSON](/help/ios/getting-started/requirements.md).

Dopo la configurazione, viene generato un Experience Cloud ID che viene incluso in tutti gli hit. Eventuali altri ID visitatore, ad esempio gli ID personalizzati o generati in automatico, continueranno a essere inviati con ogni hit.
