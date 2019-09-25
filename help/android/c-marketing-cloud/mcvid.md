---
description: Adobe Experience Platform Identity Service fornisce un ID visitatore universale tra le soluzioni Experience Cloud. Il servizio ID è richiesto da Analytics per Target, heartbeat video e integrazioni future di Experience Cloud.
seo-description: The Adobe Experience Platform Identity Service provides a universal visitor ID across Experience Cloud solutions. Il servizio ID è richiesto da Analytics per Target, heartbeat video e integrazioni future di Experience Cloud.
seo-title: Configurazione Experience Cloud ID
solution: Marketing Cloud,Analytics
title: Configurazione Experience Cloud ID
topic: Sviluppatore e implementazione
uuid: 8ebdf2bf-c581-448f-9542-f99a19784fe7
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Experience Cloud ID configuration {#experience-cloud-id-configuration}

Adobe Experience Platform Identity Service fornisce un ID visitatore universale tra le soluzioni Experience Cloud. Il servizio ID è richiesto da Analytics per Target, heartbeat video e integrazioni future di Experience Cloud.

>[!TIP]
>
>Non devi compilare questo ID a meno che non utilizzi Adobe Experience Platform Identity Service. For more information, see [Adobe Experience Platform Identity Service](https://marketing.adobe.com/resources/help/en_US/mcvid/).

>[!IMPORTANT]
>
>Questa funzionalità richiede la versione SDK 4.3 o successiva.

Per attivare l'Experience Cloud ID:

1. Aggiungi la libreria al tuo progetto e implementa le funzioni di ciclo di vita (lifecycle).

   Per ulteriori informazioni, consulta *Aggiungere l’SDK e il file di configurazione al progetto* IntelliJ IDEA o Eclipse nell’implementazione e nel ciclo di vita [](/help/android/getting-started/dev-qs.md)core.

1. Importa la libreria:

   ```java
   import com.adobe.mobile.*;
   ```

1. Verificate che il `ADBMobileConfig.json` file contenga `marketingCloudorg`:

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
   >Dovete includere `@AdobeOrg`.

   If these IDs are not configured, download an updated `ADBMobileConfig.json` file from Adobe Mobile services. Per ulteriori informazioni, consulta [Prima di iniziare](/help/android/getting-started/requirements.md).

Quando la configurazione è completa, viene generato un Experience Cloud ID che viene incluso in tutti gli hit. Altri ID, come ID personalizzati e generati automaticamente, continuano a essere inviati con ciascun hit.
