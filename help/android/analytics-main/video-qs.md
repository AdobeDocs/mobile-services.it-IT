---
description: Queste informazioni spiegano come misurare i video su Android con la soluzione di misurazione video.
keywords: android;library;mobile;sdk
seo-description: Queste informazioni spiegano come misurare i video su Android con la soluzione di misurazione video.
seo-title: Analisi dei video
solution: Experience Cloud,Analytics
title: Analisi dei video
topic: Developer and implementation
uuid: a137cc27-dc28-48c0-b08e-2ca17d2c7e1d
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '881'
ht-degree: 100%

---


# Analisi dei video {#video-analytics}

Queste informazioni spiegano come misurare i video su Android con la soluzione di misurazione video.

>[!TIP]
>
>Durante la riproduzione di un video, vengono inviate al servizio frequenti chiamate &quot;heartbeat&quot; che consentono di misurare il tempo di riproduzione. Tali chiamate heartbeat sono inviate ogni 10 secondi e consentono di ottenere metriche di coinvolgimento dettagliate e rapporti più precisi sull&#39;abbandono. Per ulteriori informazioni sulla soluzione di misurazione video di Adobe, consulta [Misurazione di audio e video in Adobe Analytics](https://docs.adobe.com/content/help/it-IT/media-analytics/using/media-overview.html).

Il processo generale da seguire per la misurazione dei video è molto simile per tutte le piattaforme. Di seguito viene fornita una panoramica di base delle attività di sviluppo, con esempi di codice. Nella tabella seguente sono elencati i dati multimediali inviati ad Analytics. Le regole di elaborazione vengono utilizzate per mappare i dati contestuali in una variabile Analytics.

## Mappare gli eventi del lettore sulle variabili di Analytics {#section_E84987F878AB4A3A83AE700FEC4C9D4D}

* **a.media.name**
   * Tipo di variabile: eVar
      * Scadenza predefinita: visita
      * Custom Insight (s.prop, utilizzato per il percorso del video)
   * (**Obbligatorio**) Quando un visitatore visualizza il video, questa variabile di dati di contesto raccoglie il nome del video in base a come è stato specificato nell’implementazione. Puoi aggiungere delle classificazioni per questa variabile.
   * (**Facoltativo**) La variabile Custom Insight fornisce informazioni sul percorso del video.

* **a.media.name**
   * Tipo evento: Custom Insight (s.prop)
   * (**Facoltativo**) Fornisce informazioni sul percorso del video.

      >[!IMPORTANT]
      >
      >Il percorso deve essere abilitato per questa variabile da ExpCare.
   * Tipo evento: Custom Insight (s.prop)

* **a.media.segment**
   * Tipo di variabile: eVar
   * Scadenza predefinita: visualizzazioni pagina
   * (**Obbligatorio**) Raccoglie dati sui segmenti video, tra cui il nome del segmento e l’ordine in cui il segmento appare nel video.

      Puoi popolare questa variabile abilitando la variabile `segmentByMilestones` quando monitori automaticamente gli eventi del lettore oppure impostando un nome del segmento personalizzato quando monitori manualmente gli eventi del lettore. Ad esempio, quando un visitatore visualizza il primo segmento di un video, SiteCatalyst potrebbe raccogliere quanto segue nella eVar dei segmenti: `1:M:0-25`.

      Il metodo predefinito per la raccolta dei dati video raccoglie i dati nei seguenti punti:

      * inizio video (Riproduci)
      * inizio segmento
      * fine video (Interrompi)

      Analytics conta la visualizzazione del primo segmento all’inizio del segmento, quando il visitatore inizia a guardarlo. Le visualizzazioni dei segmenti successivi vengono contate quando ogni inizia ogni segmento.


* **a.contentType**
   * Tipo di variabile: eVar
   * Scadenza predefinita: visualizzazioni pagina
   * Raccoglie dati relativi al tipo di contenuto visualizzato da un visitatore.

      Agli hit inviati dalla misurazione video è assegnato il tipo di contenuto `video`. Dal punto di vista della misurazione video, il **tipo di contenuto** ti consente di identificare i visitatori del video e di calcolare i tassi di conversione relativi al video.

* **a.media.timePlayed**
   * Tipo di variabile: Event
   * Tipo: contatore
   * Conta il tempo, in secondi, trascorso a guardare un video dall’ultimo processo di raccolta di dati (richiesta immagine).

* **a.media.view**
   * Tipo di variabile: Event
   * Tipo: contatore
   * Indica che un visitatore ha visualizzato una parte del video.

      Tuttavia, non fornisce informazioni sulla durata della visualizzazione o sulla parte di video visualizzata dal visitatore.

* **a.media.segmentView**
   * Tipo di variabile: Event
   * Tipo: contatore
   * Indica che un visitatore ha visualizzato una parte di un segmento di video.

      Tuttavia, non fornisce informazioni sulla durata della visualizzazione o sulla parte di video visualizzata dal visitatore.

