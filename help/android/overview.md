---
description: L'SDK 4.x per Android per le soluzioni Experience Cloud consente di misurare le applicazioni native Android, inviare contenuti mirati all'interno dell'app, nonché sfruttare e raccogliere i dati sul pubblico tramite Gestione dell'audience.
keywords: android;library;mobile;sdk
seo-description: L'SDK 4.x per Android per le soluzioni Experience Cloud consente di misurare le applicazioni native Android, inviare contenuti mirati all'interno dell'app, nonché sfruttare e raccogliere i dati sul pubblico tramite Gestione dell'audience.
seo-title: SDK 4.x per Android per le soluzioni Experience Cloud
solution: Marketing Cloud,Analytics
title: SDK 4.x per Android per le soluzioni Experience Cloud
topic: Developer and implementation
uuid: 56f1ff41-0365-41dd-bdde-245c823dff07
translation-type: ht
source-git-commit: 82b3dc38a0325b3aa733b491ddad9b59dbe84eaa
workflow-type: ht
source-wordcount: '447'
ht-degree: 100%

---


# Android SDK 4.x per soluzioni Experience Cloud {#android-sdk-x-for-experience-cloud-solutions}

L&#39;SDK 4.x per Android per le soluzioni Experience Cloud consente di misurare le applicazioni native Android, inviare contenuti mirati all&#39;interno dell&#39;app, nonché sfruttare e raccogliere i dati sul pubblico tramite Gestione dell&#39;audience.

## Nuova versione dell&#39;SDK per dispositivi mobili di Adobe Experience Platform

Hai bisogno di informazioni e documentazione relative all’SDK per dispositivi mobili di Adobe Experience Platform? Fai clic [qui](https://aep-sdks.gitbook.io/docs/) per la documentazione più recente.

A settembre 2018 è stata rilasciata una nuova versione principale dell&#39;SDK. Questi nuovi SDK per dispositivi mobili di Adobe Experience Platform sono configurabili tramite [Experience Platform Launch](https://www.adobe.com/it/experience-platform/launch.html).

* Per iniziare, vai su Adobe Experience Platform Launch.
* Per visualizzare cosa è compreso negli archivi Experience Platform SDK, passa a [Github: SDK di Adobe Experience Platform](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

>[!IMPORTANT]
>
>Lo SKU del componente aggiuntivo Adobe Analytics Mobile Marketing è necessario per consentire a Mobile Services di accedere alle funzionalità di acquisizione mobile, collegamento diretto, geolocalizzazione e messaggistica mobile. Per ulteriori informazioni, contatta il tuo CSM Adobe.

>[!IMPORTANT]
>
>Anche se puoi configurare le funzionalità nell&#39;interfaccia utente, non funzioneranno finché non avrai scaricato il file di configurazione generato e aggiunto il file all&#39;SDK. Per informazioni sul download e sulla configurazione degli SDK, vedi [Implementazione e ciclo di vita di base](/help/android/getting-started/dev-qs.md).

Gli SDK supportano le seguenti versioni di Android:

* La versione 4.6.0 o precedente supporta Android 2.2 (API 8)-Android 5.1.1 (API 22)
* La versione 4.6.1 o successiva supporta Android 2.3 (API 9) o versioni successive

Alcune informazioni da tenere a mente:

* Nella versione 4.2 o successive, tutti gli hit sono ora inviati tramite HTTP POST.

   Questo non ha alcun impatto sui dati raccolti o segnalati, ma per visualizzare gli hit dovrai usare un analizzatore di pacchetti che supporta l&#39;ispezione di dati POST.

* Per l&#39;aggiornamento da una versione precedente, consulta la [Guida alla migrazione 4.x](/help/android/getting-started/migration-v3.md).

## Documentazione di Adobe Mobile Services {#section_7583FD5FDED143619048E9744A3F2D21}

Adobe Mobile Services fornisce un&#39;interfaccia utente che riunisce le funzionalità di mobile marketing per applicazioni per dispositivi mobili dalle diverse soluzioni Adobe Experience Cloud. Per ulteriori informazioni sull&#39;interfaccia utente di e per consultare la documentazione, vedi [Adobe Mobile Services](https://docs.adobe.com/content/help/it-IT/mobile-services/using/home.html).

## Note sulla versione {#section_F8181DC052D44DD2A99AB40A41F6792C}

Per informazioni aggiornate sulle release di Experience Cloud, consulta le [note sulla versione di Experience Cloud](https://docs.adobe.com/content/help/it-IT/release-notes/experience-cloud/current.html).

## Utilizzo di Bloodhound

>[!IMPORTANT]
>
>Dal **30 aprile 2017**, Adobe Bloodhound è stato
ritirato. A partire dal 1° maggio 2017, non verranno più forniti ulteriori miglioramenti né supporto aggiuntivo Engineering o Adobe Expert Care.
