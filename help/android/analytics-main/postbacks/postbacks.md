---
description: I postback consentono di inviare i dati raccolti dall'SDK a un server di terze parti. Sfruttando le caratteristiche e gli attivatori utilizzati per visualizzare un messaggio in-app, puoi configurare l'SDK per l'invio di dati personalizzati a una destinazione terza.
keywords: android;library;mobile;sdk
seo-description: I postback consentono di inviare i dati raccolti dall'SDK a un server di terze parti. Sfruttando le caratteristiche e gli attivatori utilizzati per visualizzare un messaggio in-app, puoi configurare l'SDK per l'invio di dati personalizzati a una destinazione terza.
seo-title: Postback
solution: Marketing Cloud,Analytics
title: Postbacks overview
topic: Sviluppatore e implementazione
uuid: 8bfd4374-2767-421d-891d-e1e9a99b6977
translation-type: tm+mt
source-git-commit: f26dcd5cf9b19de49c9d034c854d9738c7843fb2

---


# Postback {#postbacks}

I postback consentono di inviare i dati raccolti dall'SDK a un server di terze parti. Sfruttando le caratteristiche e gli attivatori utilizzati per visualizzare un messaggio in-app, puoi configurare l'SDK per l'invio di dati personalizzati a una destinazione terza.

>[!IMPORTANT]
>
>Questa funzionalità richiede la versione SDK 4.6.0 o successiva.

I messaggi postback vengono messi in coda e seguono le regole online/offline esistenti per la raccolta dei dati Analytics. Quando un messaggio soddisfa tali regole (come ad esempio i messaggi visualizzati), i messaggi postback non cancellano i restanti messaggi. In questo modo si possono avere più postback per uno stesso hit di Analytics. Per una definizione, vedi la riga *postbacks* in [File di configurazione ADBMobile JSON](/help/android/configuration/json-config/json-config.md).

## Template expansions {#section_6758AD05A24C4E9E965F5253294C164A}

Template expansions are available in the `templateurl` and `templatebody` properties. Template items take the form of `{key}`, where `key` is a context data key or traditional data key. The values that are available for template expansion are limited to the [Lifecycle metrics](/help/android/metrics.md), in addition to any custom data that is attached to the hit that triggers the message. Al momento non sono disponibili dati basati sullo storico o su segmenti.

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