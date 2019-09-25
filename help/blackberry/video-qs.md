---
description: Il processo generale da seguire per la misurazione del video è molto simile per tutte le piattaforme AppMeasurement. Questa sezione fornisce una panoramica di base delle attività di sviluppo, con esempi di codice.
seo-description: Il processo generale da seguire per la misurazione del video è molto simile per tutte le piattaforme AppMeasurement. Questa sezione fornisce una panoramica di base delle attività di sviluppo, con esempi di codice.
seo-title: Analisi del video
title: Analisi del video
uuid: 0d2731f3-77a9-4db1-9a8c-1e56c212ecb4
translation-type: tm+mt
source-git-commit: 5fbba02eb61679344f638b6465e47b0d9ae5a988

---


# Analisi del video {#video-analytics}

Il processo generale da seguire per la misurazione del video è molto simile per tutte le piattaforme AppMeasurement. Questa sezione fornisce una panoramica di base delle attività di sviluppo, con esempi di codice.

Per ulteriori informazioni sulla misurazione dei video, consultate la guida [Misurazione audio e video nella guida di Adobe Analytics](https://docs.adobe.com/content/help/en/media-analytics/using/media-overview.html) .  Nella tabella seguente sono elencati i dati multimediali inviati ad Analytics. Utilizza le regole di elaborazione per mappare i dati di contesto della colonna "Variabile dati di contesto" su una variabile di Analytics, come descritto nella colonna "Tipo di variabile".

## Mappare gli eventi del lettore alle variabili di Analytics

* **a.media.name**

   (Obbligatorio) Raccoglie il nome del video, in base a quanto specificato nell’implementazione, quando un visitatore visualizza il video in qualche modo. Per questa variabile puoi aggiungere delle classificazioni.

   **(Facoltativo)** La variabile Custom Insight fornisce informazioni sul percorso del video.

   * Nome variabile: eVar
      * Scadenza predefinita: visita
      * Insight personalizzato (s.prop, usato per il percorso del video)

* **a.media.name**

   (**Facoltativo**) Fornisce informazioni sul percorso del video. Il percorso deve essere abilitato per questa variabile da ClientCare.

   * Tipo evento: Insight personalizzato (s.prop)
   * Insight personalizzato (s.prop)

* **a.media.segment**

   (**Obbligatorio**) Raccoglie dati sui segmenti video, tra cui il nome del segmento e l'ordine in cui il segmento appare nel video. Quando viene eseguito il tracciamento automatico degli eventi del lettore, questa variabile viene compilata abilitando la variabile `segmentByMilestones`. Quando gli eventi del lettore vengono tracciati manualmente, viene compilata impostando un nome di segmento personalizzato.

   For example, when a visitor views the first segment in a video, SiteCatalyst might collect `1:M:0-25` in the Segments eVar. Il metodo di raccolta dei dati video predefinito raccoglie i dati ai punti di inizio video (riproduzione), inizio segmento e fine video (arresto).

   Analytics conta la visualizzazione del primo segmento all'inizio del segmento, quando il visitatore inizia la visualizzazione. Il segmento successivo viene visualizzato quando inizia il segmento.

   * Tipo di variabile: eVar
   * Scadenza predefinita: visualizzazioni pagina

* **a.contentType**

   Raccoglie dati relativi al tipo di contenuto visualizzato da un visitatore. Agli hit inviati dalla misurazione video è assegnato il tipo di contenuto “video”. Non è necessario riservare questa variabile esclusivamente al tracciamento video. Se la stessa variabile viene usata anche per ottenere il tipo di altri contenuti, è possibile analizzare la distribuzione dei visitatori per diversi tipi di contenuto. Ad esempio, puoi usare questa variabile per assegnare valori quali "articolo" o "pagina prodotto" ad altri tipi di contenuti. Dal punto di vista della misurazione dei video, il tipo di contenuto permette di individuare i visitatori che guardano un video e quindi calcolare i tassi di conversioni derivanti dal video.

   * Tipo di variabile: eVar
   * Scadenza predefinita: visualizzazioni pagina

* **a.media.timePlayed**

   Conta il tempo, in secondi, trascorso a guardare un video dall'ultimo processo di raccolta di dati (richiesta immagine).

   * Tipo di variabile: Evento
   * Tipo: contatore

* **a.media.view**

   Indica che un visitatore ha visualizzato una parte di un video. Tuttavia, non fornisce informazioni sulla parte specifica visualizzata, né sulla durata della visualizzazione.

   * Tipo di variabile: Evento
   * Tipo: contatore

* **a.media.segmentView**

   Indica che un visitatore ha visualizzato una parte di un segmento video. Tuttavia, non fornisce informazioni sulla parte specifica visualizzata, né sulla durata della visualizzazione.

   * Tipo di variabile: Evento
   * Tipo: contatore

* **a .media.complete**

   Indica che un utente ha visualizzato un video completo. Per impostazione predefinita, l'evento completo è misurato 1 secondo prima della fine del video. Durante l’implementazione, puoi specificare quanti secondi dalla fine del video considerare come una visualizzazione dell’intero video. Per i video in diretta e altri flussi che non hanno una fine definita, puoi specificare un punto personalizzato per misurare il completamento. Ad esempio, dopo un tempo di visualizzazione specifico.

   * Tipo di variabile: Evento
   * Tipo: contatore

## Track player events {#section_C7F43AECBC0D425390F7FCDF3035B65D}

To measure video playback, The `mediaPlay`, `mediaStop`, and `mediaClose` methods need to be called at the appropriate times. Ad esempio, `mediaStop` deve essere invocato quando il lettore viene messo in pausa e `mediaPlay` quando la riproduzione viene avviata o ripresa.

## Media measurement class and method reference {#section_50DF9359A7B14DF092634C8E913C77FE}

* **open**

   Apre un video per il tracciamento.

   * Di seguito è riportata la sintassi per questo metodo:

      ```cpp
      void open(QString name, double length, QString playerName, QString playerID = QString()); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```cpp
        ADBMediaAnalytics::sharedInstance()->open("name", 10.0, "playerName", "playerID"); 
      ```

* **openAd**

   Apre un oggetto `MediaSettings` per il tracciamento.

   * Di seguito è riportata la sintassi per questo metodo:

      ```cpp
      void openAd(QString name, double length, QString playerName, QString parentName, QString parentPod, double parentPodPosition, QString CPM); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```cpp
      ADBMediaAnalytics::sharedInstance()->openAd("name", 10, "playerName", "parentName", "podName", 0, "CPM"); 
      ```

* **close**

   Chiude l'elemento multimediale denominato *`name`*.

   * Di seguito è riportata la sintassi per questo metodo:

      ```cpp
      void close(QString name);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```cpp
      ADBMediaAnalytics::sharedInstance()->close("name");
      ```

* **play**

   Plays the media item named *`name`* at the given *`offset`* (in seconds).

   * Di seguito è riportata la sintassi per questo metodo:

      ```cpp
      void play(QString name, double offset);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```cpp
      ADBMediaAnalytics::sharedInstance()->play("name", 0); 
      ```

* **completato**

   Contrassegna manualmente l'elemento multimediale come completato in corrispondenza dell'*`offset`indicato (in secondi).*

   * Di seguito è riportata la sintassi per questo metodo:

      ```cpp
      void complete(QString name, double offset);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```cpp
      ADBMediaAnalytics::sharedInstance()->complete("name", 0);
      ```

* **stop**

   Notifica al modulo multimediale che il video è stato interrotto o messo in pausa in corrispondenza dell'*offset* indicato.

   * Di seguito è riportata la sintassi per questo metodo:

      ```cpp
      stop(QString name, double offset);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```cpp
      ADBMediaAnalytics::sharedInstance()->stop("name", 0);
      ```

* **click**

   Notifica al modulo multimediale l'avvenuto clic sull'elemento multimediale.

   * Di seguito è riportata la sintassi per questo metodo:

      ```cpp
      void click(QString name, double offset);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```cpp
      ADBMediaAnalytics::sharedInstance()->close("name", 0);
      ```

* **Codice**

   Invia una chiamata Track Action (senza visualizzazioni pagina) per lo stato corrente dell'elemento multimediale.

   * Di seguito è riportata la sintassi per questo metodo:

      ```cpp
      track(QString name, QHash<QString, QString> additionalData = QHash<QString, QString>()); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```cpp
      ADBMediaAnalytics::sharedInstance()->track("name", null);
      ```
