---
description: Adobe Experience Platform Identity Service fornisce un ID visitatore universale tra le soluzioni Experience Cloud. Il servizio ID è richiesto da Analytics per Target, heartbeat video e integrazioni future di Experience Cloud.
seo-description: Adobe Experience Platform Identity Service fornisce un ID visitatore universale tra le soluzioni Experience Cloud. Il servizio ID è richiesto da Analytics per Target, heartbeat video e integrazioni future di Experience Cloud.
seo-title: Experience Cloud ID
solution: Marketing Cloud,Analytics
title: Experience Cloud ID
topic: Sviluppatore e implementazione
uuid: 13628ea8-3cd4-4cfc-8ff6-722c33f7813a
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Experience Cloud ID {#experience-cloud-id}

The Adobe Experience Platform Identity Service provides a universal visitor ID across Experience Cloud solutions. Il servizio ID è richiesto da Analytics per Target, heartbeat video e integrazioni future di Experience Cloud.

>[!TIP]
>
>Non devi compilare l’Experience Cloud ID se non utilizzi Adobe Experience Platform Identity Service. For more information, see [Adobe Experience Platform Identity Service](https://marketing.adobe.com/resources/help/en_US/mcvid/).

**Richiede SDK versione 4.3 o successiva**

## Enable the Experience Cloud ID {#section_79F984271C3B4366B7B04F864F4FF8C2}

1. Aggiungi la libreria al tuo progetto e implementa le funzioni di ciclo di vita (lifecycle).

   Per ulteriori informazioni, consulta *Aggiungere l’SDK e il file di configurazione al progetto* in Implementazione e ciclo di vita [di](/help/ios/getting-started/dev-qs.md)base.
1. Importa la libreria:

   ```objective-c
   #import "ADBMobile.h"
   ```

1. Verificate che i `ADBMobileConfig.json` file contengano i `marketingCloud` `org`seguenti elementi:

   ```js
   "marketingCloud" : { 
     "org": "YOUR-MCORG-ID" 
   }
   ```

   Gli ID organizzazione di Experience Cloud identificano in modo univoco ogni società cliente in Adobe Experience Cloud e hanno un valore simile al seguente: `016D5C175213CCA80A490D05@AdobeOrg`.

   >[!IMPORTANT]
   >
   >Dovete includere `@AdobeOrg`.

   If these values are not present, download an updated `ADBMobileConfig.json` file from Adobe Mobile services. Per ulteriori informazioni, vedi [ADBMobile JSON config](/help/ios/getting-started/requirements.md).

Dopo la configurazione, viene generato un Experience Cloud ID che viene incluso in tutti gli hit. Eventuali altri ID visitatore, ad esempio gli ID personalizzati o generati in automatico, continueranno a essere inviati con ogni hit.
