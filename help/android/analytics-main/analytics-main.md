---
description: Queste informazioni sono utili per usare l'SDK per Android con Adobe Analytics.
keywords: android,libreria,mobile,sdk
solution: Experience Cloud,Analytics
title: Panoramica di Analytics
topic-fix: Developer and implementation
uuid: cc9fa1d9-bc48-4d03-854a-f7b263580a91
exl-id: ed9f55e6-f3ab-4c1e-9a2f-1ee67a7b4c03
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 95%

---

# Panoramica di Analytics {#analytics}

Le informazioni in questa sezione sono utili per usare l’SDK per Android con Adobe Analytics.

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

L’AID, a cui talvolta si fa riferimento come identificativo di monitoraggio, viene generato dall’SDK quando l’applicazione non è configurata per l’utilizzo di un MID. Il valore viene mantenuto tra i lanci e gli aggiornamenti dell’app in `SharedPreferences`: Se l’utente elimina l’app dal proprio dispositivo e successivamente la reinstalla, o se lo sviluppatore dell’app cancella SharedPreferences, un nuovo identificativo viene generato dall’SDK. Questo processo determina un nuovo utente nei rapporti di Analytics.

Per gli utenti di un’app in cui viene introdotto il supporto del servizio di identità (MID), i valori AID esistenti vengono inviati con hit di Analytics contenenti un AID e un MID. Per i nuovi utenti di un’app che supporta il servizio Identità, le richieste di Analytics contengono solo un MID. Per ulteriori informazioni sull&#39;identificazione dei visitatori, consulta [Visitatori unici](https://experienceleague.adobe.com/docs/analytics/components/metrics/unique-visitors.html?lang=it) nella documentazione di Adobe Analytics.
