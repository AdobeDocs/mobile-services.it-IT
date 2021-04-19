---
description: L'SDK di Adobe sfrutta le API di attribuzione app di Apple Search Ads per consentire agli sviluppatori e ai professionisti del marketing di tracciare e attribuire i download delle app derivanti da campagne Search Ads nell'Apple App Store.
seo-description: L'SDK di Adobe sfrutta le API di attribuzione app di Apple Search Ads per consentire agli sviluppatori e ai professionisti del marketing di tracciare e attribuire i download delle app derivanti da campagne Search Ads nell'Apple App Store.
seo-title: Apple Search Ads
solution: Experience Cloud,Analytics
title: Apple Search Ads
topic-fix: Developer and implementation
uuid: 790080e8-067e-4bfd-a169-0027db4fdff3
exl-id: efcdd430-f08d-4ee2-85f3-2697c3bd72db
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 100%

---

# Apple Search Ads {#apple-search-ads}

L&#39;SDK di Adobe sfrutta le API di attribuzione app di Apple Search Ads per consentire agli sviluppatori e ai professionisti del marketing di tracciare e attribuire i download delle app derivanti da campagne Search Ads nell&#39;Apple App Store. Per ulteriori informazioni sulle campagne Search Ads, vedi [Apple Search Ads](https://searchads.apple.com/it/).

## Vantaggi {#section_CEA30C652AC8470784B8054E299B80FA}

Alcuni vantaggi offerti dagli annunci Apple Ads:

* Consentono di misurare facilmente l&#39;efficacia delle campagne Search Ads per il download della tua app, aggiungendo poche righe di codice all&#39;app.
* Gli sviluppatori possono accedere alla data/ora del download e alla parola chiave che ha portato alla conversione.

## Implementazione di annunci Apple Ads   {#section_F1094676793540CFA1DBB540174EEB6A}

>[!TIP]
>
>Per implementare Apple Ads, devi disporre della versione SDK 4.13.2 o successiva per iOS.

Per abilitare l&#39;app all&#39;attribuzione Search Ad:

1. Implementa la versione dell’SDK Adobe 4.13.2 o successiva.

   Per ulteriori informazioni, vedi [Implementazione e ciclo di vita di base](/help/ios/getting-started/dev-qs.md).

1. Aggiungi il framework iAd al file del progetto Xcode per la tua app.

## Generazione di rapporti sull&#39;attribuzione Search Ads    {#section_1AF4E0B4F8E94F36B38CA3D3E384D0A4}

1. I dati di attribuzione di Apple Search Ads sono forniti nel nome dell&#39;acquisizione, nella sorgente e nei valori dei termini.

   Se l&#39;attribuzione è `true`, tutti i campi `iad-*` verranno inclusi nell&#39;hit del ciclo di vita.

   Inoltre, i seguenti valori saranno mappati dal dizionario `"iad"` ai nostri tipici campi per dati contestuali per l&#39;acquisizione:

   * `"iad-campaign-id"` --> `"a.referrer.campaign.trackingcode"`
   * `"iad-campaign-name"` —>  `"a.referrer.campaign.name"`
   * `"iad-adgroup-id"` —>  `"a.referrer.campaign.content"`
   * `"iad-keyword"` —>  `"a.referrer.campaign.term"`
   Con questa mappatura, i valori diventano disponibili per le nostre funzioni standard di generazione dei rapporti.
