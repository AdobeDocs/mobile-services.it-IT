---
description: Queste informazioni sono utili per usare l’SDK per iOS con  Adobe Analytics.
seo-description: Queste informazioni sono utili per usare l’SDK per iOS con  Adobe Analytics.
seo-title: Panoramica di Analytics
solution: Experience Cloud,Analytics
title: Panoramica di Analytics
topic: Developer and implementation
uuid: 8c7fb76a-be0b-4465-8151-ece7bad11b55
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 67%

---


# Panoramica di Analytics {#analytics}

Le informazioni contenute in questa sezione sono utili per usare l’SDK per iOS con Adobe Analytics.

## Nuova versione dell&#39;SDK per dispositivi mobili di Adobe Experience Platform

Hai bisogno di informazioni e documentazione relative all’SDK per dispositivi mobili di Adobe Experience Platform? Fai clic [qui](https://aep-sdks.gitbook.io/docs/) per la documentazione più recente.

A settembre 2018 è stata rilasciata una nuova versione principale dell&#39;SDK. Questi nuovi SDK per dispositivi mobili di Adobe Experience Platform sono configurabili tramite [Experience Platform Launch](https://www.adobe.com/it/experience-platform/launch.html).

* Per iniziare, vai su Adobe Experience Platform Launch.
* Per visualizzare cosa è compreso negli archivi Experience Platform SDK, passa a [Github: SDK di Adobe Experience Platform](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

## Generazione di identificativi di tracciamento di Analytics

Negli SDK, gli identificatori vengono utilizzati per monitorare gli utenti, ed ecco la gerarchia di identificatori:

1. Identificatore visitatore personalizzato (VID)
2. Identificatore tracciamento analisi (AID)
3.  ID Experience Cloud (MID)

>[!TIP]
>
>L’acronimo corretto per l’identificatore di Experience Cloud è ECID. MID è l’acronimo obsoleto, anche se gli SDK lo usano ancora. 
L’AID, a cui talvolta si fa riferimento come identificativo di monitoraggio, viene generato dall’SDK quando l’applicazione non è configurata per l’utilizzo di un MID. Il valore viene mantenuto tra i lanci e gli aggiornamenti dell’app in `NSUserDefaults`: Se l’utente elimina l’app dal proprio dispositivo e successivamente la reinstalla, o se lo sviluppatore dell’app cancella `NSUserDefaults`, un nuovo identificativo viene generato dall’SDK. Questo processo genera un nuovo utente nel reporting di Analytics.

Per gli utenti in un&#39;app che introduce il supporto per il servizio di identità (MID), i valori AID esistenti vengono inviati con hit Analytics, e l&#39;hit Analytics contiene un AID e un MID. Per i nuovi utenti in un&#39;app con supporto del servizio Identità, le richieste di Analytics contengono solo un MID. Per ulteriori informazioni sull’identificazione dei visitatori, consulta [Identificazione dei visitatori](https://docs.adobe.com/content/help/it-IT/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-visid.html).
