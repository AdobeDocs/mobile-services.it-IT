---
description: I postback consentono di inviare i dati raccolti dall'SDK a un server di terze parti. Sfruttando le caratteristiche e gli attivatori utilizzati per visualizzare un messaggio in-app, puoi configurare l'SDK per l'invio di dati personalizzati a una destinazione terza.
seo-description: I postback consentono di inviare i dati raccolti dall'SDK a un server di terze parti. Sfruttando le caratteristiche e gli attivatori utilizzati per visualizzare un messaggio in-app, puoi configurare l'SDK per l'invio di dati personalizzati a una destinazione terza.
seo-title: Postback
solution: Marketing Cloud, Analytics
title: Panoramica dei postback
uuid: 25 e 2 a 5 fb -1203-40 dd -96 cd-b 23 e 0 f 23376 d
translation-type: tm+mt
source-git-commit: 83e6968efb0ed1b4ef504286c6cb2e8e4d2eaf94

---


# Panoramica dei postback {#postbacks}

I postback consentono di inviare i dati raccolti dall'SDK a un server di terze parti. Sfruttando le caratteristiche e gli attivatori utilizzati per visualizzare un messaggio in-app, puoi configurare l'SDK per l'invio di dati personalizzati a una destinazione terza.

>[!IMPORTANT]
>
>Questa funzionalità richiede la versione SDK 4.6.0 o successiva.

I messaggi postback vengono messi in coda e seguono le regole online/offline esistenti per la raccolta dei dati Analytics. Quando un messaggio soddisfa tali regole (come ad esempio i messaggi visualizzati), i messaggi postback non cancellano i restanti messaggi. In questo modo si possono avere più postback per uno stesso hit di Analytics. Per una definizione, vedi la riga *postbacks* in [File di configurazione ADBMobile JSON](/help/ios/configuration/json-config/json-config.md).

## Template expansions {#section_6758AD05A24C4E9E965F5253294C164A}

Template expansions are available in both the `templateurl` and `templatebody` properties. Template items take the form of `{key}`, where `key` is a context-data key, or traditional data key. I valori disponibili per l'espansione dei modelli sono limitati all'[elenco delle variabili ciclo di vita standard](/help/ios/metrics.md), oltre a eventuali dati personalizzati allegati all'hit che attiva il messaggio. Al momento non sono disponibili dati basati sullo storico o su segmenti.

Vi sono inoltre specifici modelli riservati che saranno sostituiti automaticamente dall'SDK con dati interni noti all'SDK.

L'elenco comprende:

| Nome token | Descrizione token |
|--- |--- |
| `{%sdkver%}` | Restituisce la versione SDK. |
| `{%cachebust%}` | Viene risolto su un numero casuale compreso tra 1 e 100000000. |
| `{%adid%}` | Restituisce IDFA. Questo token funziona solo `setAdvertisingIdentifier`se utilizzato. |
| `{%pushid%}` | Restituisce il token dell'identificatore push. Questo token funziona solo `setPushIdentifier`se utilizzato. |
| `{%timestampu%}` | Restituisce la marca temporale corrente sotto forma di tempo Unix (o tempo epoca). |
| `{%timestampz%}` | Restituisce la marca temporale corrente in formato JavaScript (ISO 8601). |