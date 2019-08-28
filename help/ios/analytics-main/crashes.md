---
description: Queste informazioni sono utili per capire come vengono tracciati gli arresti anomali dell'app e quali best practice adottare per gestire i falsi arresti anomali.
seo-description: Queste informazioni sono utili per capire come vengono tracciati gli arresti anomali dell'app e quali best practice adottare per gestire i falsi arresti anomali.
seo-title: Tenere traccia degli arresti anomali delle app
solution: Marketing Cloud, Analytics
title: Tracciare gli arresti anomali dell'app
topic: Sviluppatore e implementazione
uuid: 4 f 81988 b -198 a -4 ba 9-ad 53-78 af 90 e 43856
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Track app crashes {#track-app-crashes}

Queste informazioni sono utili per capire come vengono tracciati gli arresti anomali dell'app e quali best practice adottare per gestire i falsi arresti anomali.

>[!IMPORTANT]
>
>È necessario effettuare l'aggiornamento alla versione 4.8.6 dell'SDK per iOS, contenente modifiche importanti che impediscono la segnalazione di falsi arresti anomali.

## Quando viene segnalato un arresto anomalo?

Se l'applicazione viene terminata senza prima passare in background, l'SDK segnala un arresto anomalo al successivo avvio dell'app.

## Come funziona la segnalazione di arresti anomali?

iOS usa le notifiche di sistema che permettono agli sviluppatori di tenere traccia e rispondere a diversi stati ed eventi nel ciclo di vita dell'applicazione.

L'SDK di Adobe Mobile per iOS ha un gestore di notifiche che risponde alla notifica `UIApplicationDidEnterBackgroundNotification`. In questo codice, viene impostato un valore che indica che l'app è stata messa in background dall'utente. Al successivo avvio, se tale valore non viene trovato, viene segnalato un arresto anomalo.

## Perché Adobe misura gli arresti anomali in questo modo?

Questo approccio fornisce una risposta di alto livello alla domanda *L'utente è uscito intenzionalmente dall'app?*

Le librerie per la segnalazione di arresti anomali fornite da aziende come Apteligent (già Crittercism) usano un gestore `NSException` globale per fornire informazioni più dettagliate sugli arresti anomali. Un'app può avere un solo gestore di questo tipo. Adobe è consapevole che i suoi clienti potrebbero usare altri provider per la segnalazione di arresti anomali, e ha pertanto deciso di non implementare un gestore `NSException` globale, al fine di evitare errori durante la generazione dell'app.

## Cosa causa la segnalazione di un arresto anomalo falso?

Nelle seguenti condizioni, l'SDK può segnalare falsi arresti anomali:

* Se esegui il debug con Xcode, si verifica un arresto anomalo quando si avvia di nuovo l'app mentre questa è in esecuzione in primo piano.

   >[!TIP]
   >
   >In questo scenario, in background potete evitare un arresto anomalo prima di avviare nuovamente l'app da Xcode.

* If your app is in the background and sends Analytics hits through a call other than `trackActionFromBackground`, `trackLocation`, or `trackBeacon`, and the app is terminated (manually or by the OS) while in the background, and the next launch will be a crash.

   >[!TIP]
   >
   >Background activity that occurs beyond the `lifecycleTimeout` threshold might also result in an additional false launch.

* Se l'app viene avviata in background in seguito a un richiamo in background, all'aggiornamento della posizione, e così via, e viene terminata dal sistema operativo senza tornare in primo piano, all'avvio successivo (in background o in primo piano) si verifica un arresto anomalo.
* Se elimini in modo programmatico il flag di pausa di Adobe da `NSUserDefaults` mentre l'app è in background, al prossimo avvio o alla prossima ripresa si verifica un arresto anomalo.

## Come posso evitare la segnalazione di falsi arresti anomali?

Le pratiche descritte di seguito permettono di evitare la segnalazione di falsi arresti anomali:

* Nell'SDK per iOS versione 4.8.6, è stato aggiunto del codice che consente di determinare meglio se una nuova sessione del ciclo di vita sia effettivamente desiderata.

   Questo codice corregge i casi di falsi arresti anomali descritti nella sezione precedente ai punti 2 e 3.

* Assicurati di eseguire le operazioni di sviluppo con suite di report non destinate alla versione di produzione, per evitare il caso di falsi allarmi descritto al punto 1.
* Non eliminare e non modificare i valori inseriti dall'SDK di Adobe Mobile in `NSUserDefaults`.

   Se tali valori vengono modificati al di fuori dell'SDK, i dati segnalati non saranno validi.

