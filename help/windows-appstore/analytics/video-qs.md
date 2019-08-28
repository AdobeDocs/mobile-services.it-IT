---
description: Informazioni utili per l’analisi del video.
seo-description: Informazioni utili per l’analisi del video.
seo-title: Analisi del video
solution: Marketing Cloud, Analytics
title: Analisi del video
topic: Sviluppatore e implementazione
uuid: 7 d 4 e 6668-a 1 d 9-41 da -96 c 8-8 baac 860 c 5 b 0
translation-type: tm+mt
source-git-commit: 4b5be6c51c716114e597a80d475f838e23abb1b1

---


# Analisi del video {#video-analytics}

Informazioni utili per l’analisi del video.

Video measurement is described in detail in the [Measuring audio and video in Adobe Analytics](https://docs.adobe.com/content/help/en/media-analytics/using/media-overview.html/) guide. Il processo generale da seguire per la misurazione del video è molto simile per tutte le piattaforme AppMeasurement. Questa sezione di avvio rapido fornisce una panoramica di base delle attività di sviluppo, con esempi di codice.

Nella tabella seguente sono elencati i dati multimediali inviati ad Analytics. Utilizza le regole di elaborazione per mappare i dati contestuali su una variabile di Analytics.

* **a.media.name**

   (Obbligatorio) Raccoglie il nome del video, in base a quanto specificato nell’implementazione, quando un visitatore visualizza il video in qualche modo. Per questa variabile puoi aggiungere delle classificazioni.

   (**Facoltativo**) La variabile Insight personalizzato fornisce informazioni sul percorso del video.

   * Tipo di variabile: Evar
   * Scadenza predefinita: visita
   * Insight personalizzato (s.prop, usato per il percorso del video)

* **a.media.name**

   (Facoltativo) Fornisce informazioni sul percorso del video. Il percorso deve essere abilitato per questa variabile da ClientCare.

   Tipo evento: Insight personalizzato (s.prop)

   * Tipo di variabile: Custom Insight (s. prop)

* **a.media.segment**

   (Obbligatorio) Raccoglie dati sui segmenti video, tra cui il nome del segmento e l'ordine in cui il segmento appare nel video. Quando viene eseguito il tracciamento automatico degli eventi del lettore, questa variabile viene compilata abilitando la variabile `segmentByMilestones`. Quando gli eventi del lettore vengono tracciati manualmente, viene compilata impostando un nome di segmento personalizzato. For example, when a visitor views the first segment in a video, SiteCatalyst might collect the following in the `1:M:0-25` segment eVar.

   Il metodo predefinito di raccolta dei dati video raccoglie i dati presso i seguenti punti:

   * inizio video (play)
   * inizio del segmento
   * fine del video (stop)
   Analytics conta la visualizzazione del primo segmento all'inizio del segmento, quando il visitatore inizia la visualizzazione. Il segmento successivo viene visualizzato quando inizia il segmento.

   * Tipo di variabile: Evar
   * Scadenza predefinita: visualizzazioni pagina


* **a.contentType**

   Raccoglie dati relativi al tipo di contenuto visualizzato da un visitatore. Agli hit inviati dalla misurazione video è assegnato il tipo di contenuto “video”. Non è necessario riservare questa variabile esclusivamente al tracciamento video. Se la stessa variabile viene usata anche per ottenere il tipo di altri contenuti, è possibile analizzare la distribuzione dei visitatori per diversi tipi di contenuto. Ad esempio, puoi usare questa variabile per assegnare valori quali "articolo" o "pagina prodotto" ad altri tipi di contenuti. Dal punto di vista della misurazione video, il tipo di contenuto consente di identificare i visitatori del video e di calcolare i tassi di conversione del video.

   * Tipo di variabile: Evar
   * Scadenza predefinita: visualizzazioni pagina

* **a.media.timePlayed**

   Conta il tempo, in secondi, trascorso a guardare un video dall'ultimo processo di raccolta di dati (richiesta immagine).

   * Tipo di variabile: Evento
   * Tipo: contatore

* **a.media.view**

   Indica che un visitatore ha visualizzato una parte di un video. Tuttavia, non fornisce informazioni sulla parte specifica visualizzata, né sulla durata della visualizzazione.

   * Variabile: Evento
   * Tipo: contatore

* **a.media.segmentView**

   Indica che un visitatore ha visualizzato una parte di un segmento video. Tuttavia, non fornisce informazioni sulla parte specifica visualizzata, né sulla durata della visualizzazione.

   * Tipo di variabile: Evento
   * Tipo: contatore

* **a .media.complete**

   Indica che un utente ha visualizzato un video completo. Per impostazione predefinita, l'evento completo è misurato 1 secondo prima della fine del video. Durante l’implementazione, puoi specificare quanti secondi dalla fine del video considerare come una visualizzazione dell’intero video. Per i video in diretta e altri flussi che non hanno una fine definita, puoi specificare un punto personalizzato per misurare il completamento. Ad esempio, dopo un tempo di visualizzazione specifico.

   * Tipo di variabile: Evento
   * Tipo: contatore


## Configure media settings {#section_929945D4183C428AAF3B983EFD3E2500}

Configura un oggetto `MediaSettings` con le impostazioni che desideri utilizzare per tracciare il video:

```js
var mySettings = ADB.Media.settingsWith("name", 10, "playerName", "playerId");
```

## Track player events {#section_C7F43AECBC0D425390F7FCDF3035B65D}

To measure video playback, The `Play`, `Stop`, and `Close` methods need to be called at the appropriate times. Ad esempio, `Stop` deve essere invocato quando il lettore viene messo in pausa e `Play` quando la riproduzione viene avviata o ripresa.

## Classi {#section_16838332727348F990305C0C6B0D795C}

### Classe: MediaSettings

```
property Platform::String ^name; 
property Platform::String ^playerName; 
property Platform::String ^playerID; 
property double length; 
property Platform::String ^channel; 
property Platform::String ^milestones; 
property Platform::String ^offsetMilestones; 
property bool segmentByMilestones; 
property bool segmentByOffsetMilestones; 
property int trackSeconds; 
property int completeCloseOffsetThreshold; 
 
// MediaAnalytics Ad settings 
property Platform::String ^parentName; 
property Platform::String ^parentPod; 
property Platform::String ^CPM; 
property double parentPodPosition; 
property bool isMediaAd;
```

## Media measurement class and method reference {#section_50DF9359A7B14DF092634C8E913C77FE}

* **Settingswith (winjs: Settingswith**

   Restituisce un oggetto `MediaSetting` con i parametri specificati.

   * Di seguito è riportata la sintassi per questo metodo:

      ```csharp
      static MediaSettings ^SettingsWith(Platform::String ^name, double length, Platform::String ^playerName, Platform::String ^playerID); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```js
      var mySettings = ADB.Media.settingsWith("name", 10, "playerName", "playerId"); 
      ```

* **Adsettingswith (winjs: Adsettingswith**

   Restituisce un oggetto `MediaSettings` per l'uso con il tracciamento di un video annuncio.

   * Di seguito è riportata la sintassi per questo metodo:

      ```csharp
      static MediaSettings ^AdSettingsWith(Platform::String ^name, double length, Platform::String ^playerName, Platform::String ^parentName, Platform::String ^parentPod, double parentPosition, Platform::String ^CPM); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```js
      var myAdSettings = ADB.Media.adSettingsWith("name", 10, "playerName", "parentName", "parentPod", 5, "myCPM"); 
      ```

* **Open (winjs: open)**

   Tiene traccia dell’apertura di un file multimediale tramite le impostazioni definite in `settings`.

   * Di seguito è riportata la sintassi per questo metodo:

      ```csharp
      static void Open(MediaSettings ^settings);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```js
      ADB.Media.open(mySettings); 
      ```

* **Chiudi (winjs: close)**

   Tiene traccia della chiusura di un file multimediale per l’elemento del file multimediale denominato *name*.

   * Di seguito è riportata la sintassi per questo metodo:

      ```csharp
      static void Close(Platform::String ^name);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```js
      ADB.Media.close("mediaName");
      ```

* **Riproduci (winjs: play)**

   Tiene traccia della riproduzione di un file multimediale per l’elemento del file multimediale denominato *`name`* ad un dato *offset* (in secondi).

   * Di seguito è riportata la sintassi per questo metodo:

      ```csharp
      static void Play(Platform::String ^name, double offset);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```js
      ADB.Media.play("mediaName", 0);
      ```

* **Complete (winjs: complete)**

   Contrassegna manualmente l'elemento multimediale come completato in corrispondenza dell'*offset* indicato (in secondi).

   * Di seguito è riportata la sintassi per questo metodo:

      ```csharp
      static void Complete(Platform::String ^name, double offset);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```js
      ADB.Media.complete("mediaName", 8); 
      ```

* **Interrompi (winjs: stop)**

   Notifica al modulo multimediale che il video è stato interrotto o messo in pausa in corrispondenza dell'*offset* indicato.

   * Di seguito è riportata la sintassi per questo metodo:

      ```csharp
      static void Stop(Platform::String ^name, double offset);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```js
      ADB.Media.stop("mediaName", 4);
      ```

* **Click (winjs: click)**

   Notifica al modulo multimediale l'avvenuto clic sull'elemento multimediale.

   * Di seguito è riportata la sintassi per questo metodo:

      ```csharp
      static void Click(Platform::String ^name, double offset);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```js
      ADB.Media.click("mediaName", 3);
      ```

* **Track (winjs: track)**

   Invia una chiamata Track Action (senza visualizzazioni pagina) per lo stato corrente dell'elemento multimediale.

   * Di seguito è riportata la sintassi per questo metodo:

      ```csharp
      static void Track(Platform::String ^name, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^contextData);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```js
      ADB.Media.track("mediaName", null);
      ```

