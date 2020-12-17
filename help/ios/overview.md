---
description: L'SDK 4.x per iOS per le soluzioni Experience Cloud consente di misurare le applicazioni native per Apple iPhone e iPad, inviare contenuti mirati all'interno delle app, nonché sfruttare e raccogliere i dati sul pubblico tramite Audience Manager.
seo-description: L'SDK 4.x per iOS per le soluzioni Experience Cloud consente di misurare le applicazioni native per Apple iPhone e iPad, inviare contenuti mirati all'interno delle app, nonché sfruttare e raccogliere i dati sul pubblico tramite Audience Manager.
seo-title: SDK 4.x per iOS per le soluzioni Experience Cloud
solution: Experience Cloud,Analytics
title: SDK 4.x per iOS per le soluzioni Experience Cloud
topic: Developer and implementation
uuid: 8b374cee-1432-460b-aac2-70623dd80a04
translation-type: tm+mt
source-git-commit: 1b888d0184e20d2134edbc488d36c09d0492a334
workflow-type: tm+mt
source-wordcount: '538'
ht-degree: 84%

---


# SDK 4.x per iOS per le soluzioni Experience Cloud {#ios-sdk-x-for-experience-cloud-solutions}

L&#39;SDK 4.x per iOS per le soluzioni Experience Cloud consente di misurare le applicazioni native per Apple iPhone e iPad, inviare contenuti mirati all&#39;interno delle app, nonché sfruttare e raccogliere i dati sul pubblico tramite Audience Manager.

>[!IMPORTANT]
>
>A partire dalla versione 4.21.0, l’SDK per iOS dispone di una versione minima richiesta di Xcode 12. Se utilizzate i cococoapodi per gestire le dipendenze nell’app, l’SDK per Adobi  richiede la versione 1.10.0 o successiva dei cococoapodi.

Se si utilizza la versione 4.21.0 o successiva, leggere la documentazione tenendo presenti le seguenti modifiche:

* Ogni volta che si fa riferimento a un file di libreria binaria, si deve usare la sostituzione XCFrframework:
   * `AdobeMobileLibrary.a` > `AdobeMobile.xcframework`
   * `AdobeMobileLibrary_Extension.a` >  `AdobeMobileExtension.xcframework`
   * `AdobeMobileLibrary_Watch.a` >  `AdobeMobileWatch.xcframework`
   * `AdobeMobileLibrary_TV.a` >  `AdobeMobileTV.xcframework`
* Il file di intestazione `ADBMobile.h` è incorporato in ogni XCFrframework.
* Se aggiungete manualmente al progetto i framework XCF  Adobe, accertatevi che non siano incorporati.

>[!IMPORTANT]
>
>Lo SKU del componente aggiuntivo Adobe Analytics Mobile Marketing è necessario per consentire a Mobile Services di accedere alle funzionalità di acquisizione mobile, collegamento diretto, geolocalizzazione e messaggistica mobile. Per ulteriori informazioni, contatta il tuo CSM Adobe.

>[!IMPORTANT]
>
>L&#39;SDK 4.x per iOS per le soluzioni Experience Cloud supporta ora [iOS 13 e Xcode 11](https://developer.apple.com/ios/). Per garantire la compatibilità diretta, usa le versioni più recenti degli SDK iOS 4.x. Per ulteriori informazioni sull’ultima versione, consulta le [note sulla versione](/help/ios/rel-notes.md).

## Nuova versione dell&#39;SDK per dispositivi mobili di Adobe Experience Platform

Hai bisogno di informazioni e documentazione relative all’SDK per dispositivi mobili di Adobe Experience Platform? Fai clic [qui](https://aep-sdks.gitbook.io/docs/) per la documentazione più recente.

A settembre 2018 è stata rilasciata una nuova versione principale dell&#39;SDK. Questi nuovi SDK per dispositivi mobili di Adobe Experience Platform sono configurabili tramite [Experience Platform Launch](https://www.adobe.com/it/experience-platform/launch.html).

* Per iniziare, vai su Adobe Experience Platform Launch.
* Per visualizzare cosa è compreso negli archivi Experience Platform SDK, passa a [Github: SDK di Adobe Experience Platform](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

Alcune informazioni da tenere a mente:

* Supporta iOS 8 e versioni successive.

   Per iOS 11 o versione successiva, **è richiesta** la versione SDK 4.13.8 o successiva.

* Nella versione 4.2 dell&#39;SDK e nelle versioni successive, tutti gli hit vengono inviati tramite HTTP POST.

   Questo non ha alcun impatto sui dati raccolti o segnalati, ma per visualizzare gli hit dovrai usare un analizzatore di pacchetti che supporta l&#39;ispezione di dati POST.

* Per l&#39;aggiornamento da una versione precedente (2.x o 3.x), consulta la [Guida alla migrazione 4.x](/help/ios/getting-started/migration-v3.md).

## Documentazione di Adobe Mobile Services {#section_7583FD5FDED143619048E9744A3F2D21}

Adobe Mobile Services fornisce una nuova interfaccia utente che riunisce le funzionalità di mobile marketing per applicazioni mobile da Adobe Experience Cloud. Inizialmente, Mobile Services offre l&#39;integrazione diretta di funzioni di analisi e targeting delle app dalle soluzioni Adobe Analytics, Adobe Audience Manager e Adobe Target, nonché il servizio Adobe Experience Platform Identity.

Per ulteriori informazioni sull&#39;interfaccia utente di Mobile Services e per consultare la documentazione, vedi [Adobe Mobile Services](/help/using/home.md).

## Utilizzo di Bloodhound

>[!IMPORTANT]
>
>Dal **30 aprile 2017**, Adobe Bloodhound è stato ritirato. A partire dal 1° maggio 2017, non verranno più forniti ulteriori miglioramenti né supporto aggiuntivo Engineering o Adobe Expert Care.
