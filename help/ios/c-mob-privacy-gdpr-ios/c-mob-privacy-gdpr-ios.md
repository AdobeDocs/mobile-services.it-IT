---
description: Gli SDK di Experience Cloud Mobile forniscono API che supportano i requisiti del Regolamento generale sulla protezione dei dati (GDPR) per i titolari del trattamento dei dati. Consentono di recuperare le identità memorizzate localmente e impostare il flag per lo stato di consenso o diniego per la raccolta e la trasmissione dei dati.
seo-description: Gli SDK di Experience Cloud Mobile forniscono API che supportano i requisiti del Regolamento generale sulla protezione dei dati (GDPR) per i titolari del trattamento dei dati. Consentono di recuperare le identità memorizzate localmente e impostare il flag per lo stato di consenso o diniego per la raccolta e la trasmissione dei dati.
seo-title: Privacy e Regolamento generale sulla protezione dei dati (RGPD)
title: Privacy e Regolamento generale sulla protezione dei dati (GDPR)
uuid: 69bb82de-1993-440c-a1b0-8d37919b48b6
translation-type: tm+mt
source-git-commit: b690ec677cf5aedfb2673b707f82716af1851124
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 74%

---


# Privacy e Regolamento generale sulla protezione dei dati (RGPD){#privacy-and-general-data-protection-regulation}

Gli SDK di Experience Cloud Mobile forniscono API che supportano i requisiti del Regolamento generale sulla protezione dei dati (RGPD) per i titolari del trattamento dei dati. Consentono di recuperare le identità memorizzate localmente e impostare il flag per lo stato di consenso o diniego per la raccolta e la trasmissione dei dati.

>[!IMPORTANT]
>
>Le funzioni per i requisiti RGPD sono supportate **solo** dall&#39;SDK di Mobile versione 4.16.0 o successiva.

## Nuova versione dell&#39;SDK per dispositivi mobili di Adobe Experience Platform

Hai bisogno di informazioni e documentazione relative all’SDK per dispositivi mobili di Adobe Experience Platform? Fai clic [qui](https://aep-sdks.gitbook.io/docs/) per la documentazione più recente.

A settembre 2018 è stata rilasciata una nuova versione principale dell&#39;SDK. Questi nuovi SDK per dispositivi mobili di Adobe Experience Platform sono configurabili tramite [Experience Platform Launch](https://www.adobe.com/it/experience-platform/launch.html).

* Per iniziare, vai su Adobe Experience Platform Launch.
* Per visualizzare cosa è compreso negli archivi Experience Platform SDK, passa a [Github: SDK di Adobe Experience Platform](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

## Panoramica

Quando  Adobe fornisce software e servizi a un&#39;azienda,  Adobe funge da elaboratore di dati per tutti i dati personali che elabora e archivia nell&#39;ambito della fornitura di tali servizi. In qualità di elaboratore di dati,  Adobe elabora i dati personali in conformità con l&#39;autorizzazione e le istruzioni della tua azienda (ad esempio, come indicato nel tuo contratto con  Adobe).

Come controller di dati, puoi utilizzare  SDK di Mobile Services per supportare il recupero e l&#39;eliminazione di richieste GDPR dalle tue app mobili.

Per le aree delle tue applicazioni mobili gestite tramite l&#39;SDK di Adobe Mobile, puoi utilizzare le seguenti impostazioni e metodi:

* Per recuperare i dati dagli SDK e inviarli ai tuoi server, utilizza il metodo `getAllIdentifiersAsync`.

   Per ulteriori informazioni, vedi [Recupero degli ID memorizzati](/help/ios/c-mob-privacy-gdpr-ios/c-mob-gdpr-ret-stored-ids-ios.md).

* Per impostare lo stato di consenso o diniego e poter dare seguito alle richieste di cancellazione dati in conformità ai requisiti RGPD, utilizza le impostazioni seguenti:

   * `privacyDefault`
   * `setPrivacyStatus`

   Per ulteriori informazioni, consulta [Impostazione dello stato di consenso o diniego dell&#39;utente](/help/ios/c-mob-privacy-gdpr-ios/privacy.md).

## Informazioni aggiuntive {#section_7C7124C50D85469C8C8714533FB1A37D}

* Per ulteriori informazioni sul GDPR, consulta [GDPR e la sezione dedicata agli affari](https://www.adobe.com/it/privacy/general-data-protection-regulation.html).
* To see the GDPR API documentation, go to [General Data Protection Regulation API](https://adobe.io/apis/cloudplatform/gdpr.html).

