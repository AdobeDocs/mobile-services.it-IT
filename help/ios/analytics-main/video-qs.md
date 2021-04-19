---
description: Queste informazioni spiegano come misurare i video su iOS mediante la misurazione di specifici eventi video.
seo-description: Queste informazioni spiegano come misurare i video su iOS mediante la misurazione di specifici eventi video.
seo-title: Analisi dei video
solution: Experience Cloud,Analytics
title: Analisi dei video
topic-fix: Developer and implementation
uuid: d75fa415-78f6-4f50-a563-76949f040138
exl-id: d4d11ca0-1280-49db-8983-5b6d83856482
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '952'
ht-degree: 100%

---

# Analisi dei video {#video-analytics}

Queste informazioni spiegano come misurare i video su iOS mediante la misurazione di specifici eventi video.

>[!TIP]
>
>Durante la riproduzione di un video, vengono inviate al servizio frequenti chiamate &quot;heartbeat&quot; che consentono di misurare il tempo di riproduzione. Tali chiamate heartbeat sono inviate ogni 10 secondi e consentono di ottenere metriche di coinvolgimento dettagliate e rapporti più precisi sull&#39;abbandono. Per ulteriori informazioni, consulta [Misurazione di audio e video in Adobe Analytics](https://docs.adobe.com/content/help/it-IT/media-analytics/using/media-overview.html).

Il processo generale da seguire per la misurazione dei video è molto simile per tutte le piattaforme. Di seguito viene fornita una panoramica di base delle attività di sviluppo, con esempi di codice.

## Mappare gli eventi del lettore sulle variabili di Analytics {#section_E84987F878AB4A3A83AE700FEC4C9D4D}

Nella tabella seguente sono elencati i dati multimediali inviati ad Analytics. Utilizza le regole di elaborazione per mappare i dati contestuali in una variabile di Analytics.

* **a.media.name**

   (Obbligatorio) Raccoglie il nome del video, come specificato nell’implementazione, quando un visitatore lo visualizza in qualche modo. Puoi aggiungere delle classificazioni per questa variabile.

   (Facoltativo) La variabile Custom Insight fornisce informazioni sul percorso del video.

   * Tipo di variabile: eVar
   * Scadenza predefinita: visita
   * Custom Insight (s.prop, utilizzato per il percorso del video)

* **a.media.name**

   (Facoltativo) Fornisce informazioni sul percorso del video. Il percorso deve essere abilitato per questa variabile dall’assistenza clienti.

   * Tipo evento: Custom Insight (s.prop)
   * Tipo evento: Custom Insight (s.prop)

* **a.media.segment**

   (Obbligatorio) Raccoglie dati sui segmenti video, tra cui il nome del segmento e l’ordine in cui il segmento appare nel video. Quando viene eseguito il tracciamento automatico degli eventi del lettore, questa variabile viene compilata abilitando la variabile `segmentByMilestones`. Quando gli eventi del lettore vengono tracciati manualmente, viene compilata impostando un nome di segmento personalizzato. Ad esempio, quando un visitatore visualizza il primo segmento di un video, SiteCatalyst potrebbe raccogliere quanto segue nella eVar dei segmenti `1:M:0-25`.

   Il metodo predefinito per la raccolta dei dati video raccoglie i dati nei seguenti punti:

   * inizio video (Riproduci)
   * inizio segmento
   * fine video (Interrompi)

   Analytics conta la visualizzazione del primo segmento all’inizio del segmento, quando il visitatore inizia a guardarlo. Le visualizzazioni dei segmenti successivi vengono contate quando ogni inizia ogni segmento.

   * Tipo di variabile: eVar
   * Scadenza predefinita: visualizzazioni pagina


* **a.contentType**

   Raccoglie dati relativi al tipo di contenuto visualizzato da un visitatore. Agli hit inviati dalla misurazione video è assegnato il tipo di contenuto `video`. Questa variabile non è riservata esclusivamente al tracciamento dei video. Se anche altri contenuti trasmettono il tipo di contenuto mediante questa stessa variabile, puoi analizzare la distribuzione dei visitatori per i diversi tipi di contenuto. Ad esempio, puoi usare questa variabile per assegnare valori quali &quot;articolo&quot; o &quot;pagina prodotto&quot; ad altri tipi di contenuti. Dal punto di vista della misurazione video, il tipo di contenuto ti consente di identificare i visitatori del video e di calcolare i tassi di conversione relativi al video.

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

* **a.media.complete**

   Indica che un utente ha visualizzato un video completo. Per impostazione predefinita, l&#39;evento completo è misurato 1 secondo prima della fine del video. Durante l’implementazione, puoi specificare a quanti secondi dalla fine del video la visualizzazione potrà essere considerata come una visualizzazione completa. Per i video in diretta e altri flussi che non hanno una fine definita, puoi specificare un punto personalizzato in base al quale misurare le visualizzazioni complete, ad esempio dopo che è stato visualizzato un dato punto temporale.

   * Tipo di variabile: Event
   * Tipo: contatore

