---
description: Con la gestione degli hit in batch, le applicazioni per le quali è stato abilitato il tracciamento offline possono rimandare l'invio degli hit fino al raggiungimento di un determinato numero di hit in coda.
solution: Experience Cloud,Analytics
title: Gestione degli hit in batch
topic-fix: Developer and implementation
uuid: 3dda7372-0695-4cb7-b779-6abca2d6e0d9
exl-id: af21f435-13cb-4353-9fbb-c99274bce411
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 100%

---

# Gestione degli hit in batch {#hit-batching}

Con la gestione degli hit in batch, le applicazioni per le quali è stato abilitato il tracciamento offline possono rimandare l&#39;invio degli hit fino al raggiungimento di un determinato numero di hit in coda.

>[!IMPORTANT]
>
>La gestione degli hit in batch richiede la versione SDK 4.1 o successiva.

Per abilitare la gestione degli hit in batch, devi aggiornare il file `ADBMobileConfig.json` e specificare un valore per `batchLimit`:

```js
"analytics": {
    "batchLimit": 5,
    ...
}
```

Se lo imposti su un numero maggiore di 0, l’SDK mette in coda il numero di hit pari a *`batchLimit`*. Una volta superata questa soglia, vengono inviati tutti gli hit presenti nella coda.

Nella gestione in batch degli hit, vengono utilizzati i seguenti metodi:

* `trackingGetQueueSize()` restituisce un valore `NSUInteger` con il numero di hit attualmente nella coda del batch di hit.
* `trackingSendQueuedHits()` forza l&#39;invio da parte della libreria di tutti gli hit nella coda, indipendentemente dal numero di hit attualmente presenti nella coda.
* `trackingClearQueue()` cancella tutti gli hit dalla coda senza inviarli.

>[!CAUTION]
>
>Per poter usare i batch di hit, il tracciamento offline deve essere abilitato.
