---
description: Il processo generale da seguire per la misurazione dei video è molto simile per tutte le piattaforme AppMeasurement. Questa sezione fornisce una panoramica di base delle attività di sviluppo, con esempi di codice.
title: Analisi dei video
uuid: 0d2731f3-77a9-4db1-9a8c-1e56c212ecb4
exl-id: 90da1a9e-2faa-429c-969e-869ebedf08cc
source-git-commit: d1ebb2bbc4742f5288f90a90e977d252f3f30aa3
workflow-type: tm+mt
source-wordcount: '835'
ht-degree: 65%

---

# Analisi dei video {#video-analytics}

Il processo generale da seguire per la misurazione dei video è molto simile per tutte le piattaforme AppMeasurement. Questa sezione fornisce una panoramica di base delle attività di sviluppo, con esempi di codice.

Per ulteriori informazioni sulla misurazione dei video, consulta la guida [Misurazione dei contenuti multimediali in streaming in Adobe Analytics](https://experienceleague.adobe.com/docs/media-analytics/using/media-overview.html?lang=it) .  Nella tabella seguente sono elencati i dati multimediali inviati ad Analytics. Utilizza le regole di elaborazione per mappare i dati contestuali della colonna Variabile dati di contesto su una variabile Analytics come descritto nella colonna Tipo di variabile .

## Mappare gli eventi del lettore sulle variabili di Analytics

* **a.media.name**

   (Obbligatorio) Raccoglie il nome del video, come specificato nell’implementazione, quando un visitatore visualizza il video in qualche modo. Puoi aggiungere classificazioni per questa variabile.

   **(Facoltativo)** La variabile Custom Insight fornisce informazioni sul percorso del video.

   * Nome della variabile: eVar
      * Scadenza predefinita: visita
      * Custom Insight (s.prop, utilizzato per il percorso del video)

* **a.media.name**

   (**Facoltativo**) Fornisce informazioni sul percorso del video. Il percorso deve essere abilitato per questa variabile dall’assistenza clienti.

   * Tipo evento: Custom Insight (s.prop)
   * Custom Insight (s.prop)

* **a.media.segment**

   (**Obbligatorio**) Raccoglie dati sui segmenti video, tra cui il nome del segmento e l’ordine in cui il segmento appare nel video. Quando viene eseguito il tracciamento automatico degli eventi del lettore, questa variabile viene compilata abilitando la variabile `segmentByMilestones`. Quando gli eventi del lettore vengono tracciati manualmente, viene compilata impostando un nome di segmento personalizzato.

   Ad esempio, quando un visitatore visualizza il primo segmento di un video, il SiteCatalyst potrebbe raccogliere `1:M:0-25` nell’eVar Segmenti. Il metodo di raccolta dei dati video predefinito raccoglie i dati ai punti di inizio (riproduzione) del video, inizio del segmento e fine del video (arresto).

   Analytics conta la visualizzazione del primo segmento all’inizio del segmento, quando il visitatore inizia a guardarlo. Le visualizzazioni dei segmenti successivi vengono contate quando ogni inizia ogni segmento.

   * Tipo di variabile: eVar
   * Scadenza predefinita: visualizzazioni pagina

* **a.contentType**

   Raccoglie dati sul tipo di contenuto visualizzato da un visitatore. Agli hit inviati dalla misurazione video è assegnato il tipo di contenuto &quot;video&quot;. Questa variabile non è riservata esclusivamente al tracciamento dei video. Se altri contenuti segnalano il tipo di contenuto utilizzando la stessa variabile, puoi analizzare la distribuzione dei visitatori per diversi tipi di contenuto. Ad esempio, puoi utilizzare questa variabile per assegnare valori quali &quot;articolo&quot; o &quot;pagina prodotto&quot; ad altri tipi di contenuto. Dal punto di vista della misurazione video, il tipo di contenuto ti consente di identificare i visitatori del video e quindi di calcolare i tassi di conversione relativi al video.

   * Tipo di variabile: eVar
   * Scadenza predefinita: visualizzazioni pagina

* **a.media.timePlayed**

   Conta il tempo, in secondi, trascorso a guardare un video dall&#39;ultimo processo di raccolta di dati (richiesta immagine).

   * Tipo di variabile: Event
   * Tipo: contatore

* **a.media.view**

   Indica che un visitatore ha visualizzato una parte del video. Tuttavia, non fornisce informazioni sulla durata della visualizzazione o sulla parte di video visualizzata dal visitatore.

   * Tipo di variabile: Event
   * Tipo: contatore

* **a.media.segmentView**

   Indica che un visitatore ha visualizzato una parte di un segmento di video. Tuttavia, non fornisce informazioni sulla durata della visualizzazione o sulla parte di video visualizzata dal visitatore.

   * Tipo di variabile: Event
   * Tipo: contatore

* **a .media.complete**

   Indica che un utente ha visualizzato un video completo. Per impostazione predefinita, l&#39;evento completo è misurato 1 secondo prima della fine del video. Durante l’implementazione, puoi specificare a quanti secondi dalla fine del video la visualizzazione potrà essere considerata come una visualizzazione completa. Per i video in diretta e altri flussi che non hanno una fine definita, puoi specificare un punto personalizzato per misurare le visualizzazioni complete. Ad esempio, dopo che è stato visualizzato un periodo di tempo specifico.

   * Tipo di variabile: Event
   * Tipo: contatore

## Tracciare gli eventi del lettore {#section_C7F43AECBC0D425390F7FCDF3035B65D}

Per misurare la riproduzione di un video, è necessario invocare i metodi `mediaPlay`, `mediaStop` e `mediaClose` nei momenti opportuni. Ad esempio, `mediaStop` deve essere invocato quando il lettore viene messo in pausa e `mediaPlay` quando la riproduzione viene avviata o ripresa.

## Guida di riferimento delle classi e dei metodi per la misurazione di file multimediali {#section_50DF9359A7B14DF092634C8E913C77FE}

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

   Chiude l&#39;elemento multimediale denominato *`name`*.

   * Di seguito è riportata la sintassi per questo metodo:

      ```cpp
      void close(QString name);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```cpp
      ADBMediaAnalytics::sharedInstance()->close("name");
      ```

* **play**

   Riproduce l&#39;elemento multimediale denominato *`name`* in corrispondenza dell&#39;*`offset`* indicato (in secondi).

   * Di seguito è riportata la sintassi per questo metodo:

      ```cpp
      void play(QString name, double offset);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```cpp
      ADBMediaAnalytics::sharedInstance()->play("name", 0); 
      ```

* **completato**

   Contrassegna manualmente l&#39;elemento multimediale come completato in corrispondenza dell&#39;*`offset`* indicato (in secondi).

   * Di seguito è riportata la sintassi per questo metodo:

      ```cpp
      void complete(QString name, double offset);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```cpp
      ADBMediaAnalytics::sharedInstance()->complete("name", 0);
      ```

* **stop**

   Notifica al modulo multimediale che il video è stato interrotto o messo in pausa in corrispondenza dell&#39;*offset* indicato.

   * Di seguito è riportata la sintassi per questo metodo:

      ```cpp
      stop(QString name, double offset);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```cpp
      ADBMediaAnalytics::sharedInstance()->stop("name", 0);
      ```

* **click**

   Notifica al modulo multimediale l&#39;avvenuto clic sull&#39;elemento multimediale.

   * Di seguito è riportata la sintassi per questo metodo:

      ```cpp
      void click(QString name, double offset);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```cpp
      ADBMediaAnalytics::sharedInstance()->close("name", 0);
      ```

* **track**

   Invia una chiamata Track Action (senza visualizzazioni pagina) per lo stato corrente dell&#39;elemento multimediale.

   * Di seguito è riportata la sintassi per questo metodo:

      ```cpp
      track(QString name, QHash<QString, QString> additionalData = QHash<QString, QString>()); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```cpp
      ADBMediaAnalytics::sharedInstance()->track("name", null);
      ```