## Configurare le impostazioni per i file multimediali {#section_929945D4183C428AAF3B983EFD3E2500}

Configura un oggetto `ADBMediaSettings` con le impostazioni che desideri usare per tenere traccia del video:

```objective-c
ADBMediaSettings *mediaSettings = [ADBMobile mediaCreateSettingsWithName:MEDIA_NAME  
length:MEDIA_LENGTH playerName:PLAYER_NAME playerID:PLAYER_ID]; 
 
// milestone tracking. Use either standard milestones (percentage of total length) 
// or offset milestones (seconds elapsed from the beginning of the video) 
mediaSettings.milestones = @"25,50,75"; 
mediaSettings.segmentByMilestones = YES; 
 
mediaSettings.offsetMilestones = @"60,120"; 
mediaSettings.segmentByOffsetMilestones = YES; 
 
// seconds tracking - sends a hit every x seconds 
mediaSettings.trackSeconds = 30; // sends a hit every 30 seconds 
 
// open the video 
[ADBMobile mediaOpenWithSettings:mediaSettings callback:nil]; 
 
// You are now ready to play the video, for example, [movieViewController.moviePlayer play]; 
// Note the mediaPlay, mediaStop and mediaClose methods are called in the 
// event handlers described in the next section
```

## Tracciare gli eventi del lettore {#section_C7F43AECBC0D425390F7FCDF3035B65D}

Per misurare la riproduzione di un video, è necessario invocare i metodi `mediaPlay`, `mediaStop` e `mediaClose` nei momenti opportuni. Ad esempio, `mediaStop` deve essere invocato quando il lettore viene messo in pausa e `mediaPlay` quando la riproduzione viene avviata o ripresa.

L&#39;esempio di seguito illustra come configurare le notifiche e invocare i metodi per i file multimediali per ottenere le misurazioni relative ai video:

```objective-c
// configure notifications for when the video is finished, and when the 
media playback state changes 
 
- (void) configureNotifications:(MPMoviePlayerController *) movieController { 
 [[NSNotificationCenter defaultCenter] 
  addObserver: self 
  selector: @selector(mediaFinishedCallback:) 
  name: MPMoviePlayerPlaybackDidFinishNotification 
  object: movieController]; 
  
 [[NSNotificationCenter defaultCenter] 
  addObserver: self 
  selector: @selector(mediaPlaybackChangedCallback:) 
  name: MPMoviePlayerPlaybackStateDidChangeNotification 
  object: movieController]; 
} 
 
// define your notification callbacks. 
 
- (void) mediaFinishedCallback: (NSNotification*) notification { [ADBMobile mediaClose:MEDIA_NAME];} 
 
- (void) mediaPlaybackChangedCallback: (NSNotification*) notification { 
 MPMoviePlayerController *mediaController = notification.object; 
 if (mediaController.playbackState == MPMoviePlaybackStatePlaying) { 
  [ADBMobile mediaPlay:MEDIA_NAME offset: isnan(mediaController.currentPlaybackTime) ? 0.0 : mediaController.currentPlaybackTime]; 
 } 
 else if (mediaController.playbackState == MPMoviePlaybackStateSeekingBackward) { 
  [ADBMobile mediaStop:MEDIA_NAME offset:mediaController.currentPlaybackTime]; 
 } 
 else if (mediaController.playbackState == MPMoviePlaybackStateSeekingForward) { 
  [ADBMobile mediaStop:MEDIA_NAME offset:mediaController.currentPlaybackTime]; 
 } 
 else if (mediaController.playbackState == MPMoviePlaybackStatePaused) { 
  [ADBMobile mediaStop:MEDIA_NAME offset:mediaController.currentPlaybackTime]; 
 } 
 else if (mediaController.playbackState == MPMoviePlaybackStateInterrupted) { 
  [ADBMobile mediaStop:MEDIA_NAME offset:mediaController.currentPlaybackTime]; 
 } 
 else if (mediaController.playbackState == MPMoviePlaybackStateStopped) { 
  [ADBMobile mediaStop:MEDIA_NAME offset:mediaController.currentPlaybackTime]; 
 } 
}
```

## Classi {#section_16838332727348F990305C0C6B0D795C}

### Classe: ADBMediaSettings

```objective-c
bool segmentByMilestones; 
bool segmentByOffsetMilestones; 
double length; 
NSString *channel; 
NSString *name; 
NSString *playerName; 
NSString *playerID; 
NSString *milestones; 
NSString *offsetMilestones; 
NSUInteger trackSeconds; 
NSUInteger completeCloseOffsetThreshold; 
// settings used for ad tracking. For  
bool isMediaAd; 
double parentPodPosition; 
NSString *CPM; 
NSString *parentName; 
NSString *parentPod; 
```

