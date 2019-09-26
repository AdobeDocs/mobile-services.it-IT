---
description: L'SDK 4.x per Android per le soluzioni Experience Cloud consente di misurare le applicazioni native Android, inviare contenuti mirati all'interno dell'app, nonché sfruttare e raccogliere i dati sul pubblico tramite Gestione dell'audience.
keywords: android;library;mobile;sdk
seo-description: L'SDK 4.x per Android per le soluzioni Experience Cloud consente di misurare le applicazioni native Android, inviare contenuti mirati all'interno dell'app, nonché sfruttare e raccogliere i dati sul pubblico tramite Gestione dell'audience.
seo-title: SDK 4.x per Android per le soluzioni Experience Cloud
solution: Marketing Cloud,Analytics
title: SDK 4.x per Android per le soluzioni Experience Cloud
topic: Sviluppatore e implementazione
uuid: 56f1ff41-0365-41dd-bdde-245c823dff07
translation-type: tm+mt
source-git-commit: b690ec677cf5aedfb2673b707f82716af1851124

---


# Android SDK 4.x for Experience Cloud solutions{#android-sdk-x-for-experience-cloud-solutions}

L'SDK 4.x per Android per le soluzioni Experience Cloud consente di misurare le applicazioni native Android, inviare contenuti mirati all'interno dell'app, nonché sfruttare e raccogliere i dati sul pubblico tramite Gestione dell'audience.

## New Adobe Experience Platform Mobile SDK Release

Stai cercando informazioni e documentazione sull’SDK per dispositivi mobili di Adobe Experience Platform? Fai clic [qui](https://aep-sdks.gitbook.io/docs/) per la documentazione più recente.

A settembre 2018 è stata rilasciata una nuova versione principale dell’SDK. Questi nuovi SDK per dispositivi mobili di Adobe Experience Platform sono configurabili tramite [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* To get started, go to Adobe Experience Platform Launch.
* Per visualizzare cosa è compreso negli archivi Experience Platform SDK, passa a [Github: SDK di Adobe Experience Platform](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

>[!IMPORTANT]
>
>The Adobe Analytics Mobile Marketing Add-on SKU is required to enable Mobile Services access to mobile acquisition, deep linking, geolocation, and mobile messaging capabilities. For more information, contact your Adobe CSM.

>[!IMPORTANT]
>
>Although you can configure features in the UI, these features will not work until you download the generated configuration file and add this file to the SDK. For information about downloading and configuring the SDKs, see Core Implementation and Lifecycle.[](/help/android/getting-started/dev-qs.md)

Gli SDK supportano le seguenti versioni di Android:

* La versione 4.6.0 o precedente supporta Android 2.2 (API 8) - Android 5.1.1 (API 22)
* La versione 4.6.1 o successiva supporta Android 2.3 (API 9) o successivo

Alcune considerazioni da tenere a mente:

* Nella versione 4.2 dell'SDK e nelle versioni successive, tutti gli hit vengono inviati tramite HTTP POST.

   Questo non ha alcun impatto sui dati raccolti o segnalati, ma per visualizzare gli hit è necessario utilizzare un analizzatore di pacchetti che supporti l’ispezione dei dati POST.

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
