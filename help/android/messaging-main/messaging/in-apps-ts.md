---
description: Queste informazioni sono utili per risolvere eventuali problemi dei messaggi in-app.
keywords: dispositivi mobili
solution: Experience Cloud Services,Analytics
title: Risoluzione dei problemi di messaggistica in-app
topic-fix: Metrics
uuid: 39c3a21d-92c2-4004-b00f-99b6f91d3696
exl-id: 6c7d97ed-3b0a-48ff-b761-1485aea5e96d
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '519'
ht-degree: 100%

---

# Risoluzione dei problemi di messaggistica in-app {#troubleshooting-in-app-messaging}

Queste informazioni sono utili per risolvere eventuali problemi dei messaggi in-app.

Se hai soddisfatto tutti i requisiti per i messaggi in-app, ma i messaggi non vengono visualizzati, verifica quanto segue:

## La nuova configurazione e il nuovo SDK sono inclusi nell’app?

Verifica che nella configurazione sia presente una sezione relativa alla [Messaggistica in-app](/help/android/messaging-main/messaging/messaging.md) (file JSON scaricato) o di avere un endpoint remoto per i messaggi, in modo che sia possibile recuperarlo dalla gestione dinamica dei tag.

## Il mio messaggio a schermo intero in Android non viene visualizzato. L’SDK utilizzato e la configurazione sono corretti, così come gli attivatori.

Hai aggiornato il file manifesto per definire l’attività a schermo intero?

## Il mio messaggio di notifica locale in Android non funziona.

Assicurati che nel file manifesto sia dichiarato il destinatario della trasmissione della notifica locale. Per ulteriori informazioni, vedi il passaggio 2 in *Abilitazione della messaggistica in-app* in [Messaggistica in-app](/help/android/messaging-main/messaging/messaging.md).

## Il messaggio è attivo?

Per verificare se il messaggio è attivo, passa alla pagina per la gestione dei messaggi in-app e controlla l’elenco dei messaggi nella colonna **[!UICONTROL Stato]**.

## Osserva le impostazioni *mostra una volta*, *mostra sempre*, *mostra offline* nella scheda Pubblico.

Verifica che queste impostazioni siano impostate nel modo desiderato. Nella scheda **[!UICONTROL Pubblico]**, controlla le opzioni **[!UICONTROL Attivatore]**, che consentono di specificare la frequenza con cui viene mostrato il messaggio.

## Se utilizzi un evento di avvio come attivatore...

L’avvio viene attivato solo su una nuova sessione. Per ulteriori informazioni sull&#39;inizio di una sessione, vedi la riga `lifecycleTimeout` nel [file di configurazione JSON](/help/android/configuration/json-config/json-config.md).

## Ho aggiornato il mio messaggio in remoto, ma l&#39;app visualizza ancora il messaggio precedente.

Considerazioni da ricordare:

* Nella gestione dinamica dei tag, l&#39;aggiornamento dell&#39;endpoint con la nuova definizione potrebbe richiedere alcuni minuti. Attendi e riprova.
* La configurazione verrà aggiornata solo al successivo avvio. Se l&#39;app è stata riavviata entro il periodo di timeout della sessione del ciclo di vita, è possibile che la nuova configurazione non sia stata scaricata.

Per ulteriori informazioni, vedi [Metriche del ciclo di vita](/help/android/metrics.md).

## L’immagine non rientra esattamente nello spazio disponibile nel modello.

Il modello a schermo intero per i messaggi in-app supporta la visualizzazione di un’immagine da un server remoto (URL immagine) o dal pacchetto dell’app (immagine nel pacchetto). L&#39;immagine deve essere in un formato grafico standard, ad esempio JPG, GIF o PNG. Poiché gli schermi dei dispositivi hanno dimensioni diverse, è probabile che l&#39;immagine non rientri perfettamente nello spazio disponibile nel modello. Nel modello viene data precedenza al centro dell&#39;immagine; se questa non rientra completamente, i lati vengono ritagliati (per le immagini in verticale) o sfumati (per le immagini in orizzontale).

Regole di posizionamento e dimensionamento per ciascun orientamento:

* **Verticale**
   * Altezza di 195 pixel per telefoni.
   * Altezza di 529 pixel per tablet.
   * Centrata se la larghezza dell’immagine è inferiore alla larghezza del dispositivo.
   * Ritagliata se la larghezza dell’immagine è maggiore della larghezza del dispositivo.

* **Orizzontale**
   * L’immagine viene ridimensionata al 100% dell’altezza del dispositivo.
   * La larghezza è pari al 75% del dispositivo, con una dissolvenza a destra.
   In caso di problemi con il modello a schermo intero, puoi scaricare e utilizzare il modello HTML personalizzato. Questo modello offre maggiore flessibilità per le immagini e consente il controllo completo del modello.