### Classe: ADBMediaState

```objective-c
bool ad; 
bool clicked; 
bool complete; 
bool eventFirstTime; 
double length; 
double offset; 
double percent; 
double segmentLength; 
double timePlayed; 
double timePlayedSinceTrack; 
double timestamp; 
NSDate *openTime  
NSString *name 
NSString *playerName 
NSString *mediaEvent 
NSString *segment 
NSUInteger milestone 
NSUInteger offsetMilestone 
NSUInteger segmentNum 
NSUInteger eventType
```

## Guida di riferimento delle classi e dei metodi per la misurazione di file multimediali {#section_50DF9359A7B14DF092634C8E913C77FE}

* **mediaCreateSettings&#x200B;WithName:&#x200B;length:&#x200B;playerName:&#x200B;playerID:**

   Restituisce un oggetto `ADBMediaSettings` con i parametri specificati.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      +(ADBMediaSettings *) mediaCreateSettingsWithName:(NSString *)name
                                                 length:(double)length
                                              playerName:(NSString *)playerName
                                               playerID:(NSString *)playerID;
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      ADBMediaSettings *myCatSettings =
            [ADBMobile mediaCreateSettingsWithName:@"catVideo"                                               length:85
                                        playerName:@"catVideoPlayer"
                                          playerID:@"catPlayerId"]; 
      ```

* **mediaAdCreateSettings&#x200B;WithName:&#x200B;length:&#x200B;playerName:&#x200B;parentName:&#x200B;parentPod:&#x200B;parentPodPosition:&#x200B;CPM:**

   Restituisce un oggetto `ADBMediaSettings` per l&#39;uso con il monitoraggio di un video annuncio.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      + (ADBMediaSettings *) mediaAdCreateSettingsWithName:(NSString *)name
                                                    length:(double)length   
                                                playerName:(NSString *)playerName
                                                parentName:(NSString *)parentName
                                                 parentPod:(NSString *)parentPod
                                        parentPodPosition:(double)parentPodPosition
                                                      CPM:(NSString *)CPM; 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
        ADBMediaSettings *mySettings = 
             [ADBMobile mediaAdCreateSettingsWithName:@"ad"                                       length:30
                                           playerName:@"adPlayer"
                                           parentName:@"catVideo"
                                           parentPod:@"catCollection"
                                           parentPodPosition:2
                                                        CPM:nil];
      ```

* **mediaOpenWithSettings:&#x200B;callback:**

   Apre un oggetto `ADBMediaSettings` per il monitoraggio.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      + (void) mediaOpenWithSettings:(ADBMediaSettings *)settings
                            callback:(void (^)(ADBMediaState *mediaState))callback; 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      [ADBMobile mediaOpenWithSettings:mySettings callback:^(ADBMediaState *mediaState) {
           // do something with media state if you want}];
      ```

* **mediaClose:**

   Chiude l&#39;elemento multimediale denominato *name*.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
       + (void) mediaClose:(NSString *)name; 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      [ADBMobile mediaClose:@"kittiesPlaying"];
      ```

* **mediaPlay:&#x200B;offset:**

   Riproduce l&#39;elemento multimediale denominato *name* in corrispondenza dell&#39;*offset* indicato (in secondi).

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
       + (void) mediaPlay:(NSString *)name offset:(double)offset;
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      [ADBMobile mediaPlay:@"cats" offset:25];
      ```

* **mediaComplete:&#x200B;offset:**

   Contrassegna manualmente l&#39;elemento multimediale come completato in corrispondenza dell&#39;*offset* indicato (in secondi).

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
       + (void) mediaComplete:(NSString *)name offset:(double)offset;
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
       [ADBMobile mediaComplete:@"meowzah" offset:90]; 
      ```

* **mediaStop:&#x200B;offset:**

   Notifica al modulo multimediale che il video è stato interrotto o messo in pausa in corrispondenza dell&#39;*offset* indicato.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      + (void) mediaStop:(NSString *)name offset:(double)offset; 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      [ADBMobile mediaStop:@"toonses" offset:30]; 
      ```

* **mediaClick:&#x200B;offset:**

   Notifica al modulo multimediale l&#39;avvenuto clic sull&#39;elemento multimediale.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      + (void) mediaClick:(NSString *)name offset:(double)offset;
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      [ADBMobile mediaClick:@"soManyCats" offset:47];
      ```

* **mediaTrack:&#x200B;withData:**

   Invia una chiamata Track Action (senza visualizzazioni pagina) per lo stato corrente dell&#39;elemento multimediale.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      + (void) mediaTrack:(NSString *)name withData:(NSDictionary *)data;
      ```