* **a .media.complete**
   * Tipo di variabile: Event
   * Tipo: contatore
   * Indica che un utente ha visualizzato un video completo.

      Per impostazione predefinita, l&#39;evento completo è misurato 1 secondo prima della fine del video. Durante l’implementazione, puoi specificare a quanti secondi dalla fine del video la visualizzazione potrà essere considerata come una visualizzazione completa. Per i video in diretta e altri flussi che non hanno una fine definita, puoi specificare un punto personalizzato in base al quale misurare le visualizzazioni complete, ad esempio dopo che è stato visualizzato un dato punto temporale.


## Configurare le impostazioni per i file multimediali {#section_929945D4183C428AAF3B983EFD3E2500}

Configura un oggetto `MediaSettings` con le impostazioni che desideri utilizzare per tracciare il video:

```java
MediaSettings mySettings = Media.settingsWith("name", 10, "playerName", "playerId");
```

## Tracciare gli eventi del lettore {#section_C7F43AECBC0D425390F7FCDF3035B65D}

Per misurare la riproduzione di un video, è necessario invocare i metodi `mediaPlay`, `mediaStop` e `mediaClose` nei momenti opportuni. Ad esempio, chiama `mediaStop` quando il lettore viene messo in pausa e `mediaPlay` quando la riproduzione viene avviata o ripresa.

## Classi {#section_16838332727348F990305C0C6B0D795C}

**Classe: MediaSettings**

```java
public String name; 
public String playerName; 
public String playerID; 
public double length; 
public String channel; 
public String milestones; 
public String offsetMilestones; 
public boolean segmentByMilestones; 
public boolean segmentByOffsetMilestones; 
public int trackSeconds = 0; 
public int completeCloseOffsetThreshold = 1; 
 
// MediaAnalytics Ad settings 
public String parentName; 
public String parentPod; 
public String CPM; 
public double parentPodPosition; 
public boolean isMediaAd;
```

**Classe: MediaState**

```java
public Date openTime = new Date(); 
public String name; 
public String segment; 
public String playerName; 
public String mediaEvent; 
public int offsetMilestone; 
public int segmentNum; 
public int milestone; 
public double length; 
public double offset; 
public double percent; 
public double timePlayed; 
public double segmentLength; 
public boolean complete = false; 
public boolean clicked = false; 
public boolean ad; 
public boolean eventFirstTime;
```

## Guida di riferimento delle classi e dei metodi per la misurazione di file multimediali {#section_50DF9359A7B14DF092634C8E913C77FE}

Di seguito sono riportati i metodi della classe Misurazione di file multimediali:

* **settingsWith**

   Restituisce un oggetto `MediaSettings` con i parametri specificati.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static MediaSettings adSettingsWith(String name, double length, String playerName, String parentName, String parentPod, double parentPodPosition, String CPM);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      MediaSettingsmySettings = Media.settingsWith("name", 10, "playerName", "playerId");
      ```

* **adSettingsWith**

   Restituisce un oggetto `MediaSettings` per l&#39;uso con il tracciamento di un video annuncio.
   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static MediaSettings adSettingsWith(String name, double length, String playerName, String parentName, String parentPod, double parentPodPosition, String CPM);
      ```

* **open**

   Apre un oggetto `MediaSettings` per il tracciamento.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void open(MediaSettings settings, MediaCallback callback); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      Media.open(mySettings, new Media.MediaCallback() { 
        @Override 
        public void call(Object item)
        {//  monitor  callback  if  you  want  to  be  notified  every  second  the  media  is  playing  }
        }); 
      ```

   * **close**

      Chiude l&#39;elemento multimediale denominato *name*.

      * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void close(String name);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      Media.close("name"); 
      ```


* **play**
   * Riproduce l&#39;elemento multimediale denominato *name* in corrispondenza dell&#39;*offset* indicato in secondi.
   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      publicstatic void play(String name, double offset); 
      ```

* **completato**

   Contrassegna manualmente l&#39;elemento multimediale come completato in corrispondenza dell&#39;*offset* indicato in secondi.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void complete(String name, double offset); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      Media.complete("name", 0); 
      ```

* **stop**

   Notifica al modulo multimediale che il video è stato interrotto o messo in pausa in corrispondenza dell&#39;*offset* indicato.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void stop(String name, double offset); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      Media.stop("name", 0);
      ```

* **click**

   Notifica al modulo multimediale l&#39;avvenuto clic sull&#39;elemento multimediale.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void click(String name double offset); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      Media.click("name", 0);
      ```

* **track**

   Invia una chiamata Track Action (senza visualizzazioni pagina) per lo stato corrente dell&#39;elemento multimediale.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      publicstatic void track(String name, Map<String, Object> data); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      Media.track("name", null); 
      ```
