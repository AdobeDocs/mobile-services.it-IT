---
description: Il servizio Adobe Experience Platform Identity fornisce un ID visitatore universale per le soluzioni Experience Cloud. Il servizio ID è richiesto da Analytics per Target, heartbeat video e integrazioni future di Experience Cloud.
seo-description: Il servizio Adobe Experience Platform Identity fornisce un ID visitatore universale per le soluzioni Experience Cloud. Il servizio ID è richiesto da Analytics per Target, heartbeat video e integrazioni future di Experience Cloud.
seo-title: Configurazione del servizio Experience Cloud ID
solution: Experience Cloud,Analytics
title: Configurazione del servizio Experience Cloud ID
topic: Developer and implementation
uuid: 8ebdf2bf-c581-448f-9542-f99a19784fe7
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '270'
ht-degree: 100%

---


# Configurazione del servizio Experience Cloud ID {#experience-cloud-id-configuration}

Il servizio Adobe Experience Platform Identity fornisce un ID visitatore universale per le soluzioni Experience Cloud. Il servizio ID è richiesto da Analytics per Target, heartbeat video e integrazioni future di Experience Cloud.

>[!TIP]
>
>Devi compilare l&#39;ID solo se utilizzi il servizio Adobe Experience Platform Identity. Per ulteriori informazioni, consulta [Adobe Experience Platform Identity Service](https://docs.adobe.com/content/help/it-IT/id-service/using/home.html).

>[!IMPORTANT]
>
>Questa funzione richiede la versione SDK 4.3 o successiva.

Per attivare l&#39;Experience Cloud ID:

1. Aggiungi la libreria al tuo progetto e implementa le funzioni di ciclo di vita (lifecycle).

   Per ulteriori informazioni, consulta *Aggiungere l’SDK e il file di configurazione al progetto IntelliJ IDEA o Eclipse* in [Implementazione e ciclo di vita di base](/help/android/getting-started/dev-qs.md).

1. Importa la libreria:

   ```java
   import com.adobe.mobile.*;
   ```

1. Verifica che il file `ADBMobileConfig.json` contenga `marketingCloudorg`:

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
   >Devi includere `@AdobeOrg`.

   Se tali ID non sono configurati, scarica un file `ADBMobileConfig.json` aggiornato da Adobe Mobile Services. Per ulteriori informazioni, consulta [Prima di iniziare](/help/android/getting-started/requirements.md).

Al termine della configurazione, viene generato un Experience Cloud ID che viene incluso in tutti gli hit. Eventuali altri ID, ad esempio gli ID personalizzati o generati in automatico, continuano a essere inviati con ogni hit.
