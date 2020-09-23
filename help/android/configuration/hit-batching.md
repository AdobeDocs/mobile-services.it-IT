---
description: Con la gestione degli hit in batch, le applicazioni possono rimandare l'invio degli hit fino al superamento di un determinato numero di hit in coda.
keywords: android;library;mobile;sdk
seo-description: Con la gestione degli hit in batch, le applicazioni possono rimandare l'invio degli hit fino al superamento di un determinato numero di hit in coda.
seo-title: Gestione degli hit in batch
solution: Experience Cloud,Analytics
title: Gestione degli hit in batch
topic: Developer and implementation
uuid: ada35be3-242b-4b2b-a828-9bf998dd58b5
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 89%

---


# Invio in batch di hit {#hit-batching}

Con la gestione degli hit in batch, le applicazioni possono rimandare l&#39;invio degli hit fino al superamento di un determinato numero di hit in coda.

>[!IMPORTANT]
>
>Per utilizzare la gestione degli hit in batch, **devi** abilitare il tracciamento offline e disporre della versione SDK 4.1 o successiva

Per abilitare la gestione degli hit in batch, devi aggiornare il file `ADBMobileConfig.json` e specificare un valore per `batchLimit`:

```js
"analytics": {
    "batchLimit": 5,
    ...
}
```

Se imposti il valore su un numero maggiore di 0, l&#39;SDK mette in coda il numero di hit pari al valore *`batchLimit`*. Una volta superata questa soglia, tutti gli hit nella coda vengono inviati.

I seguenti metodi vengono utilizzati con la gestione degli hit in batch:

* `Analytics.getQueueSize` restituisce un `long` con il numero di hit attualmente presenti nella coda di invio in batch di hit.

* `Analytics.sendQueuedHits` forza l&#39;invio da parte della libreria di tutti gli hit nella coda, indipendentemente dal numero di hit attualmente presenti nella coda.
* `Analytics.clearQueue` cancella tutti gli hit dalla coda senza inviarli.
