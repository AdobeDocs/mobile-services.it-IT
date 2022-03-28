---
description: Gli SDK di Experience Cloud Mobile forniscono API che supportano i requisiti del Regolamento generale sulla protezione dei dati (GDPR) per i titolari del trattamento dei dati. Consentono di recuperare le identità memorizzate localmente e impostare il flag per lo stato di consenso o diniego per la raccolta e la trasmissione dei dati.
title: Privacy e Regolamento generale sulla protezione dei dati (RGPD)
uuid: 69bb82de-1993-440c-a1b0-8d37919b48b6
exl-id: 8549310d-31b8-49a3-9276-f8e9ab980a10
source-git-commit: bd55e3525488f24bc9845220f0df62706ec28f31
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 74%

---

# Privacy e Regolamento generale sulla protezione dei dati (GDPR) {#privacy-and-general-data-protection-regulation}

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

Quando Adobe fornisce software e servizi a un&#39;azienda, Adobe agisce come responsabile del trattamento dei dati per tutti i dati personali trattati e memorizzati nell&#39;ambito della fornitura di tali servizi. In qualità di responsabile del trattamento dei dati, Adobe tratta i dati personali in conformità alle autorizzazioni e alle istruzioni della tua azienda (ad esempio, come stabilito nell’accordo con l’Adobe).

In qualità di titolare del trattamento dei dati, puoi utilizzare Adobe Mobile Services SDK per supportare le richieste di recupero ed eliminazione dal RGPD provenienti dalle tue app mobili.

Per le aree delle tue applicazioni mobili gestite tramite l&#39;SDK di Adobe Mobile, puoi utilizzare le seguenti impostazioni e metodi:

* Per recuperare i dati dagli SDK e inviarli ai tuoi server, utilizza il metodo `getAllIdentifiersAsync`.

   Per ulteriori informazioni, vedi [Recupero degli ID memorizzati](/help/ios/c-mob-privacy-gdpr-ios/c-mob-gdpr-ret-stored-ids-ios.md).

* Per impostare lo stato di consenso o diniego e poter dare seguito alle richieste di cancellazione dati in conformità ai requisiti RGPD, utilizza le impostazioni seguenti:

   * `privacyDefault`
   * `setPrivacyStatus`

   Per ulteriori informazioni, consulta [Impostazione dello stato di consenso o diniego dell&#39;utente](/help/ios/c-mob-privacy-gdpr-ios/privacy.md).

## Informazioni aggiuntive {#section_7C7124C50D85469C8C8714533FB1A37D}

* Per ulteriori informazioni sul RGPD, consulta [RGPD e la tua azienda](https://www.adobe.com/it/privacy/general-data-protection-regulation.html).
