---
description: Con la gestione degli hit in batch, le applicazioni possono rimandare l'invio degli hit fino al superamento di un determinato numero di hit in coda.
keywords: android; libreria; mobile; sdk
seo-description: Con la gestione degli hit in batch, le applicazioni possono rimandare l'invio degli hit fino al superamento di un determinato numero di hit in coda.
seo-title: Gestione degli hit in batch
solution: Marketing Cloud, Analytics
title: Gestione degli hit in batch
topic: Sviluppatore e implementazione
uuid: ada 35 be 3-242 b -4 b 2 b-a 828-9 bf 998 dd 58 b 5
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Invio in batch di hit {#hit-batching}

Con la gestione degli hit in batch, le applicazioni possono rimandare l'invio degli hit fino al superamento di un determinato numero di hit in coda.

>[!IMPORTANT]
>
>Per utilizzare la gestione degli hit **in batch,** è necessario abilitare il tracciamento offline e disporre della versione SDK 4.1 o successiva

To enable hit batching, update your `ADBMobileConfig.json` file and specify a value for `batchLimit`:

```js
"analytics": {
    "batchLimit": 5,
    ...
}
```

When the value is set to a number greater than 0, the SDK queues the number of hits equal to the *`batchLimit`* value. Una volta raggiunta questa soglia, vengono inviati tutti gli hit presenti nella coda.

I metodi seguenti vengono usati insieme alla gestione degli hit in batch:

* `Analytics.getQueueSize` restituisce un `long` con il numero di hit attualmente presenti nella coda di invio in batch di hit.

* `Analytics.sendQueuedHits` forza l'invio da parte della libreria di tutti gli hit nella coda, indipendentemente dal numero di hit attualmente presenti nella coda.
* `Analytics.clearQueue` cancella tutti gli hit dalla coda senza inviarli.
