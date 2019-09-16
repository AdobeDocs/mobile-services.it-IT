---
description: L'SDK di Adobe sfrutta le API di attribuzione app di Apple Search Ads per consentire agli sviluppatori e ai professionisti del marketing di tracciare e attribuire i download delle app derivanti da campagne Search Ads nell'Apple App Store.
seo-description: L'SDK di Adobe sfrutta le API di attribuzione app di Apple Search Ads per consentire agli sviluppatori e ai professionisti del marketing di tracciare e attribuire i download delle app derivanti da campagne Search Ads nell'Apple App Store.
seo-title: Apple Search Ads
solution: Marketing Cloud,Analytics
title: Apple Search Ads
topic: Sviluppatore e implementazione
uuid: 790080e8-067e-4bfd-a169-0027db4fdff3
translation-type: tm+mt
source-git-commit: 1fba1bafcf43b87b47375f203cdcdcff29e9102e

---


# Apple Search Ads {#apple-search-ads}

L'SDK di Adobe sfrutta le API di attribuzione app di Apple Search Ads per consentire agli sviluppatori e ai professionisti del marketing di tracciare e attribuire i download delle app derivanti da campagne Search Ads nell'Apple App Store. Per ulteriori informazioni sulle campagne Search Ads, vedi [Apple Search Ads](https://searchads.apple.com).

## Vantaggi {#section_CEA30C652AC8470784B8054E299B80FA}

Alcuni vantaggi offerti dagli annunci Apple Ads:

* Consentono di misurare facilmente l'efficacia delle campagne Search Ads per il download della tua app, aggiungendo poche righe di codice all'app.
* Gli sviluppatori possono accedere alla data/ora del download e alla parola chiave che ha portato alla conversione.

## Implementazione di annunci Apple Ads {#section_F1094676793540CFA1DBB540174EEB6A}

>[!TIP]
>
>Per implementare Apple Ads, devi disporre della versione SDK 4.13.2 o successiva per iOS.

Per abilitare l'app all'attribuzione Search Ad:

1. Implementa la versione SDK Adobe 4.13.2 o successiva.

   Per ulteriori informazioni, consulta [Core implementation and lifecycle](/help/ios/getting-started/dev-qs.md).

1. Aggiungi il framework iAd al file del progetto Xcode per la tua app.

## Generazione di rapporti sull'attribuzione Search Ads {#section_1AF4E0B4F8E94F36B38CA3D3E384D0A4}

1. I dati di attribuzione di Apple Search Ads sono forniti nel nome dell'acquisizione, nella sorgente e nei valori dei termini.

   If attribution = `true`, all of the `iad-*` fields will be included in the lifecycle hit.

   Inoltre, i seguenti valori saranno mappati dal dizionario "`iad`" ai nostri tipici campi per dati contestuali per l'acquisizione:

   * `"iad-campaign-id"` --&gt; `"a.referrer.campaign.trackingcode"`
   * `"iad-campaign-name"` --&gt; `"a.referrer.campaign.name"`
   * `"iad-adgroup-id"` --&gt; `"a.referrer.campaign.content"`
   * `"iad-keyword"` --&gt; `"a.referrer.campaign.term"`
   Questa mappatura assicura che i valori siano disponibili nel nostro reporting standard.

