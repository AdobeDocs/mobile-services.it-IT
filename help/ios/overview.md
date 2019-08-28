---
description: L'SDK 4.x per iOS per le soluzioni Experience Cloud consente di misurare le applicazioni native per Apple iPhone e iPad, inviare contenuti mirati all'interno delle app, nonché sfruttare e raccogliere i dati sul pubblico tramite Audience Manager.
seo-description: L'SDK 4.x per iOS per le soluzioni Experience Cloud consente di misurare le applicazioni native per Apple iPhone e iPad, inviare contenuti mirati all'interno delle app, nonché sfruttare e raccogliere i dati sul pubblico tramite Audience Manager.
seo-title: SDK 4.x per iOS per le soluzioni Experience Cloud
solution: Marketing Cloud, Analytics
title: SDK 4.x per iOS per le soluzioni Experience Cloud
topic: Sviluppatore e implementazione
uuid: 8 b 374 cee -1432-460 b-aac 2-70623 dd 80 a 04
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# SDK 4.x per iOS per le soluzioni Experience Cloud{#ios-sdk-x-for-experience-cloud-solutions}

L'SDK 4.x per iOS per le soluzioni Experience Cloud consente di misurare le applicazioni native per Apple iPhone e iPad, inviare contenuti mirati all'interno delle app, nonché sfruttare e raccogliere i dati sul pubblico tramite Audience Manager.

>[!IMPORTANT]
>
>Lo SKU di Adobe Analytics Mobile Marketing Add-on è richiesto per abilitare Mobile Services ad accedere alle funzionalità di acquisizione mobile, collegamenti profondi, geolocalizzazione e messaggistica mobile. Per ulteriori informazioni, contatta il tuo Adobe CSM.

## Nuova versione di Adobe Experience Cloud SDK

Stai cercando informazioni e documentazione sull’SDK per dispositivi mobili di Adobe Experience Platform? Fai clic [qui](https://aep-sdks.gitbook.io/docs/) per la documentazione più recente.

A settembre 2018 è stata rilasciata una nuova versione principale dell’SDK. Questi nuovi SDK per dispositivi mobili di Adobe Experience Platform sono configurabili tramite [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* Per iniziare, passa ad Launch.
* Per visualizzare cosa è compreso negli archivi Experience Platform SDK, passa a [Github: SDK di Adobe Experience Platform](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

>[!IMPORTANT]
>
> If you are using the Adobe Experience Platform Mobile SDKs with Adobe Launch, you **must** also install the Adobe Analytics Mobile Services extension to use Adobe Mobile Services features such as in-App messaging, push notifications or Acquisition links. Per ulteriori informazioni, consulta [Adobe Analytics - Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services).

Alcune considerazioni da tenere a mente:

* È supportato iOS 5 o versioni successive

   Per iOS 11 o versioni successive, è **necessario** essere in possesso di SDK versione 4.13.8 o successiva.

* Nella versione 4.2 dell'SDK e nelle versioni successive, tutti gli hit vengono inviati tramite HTTP POST.

   Questo non ha alcun impatto sui dati raccolti o segnalati, ma è necessario utilizzare un analizzatore di pacchetti che supporti l'ispezione dei dati POST per visualizzare gli hit.

* If you are upgrading from a previous version (2.x or 3.x), see the [4.x Migration Guide](/help/ios/getting-started/migration-v3.md).

## Documentazione di Adobe Mobile Services {#section_7583FD5FDED143619048E9744A3F2D21}

Adobe Mobile Services fornisce una nuova interfaccia utente che riunisce le funzionalità di mobile marketing per applicazioni mobile da Adobe Experience Cloud. Inizialmente, Mobile Services fornisce un'integrazione perfetta delle funzionalità di analisi e targeting delle app dalle soluzioni Adobe Analytics, Adobe Audience Manager e Adobe Target e Adobe Experience Platform Identity Service.

Per ulteriori informazioni sull'interfaccia utente di Mobile Services e per consultare la documentazione, vedi [Adobe Mobile Services](/help/using/home.md).

## Utilizzo di Bloodhound

>[!IMPORTANT]
>
>As of **April 30, 2017**, Adobe Bloodhound has been
sunset. A partire dal 1° maggio 2017, non verranno più forniti ulteriori miglioramenti né supporto aggiuntivo Engineering o Adobe Expert Care.
