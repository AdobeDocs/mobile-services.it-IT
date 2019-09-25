---
description: Queste informazioni sono utili per usare l'SDK per iOS con Adobe Analytics.
seo-description: Queste informazioni sono utili per usare l'SDK per iOS con Adobe Analytics.
seo-title: Panoramica di Analytics
solution: Marketing Cloud,Analytics
title: Panoramica di Analytics
topic: Sviluppatore e implementazione
uuid: 8c7fb76a-be0b-4465-8151-ece7bad11b55
translation-type: tm+mt
source-git-commit: 9257d6b6c2c14d0422cda65fcc9c677ac5ac47a9

---


# Panoramica di Analytics {#analytics}

The information in this section helps you use the iOS SDK with Adobe Analytics.

## Nuova versione di Adobe Experience Cloud SDK

Stai cercando informazioni e documentazione sull’SDK per dispositivi mobili di Adobe Experience Platform? Fai clic [qui](https://aep-sdks.gitbook.io/docs/) per la documentazione più recente.

A settembre 2018 è stata rilasciata una nuova versione principale dell’SDK. Questi nuovi SDK per dispositivi mobili di Adobe Experience Platform sono configurabili tramite [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* Per iniziare, passa ad Launch.
* Per visualizzare cosa è compreso negli archivi Experience Platform SDK, passa a [Github: SDK di Adobe Experience Platform](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

>[!IMPORTANT]
>
> If you are using the Adobe Experience Platform Mobile SDKs with Adobe Launch, you **must** also install the Adobe Analytics Mobile Services extension to use Adobe Mobile Services features such as in-App messaging, push notifications or Acquisition links. Per ulteriori informazioni, consulta [Adobe Analytics - Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services).

## Generazione di identificatori di tracciamento di Analytics

Negli SDK, gli identificativi sono usati per monitorare gli utenti. La loro gerarchia è la seguente:

1. Identificativo di visitatore personalizzato (VID)
2. Identificativo di monitoraggio Analytics (AID)
3. Identificativo di Experience Cloud (MID)

>[!TIP]
>
>L’acronimo corretto per Experience Cloud Identifier è ECID. MID è l’acronimo obsoleto, anche se gli SDK lo usano ancora.
L’AID, a cui talvolta si fa riferimento come identificativo di monitoraggio, viene generato dall’SDK quando l’applicazione non è configurata per l’utilizzo di un MID. Il valore viene mantenuto tra i lanci e gli aggiornamenti dell’app in `NSUserDefaults` : Se l’utente elimina l’app dal proprio dispositivo e successivamente la reinstalla, o se lo sviluppatore dell’app cancella `NSUserDefaults`, un nuovo identificativo viene generato dall’SDK. Questo processo si traduce in un nuovo utente nella reportistica di Analytics.

Per gli utenti di un’applicazione che introduce il supporto del servizio Identity (MID), i valori AID esistenti vengono inviati con i risultati di Analytics, ciascuno contenente un AID e un MID. Per i nuovi utenti di un’applicazione con supporto del servizio Identity, le richieste Analytics contengono solo un MID. For more information about identifying visitors, see [Identify visitors](https://docs.adobe.com/content/help/en/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-visid.html).
