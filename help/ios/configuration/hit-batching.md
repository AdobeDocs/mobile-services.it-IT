---
description: Con la gestione degli hit in batch, le applicazioni per le quali è stato abilitato il tracciamento offline possono rimandare l'invio degli hit fino al raggiungimento di un determinato numero di hit in coda.
seo-description: Con la gestione degli hit in batch, le applicazioni per le quali è stato abilitato il tracciamento offline possono rimandare l'invio degli hit fino al raggiungimento di un determinato numero di hit in coda.
seo-title: Invio in batch di hit
solution: Marketing Cloud, Analytics
title: Invio in batch di hit
topic: Sviluppatore e implementazione
uuid: 3 dda 7372-0695-4 cb 7-b 779-6 abca 2 d 6 e 0 d 9
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Invio in batch di hit {#hit-batching}

Con la gestione degli hit in batch, le applicazioni per le quali è stato abilitato il tracciamento offline possono rimandare l'invio degli hit fino al raggiungimento di un determinato numero di hit in coda.

>[!IMPORTANT]
>
>La gestione degli hit in batch richiede la versione SDK 4.1 o successiva.

To enable hit batching, update your `ADBMobileConfig.json` file and specify a value for `batchLimit`:

```js
"analytics": {
    "batchLimit": 5,
    ...
}
```

Se lo imposti su un numero maggiore di 0, l'SDK mette in coda il numero di hit pari a *`batchLimit`*. Una volta raggiunta questa soglia, vengono inviati tutti gli hit presenti nella coda.

I metodi seguenti vengono usati insieme alla gestione degli hit in batch:

* `trackingGetQueueSize()` restituisce un valore `NSUInteger` con il numero di hit attualmente nella coda del batch di hit.
* `trackingSendQueuedHits()` forza l'invio da parte della libreria di tutti gli hit nella coda, indipendentemente dal numero di hit attualmente presenti nella coda.
* `trackingClearQueue()` cancella tutti gli hit dalla coda senza inviarli.

>[!CAUTION]
>
>Per utilizzare la gestione degli hit in batch, è necessario abilitare il tracciamento offline.

