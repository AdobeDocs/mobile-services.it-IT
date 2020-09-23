---
description: I postback consentono di inviare i dati raccolti dall’SDK a un server di terze parti. Sfruttando le caratteristiche e gli attivatori utilizzati per visualizzare un messaggio in-app, puoi configurare l’SDK per l’invio di dati personalizzati a una destinazione terza.
seo-description: I postback consentono di inviare i dati raccolti dall’SDK a un server di terze parti. Sfruttando le caratteristiche e gli attivatori utilizzati per visualizzare un messaggio in-app, puoi configurare l’SDK per l’invio di dati personalizzati a una destinazione terza.
seo-title: Postback
solution: Experience Cloud,Analytics
title: Panoramica sui postback
uuid: 25e2a5fb-1203-40dd-96cd-b23e0f23376d
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 27%

---


# Panoramica sui postback {#postbacks}

I postback consentono di inviare i dati raccolti dall’SDK a un server di terze parti. Sfruttando le caratteristiche e gli attivatori utilizzati per visualizzare un messaggio in-app, puoi configurare l’SDK per l’invio di dati personalizzati a una destinazione terza.

>[!IMPORTANT]
>
>Questa funzione richiede la versione SDK 4.6.0 o successiva.

I messaggi di postback vengono messi in coda e seguono tutte le regole online/offline esistenti che disciplinano la raccolta dei dati di analisi. Quando un messaggio corrisponde (come fanno i messaggi visualizzati), i messaggi postback non annullano gli altri messaggi. Questo consente di avere più postback sullo stesso hit di analisi. Per una definizione, vedi la riga *postbacks* in  [File di configurazione ADBMobile JSON](/help/ios/configuration/json-config/json-config.md).

## Espansioni dei modelli {#section_6758AD05A24C4E9E965F5253294C164A}

Sono disponibili espansioni dei modelli nelle proprietà `templateurl` e `templatebody`. Gli elementi modello si presentano come `{key}`, dove `key` è una chiave di dati contestuali o una chiave di dati tradizionali. The values available for template expansion are limited to the [standard Lifecycle variables list](/help/ios/metrics.md), in addition to any custom data attached to the hit that triggers the message. Al momento non sono disponibili dati basati sullo storico o su segmenti.

Esistono anche modelli specifici e riservati che l’SDK sostituirà automaticamente con dati interni noti all’SDK.

Questo elenco include:

| Nome token | Descrizione token |
|--- |--- |
| `{%sdkver%}` | Restituisce la versione SDK. |
| `{%cachebust%}` | Viene risolto su un numero casuale compreso tra 1 e 100000000. |
| `{%adid%}` | Restituisce IDFA. Questo token funziona solo se è stato utilizzato `setAdvertisingIdentifier`. |
| `{%pushid%}` | Restituisce il token dell&#39;identificatore push. Questo token funziona solo se è stato utilizzato `setPushIdentifier`. |
| `{%timestampu%}` | Restituisce la marca temporale corrente sotto forma di tempo Unix (o tempo epoca). |
| `{%timestampz%}` | Restituisce la marca temporale corrente in formato JavaScript (ISO 8601). |