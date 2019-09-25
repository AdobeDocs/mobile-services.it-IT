---
description: Queste informazioni sono utili per risolvere eventuali problemi dei messaggi in-app.
keywords: dispositivi mobili
seo-description: Queste informazioni sono utili per risolvere eventuali problemi dei messaggi in-app.
seo-title: Risoluzione dei problemi dei messaggi in-app
solution: Marketing Cloud,Analytics
title: Risoluzione dei problemi dei messaggi in-app
topic: Metrics (Metriche)
uuid: 39c3a21d-92c2-4004-b00f-99b6f91d3696
translation-type: tm+mt
source-git-commit: 12e01e112debffd877dd62f1fd2505724b2aae7d

---


# Risoluzione dei problemi dei messaggi in-app{#troubleshooting-in-app-messaging}

Queste informazioni sono utili per risolvere eventuali problemi dei messaggi in-app.

Se hai completato tutti i requisiti relativi ai messaggi in-app, ma i messaggi non vengono visualizzati, verifica i seguenti elementi:

## La nuova configurazione e il nuovo SDK sono inclusi nell'app?

Ensure that you have an [In-App Messaging](/help/android/messaging-main/messaging/messaging.md) section in your configuration (downloaded JSON file) or have a Messages remote endpoint, so that it can be retrieved from dynamic tag management.

## In Android il mio messaggio a schermo intero non viene visualizzato. L'SDK utilizzato e la configurazione sono corretti, così come gli attivatori.

Hai aggiornato il file manifesto per definire l'attività a schermo intero?

## Il mio messaggio di notifica locale in Android non funziona.

Assicurati che nel file manifesto sia dichiarato il destinatario della trasmissione della notifica locale. For more information, see step 2 in *Enabling In-App Messaging* in [In-App Messaging](/help/android/messaging-main/messaging/messaging.md).

## Il messaggio è attivo?

Per verificare se il messaggio è attivo, nella pagina Gestisci messaggi in-app, nella colonna **Stato**, controlla l'elenco dei messaggi.

## Osservare *la visualizzazione una volta*, *mostrare sempre*, *mostrare le impostazioni offline* nella scheda Pubblico.

Verifica che queste impostazioni siano impostate nel modo desiderato. Nella scheda **[!UICONTROL Pubblico]**, controlla le opzioni **Attivatore], che consentono di specificare la frequenza con cui viene mostrato il messaggio.[!UICONTROL **

## Se si utilizza un evento di avvio come trigger...

L'avvio viene attivato solo su una nuova sessione. Per ulteriori informazioni sull'inizio di una sessione, vedi la riga `lifecycleTimeout` nel [file di configurazione JSON](/help/android/configuration/json-config/json-config.md).

## Ho aggiornato il mio messaggio in remoto, ma l'app visualizza ancora il messaggio precedente.

Considerazioni da ricordare:

* Per l'aggiornamento dell'endpoint della gestione tag dinamica con la nuova definizione potrebbero essere necessari alcuni minuti. Attendi e riprova.
* La configurazione verrà aggiornata solo con il nuovo avvio. Se l'app è stata riavviata entro il periodo di timeout della sessione del ciclo di vita, è possibile che la nuova configurazione non sia stata scaricata.

Per ulteriori informazioni, vedi [Metriche del ciclo di vita](/help/android/metrics.md).

## La mia immagine non rientra esattamente nello spazio disponibile nel modello.

Il modello a schermo intero per i messaggi in-app supporta la visualizzazione di un'immagine da un server remoto (URL immagine) o dal pacchetto dell'app (immagine nel pacchetto). L'immagine deve essere in un formato grafico standard, ad esempio JPG, GIF o PNG. Poiché gli schermi dei dispositivi hanno dimensioni diverse, è probabile che l'immagine non rientri perfettamente nello spazio disponibile nel modello. Nel modello viene data precedenza al centro dell'immagine; se questa non rientra completamente, i lati vengono ritagliati (per le immagini in verticale) o sfumati (per le immagini in orizzontale).

Regole di posizionamento e dimensionamento per ciascun orientamento:

* **Verticale**
   * Altezza di 195 pixel per telefoni.
   * Altezza di 529 pixel per tablet.
   * Centrata se la larghezza dell'immagine è inferiore alla larghezza del dispositivo.
   * Ritagliata se la larghezza dell'immagine è superiore alla larghezza del dispositivo.

* **Orizzontale**
   * Immagine ridimensionata al 100% dell'altezza del dispositivo.
   * Larghezza pari al 75% del dispositivo, con dissolvenza verso i bordi a destra.
   In caso di problemi con il modello a schermo intero, prova a scaricare e usare il modello HTML personalizzato. Questo offre maggiore flessibilità per le immagini e permette di controllare ogni aspetto del modello.

