---
description: L'SDK 4.x per Android per le soluzioni Experience Cloud consente di misurare le applicazioni native Android, inviare contenuti mirati all'interno dell'app, nonché sfruttare e raccogliere i dati sul pubblico tramite Gestione dell'audience.
keywords: android; libreria; mobile; sdk
seo-description: L'SDK 4.x per Android per le soluzioni Experience Cloud consente di misurare le applicazioni native Android, inviare contenuti mirati all'interno dell'app, nonché sfruttare e raccogliere i dati sul pubblico tramite Gestione dell'audience.
seo-title: SDK 4.x per Android per le soluzioni Experience Cloud
solution: Marketing Cloud, Analytics
title: SDK 4.x per Android per le soluzioni Experience Cloud
topic: Sviluppatore e implementazione
uuid: 56 f 1 ff 41-0365-41 dd-bdde -245 c 823 dff 07
translation-type: tm+mt
source-git-commit: 3b744229b3fc288363be74c3c4adcd71ecc4fad4

---


# Android SDK 4.x for Experience Cloud solutions{#android-sdk-x-for-experience-cloud-solutions}

L'SDK 4.x per Android per le soluzioni Experience Cloud consente di misurare le applicazioni native Android, inviare contenuti mirati all'interno dell'app, nonché sfruttare e raccogliere i dati sul pubblico tramite Gestione dell'audience.

>[!IMPORTANT]
>
>Lo SKU di Adobe Analytics Mobile Marketing Add-on è richiesto per abilitare Mobile Services ad accedere alle funzionalità di acquisizione mobile, collegamenti profondi, geolocalizzazione e messaggistica mobile. Per ulteriori informazioni, contatta il tuo Adobe CSM.

## Nuova versione di Adobe Experience Cloud SDK

Stai cercando informazioni e documentazione sull’SDK per dispositivi mobili di Adobe Experience Platform? Fai clic [qui](https://aep-sdks.gitbook.io/docs/) per la documentazione più recente.

>[!IMPORTANT]
>
>A settembre 2018 è stata rilasciata una nuova versione principale dell’SDK. Questi nuovi SDK per dispositivi mobili di Adobe Experience Platform sono configurabili tramite [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* Per iniziare, passa ad [Launch](https://launch.adobe.com/).
* Per visualizzare cosa è compreso negli archivi Experience Platform SDK, passa a [Github: SDK di Adobe Experience Platform](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

>[!IMPORTANT]
>
> If you are using the Adobe Experience Platform Mobile SDKs with Adobe Launch, you **must** also install the Adobe Analytics Mobile Services extension to use Adobe Mobile Services features such as in-App messaging, push notifications or Acquisition links. Per ulteriori informazioni, consulta [Adobe Analytics - Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services).

>[!IMPORTANT]
>
>Anche se puoi configurare le funzionalità nell'interfaccia utente, queste funzioni non funzioneranno finché non scaricate il file di configurazione generato e aggiungete questo file all'SDK. Per informazioni sul download e la configurazione degli SDK, vedi [Implementazione di base e ciclo di vita](/help/android/getting-started/dev-qs.md).

Gli SDK supportano le seguenti versioni di Android:

* La versione 4.6.0 o precedente supporta Android 2.2 (API 8) - Android 5.1.1 (API 22)
* La versione 4.6.1 o successiva supporta Android 2.3 (API 9) o successivo

Alcune considerazioni da tenere a mente:

* Nella versione 4.2 dell'SDK e nelle versioni successive, tutti gli hit vengono inviati tramite HTTP POST.

   Questo non ha alcun impatto sui dati raccolti o segnalati, ma è necessario utilizzare un analizzatore di pacchetti che supporti l'ispezione dei dati POST per visualizzare gli hit.

* If you are upgrading from a previous version, see the [4.x Migration Guide](/help/android/getting-started/migration-v3.md).

## Adobe Mobile user documentation {#section_7583FD5FDED143619048E9744A3F2D21}

Adobe Mobile Services fornisce un'interfaccia utente che riunisce le funzionalità di mobile marketing per applicazioni per dispositivi mobili dalle diverse soluzioni Adobe Experience Cloud. Per ulteriori informazioni sull'interfaccia utente e per leggere la documentazione per l'utente, consulta [Adobe Mobile Services](https://marketing.adobe.com/resources/help/en_US/mobile/).

## Note sulla versione {#section_F8181DC052D44DD2A99AB40A41F6792C}

Per informazioni aggiornate sulle release di Experience Cloud, consulta le [note sulla versione di Experience Cloud](https://marketing.adobe.com/resources/help/en_US/whatsnew/).

## Utilizzo di Bloodhound

>[!IMPORTANT]
>
>As of **April 30, 2017**, Adobe Bloodhound has been
sunset. A partire dal 1° maggio 2017, non verranno più forniti ulteriori miglioramenti né supporto aggiuntivo Engineering o Adobe Expert Care.
