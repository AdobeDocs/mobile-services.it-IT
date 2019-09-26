---
description: Queste informazioni sono utili per usare l'SDK per Android con Adobe Analytics.
keywords: android;library;mobile;sdk
seo-description: Queste informazioni sono utili per usare l'SDK per Android con Adobe Analytics.
seo-title: Panoramica di Analytics
solution: Marketing Cloud,Analytics
title: Analytics overview
topic: Sviluppatore e implementazione
uuid: cc9fa1d9-bc48-4d03-854a-f7b263580a91
translation-type: tm+mt
source-git-commit: b690ec677cf5aedfb2673b707f82716af1851124

---


# Panoramica di Analytics {#analytics}

Le informazioni presenti in questa sezione sono utili per usare l’SDK per Android con Adobe Analytics.

## Nuova versione SDK per Adobe Experience Platform Mobile

Stai cercando informazioni e documentazione sull’SDK per dispositivi mobili di Adobe Experience Platform? Fai clic [qui](https://aep-sdks.gitbook.io/docs/) per la documentazione più recente.

A settembre 2018 è stata rilasciata una nuova versione principale dell’SDK. Questi nuovi SDK per dispositivi mobili di Adobe Experience Platform sono configurabili tramite [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* Per iniziare, vai ad Adobe Experience Platform Launch.
* Per visualizzare cosa è compreso negli archivi Experience Platform SDK, passa a [Github: SDK di Adobe Experience Platform](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

## Generazione di identificatori di tracciamento di Analytics

Negli SDK, gli identificativi sono usati per monitorare gli utenti. La loro gerarchia è la seguente:

1. Identificativo di visitatore personalizzato (VID)
2. Identificativo di monitoraggio Analytics (AID)
3. Identificativo di Experience Cloud (MID)

>[!TIP]
>
>L’acronimo corretto per Experience Cloud Identifier è ECID. MID è l’acronimo obsoleto, anche se gli SDK lo usano ancora.

L’AID, a cui talvolta si fa riferimento come identificativo di monitoraggio, viene generato dall’SDK quando l’applicazione non è configurata per l’utilizzo di un MID. Il valore viene mantenuto tra i lanci e gli aggiornamenti dell’app in `SharedPreferences` : Se l’utente elimina l’app dal proprio dispositivo e successivamente la reinstalla, o se lo sviluppatore dell’app cancella SharedPreferences, un nuovo identificativo viene generato dall’SDK. Questo processo si traduce in un nuovo utente nella reportistica di Analytics.

Per gli utenti di un’applicazione che introduce il supporto del servizio Identity (MID), i valori AID esistenti vengono inviati con i risultati di Analytics, ciascuno contenente un AID e un MID. Per i nuovi utenti di un’applicazione con supporto del servizio Identity, le richieste Analytics contengono solo un MID. For more information about identifying visitors, see [Identify visitors](https://docs.adobe.com/content/help/en/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-visid.html).