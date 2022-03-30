---
description: Informazioni utili per usare l’SDK per iOS con Adobe Analytics.
solution: Experience Cloud Services,Analytics
title: Panoramica di Analytics
topic-fix: Developer and implementation
uuid: 8c7fb76a-be0b-4465-8151-ece7bad11b55
exl-id: 7c383b1d-2e59-4473-9de5-80c84d896f6d
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '311'
ht-degree: 95%

---

# Panoramica di Analytics {#analytics}

Le informazioni contenute in questa sezione sono utili per usare l’SDK per iOS con Adobe Analytics.

## Nuova versione dell&#39;SDK per dispositivi mobili di Adobe Experience Platform

Hai bisogno di informazioni e documentazione relative all’SDK per dispositivi mobili di Adobe Experience Platform? Fai clic [qui](https://aep-sdks.gitbook.io/docs/) per la documentazione più recente.

A settembre 2018 è stata rilasciata una nuova versione principale dell&#39;SDK. Questi nuovi SDK per dispositivi mobili di Adobe Experience Platform sono configurabili tramite [Experience Platform Launch](https://www.adobe.com/it/experience-platform/launch.html).

* Per iniziare, vai su Adobe Experience Platform Launch.
* Per visualizzare cosa è compreso negli archivi Experience Platform SDK, passa a [Github: SDK di Adobe Experience Platform](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

## Generazione di identificatori di tracciamento di Analytics

Negli SDK, gli identificatori vengono utilizzati per monitorare gli utenti. La gerarchia di identificatori è riportata di seguito:

1. Identificatore visitatore personalizzato (VID)
1. Identificatore di tracciamento Analytics (AID)
1. Identificatore Experience Cloud (MID)

>[!TIP]
>
>L’acronimo corretto per l’identificatore di Experience Cloud è ECID. MID è l’acronimo obsoleto, anche se gli SDK lo usano ancora.

L’AID, a cui talvolta si fa riferimento come identificativo di monitoraggio, viene generato dall’SDK quando l’applicazione non è configurata per l’utilizzo di un MID. Il valore viene mantenuto tra i lanci e gli aggiornamenti dell’app in `NSUserDefaults`: Se l’utente elimina l’app dal proprio dispositivo e successivamente la reinstalla, o se lo sviluppatore dell’app cancella `NSUserDefaults`, un nuovo identificativo viene generato dall’SDK. Questo processo determina un nuovo utente nei rapporti di Analytics.

Per gli utenti di un’app in cui viene introdotto il supporto del servizio di identità (MID), i valori AID esistenti vengono inviati con hit di Analytics contenenti un AID e un MID. Per i nuovi utenti di un’app che supporta il servizio Identità, le richieste di Analytics contengono solo un MID. Per ulteriori informazioni sull&#39;identificazione dei visitatori, vedi [Visitatori unici](https://experienceleague.adobe.com/docs/analytics/components/metrics/unique-visitors.html?lang=it) nella documentazione di Adobe Analytics.
