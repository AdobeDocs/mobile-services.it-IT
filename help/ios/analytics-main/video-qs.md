---
description: Queste informazioni spiegano come misurare i video su iOS mediante la misurazione di specifici eventi video.
seo-description: Queste informazioni spiegano come misurare i video su iOS mediante la misurazione di specifici eventi video.
seo-title: Analisi del video
solution: Marketing Cloud,Analytics
title: Analisi del video
topic: Sviluppatore e implementazione
uuid: d75fa415-78f6-4f50-a563-76949f040138
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Analisi del video {#video-analytics}

Queste informazioni spiegano come misurare i video su iOS mediante la misurazione di specifici eventi video.

>[!TIP]
>
>Durante la riproduzione video, vengono inviate a questo servizio frequenti chiamate "heartbeat" per misurare il tempo di riproduzione. Tali chiamate heartbeat sono inviate ogni 10 secondi e consentono di ottenere metriche di coinvolgimento dettagliate e rapporti più precisi sull'abbandono. Per ulteriori informazioni, consultate [Misurazione di audio e video in Adobe Analytics](https://docs.adobe.com/content/help/en/media-analytics/using/media-overview.html).

Il processo generale da seguire per la misurazione dei video è molto simile per tutte le piattaforme. Di seguito viene fornita una panoramica di base delle attività di sviluppo, con esempi di codice.

## Map player events to Analytics variables {#section_E84987F878AB4A3A83AE700FEC4C9D4D}

Nella tabella seguente sono elencati i dati multimediali inviati ad Analytics. Utilizza le regole di elaborazione per mappare i dati contestuali a una variabile Analytics.

* **a.media.name**

   (Obbligatorio) Raccoglie il nome del video, in base a quanto specificato nell'implementazione, quando un visitatore visualizza il video in qualche modo. Per questa variabile puoi aggiungere delle classificazioni.

   (Facoltativo) La variabile Insight personalizzato fornisce informazioni sul percorso del video.

   * Tipo di variabile: eVar
   * Scadenza predefinita: visita
   * Insight personalizzato (s.prop, usato per il percorso del video)

* **a.media.name**

   (Facoltativo) Fornisce informazioni sul percorso del video. Il percorso deve essere abilitato per questa variabile dall'Assistenza clienti.

   * Tipo di variabile: Custom Insight (s.prop)
   * Tipo evento: Insight personalizzato (s.prop)

* **a.media.segment**

   (Obbligatorio) Raccoglie dati sui segmenti video, tra cui il nome del segmento e l'ordine in cui il segmento appare nel video. Quando viene eseguito il tracciamento automatico degli eventi del lettore, questa variabile viene compilata abilitando la variabile `segmentByMilestones`. Quando gli eventi del lettore vengono tracciati manualmente, viene compilata impostando un nome di segmento personalizzato. For example, when a visitor views the first segment in a video, SiteCatalyst might collect the following in the `1:M:0-25` Segments evar.

   Il metodo predefinito di raccolta dei dati video raccoglie i dati presso i seguenti punti:

   * inizio video (play)
   * inizio del segmento
   * fine del video (stop)
   Analytics conta la visualizzazione del primo segmento all'inizio del segmento, quando il visitatore inizia la visualizzazione. Il segmento successivo viene visualizzato quando inizia il segmento.

   * Tipo di variabile: eVar
   * Scadenza predefinita: visualizzazioni pagina


* **a.contentType**

   Raccoglie dati relativi al tipo di contenuto visualizzato da un visitatore. Agli hit inviati dalla misurazione è assegnato il tipo di contenuto `video`video. Non è necessario riservare questa variabile esclusivamente al tracciamento video. Se la stessa variabile viene usata anche per ottenere il tipo di altri contenuti, è possibile analizzare la distribuzione dei visitatori per diversi tipi di contenuto. Ad esempio, puoi usare questa variabile per assegnare valori quali "articolo" o "pagina prodotto" ad altri tipi di contenuti. Dal punto di vista della misurazione video, il tipo di contenuto ti consente di identificare i visitatori del video e di calcolare i tassi di conversione relativi al video.

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

* **a.media.complete**

   Indica che un utente ha visualizzato un video completo. Per impostazione predefinita, l'evento completo è misurato 1 secondo prima della fine del video. Durante l'implementazione, puoi specificare quanti secondi dalla fine del video considerare come una visualizzazione dell'intero video. Per i video live e altri flussi che non hanno una fine definita, puoi specificare un punto personalizzato per misurare le visualizzazioni complete, ad esempio, dopo che il video è stato visualizzato per una data quantità di tempo.

   * Tipo di variabile: Evento
   * Tipo: contatore

## Configure media settings {#section_929945D4183C428AAF3B983EFD3E2500}

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
// Note the the mediaPlay, mediaStop and mediaClose methods are called in the 
// event handlers described in the next section
```

## Track player events {#section_C7F43AECBC0D425390F7FCDF3035B65D}

To measure video playback, The `mediaPlay`, `mediaStop`, and `mediaClose` methods need to be called at the appropriate times. Ad esempio, `mediaStop` deve essere invocato quando il lettore viene messo in pausa e `mediaPlay` quando la riproduzione viene avviata o ripresa.

L'esempio di seguito illustra come configurare le notifiche e invocare i metodi per i file multimediali per ottenere le misurazioni relative ai video:

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

## Media measurement class and method reference {#section_50DF9359A7B14DF092634C8E913C77FE}

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

   Restituisce un oggetto `ADBMediaSettings` per l'uso con il monitoraggio di un video annuncio.

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

   Chiude l'elemento multimediale denominato *name*.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
       + (void) mediaClose:(NSString *)name; 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      [ADBMobile mediaClose:@"kittiesPlaying"];
      ```

* **mediaPlay:&#x200B;offset:**

   Riproduce l'elemento multimediale denominato *name* in corrispondenza dell'*offset* indicato (in secondi).

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
       + (void) mediaPlay:(NSString *)name offset:(double)offset;
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      [ADBMobile mediaPlay:@"cats" offset:25];
      ```

* **mediaComplete:&#x200B;offset:**

   Contrassegna manualmente l'elemento multimediale come completato in corrispondenza dell'*offset* indicato (in secondi).

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
       + (void) mediaComplete:(NSString *)name offset:(double)offset;
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
       [ADBMobile mediaComplete:@"meowzah" offset:90]; 
      ```

* **mediaStop:&#x200B;offset:**

   Notifica al modulo multimediale che il video è stato interrotto o messo in pausa in corrispondenza dell'*offset* indicato.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      + (void) mediaStop:(NSString *)name offset:(double)offset; 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      [ADBMobile mediaStop:@"toonses" offset:30]; 
      ```

* **mediaClick:&#x200B;offset:**

   Notifica al modulo multimediale l'avvenuto clic sull'elemento multimediale.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      + (void) mediaClick:(NSString *)name offset:(double)offset;
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      [ADBMobile mediaClick:@"soManyCats" offset:47];
      ```

* **mediaTrack:&#x200B;withData:**

   Invia una chiamata Track Action (senza visualizzazioni pagina) per lo stato corrente dell'elemento multimediale.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      + (void) mediaTrack:(NSString *)name withData:(NSDictionary *)data;
      ```

