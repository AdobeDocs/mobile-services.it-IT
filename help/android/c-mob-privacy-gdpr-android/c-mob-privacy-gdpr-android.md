---
description: Gli SDK di Experience Cloud Mobile forniscono API che supportano i requisiti del Regolamento generale sulla protezione dei dati (GDPR) per i titolari del trattamento dei dati. Consentono di recuperare le identità memorizzate localmente e impostare il flag per lo stato di consenso o diniego per la raccolta e la trasmissione dei dati.
title: Panoramica sulla privacy e sul regolamento generale sulla protezione dei dati
uuid: 56d6f155-efec-4b3f-a972-a63155729167
exl-id: 57696f2e-87f4-4f72-bec2-80c7192576f9
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 76%

---

# Panoramica sulla privacy e sul regolamento generale sulla protezione dei dati {#privacy-and-general-data-protection-regulation}

Gli SDK di Experience Cloud Mobile forniscono API che supportano i requisiti del Regolamento generale sulla protezione dei dati (GDPR) per i titolari del trattamento dei dati. Consentono di recuperare le identità memorizzate localmente e impostare il flag per lo stato di consenso o diniego per la raccolta e la trasmissione dei dati.

## Nuova versione dell&#39;SDK per dispositivi mobili di Adobe Experience Platform

Hai bisogno di informazioni e documentazione relative all’SDK per dispositivi mobili di Adobe Experience Platform? Fai clic [qui](https://aep-sdks.gitbook.io/docs/) per la documentazione più recente.

A settembre 2018 è stata rilasciata una nuova versione principale dell&#39;SDK. Questi nuovi SDK per dispositivi mobili di Adobe Experience Platform sono configurabili tramite [Experience Platform Launch](https://www.adobe.com/it/experience-platform/launch.html).

* Per iniziare, vai su Adobe Experience Platform Launch.
* Per visualizzare cosa è compreso negli archivi Experience Platform SDK, passa a [Github: SDK di Adobe Experience Platform](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

## Panoramica

>[!IMPORTANT]
>
>Le funzioni per i requisiti RGPD sono supportate **solo** dall&#39;SDK di Mobile versione 4.16.0 o successiva.

Quando Adobe fornisce software e servizi a un&#39;azienda, Adobe agisce come responsabile del trattamento dei dati per tutti i dati personali trattati e memorizzati nell&#39;ambito della fornitura di tali servizi. In qualità di responsabile del trattamento dei dati, Adobe tratta i dati personali in conformità alle autorizzazioni e alle istruzioni della tua azienda (ad esempio, come stabilito nell’accordo con l’Adobe).

In qualità di titolare del trattamento dei dati, puoi utilizzare Adobe Mobile Services SDK per supportare le richieste di recupero ed eliminazione dal RGPD provenienti dalle tue app mobili.

Per le aree delle tue applicazioni mobili gestite tramite l&#39;SDK di Adobe Mobile, puoi utilizzare le seguenti impostazioni e metodi:

* Per recuperare i dati dagli SDK e inviarli ai tuoi server, utilizza il metodo `getAllIdentifiersAsync`.

   Per ulteriori informazioni, vedi [Recupero degli ID memorizzati](/help/android/c-mob-privacy-gdpr-android/c-mob-gdpr-ret-stored-ids-android.md).

* Per impostare lo stato di consenso o diniego e poter dare seguito alle richieste di cancellazione dati in conformità ai requisiti RGPD, utilizza le impostazioni seguenti:

   * `privacyDefault`
   * `setPrivacyStatus`
   Per ulteriori informazioni, consulta [Impostazione dello stato di consenso o diniego dell&#39;utente](/help/android/c-mob-privacy-gdpr-android/privacy.md).
