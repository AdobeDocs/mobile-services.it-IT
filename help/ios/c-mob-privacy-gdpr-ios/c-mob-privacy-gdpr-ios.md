---
description: Gli SDK di Experience Cloud Mobile forniscono API che supportano i requisiti del Regolamento generale sulla protezione dei dati (RGPD) per i titolari del trattamento dei dati. Consentono di recuperare le identità memorizzate localmente e impostare il flag per lo stato di consenso o diniego per la raccolta e la trasmissione dei dati.
seo-description: Gli SDK di Experience Cloud Mobile forniscono API che supportano i requisiti del Regolamento generale sulla protezione dei dati (RGPD) per i titolari del trattamento dei dati. Consentono di recuperare le identità memorizzate localmente e impostare il flag per lo stato di consenso o diniego per la raccolta e la trasmissione dei dati.
seo-title: Privacy e Regolamento generale sulla protezione dei dati (RGPD)
title: Privacy e Regolamento generale sulla protezione dei dati (RGPD)
uuid: 69bb82de-1993-440c-a1b0-8d37919b48b6
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Privacy e Regolamento generale sulla protezione dei dati (RGPD){#privacy-and-general-data-protection-regulation}

Gli SDK di Experience Cloud Mobile forniscono API che supportano i requisiti del Regolamento generale sulla protezione dei dati (RGPD) per i titolari del trattamento dei dati. Consentono di recuperare le identità memorizzate localmente e impostare il flag per lo stato di consenso o diniego per la raccolta e la trasmissione dei dati.

>[!IMPORTANT]
>
>GDPR is supported **only** in Mobile SDK version 4.16.0 or later.

Quando fornisce software e servizi a un'azienda, Adobe funge da “responsabile del trattamento” in merito ai dati che elabora e memorizza nell'ambito di tali servizi. In qualità di responsabile del trattamento dei dati, Adobe elabora i dati personali secondo le autorizzazioni e le istruzioni fornite dalla tua azienda (ad esempio, quelli definiti nell'accordo con Adobe).

In qualità di “titolare del trattamento”, puoi usare gli SDK di Adobe Mobile Services per supportare le richieste di recupero e cancellazione dei dati in conformità ai requisiti RGPD provenienti dalle tue applicazioni mobile.

## Nuova versione di Adobe Experience Cloud SDK

Stai cercando informazioni e documentazione sull’SDK per dispositivi mobili di Adobe Experience Platform? Fai clic [qui](https://aep-sdks.gitbook.io/docs/) per la documentazione più recente.

A settembre 2018 è stata rilasciata una nuova versione principale dell’SDK. Questi nuovi SDK per dispositivi mobili di Adobe Experience Platform sono configurabili tramite [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* Per iniziare, passa ad Launch.
* Per visualizzare cosa è compreso negli archivi Experience Platform SDK, passa a [Github: SDK di Adobe Experience Platform](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

>[!IMPORTANT]
>
> If you are using the Adobe Experience Platform Mobile SDKs with Adobe Launch, you **must** also install the Adobe Analytics Mobile Services extension to use Adobe Mobile Services features such as in-App messaging, push notifications or Acquisition links. Per ulteriori informazioni, consulta [Adobe Analytics - Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services).


Per le aree delle tue applicazioni mobili gestite tramite l'SDK di Adobe Mobile, puoi utilizzare le seguenti impostazioni e metodi:

* Per recuperare i dati dagli SDK e inviarli ai tuoi server, utilizza il metodo `getAllIdentifiersAsync`.

   Per ulteriori informazioni, vedere [Recupero degli identificatori](/help/ios/c-mob-privacy-gdpr-ios/c-mob-gdpr-ret-stored-ids-ios.md)memorizzati.

* Per impostare lo stato di consenso o diniego e poter dare seguito alle richieste di cancellazione dati in conformità ai requisiti RGPD, utilizza le impostazioni seguenti:

   * `privacyDefault`
   * `setPrivacyStatus`
   Per ulteriori informazioni, consultate [Impostazione dello stato](/help/ios/c-mob-privacy-gdpr-ios/privacy.md)di consenso dell'utente.

## Informazioni aggiuntive {#section_7C7124C50D85469C8C8714533FB1A37D}

* Per ulteriori informazioni sul regolamento RGPD, consulta la pagina dedicata all'[RGPD e il tuo business](https://www.adobe.com/privacy/general-data-protection-regulation.html).
* Per accedere alla documentazione sulle API RGPD, consulta [General Data Protection Regulation API](https://adobe.io/apis/cloudplatform/gdpr.html) (API per il regolamento generale sulla protezione dei dati).

