---
description: Adobe Experience Platform Identity Service fornisce un ID visitatore universale nelle soluzioni Experience Cloud. Il servizio ID è richiesto da Analytics per Target, heartbeat video e integrazioni future di Experience Cloud.
seo-description: Adobe Experience Platform Identity Service fornisce un ID visitatore universale nelle soluzioni Experience Cloud. Il servizio ID è richiesto da Analytics per Target, heartbeat video e integrazioni future di Experience Cloud.
seo-title: Configurazione ID di Experience Cloud
solution: Marketing Cloud, Analytics
title: Configurazione ID di Experience Cloud
topic: Sviluppatore e implementazione
uuid: 8 ebdf 2 bf-c 581-448 f -9542-f 99 a 19784 fe 7
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Experience Cloud ID configuration {#experience-cloud-id-configuration}

Adobe Experience Platform Identity Service fornisce un ID visitatore universale nelle soluzioni Experience Cloud. Il servizio ID è richiesto da Analytics per Target, heartbeat video e integrazioni future di Experience Cloud.

>[!TIP]
>
>Non devi compilare questo ID a meno che non utilizzi il servizio identità Adobe Experience Platform. For more information, see [Adobe Experience Platform Identity Service](https://marketing.adobe.com/resources/help/en_US/mcvid/).

>[!IMPORTANT]
>
>Questa funzionalità richiede la versione SDK 4.3 o successiva.

Per attivare l'Experience Cloud ID:

1. Aggiungi la libreria al tuo progetto e implementa le funzioni di ciclo di vita (lifecycle).

   Per ulteriori informazioni, vedi *Aggiungere l'SDK e il file di configurazione al progetto intellij IDEA o Eclipse* nell'implementazione [e nel ciclo di vita principali](/help/android/getting-started/dev-qs.md).

1. Importa la libreria:

   ```java
   import com.adobe.mobile.*;
   ```

1. Verificate che il `ADBMobileConfig.json` file contenga `marketingCloudorg`i seguenti elementi:

   ```js
   "marketingCloud" : { 
     "org": "YOUR-MCORG-ID" 
   }
   ```

   Gli ID organizzazione di Experience Cloud identificano in modo univoco ogni società cliente in Adobe Experience Cloud e hanno un valore simile al seguente:

   ```js
   016D5C175213CCA80A490D05@AdobeOrg`
   ```

   >[!IMPORTANT]
   >
   >È necessario includere `@AdobeOrg`.

   If these IDs are not configured, download an updated `ADBMobileConfig.json` file from Adobe Mobile services. Per ulteriori informazioni, consulta [Prima di iniziare](/help/android/getting-started/requirements.md).

Quando la configurazione è completa, viene generato un Experience Cloud ID che viene incluso in tutti gli hit. Altri ID, come ID personalizzati e generati automaticamente, continuano a essere inviati con ciascun hit.
