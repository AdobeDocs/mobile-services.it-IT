---
description: I postback consentono di inviare i dati raccolti dall'SDK a un server di terze parti. Sfruttando le caratteristiche e gli attivatori utilizzati per visualizzare un messaggio in-app, puoi configurare l'SDK per l'invio di dati personalizzati a una destinazione terza.
seo-description: I postback consentono di inviare i dati raccolti dall'SDK a un server di terze parti. Sfruttando le caratteristiche e gli attivatori utilizzati per visualizzare un messaggio in-app, puoi configurare l'SDK per l'invio di dati personalizzati a una destinazione terza.
seo-title: Postback
solution: Experience Cloud,Analytics
title: Panoramica sui postback
uuid: 25e2a5fb-1203-40dd-96cd-b23e0f23376d
translation-type: ht
source-git-commit: 83e6968efb0ed1b4ef504286c6cb2e8e4d2eaf94

---


# Panoramica sui postback {#postbacks}

I postback consentono di inviare i dati raccolti dall'SDK a un server di terze parti. Sfruttando le caratteristiche e gli attivatori utilizzati per visualizzare un messaggio in-app, puoi configurare l'SDK per l'invio di dati personalizzati a una destinazione terza.

>[!IMPORTANT]
>
>Questa funzione richiede la versione SDK 4.6.0 o successiva.

I messaggi postback vengono messi in coda e seguono le regole online/offline esistenti per la raccolta dei dati Analytics. Quando un messaggio soddisfa tali regole (come ad esempio i messaggi visualizzati), i messaggi postback non cancellano i restanti messaggi. In questo modo si possono avere più postback per uno stesso hit di Analytics. Per una definizione, vedi la riga *postbacks* in  [File di configurazione ADBMobile JSON](/help/ios/configuration/json-config/json-config.md).

## Espansioni dei modelli {#section_6758AD05A24C4E9E965F5253294C164A}

Sono disponibili espansioni dei modelli nelle proprietà `templateurl` e `templatebody`. Gli elementi modello si presentano come `{key}`, dove `key` è una chiave di dati contestuali o una chiave di dati tradizionali. I valori disponibili per l'espansione dei modelli sono limitati all'[elenco delle variabili ciclo di vita standard](/help/ios/metrics.md), oltre a eventuali dati personalizzati allegati all'hit che attiva il messaggio. Al momento non sono disponibili dati basati sullo storico o su segmenti.

Vi sono inoltre specifici modelli riservati che saranno sostituiti automaticamente dall'SDK con dati interni noti all'SDK.

L'elenco comprende:

| Nome token | Descrizione token |
|--- |--- |
| `{%sdkver%}` | Restituisce la versione SDK. |
| `{%cachebust%}` | Viene risolto su un numero casuale compreso tra 1 e 100000000. |
| `{%adid%}` | Restituisce IDFA. Questo token funziona solo se è stato utilizzato `setAdvertisingIdentifier`. |
| `{%pushid%}` | Restituisce il token dell'identificatore push. Questo token funziona solo se è stato utilizzato `setPushIdentifier`. |
| `{%timestampu%}` | Restituisce la marca temporale corrente sotto forma di tempo Unix (o tempo epoca). |
| `{%timestampz%}` | Restituisce la marca temporale corrente in formato JavaScript (ISO 8601). |