---
description: Queste informazioni sono utili per capire come vengono tracciati gli arresti anomali dell'app e quali best practice adottare per gestire i falsi arresti anomali.
solution: Experience Cloud Services,Analytics
title: Tracciare gli arresti anomali dell’app
topic-fix: Developer and implementation
uuid: 4f81988b-198a-4ba9-ad53-78af90e43856
exl-id: d6b4c763-7e02-42d0-aaf2-cda8640e5b9f
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '509'
ht-degree: 100%

---

# Tracciare gli arresti anomali dell’app {#track-app-crashes}

Queste informazioni sono utili per capire come vengono tracciati gli arresti anomali dell&#39;app e quali best practice adottare per gestire i falsi arresti anomali.

>[!IMPORTANT]
>
>Effettua l&#39;aggiornamento alla versione SDK 4.8.6 per iOS, contenente modifiche importanti grazie alle quali non vengono più segnalati i falsi arresti anomali.

## Quando viene segnalato un arresto anomalo?

Se l&#39;applicazione viene terminata senza prima passare in background, l&#39;SDK segnala un arresto anomalo al successivo avvio dell&#39;app.

## Come funziona la segnalazione di arresti anomali?

iOS usa le notifiche di sistema che permettono agli sviluppatori di tenere traccia e rispondere a diversi stati ed eventi nel ciclo di vita dell&#39;applicazione.

L&#39;SDK di Adobe Mobile per iOS ha un gestore di notifiche che risponde alla notifica `UIApplicationDidEnterBackgroundNotification`. In questo codice, viene impostato un valore che indica che l’app è stata messa in background dall’utente. Al successivo avvio, se tale valore non viene trovato, viene registrato un arresto anomalo.

## Perché Adobe misura gli arresti anomali in questo modo?

Questo approccio fornisce una risposta di alto livello alla domanda *L&#39;utente è uscito intenzionalmente dall&#39;app?*

Le librerie per la segnalazione di arresti anomali fornite da aziende come Apteligent (già Crittercism) usano un gestore `NSException` globale per fornire informazioni più dettagliate sugli arresti anomali. Un&#39;app può avere un solo gestore di questo tipo. Adobe è consapevole che i suoi clienti potrebbero usare altri provider per la segnalazione di arresti anomali, e ha pertanto deciso di non implementare un gestore `NSException` globale, al fine di evitare errori durante la generazione dell&#39;app.

## Cosa causa la segnalazione di un arresto anomalo falso?

I seguenti scenari possono causare false segnalazioni di arresti anomali da parte dell’SDK:

* Se esegui il debugging con Xcode, il riavvio dell’app mentre questa è in primo piano causa un arresto anomalo.

   >[!TIP]
   >
   >In questo caso, per evitare l&#39;arresto anomalo porta l&#39;app in background prima di avviarla di nuovo da Xcode.

* Se l&#39;app è in background e invia hit Analytics tramite una chiamata diversa da `trackActionFromBackground`, `trackLocation` o `trackBeacon` e l&#39;app viene terminata (manualmente o dal sistema operativo) mentre è in background, all&#39;avvio successivo si verifica un arresto anomalo.

   >[!TIP]
   >
   >L’attività in background che si verifica oltre la soglia `lifecycleTimeout` potrebbe inoltre causare un falso avvio.

* Se l&#39;app viene avviata in background in seguito a un richiamo in background, all&#39;aggiornamento della posizione, e così via, e viene terminata dal sistema operativo senza tornare in primo piano, all&#39;avvio successivo (in background o in primo piano) si verifica un arresto anomalo.
* Se elimini in modo programmatico il flag di pausa di Adobe da `NSUserDefaults` mentre l&#39;app è in background, al prossimo avvio o alla prossima ripresa si verifica un arresto anomalo.

## Come posso evitare la segnalazione di falsi arresti anomali?

Le seguenti procedure possono essere utili per evitare la segnalazione di falsi arresti anomali:

* Nell’SDK per iOS versione 4.8.6, è stato aggiunto del codice per determinare meglio se una nuova sessione del ciclo di vita sia effettivamente desiderata.

   Questo codice corregge i falsi arresti anomali descritti ai punti 2 e 3 della sezione precedente.

* Per evitare il verificarsi del primo tipo di falsi arresti anomali, assicurati di eseguire le attività di sviluppo rispetto alle suite di rapporti non di produzione.
* Non eliminare e non modificare i valori inseriti dall&#39;SDK di Adobe Mobile in `NSUserDefaults`.

   Se tali valori vengono modificati all&#39;esterno dell&#39;SDK, i dati segnalati nei rapporti non saranno validi.
