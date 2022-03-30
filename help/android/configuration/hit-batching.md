---
description: Con la gestione degli hit in batch, le applicazioni possono rimandare l'invio degli hit fino al superamento di un determinato numero di hit in coda.
keywords: android,libreria,mobile,sdk
solution: Experience Cloud Services,Analytics
title: Gestione degli hit in batch
topic-fix: Developer and implementation
uuid: ada35be3-242b-4b2b-a828-9bf998dd58b5
exl-id: 74147f09-52fc-46dc-b4dd-2bf60b039f6e
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '162'
ht-degree: 100%

---

# Gestione degli hit in batch {#hit-batching}

Con la gestione degli hit in batch, le applicazioni possono rimandare l’invio degli hit fino al superamento di un determinato numero di hit in coda.

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

Se imposti il valore su un numero maggiore di 0, l’SDK mette in coda il numero di hit pari al valore *`batchLimit`*. Una volta superata questa soglia, vengono inviati tutti gli hit presenti nella coda.

Nella gestione in batch degli hit, vengono utilizzati i seguenti metodi:

* `Analytics.getQueueSize` restituisce un `long` con il numero di hit attualmente presenti nella coda di invio in batch di hit.

* `Analytics.sendQueuedHits` forza l&#39;invio da parte della libreria di tutti gli hit nella coda, indipendentemente dal numero di hit attualmente presenti nella coda.
* `Analytics.clearQueue` cancella tutti gli hit dalla coda senza inviarli.
