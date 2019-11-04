---
description: I postback consentono di inviare i dati raccolti dall'SDK a un server di terze parti. Sfruttando le caratteristiche e gli attivatori utilizzati per visualizzare un messaggio in-app, puoi configurare l'SDK per l'invio di dati personalizzati a una destinazione terza.
keywords: android,libreria,mobile,sdk
seo-description: I postback consentono di inviare i dati raccolti dall'SDK a un server di terze parti. Sfruttando le caratteristiche e gli attivatori utilizzati per visualizzare un messaggio in-app, puoi configurare l'SDK per l'invio di dati personalizzati a una destinazione terza.
seo-title: Postback
solution: Experience Cloud,Analytics
title: Panoramica sui postback
topic: Sviluppatore e implementazione
uuid: 8bfd4374-2767-421d-891d-e1e9a99b6977
translation-type: ht
source-git-commit: f26dcd5cf9b19de49c9d034c854d9738c7843fb2

---


# Postback {#postbacks}

I postback consentono di inviare i dati raccolti dall'SDK a un server di terze parti. Sfruttando le caratteristiche e gli attivatori utilizzati per visualizzare un messaggio in-app, puoi configurare l'SDK per l'invio di dati personalizzati a una destinazione terza.

>[!IMPORTANT]
>
>Questa funzione richiede la versione SDK 4.6.0 o successiva.

I messaggi postback vengono messi in coda e seguono le regole online/offline esistenti per la raccolta dei dati Analytics. Quando un messaggio soddisfa tali regole (come ad esempio i messaggi visualizzati), i messaggi postback non cancellano i restanti messaggi. In questo modo si possono avere più postback per uno stesso hit di Analytics. Per una definizione, vedi la riga *postbacks* in  [File di configurazione ADBMobile JSON](/help/android/configuration/json-config/json-config.md).

## Espansioni dei modelli {#section_6758AD05A24C4E9E965F5253294C164A}

Le espansioni dei modelli sono disponibili nelle proprietà `templateurl` e `templatebody`. Gli elementi modello si presentano come `{key}`, dove `key` è una chiave di dati contestuali o una chiave di dati tradizionali. I valori disponibili per l’espansione dei modelli sono limitati alle [Metriche del ciclo di vita](/help/android/metrics.md), oltre a qualsiasi dato personalizzato associato all'hit che attiva il messaggio. Al momento non sono disponibili dati basati sullo storico o su segmenti.

Esistono anche modelli specifici e riservati che l'SDK sostituisce automaticamente con dati interni noti all'SDK.

L'elenco comprende:

| Nome token | Descrizione token |
|--- |--- |
| {%sdkver%} | Restituisce la versione SDK. |
| {%cachebust%} | Viene risolto su un numero casuale compreso tra 1 e 100000000. |
| {%adid%} | Restituisce l'ID dell'inserzionista per Android. Questo funziona solo se avevi usato `submitAdvertisingIdentifierTask`. |
| {%pushid%} | Restituisce il token dell'identificatore push. Questo funziona solo se avevi usato `setPushIdentifier`. |
| {%timestampu%} | Restituisce la marca temporale corrente sotto forma di tempo Unix (o tempo epoca). |
| {%timestampz%} | Restituisce la marca temporale corrente in formato JavaScript (ISO 8601). |