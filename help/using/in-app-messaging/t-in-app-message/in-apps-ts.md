---
description: Queste informazioni possono essere utili per risolvere eventuali problemi dei messaggi in-app.
keywords: dispositivi mobili
seo-description: Queste informazioni possono essere utili per risolvere eventuali problemi dei messaggi in-app.
seo-title: Risoluzione dei problemi dei messaggi in-app
solution: Experience Cloud,Analytics
title: Risoluzione dei problemi dei messaggi in-app
topic-fix: Metrics
uuid: 8813e8d8-bb1e-46ad-83cd-98ae68f73ce6
exl-id: 6be5beef-3bde-49f8-9ec0-c5d32bd43045
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '638'
ht-degree: 100%

---

# Risoluzione dei problemi dei messaggi in-app {#troubleshooting-in-app-messaging}

Informazioni utili per risolvere eventuali problemi dei messaggi in-app.

Se hai soddisfatto tutti i requisiti per i messaggi in-app, ma i messaggi non vengono visualizzati, verifica quanto segue:

## La nuova configurazione e il nuovo SDK sono inclusi nell’app?

* Verifica che la versione dell’SDK sia 4.2 o successiva e che sia configurata correttamente.

* Inoltre devi verificare che nella configurazione sia presente una sezione relativa ai [Messaggistica](/help/using/in-app-messaging/in-app-messaging.md) (il file JSON scaricato) o di avere un endpoint remoto per i messaggi, in modo che sia possibile recuperarlo dalla gestione dinamica dei tag.

## Il mio messaggio a schermo intero in Android non viene visualizzato. L’SDK utilizzato e la configurazione sono corretti, così come gli attivatori.

Hai aggiornato il file manifesto per definire l’attività a schermo intero?

## Il mio messaggio di notifica locale in Android non funziona.

Verifica che nel file manifesto sia dichiarato il destinatario della trasmissione della notifica locale. Per ulteriori informazioni, vedi il passaggio 1 in [Abilitare i messaggi in-app](/help/android/messaging-main/messaging/messaging.md).

## Il messaggio è attivo?

Nella vista a elenco della colonna **[!UICONTROL Stato]**, nella pagina Gestione messaggio in-app, verifica che il messaggio sia attivo.

## Osserva *mostra una volta*, *mostra sempre*, *mostra offline* sulla pagina Pubblico.

Verifica che le seguenti impostazioni siano corrette. Nella pagina Pubblico, controlla le opzioni della scheda **[!UICONTROL Attivatore]**, che consentono di specificare la frequenza con cui viene visualizzato il messaggio.

## Se utilizzi l’evento di avvio come attivatore...

L’avvio viene attivato solo su una nuova sessione. Per informazioni su quando ha inizio una sessione, vedi   `lifecycleTimeout` nel [file di configurazione ADBMobile JSON](/help/ios/configuration/json-config/json-config.md).

## Ho aggiornato il mio messaggio in remoto, ma l’app visualizza ancora il messaggio precedente.

Completa una delle seguenti attività:

* Per l’aggiornamento dell’endpoint della gestione tag dinamica con la nuova definizione potrebbero essere necessari alcuni minuti.

   Attendi e riprova.

* La configurazione verrà aggiornata solo al successivo avvio.

   Se l’app è stata riavviata entro il periodo di timeout della sessione del ciclo di vita, è possibile che la nuova configurazione non sia stata scaricata.

## L’immagine non rientra esattamente nello spazio disponibile nel modello.

Il modello a schermo intero per i messaggi in-app supporta la visualizzazione di un’immagine da un server remoto (URL immagine) o dal pacchetto dell’app (immagine nel pacchetto). L’immagine deve essere in un formato grafico standard, ad esempio JPG, GIF o PNG.

Poiché gli schermi dei dispositivi hanno dimensioni diverse, è probabile che l’immagine non rientrerà perfettamente nello spazio disponibile nel modello. Se l’immagine non rientra completamente nello spazio disponibile, il modello ne mette a fuoco sempre il centro e ritaglia (orientamento verticale) o sfoca (orientamento orizzontale) i lati.

Regole di posizionamento e dimensionamento per ciascun orientamento:

* **Verticale:** l’immagine viene ridimensionata (fino a un’altezza di 195 px per un telefono, 529 px per un tablet) e centrata (se la larghezza dell’immagine è inferiore a quella del dispositivo) o ritagliata (se la larghezza dell’immagine è maggiore di quella del dispositivo).

* **Orizzontale:** l’immagine viene ridimensionata al 100% dell’altezza del dispositivo, con una larghezza corrispondente al 75% del dispositivo e una dissolvenza sul lato destro.

   In caso di problemi con il modello a schermo intero, puoi scaricare e utilizzare il modello HTML personalizzato. Questo modello offre maggiore flessibilità per le immagini e consente il controllo completo del modello.

## I miei messaggi non riflettono le modifiche e gli aggiornamenti che ho apportato nell’interfaccia.

L’SDK richiama i messaggi nuovi e aggiornati al momento dell’avvio di un ciclo di vita. Ciò si verifica solo quando l’applicazione viene chiusa o lasciata in background per un periodo di tempo maggiore del valore di timeout del ciclo di vita, e quindi riaperta.

Completa i seguenti passaggi:

1. Per verificare che il messaggio remoto venga aggiornato, effettua un codice curl nell’URL del messaggio nel file di configurazione (ad esempio, `curl "https://assets.adobedtm.com/b213090c5204bf94318f4ef0539a38b487d10368/scripts/satellite-542c62859662383b1a0008f4.json"`)
1. Chiudi l’applicazione.
1. Attendi per un intervallo di tempo più lungo di `lifecycleTimeout` contenuto nel file di configurazione.
1. Apri l’app, vai nel punto in cui dovrebbe essere visualizzato il messaggio e verifica che sia stato aggiornato.
