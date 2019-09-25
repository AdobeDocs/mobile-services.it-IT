---
description: Queste informazioni possono essere utili per risolvere eventuali problemi dei messaggi in-app.
keywords: dispositivi mobili
seo-description: Queste informazioni possono essere utili per risolvere eventuali problemi dei messaggi in-app.
seo-title: Risoluzione dei problemi dei messaggi in-app
solution: Marketing Cloud,Analytics
title: Risoluzione dei problemi dei messaggi in-app
topic: Metrics (Metriche)
uuid: 8813e8d8-bb1e-46ad-83cd-98ae68f73ce6
translation-type: tm+mt
source-git-commit: e9691f9cbeadd171948aa752b27a014c3ab254d6

---


# Troubleshooting in-app messaging{#troubleshooting-in-app-messaging}

Queste informazioni possono essere utili per risolvere eventuali problemi dei messaggi in-app.

Se hai soddisfatto tutti i requisiti per la messaggistica in-app ma i messaggi non vengono visualizzati, verifica quanto segue:

## La nuova configurazione e il nuovo SDK sono inclusi nell'app?

* Verifica che la versione dell'SDK sia 4.2 o successiva e che sia configurata correttamente.

* Ensure that you have a [Messaging](/help/using/in-app-messaging/in-app-messaging.md) section in your configuration (the downloaded JSON file) or have a Messages remote endpoint, so that it can be retrieved from dynamic tag management.

## In Android il mio messaggio a schermo intero non viene visualizzato. L'SDK utilizzato e la configurazione sono corretti, così come gli attivatori.

Hai aggiornato il file manifesto per definire l'attività a schermo intero?

## Il mio messaggio di notifica locale in Android non funziona.

Verifica che nel file manifesto sia dichiarato il destinatario della trasmissione della notifica locale. For more information, see step #1 in [In-app messaging](/help/android/messaging-main/messaging/messaging.md).

## Il messaggio è attivo?

Nella vista a elenco della colonna **[!UICONTROL Stato]**, nella pagina Manage In-App Message (Gestisci messaggio in-app), verifica che il messaggio sia attivo.

## Look at show once, show always, show offline settings on the Audience page.******

Verifica che le seguenti impostazioni siano corrette. Nella pagina Pubblico, controlla le opzioni della scheda **Attivatore**, che consentono di specificare la frequenza con cui viene visualizzato il messaggio.

## Se utilizzi l'evento di avvio come attivatore...

L'avvio viene attivato solo su una nuova sessione. Per informazioni su quando ha inizio una sessione, vedi  in the ADBMobile JSON config file.`lifecycleTimeout`[](/help/ios/configuration/json-config/json-config.md)

## Ho aggiornato il mio messaggio in remoto, ma l'app visualizza ancora il messaggio precedente.

Completa una delle seguenti attività:

* Per l'aggiornamento dell'endpoint della gestione tag dinamica con la nuova definizione potrebbero essere necessari alcuni minuti.

   Attendi qualche minuto e poi riprova.

* La configurazione verrà aggiornata solo al successivo avvio.

   Se l'app è stata riavviata entro il periodo di timeout della sessione del ciclo di vita, è possibile che la nuova configurazione non sia stata scaricata.

## La mia immagine non rientra esattamente nello spazio disponibile nel modello.

Il modello a schermo intero per i messaggi in-app supporta la visualizzazione di un'immagine da un server remoto (URL immagine) o dal pacchetto dell'app (immagine nel pacchetto). L'immagine deve essere in un formato grafico standard, ad esempio JPG, GIF o PNG.

Poiché gli schermi dei dispositivi hanno dimensioni diverse, è probabile che l'immagine non rientrerà perfettamente nello spazio disponibile nel modello. Se l'immagine non rientra completamente nello spazio disponibile, il modello ne mette a fuoco sempre il centro e ritaglia (orientamento verticale) o sfoca (orientamento orizzontale) i lati.

Regole di posizionamento e dimensionamento per ciascun orientamento:

* **Verticale:** l'immagine viene ridimensionata (fino a un'altezza di 195 px per un telefono, 529 px per un tablet) e centrata (se la larghezza dell'immagine è inferiore a quella del dispositivo) o ritagliata (se la larghezza dell'immagine è maggiore di quella del dispositivo).

* **Orizzontale:** l'immagine viene ridimensionata al 100% dell'altezza del dispositivo, con una larghezza corrispondente al 75% del dispositivo e una dissolvenza sul lato destro.

   In caso di problemi con il modello a schermo intero, prova a scaricare e usare il modello HTML personalizzato. Questo offre maggiore flessibilità per le immagini e permette di controllare ogni aspetto del modello.

## I miei messaggi non riflettono le modifiche e gli aggiornamenti che ho apportato nell'interfaccia.

L'SDK richiama i messaggi nuovi e aggiornati al momento dell'avvio di un ciclo di vita. Ciò si verifica solo quando l'applicazione viene chiusa o lasciata in background per un periodo di tempo maggiore del valore di timeout del ciclo di vita, e quindi riaperta.

Completa i seguenti passaggi:

1. Curl your messages URL in your config file to verify the remote message is updated (for example, )`curl "https://assets.adobedtm.com/b213090c5204bf94318f4ef0539a38b487d10368/scripts/satellite-542c62859662383b1a0008f4.json"`
1. Chiudi l'applicazione.
1. Wait for a time period that is longer than the `lifecycleTimeout` in the config file.
1. Apri l'app, vai nel punto in cui dovrebbe essere visualizzato il messaggio e verifica che sia stato aggiornato.