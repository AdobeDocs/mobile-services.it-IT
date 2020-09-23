---
description: Queste informazioni sono utili per risolvere eventuali problemi dei messaggi in-app.
keywords: mobile
seo-description: Queste informazioni sono utili per risolvere eventuali problemi dei messaggi in-app.
seo-title: Risoluzione dei problemi dei messaggi in-app
solution: Experience Cloud,Analytics
title: Risoluzione dei problemi dei messaggi in-app
topic: Metrics
uuid: 58533aa3-2eb2-4597-8525-77e4e5975e56
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '595'
ht-degree: 100%

---


# Risoluzione dei problemi dei messaggi in-app {#troubleshooting-in-app-messaging}

Queste informazioni sono utili per risolvere eventuali problemi dei messaggi in-app.

Se hai soddisfatto tutti i requisiti per i messaggi in-app, ma i messaggi non vengono visualizzati, verifica quanto segue:

## La nuova configurazione e il nuovo SDK sono inclusi nell&#39;app?

Verifica che la versione dell’SDK sia 4.2 o successiva e che sia configurata correttamente. Assicurati che nella configurazione sia presente una sezione `Messages` (file JSON scaricato) o di disporre di un endpoint remoto per i messaggi, in modo che sia possibile recuperarlo dalla gestione dinamica dei tag.

## Il mio messaggio a schermo intero in Android non viene visualizzato. L’SDK utilizzato e la configurazione sono corretti, così come gli attivatori.

Hai aggiornato il file manifesto per definire l’attività a schermo intero?

## Il mio messaggio di notifica locale in Android non funziona.

Assicurati che nel file manifesto sia dichiarato il destinatario della trasmissione della notifica locale. Per ulteriori informazioni, vedi il passaggio 2 in [Abilitare la messaggistica in-app](/help/android/messaging-main/messaging/messaging.md).

## Il messaggio è attivo?

Verifica che sia attivo controllando la visualizzazione elenco della pagina Gestisci messaggi in-app, nella colonna Stato.

## Osserva le impostazioni *mostra una volta*, *mostra sempre*, *mostra offline* nella scheda Pubblico.

Verifica che queste impostazioni siano impostate nel modo desiderato. Nella scheda **[!UICONTROL Pubblico]**, controlla le opzioni **[!UICONTROL Attivatore]**, che consentono di specificare la frequenza con cui viene mostrato il messaggio.

## Se utilizzi l’evento di avvio come attivatore...

L’avvio viene attivato solo su una nuova sessione. Per ulteriori informazioni sull&#39;inizio di una sessione, vedi la riga `lifecycleTimeout` nel file di configurazione JSON. Per ulteriori informazioni, vedi [File di configurazione ADBMobile JSON](/help/ios/configuration/json-config/json-config.md).

## Ho aggiornato il mio messaggio in remoto, ma l’app visualizza ancora il messaggio precedente.

Completa una delle seguenti attività:

* Nella gestione dinamica dei tag, l&#39;aggiornamento dell&#39;endpoint con la nuova definizione potrebbe richiedere alcuni minuti.

   Attendi e riprova.

* La configurazione verrà aggiornata solo al successivo avvio.
Se l&#39;app è stata riavviata entro il periodo di timeout della sessione del ciclo di vita, è possibile che la nuova configurazione non sia stata scaricata.

   Per ulteriori informazioni, vedi [Metriche del ciclo di vita](/help/ios/metrics.md).

## La mia immagine non rientra esattamente nello spazio disponibile nel modello.

Il modello a schermo intero per i messaggi in-app supporta la visualizzazione di un’immagine da un server remoto (URL immagine) o dal pacchetto dell’app (immagine nel pacchetto). L&#39;immagine deve essere in un formato grafico standard, ad esempio JPG, GIF o PNG.

Poiché gli schermi dei dispositivi hanno dimensioni diverse, è probabile che l&#39;immagine non rientri perfettamente nello spazio disponibile nel modello. Nel modello viene data precedenza al centro dell&#39;immagine; se questa non rientra completamente, i lati vengono ritagliati (per le immagini in verticale) o sfumati (per le immagini in orizzontale).

Regole di posizionamento e dimensionamento per ciascun orientamento:

* **Verticale**:
   * Altezza di 195 pixel per telefoni
   * Altezza di 529 pixel per tablet
   * Centrata se la larghezza dell’immagine è inferiore alla larghezza del dispositivo.
   * Ritagliata se la larghezza dell’immagine è maggiore della larghezza del dispositivo.

* **Orizzontale**:
   * L’immagine viene ridimensionata al 100% dell’altezza del dispositivo.
   * La larghezza è pari al 75% del dispositivo, con una dissolvenza a destra.

In caso di problemi con il modello a schermo intero, puoi scaricare e utilizzare il modello HTML personalizzato. Questo modello offre maggiore flessibilità per le immagini e consente il controllo completo del modello.

## I messaggi in-app su un iPhone X non vengono visualizzati in modalità a schermo intero.

Per visualizzare i messaggi in-app in modalità a schermo intero su un iPhone X:

1. Aggiungi `viewport-fit=cover` nel tag meta.

   ```html
   <meta name="viewport" content="viewport-fit=cover">
   ```

1. Configura una spaziatura interna appropriata nel CSS per l’elemento dell’interfaccia utente principale, ad esempio:

   ```html
    topelement {
      padding-top:20px;
      /*Status bar height on iOS 11.0*/
      padding-top:constant(safe-area-inset-top);
      /*Status bar height on iOS 11+ */
      padding-top:env(safe-area-inset-top);
      } 
   ```

   Queste impostazioni impediscono agli elementi dell’interfaccia utente di entrare in conflitto con la barra di stato.
