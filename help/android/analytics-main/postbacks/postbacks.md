---
description: I postback consentono di inviare i dati raccolti dall’SDK a un server di terze parti. Sfruttando le caratteristiche e gli attivatori utilizzati per visualizzare un messaggio in-app, puoi configurare l’SDK per l’invio di dati personalizzati a una destinazione terza.
keywords: android,libreria,mobile,sdk
seo-description: I postback consentono di inviare i dati raccolti dall’SDK a un server di terze parti. Sfruttando le caratteristiche e gli attivatori utilizzati per visualizzare un messaggio in-app, puoi configurare l’SDK per l’invio di dati personalizzati a una destinazione terza.
seo-title: Postback
solution: Experience Cloud,Analytics
title: Panoramica sui postback
topic-fix: Developer and implementation
uuid: 8bfd4374-2767-421d-891d-e1e9a99b6977
exl-id: 318f6eab-ff71-4bfe-8eb7-51a35380b992
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 100%

---

# Postback {#postbacks}

I postback consentono di inviare i dati raccolti dall’SDK a un server di terze parti. Sfruttando le caratteristiche e gli attivatori utilizzati per visualizzare un messaggio in-app, puoi configurare l’SDK per l’invio di dati personalizzati a una destinazione terza.

>[!IMPORTANT]
>
>Questa funzione richiede la versione SDK 4.6.0 o successiva.

I messaggi di postback vengono messi in coda e seguono tutte le regole online/offline esistenti che disciplinano la raccolta dei dati di analisi. Quando viene riscontrata una corrispondenza (come nel caso dei messaggi visualizzati), i messaggi postback non annullano gli altri messaggi. In tal modo si possono verificare più postback sullo stesso hit di analisi. Per una definizione, vedi la riga *postbacks* in   [File di configurazione ADBMobile JSON](/help/android/configuration/json-config/json-config.md).

## Espansioni dei modelli {#section_6758AD05A24C4E9E965F5253294C164A}

Le espansioni dei modelli sono disponibili nelle proprietà `templateurl` e `templatebody`. Gli elementi modello si presentano come `{key}`, dove `key` è una chiave di dati contestuali o una chiave di dati tradizionali. I valori disponibili per l’espansione dei modelli sono limitati alle [metriche del ciclo di vita](/help/android/metrics.md), oltre a eventuali dati personalizzati associati all’hit che attiva il messaggio. Al momento non sono disponibili dati basati sullo storico o sui segmenti.

Esistono anche modelli specifici e riservati che l’SDK sostituirà automaticamente con dati interni noti all’SDK.

Tale elenco include:

| Nome token | Descrizione token |
|--- |--- |
| {%sdkver%} | Restituisce la versione SDK. |
| {%cachebust%} | Viene risolto su un numero casuale compreso tra 1 e 100000000. |
| {%adid%} | Restituisce l&#39;ID dell&#39;inserzionista per Android. Questo funziona solo se avevi usato `submitAdvertisingIdentifierTask`. |
| {%pushid%} | Restituisce il token dell&#39;identificatore push. Questo funziona solo se avevi usato `setPushIdentifier`. |
| {%timestampu%} | Restituisce la marca temporale corrente sotto forma di tempo Unix (o tempo epoca). |
| {%timestampz%} | Restituisce la marca temporale corrente in formato JavaScript (ISO 8601). |
