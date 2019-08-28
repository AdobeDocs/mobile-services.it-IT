---
description: Queste informazioni sono utili per usare l'SDK per Android con Adobe Analytics.
keywords: android; libreria; mobile; sdk
seo-description: Queste informazioni sono utili per usare l'SDK per Android con Adobe Analytics.
seo-title: Panoramica di Analytics
solution: Marketing Cloud, Analytics
title: Panoramica di Analytics
topic: Sviluppatore e implementazione
uuid: cc 9 fa 1 d 9-bc 48-4 d 03-854 a-f 7 b 263580 a 91
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Panoramica di Analytics {#analytics}

Le informazioni contenute in questa sezione consentono di utilizzare l'SDK per Android con Adobe Analytics.

## Nuova versione di Adobe Experience Cloud SDK

Stai cercando informazioni e documentazione sull’SDK per dispositivi mobili di Adobe Experience Platform? Fai clic [qui](https://aep-sdks.gitbook.io/docs/) per la documentazione più recente.

>[!IMPORTANT]
>
>A settembre 2018 è stata rilasciata una nuova versione principale dell’SDK. Questi nuovi SDK per dispositivi mobili di Adobe Experience Platform sono configurabili tramite [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* Per iniziare, passa ad [Launch](https://launch.adobe.com/).
* Per visualizzare cosa è compreso negli archivi Experience Platform SDK, passa a [Github: SDK di Adobe Experience Platform](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

## Generazione degli identificatori di tracciamento di Analytics

Negli SDK, gli identificativi sono usati per monitorare gli utenti. La loro gerarchia è la seguente:

1. Identificativo di visitatore personalizzato (VID)
2. Identificativo di monitoraggio Analytics (AID)
3. Identificativo di Experience Cloud (MID)

>[!TIP]
>
>L'acronimo corretto per l'identificatore Experience Cloud è ECID. MID è l’acronimo obsoleto, anche se gli SDK lo usano ancora.

L’AID, a cui talvolta si fa riferimento come identificativo di monitoraggio, viene generato dall’SDK quando l’applicazione non è configurata per l’utilizzo di un MID. Il valore viene mantenuto tra i lanci e gli aggiornamenti dell’app in `SharedPreferences` : Se l’utente elimina l’app dal proprio dispositivo e successivamente la reinstalla, o se lo sviluppatore dell’app cancella SharedPreferences, un nuovo identificativo viene generato dall’SDK. Questo processo si traduce in un nuovo utente nella reportistica di Analytics.

Per gli utenti di un’applicazione che introduce il supporto del servizio Identity (MID), i valori AID esistenti vengono inviati con i risultati di Analytics, ciascuno contenente un AID e un MID. Per i nuovi utenti di un’applicazione con supporto del servizio Identity, le richieste Analytics contengono solo un MID. For more information about identifying visitors, see [Identify visitors](https://docs.adobe.com/content/help/en/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-visid.html).