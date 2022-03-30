---
description: Informazioni utili per l’analisi dei video.
solution: Experience Cloud Services,Analytics
title: Analisi dei video
topic-fix: Developer and implementation
uuid: 7d4e6668-a1d9-41da-96c8-8baac860c5b0
exl-id: 86d70a6f-db12-4f94-a37f-4b1d4b99e0f1
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '887'
ht-degree: 68%

---

# Analisi dei video {#video-analytics}

Informazioni utili per l’analisi dei video.

La misurazione del video è descritta in dettaglio nella sezione [Misurazione dei contenuti multimediali in streaming in Adobe Analytics](https://experienceleague.adobe.com/docs/media-analytics/using/media-overview.html?lang=it) guida. Il processo generale da seguire per la misurazione dei video è molto simile per tutte le piattaforme AppMeasurement. Questa sezione di avvio rapido fornisce una panoramica di base delle attività di sviluppo, con esempi di codice.

Nella tabella seguente sono elencati i dati multimediali inviati ad Analytics. Utilizza le regole di elaborazione per mappare i dati contestuali in una variabile di Analytics.

* **a.media.name**

   (Obbligatorio) Raccoglie il nome del video, come specificato nell’implementazione, quando un visitatore visualizza il video in qualche modo. Puoi aggiungere classificazioni per questa variabile.

   (**Facoltativo**) La variabile Custom Insight fornisce informazioni sul percorso del video.

   * Tipo di variabile: eVar
   * Scadenza predefinita: visita
   * Custom Insight (s.prop, utilizzato per il percorso del video)

* **a.media.name**

   (Facoltativo) Fornisce informazioni sul percorso del video. Il percorso deve essere abilitato per questa variabile dall’assistenza clienti.

   Tipo evento: Custom Insight (s.prop)

   * Tipo evento: Custom Insight (s.prop)

* **a.media.segment**

   (Obbligatorio) Raccoglie dati sui segmenti video, tra cui il nome del segmento e l’ordine in cui il segmento appare nel video. Quando viene eseguito il tracciamento automatico degli eventi del lettore, questa variabile viene compilata abilitando la variabile `segmentByMilestones`. Quando gli eventi del lettore vengono tracciati manualmente, viene compilata impostando un nome di segmento personalizzato. Ad esempio, quando un visitatore visualizza il primo segmento di un video, il SiteCatalyst potrebbe raccogliere quanto segue in `1:M:0-25` eVar del segmento.

   Il metodo predefinito per la raccolta dei dati video raccoglie i dati nei seguenti punti:

   * inizio video (Riproduci)
   * inizio segmento
   * fine video (Interrompi)

   Analytics conta la visualizzazione del primo segmento all’inizio del segmento, quando il visitatore inizia a guardarlo. Le visualizzazioni dei segmenti successivi vengono contate quando ogni inizia ogni segmento.

   * Tipo di variabile: eVar
   * Scadenza predefinita: visualizzazioni pagina


* **a.contentType**

   Raccoglie dati sul tipo di contenuto visualizzato da un visitatore. Agli hit inviati dalla misurazione video è assegnato il tipo di contenuto &quot;video&quot;. Questa variabile non è riservata esclusivamente al tracciamento dei video. Se altri contenuti segnalano il tipo di contenuto utilizzando la stessa variabile, puoi analizzare la distribuzione dei visitatori per diversi tipi di contenuto. Ad esempio, puoi utilizzare questa variabile per assegnare valori quali &quot;articolo&quot; o &quot;pagina prodotto&quot; ad altri tipi di contenuto. Dal punto di vista della misurazione video, il tipo di contenuto ti consente di identificare i visitatori del video e di calcolare i tassi di conversione relativi al video.

   * Tipo di variabile: eVar
   * Scadenza predefinita: visualizzazioni pagina

* **a.media.timePlayed**

   Conta il tempo, in secondi, trascorso a guardare un video dall&#39;ultimo processo di raccolta di dati (richiesta immagine).

   * Tipo di variabile: Event
   * Tipo: contatore

* **a.media.view**

   Indica che un visitatore ha visualizzato una parte del video. Tuttavia, non fornisce informazioni sulla durata della visualizzazione o sulla parte di video visualizzata dal visitatore.

   * Variabile: Evento
   * Tipo: contatore

* **a.media.segmentView**

   Indica che un visitatore ha visualizzato una parte di un segmento di video. Tuttavia, non fornisce informazioni sulla durata della visualizzazione o sulla parte di video visualizzata dal visitatore.

   * Tipo di variabile: Event
   * Tipo: contatore

* **a .media.complete**

   Indica che un utente ha visualizzato un video completo. Per impostazione predefinita, l&#39;evento completo è misurato 1 secondo prima della fine del video. Durante l’implementazione, puoi specificare a quanti secondi dalla fine del video la visualizzazione potrà essere considerata come una visualizzazione completa. Per i video in diretta e altri flussi che non hanno una fine definita, puoi specificare un punto personalizzato per misurare le visualizzazioni complete. Ad esempio, dopo che è stato visualizzato un periodo di tempo specifico.

   * Tipo di variabile: Event
   * Tipo: contatore

## Configurare le impostazioni per i file multimediali {#section_929945D4183C428AAF3B983EFD3E2500}

Configura un oggetto `MediaSettings` con le impostazioni che desideri utilizzare per tracciare il video:

```js
var mySettings = ADB.Media.settingsWith("name", 10, "playerName", "playerId");
```

## Tracciare gli eventi del lettore {#section_C7F43AECBC0D425390F7FCDF3035B65D}

Per misurare la riproduzione di un video, è necessario invocare i metodi `Play`, `Stop` e `Close` nei momenti opportuni. Ad esempio, `Stop` deve essere invocato quando il lettore viene messo in pausa e `Play` quando la riproduzione viene avviata o ripresa.

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

## Guida di riferimento delle classi e dei metodi per la misurazione di file multimediali {#section_50DF9359A7B14DF092634C8E913C77FE}

* **SettingsWith (winJS: settingsWith)**

   Restituisce un oggetto `MediaSetting` con i parametri specificati.

   * Di seguito è riportata la sintassi per questo metodo:

      ```csharp
      static MediaSettings ^SettingsWith(Platform::String ^name, double length, Platform::String ^playerName, Platform::String ^playerID); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```js
      var mySettings = ADB.Media.settingsWith("name", 10, "playerName", "playerId"); 
      ```

* **AdSettingsWith (winJS: adSettingsWith**

   Restituisce un oggetto `MediaSettings` per l&#39;uso con il tracciamento di un video annuncio.

   * Di seguito è riportata la sintassi per questo metodo:

      ```csharp
      static MediaSettings ^AdSettingsWith(Platform::String ^name, double length, Platform::String ^playerName, Platform::String ^parentName, Platform::String ^parentPod, double parentPosition, Platform::String ^CPM); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```js
      var myAdSettings = ADB.Media.adSettingsWith("name", 10, "playerName", "parentName", "parentPod", 5, "myCPM"); 
      ```

* **Apri (winJS: aperto)**

   Tiene traccia dell&#39;apertura di un file multimediale utilizzando le impostazioni definite in `settings`.

   * Di seguito è riportata la sintassi per questo metodo:

      ```csharp
      static void Open(MediaSettings ^settings);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```js
      ADB.Media.open(mySettings); 
      ```

* **Chiudi (winJS: vicino)**

   Tiene traccia della chiusura di un file multimediale per l&#39;elemento multimediale denominato *name*.

   * Di seguito è riportata la sintassi per questo metodo:

      ```csharp
      static void Close(Platform::String ^name);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```js
      ADB.Media.close("mediaName");
      ```

* **Play (winJS: play)**

   Tiene traccia della riproduzione di un file multimediale per l&#39;elemento multimediale denominato *`name`* al *offset* (in secondi).

   * Di seguito è riportata la sintassi per questo metodo:

      ```csharp
      static void Play(Platform::String ^name, double offset);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```js
      ADB.Media.play("mediaName", 0);
      ```

* **Completa (winJS: completato)**

   Contrassegna manualmente l&#39;elemento multimediale come completato in corrispondenza dell&#39;*offset* indicato (in secondi).

   * Di seguito è riportata la sintassi per questo metodo:

      ```csharp
      static void Complete(Platform::String ^name, double offset);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```js
      ADB.Media.complete("mediaName", 8); 
      ```

* **Stop (winJS: stop)**

   Notifica al modulo multimediale che il video è stato interrotto o messo in pausa in corrispondenza dell&#39;*offset* indicato.

   * Di seguito è riportata la sintassi per questo metodo:

      ```csharp
      static void Stop(Platform::String ^name, double offset);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```js
      ADB.Media.stop("mediaName", 4);
      ```

* **Fai clic su (winJS: clic)**

   Notifica al modulo multimediale l&#39;avvenuto clic sull&#39;elemento multimediale.

   * Di seguito è riportata la sintassi per questo metodo:

      ```csharp
      static void Click(Platform::String ^name, double offset);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```js
      ADB.Media.click("mediaName", 3);
      ```

* **Track (winJS: binario)**

   Invia una chiamata Track Action (senza visualizzazioni pagina) per lo stato corrente dell&#39;elemento multimediale.

   * Di seguito è riportata la sintassi per questo metodo:

      ```csharp
      static void Track(Platform::String ^name, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^contextData);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```js
      ADB.Media.track("mediaName", null);
      ```
