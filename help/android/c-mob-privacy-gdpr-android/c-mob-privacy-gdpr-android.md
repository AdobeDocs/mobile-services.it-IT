---
description: Gli SDK di Experience Cloud Mobile forniscono API che supportano i requisiti del Regolamento generale sulla protezione dei dati (GDPR) per i titolari del trattamento dei dati. Consentono di recuperare le identità memorizzate localmente e impostare il flag per lo stato di consenso o diniego per la raccolta e la trasmissione dei dati.
seo-description: Gli SDK di Experience Cloud Mobile forniscono API che supportano i requisiti del Regolamento generale sulla protezione dei dati (GDPR) per i titolari del trattamento dei dati. Consentono di recuperare le identità memorizzate localmente e impostare il flag per lo stato di consenso o diniego per la raccolta e la trasmissione dei dati.
seo-title: Panoramica sulla privacy e sul regolamento generale sulla protezione dei dati
title: Panoramica sulla privacy e sul regolamento generale sulla protezione dei dati
uuid: 56d6f155-efec-4b3f-a972-a63155729167
translation-type: ht
source-git-commit: 718e336b9002fe3d5282697d4302d12a89297181

---


# Panoramica sulla privacy e sul regolamento generale sulla protezione dei dati {#privacy-and-general-data-protection-regulation}

Gli SDK di Experience Cloud Mobile forniscono API che supportano i requisiti del Regolamento generale sulla protezione dei dati (RGPD) per i titolari del trattamento dei dati. Consentono di recuperare le identità memorizzate localmente e impostare il flag per lo stato di consenso o diniego per la raccolta e la trasmissione dei dati.

## Nuova versione dell'SDK per dispositivi mobili di Adobe Experience Platform

Stai cercando informazioni e documentazione sull’SDK per dispositivi mobili di Adobe Experience Platform? Fai clic [qui](https://aep-sdks.gitbook.io/docs/) per la documentazione più recente.

A settembre 2018 è stata rilasciata una nuova versione principale dell'SDK. Questi nuovi SDK per dispositivi mobili di Adobe Experience Platform sono configurabili tramite [Experience Platform Launch](https://www.adobe.com/it/experience-platform/launch.html).

* Per iniziare, vai su Adobe Experience Platform Launch.
* Per visualizzare cosa è compreso negli archivi Experience Platform SDK, passa a [Github: SDK di Adobe Experience Platform](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

## Panoramica

>[!IMPORTANT]
>
>Le funzioni per i requisiti RGPD sono supportate **solo** dall'SDK di Mobile versione 4.16.0 o successiva.

Quando fornisce software e servizi a un'azienda, Adobe funge da “responsabile del trattamento” in merito ai dati che elabora e memorizza nell'ambito di tali servizi. In qualità di responsabile del trattamento dei dati, Adobe elabora i dati personali secondo le autorizzazioni e le istruzioni fornite dalla tua azienda (ad esempio, quelli definiti nell'accordo con Adobe).

In qualità di “titolare del trattamento”, puoi usare gli SDK di Adobe Mobile Services per supportare le richieste di recupero e cancellazione dei dati in conformità ai requisiti RGPD provenienti dalle tue applicazioni mobile.

Per le aree delle tue applicazioni mobili gestite tramite l'SDK di Adobe Mobile, puoi utilizzare le seguenti impostazioni e metodi:

* Per recuperare i dati dagli SDK e inviarli ai tuoi server, utilizza il metodo `getAllIdentifiersAsync`.

   Per ulteriori informazioni, vedi [Recupero degli ID memorizzati](/help/android/c-mob-privacy-gdpr-android/c-mob-gdpr-ret-stored-ids-android.md).

* Per impostare lo stato di consenso o diniego e poter dare seguito alle richieste di cancellazione dati in conformità ai requisiti RGPD, utilizza le impostazioni seguenti:

   * `privacyDefault`
   * `setPrivacyStatus`
   Per ulteriori informazioni, consulta [Impostazione dello stato di consenso o diniego dell'utente](/help/android/c-mob-privacy-gdpr-android/privacy.md).