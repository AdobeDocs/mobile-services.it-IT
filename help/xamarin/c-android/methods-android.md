---
description: Metodi Android per componenti Xamarin per soluzioni SDK 4.x di Experience Cloud.
keywords: Xamarin
seo-description: Metodi Android per componenti Xamarin per soluzioni SDK 4.x di Experience Cloud.
seo-title: Metodi Android
solution: Marketing Cloud, Sviluppatore
title: Metodi Android
uuid: 860 af 1 c 4-f 57 e -4 bcb -8308-4 e 316 da 9 a 27 b
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Android methods{#android-methods}

Metodi Android per componenti Xamarin per soluzioni SDK 4.x di Experience Cloud.

## Configuration methods {#section_405AA09390E346E5BB7B1F4E0F65F51E}

* **DebugLogging**

   Restituisce l'attuale preferenza di accesso di debug e il valore predefinito è false.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static Boolean DebugLogging;
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      getter: var debuglog = Config.DebugLogging;
      setter: Config.DebugLogging = (Java.Lang.Boolean)true;
      ```

* **LifetimeValue**

   Restituisce il valore "lifetime" del ciclo di vita dell'utente corrente.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static BigDecimal LifetimeValue; 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
       var lifetimeValue = Config.LifetimeValue;
      ```

* **PrivacyStatus**

   Restituisce la rappresentazione enum dello stato di privacy per l’utente corrente.
   * `ADBMobilePrivacyStatus.OptIn` - gli hit vengono inviati immediatamente.
   * `ADBMobilePrivacyStatus.OptOut` - gli hit vengono eliminati.
   * `ADBMobilePrivacyStatus.Unknown` - se è abilitato il tracciamento offline, gli hit vengono salvati finché lo stato di privacy non cambia quando l'utente acconsente (opt in, gli hit vengono inviati) o rinuncia (opt out, gli hit vengono eliminati). Se il tracciamento offline non è abilitato, gli hit vengono eliminati finché lo stato di privacy non cambia quando l'utente acconsente.
   Il valore predefinito è impostato nel file [ADBMobileConfig.json](/help/android/configuration/json-config/json-config.md).

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static MobilePrivacyStatus PrivacyStatus; 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      getter: var privacyStatus = Config.PrivacyStatus; 
      setter: Config.PrivacyStatus = MobilePrivacyStatus.MobilePrivacyStatusUnknown;
      ```


* **UserIdentifier**

   Se è stato impostato un identificatore personalizzato, restituisce questo identificatore. Se non viene impostato un identificatore personalizzato, restituisce null. Il valore predefinito è `null`.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static UserIdentifier();
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      getter: var userId = Config.UserIdentifier;
      setter: Config.UserIdentifier = "imBatman";
      ```

* **Versione**

   Ottiene la versione della libreria.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static string Version;
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      var version = ADBMobile.Version;
      ```

* **PauseCollectingLifecycleData**

   Indica all’SDK che l’applicazione è in pausa, in modo che le metriche del ciclo di vita vengano calcolate correttamente. Ad esempio, all'avvio della pausa recupera un timestamp per determinare la durata della sessione precedente. Inoltre, questo imposta un flag in modo che il ciclo di vita acquisisca correttamente che l'applicazione non si è bloccata. Per ulteriori informazioni, vedi [Metriche del ciclo di vita](/help/android/metrics.md).

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void PauseCollectingLifecycleData (); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      Config.PauseCollectingLifecycleData();
      ```

* **CollectLifecycleData (attività Activity)**

   (4.2 o versioni successive) Indica all'SDK che i dati del ciclo di vita devono essere raccolti per l'utilizzo in tutte le soluzioni nell'SDK. Per ulteriori informazioni, vedi [Metriche del ciclo di vita](/help/android/metrics.md).

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void collectLifecycleData(Activity activity); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      Config.CollectLifecycleData (this);
      ```

* **CollectLifecycleData (attività Activity)**

   (4.2 o versioni successive) Indica all'SDK che i dati del ciclo di vita devono essere raccolti per l'utilizzo in tutte le soluzioni nell'SDK. Per ulteriori informazioni, vedi [Metriche del ciclo di vita](/help/android/metrics.md).

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void collectLifecycleData(Activity activity, IDictionary<string, Object> context));
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      IDictionary<string, Java.Lang.Object> context = new Dictionary<string, 
      Java.Lang.Object> ();
      context.Add ("key", "value");
      Config.CollectLifecycleData (this, context);
      ```

* **OverrideConfigStream**

   (4.2 or later) Lets you load a different `ADBMobile JSON` config file when the application starts. La diversa configurazione viene utilizzata fino alla chiusura dell'applicazione.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void OverrideConfigStream (Stream stream);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      Stream st1 = Assets.Open ("ADBMobileConfig-2.json"); 
      Config.OverrideConfigStream (st1); 
      ```

* **SetLargeIconResourceId(int resourceId)**

   (4.2 o versione successiva) Imposta l'icona grande utilizzata per le notifiche create dall'SDK. Questa icona è l'immagine principale visualizzata quando l'utente visualizza la notifica completa nel Centro notifiche.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void SetLargeIconResourceId( int resourceId);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      Config.SetLargeIconResourceId(R.drawable.appIcon);
      ```

* **SetSmallIconResourceId(int resourceId)**

   (4.2 o versione successiva) Imposta l'icona piccola utilizzata per le notifiche create dall'SDK. Questa icona viene visualizzata nella barra di stato e corrisponde all'immagine secondaria visualizzata quando l'utente visualizza la notifica completa nel Centro notifiche.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void SetSmallIconResourceId( int resourceId); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
       Config.SetSmallIconResourceId(R.drawable.appIcon);
      ```

## Analytics methods {#section_63CF636104EF41F790C3E4190D755BBA}

* **TrackingIdentifier**

   Restituisce l’ID generato automaticamente per Analytics. Si tratta di un ID univoco specifico per l'app, che viene generato all'avvio iniziale e quindi memorizzato e utilizzato da quel momento in poi. Questo ID viene conservato tra gli aggiornamenti dell'app e rimosso alla disinstallazione.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static string TrackingIdentifier;
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      Var trackingId = Analytics.TrackingIdentifier
      ```

* **TrackState**

   Tiene traccia dello stato di un'app con dati contestuali facoltativi. `States`sono le visualizzazioni disponibili nell'applicazione, come "schermata del titolo", "livello 1", "pausa" e così via. Questi stati sono simili alle pagine di un sito Web e le chiamate `TrackState` incrementano le visualizzazioni di pagina. Se lo stato è vuoto, viene visualizzato come "nome app versione app (build)" nei report. Se visualizzi questo valore nel report, assicurati che lo stato in ogni chiamata sia impostato su `TrackState`.

   >[!TIP]
   >
   >Questa è l'unica chiamata di tracciamento che incrementa le visualizzazioni di pagina.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void TrackState (string state, IDictionary<string, Object> cdata); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      var cdata = new Dictionary<string, Java.Lang.Object>(); 
      cdata.Add ("key", (Java.Lang.Object)"value"); 
      Analytics.TrackState ("stateName", (IDictionary<string, 
      Java.Lang.Object>)cdata);
      ```

* **TrackAction**

   Monitora un'azione nell'applicazione. Le azioni sono gli eventi che avvengono nell'applicazione e che desideri misurare, come "morti", "livello acquisito", "iscrizioni al feed" e altri parametri.

   >[!TIP]
   >
   >
   >If you have code that might run while the app is in the background (for example, a background data retrieval), use `trackActionFromBackground` instead.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void TrackAction(string action, IDictionary<string,Object> cdata); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      var cdata = new Dictionary<string, Java.Lang.Object> (); 
      cdata.Add ("key", (Java.Lang.Object)"value");
      Analytics.TrackAction ("actionName", (IDictionary<string, 
      Java.Lang.Object>)cdata);
      ```

* **TrackLocation**

   Invia le coordinate di latitudine e longitudine correnti. Also uses points of interest defined in the `ADBMobileConfig.json` file to determine whether the location that was provided as a parameter is in any of your POIs. Se le coordinate correnti si trovano in un POI definito, una variabile di dati di contesto viene compilata e inviata insieme alla chiamata `TrackLocation`.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void TrackLocation(Location location, IDictionary<string, Object> cdata); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
       Location loc = new Location(LocationManager.GpsProvider);;
       loc.Latitude = 111; 
       loc.Longitude = 44; 
       loc.Accuracy = 5; 
       Analytics.TrackLocation (loc, null);
      ```

* **TrackBeacon**

   Monitora quando un utente arriva in prossimità di un beacon.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void TrackBeacon (string uuid, string major, string minor,  Analytics.BEACON_PROXIMITY prox, IDictionary<string, Object> cdata); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      Analytics.TrackBeacon ("UUID", "1", "2", 
      Analytics.BEACON_PROXIMITY.ProximityImmediate, null); 
      ```

* **ClearBeacon**

   Elimina i dati del beacon dopo che un utente si allontana dalle vicinanze del beacon.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void TrackingClearCurrentBeacon();
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      Analytics.ClearBeacon(); 
      ```

* **TrackLifetimeValueIncrease**

   Aggiunge un incremento al valore "lifetime" del ciclo di vita dell'utente.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void TrackLifetimeValueIncrease (double amount, IDictionary<string,Object> cdata); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      Analytics.TrackLifetimeValueIncrease(5,null);
      ```

* **TrackTimedActionStart**

   Avvia un'azione temporizzata con il nome action. Se invochi questo metodo per un'azione già avviata, l'azione temporizzata precedente viene sovrascritta.

   >[!TIP]
   >
   > Questa chiamata non invia un hit.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void TrackTimedActionStart(string action,IDictionary<string, Object> cdata); 
      ```

   * Esempio di codice per questo metodo:

      ```java
      Analytics.TrackTimedActionStart("level2", null);
      ```

* **TrackTimedActionUpdate**

   Passa i dati con cui aggiornare i dati contestuali associati all'azione. I dati trasmessi vengono aggiunti in coda ai dati esistenti per l'azione, e li sovrascrivono se per l'azione è già definita la stessa chiave.

   >[!TIP]
   >
   >Questa chiamata non invia un hit.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void TrackTimedActionUpdate(string action, IDictionary<string, Object> cdata); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      var updatedData = new Dictionary<string, Java.Lang.Object> (); 
      cdata.Add ("key", (Java.Lang.Object)"value"); 
      Analytics.TrackTimedActionUpdate("level2", updatedData); 
      ```

* **TrackTimedActionEnd**

   Termina un'azione temporizzata.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void TrackTimedActionEnd(string action,
        Analytics.ITimedActionBlock block);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      Analytics.TrackTimedActionEnd ("level2", new TimedActionBlock()); 
           class TimedActionBlock: Java.Lang.Object, 
      Analytics.ITimedActionBlock{ 
           public Java.Lang.Object Call (long inAppDuration, long 
      totalDuration IDictionary<string, Java.Lang.Object> contextData){ 
           return Java.Lang.Boolean.True; 
        } 
      }
      ```

* **TrackingTimedActionExists**

   Restituisce un valore che indica se un'azione temporizzata è in corso o meno.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static bool TrackingTimedActionExists(string action); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      var level2InProgress = Analytics.TrackingTimedActionExists("level2"); 
      ```

* **SendQueuedHits**

   Forza l'invio da parte della libreria di tutti gli hit nella coda offline, indipendentemente dal numero di hit attualmente presenti nella coda.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void SendQueuedHits();
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      Analytics.SendQueuedHits(); 
      ```

* **ClearQueue**

   Elimina tutti gli hit dalla coda offline.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void ClearQueue(); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      Analytics.ClearQueue(); 
      ```

* **QueueSize**

   Recupera il numero di hit attualmente presenti nella coda offline.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static long QueueSize(); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      var queueSize = Analytics.QueueSize();
      ```

## Experience Cloud ID methods {#section_157919E46030443DBB5CED60D656AD9F}

* **MarketingCloudId**

   Recupera l'Experience Cloud ID dal servizio ID.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static string MarketingCloudId;
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      var mcid = Visitor.MarketingCloudId;
      ```

* **SyncIdentifiers**

   Utilizzando l’ID Experience Cloud, è possibile impostare ID cliente aggiuntivi da associare a ciascun visitatore. L'API Visitor accetta più ID cliente per lo stesso visitatore, con un identificatore del tipo di cliente che consente di distinguere l'ambito dei diversi ID cliente. Questo metodo corrisponde a `setCustomerIDs` nella libreria JavaScript.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void SyncIdentifiers((IDictionary<string> identifiers);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      IDictionary<string,string> ids = new Dictionary<string, string> ();
      ids.Add ("pushID", ;"value2");
      Visitor.SyncIdentifiers (ids);
      ```

## Target methods {#section_C1E4121CAF9D43538511D857A1F549A7}

* **LoadRequest**

   Sends a request to your configured Target server and returns the string value of the offer generated in a `Action<NSDictionary>` callback.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void LoadRequest (TargetLocationRequest request, Target.ITargetCallback callback); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      class TargetBlock: Java.Lang.Object, Target.ITargetCallback{ 
          public void Call (Java.Lang.Object content) 
         { 
          Console.WriteLine (content.ToString()); 
         } 
      } 
      var req = Target.CreateRequest ("AndroidTest", "defGal", parameters); 
           Target.LoadRequest (req, new TargetBlock()); 
      ```

* **CreateRequest**

   Costruttore di convenienza per creare un oggetto `ADBTargetLocationRequest` con i parametri indicati.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static TargetLocationRequest TargetCreateRequest(string name,string defaultContent,IDictionary<string,string> parameters); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      IDictionary<string, Java.Lang.Object> parameters = new Dictionary> string, Java.Lang.Object> (); 
          parameters.Add ("key1", "value2"); 
      var req = Target.CreateRequest ("AndroidTest", "defGal", parameters); 
      ```

* **CreateOrderConfirmRequest**

   Crea un `ADBTargetLocationRequest`.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static TargetLocationRequest TargetCreateRequest (string name, string defaultContent, IDictionary<;string, string> parameters);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      var orderConfirm = Target.CreateOrderConfirmRequest ("myOrder", "12345", "29.41", "cool stuff", null); 
      ```

* **ClearCookies**

   Cancella i cookie di Target dall'app.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void ClearCookies(); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      Target.ClearCookies (); 
      ```

## Audience Manager {#section_862C4202B6294B978DEEBB15C5CD5C01}

* **VisitorProfile**

   Restituisce il profilo del visitatore ottenuto più di recente. Restituisce nil se non è stato ancora inviato alcun segnale. Il profilo del visitatore viene salvato in `NSUserDefaults` in modo da essere facilmente accessibile per diversi avvii dell'applicazione.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static IDictionary<string, Object> VisitorProfile; 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      NSDictionary profile = AudienceManager.VisitorProfile; 
      ```

* **Dpid**

   Returns the current `DPID`.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static string Dpuuid; 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      string currentDpid = AudienceManager.Dpid;
      ```

* **Dpuuid**

   Returns the current `DPUUID`.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static string AudienceDpuuid; 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      string currentDpuuid = AudienceManager.Dpuuid;
      ```

* **AudienceSetDpidAndDpuuid**

   Imposta l' `dpid` e `dpuuid`. If `dpid` and `dpuuid` are set, they are sent with each signal.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void AudienceSetDpidAndDpuuid (string Dpid, String Dpuuid);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      AudienceManager.SetDpidAndDpuuid ("testDpid", "testDpuuid");
      ```

* **SignalWithData**

   Sends audience management a signal with traits and get the matching segments returned in a `Action<NSDictionary>` callback.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void SignalWithData (IDictionary<string, Object> audienceData, AudienceManager.IAudienceManagerCallback callback); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      class AudienceManagerCallback: Java.Lang.Object, 
       AudienceManager.IAudienceManagerCallback{ 
         public void Call (Java.Lang.Object content) 
        {
          Console.WriteLine (content.ToString()); 
        }
      }
      IDictionary<string, Java.Lang.Object> traits = new Dictionary<string, 
      Java.Lang.Object> (); 
         traits.Add ("trait", "b");
      AudienceManager.SignalWithData (traits, new AudienceManagerCallback());
      ```

* **Reset**

   Ripristina l'`UUID` di Audience Manager ed elimina il profilo del visitatore corrente.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void Reset ();
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
       AudienceManager.Reset ();
      ```

## Video {#section_CBCE1951CE204A108AD4CA7BB07C7F98}

Per ulteriori informazioni su Video Analytics, consulta [Analisi video](/help/android/analytics-main/video-qs.md).

* **MediaSettings**

   Restituisce un oggetto `MediaSettings` con i parametri specificati.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static MediaSettings SettingsWith (string name, double length, string playerName, string playerID);  
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      MediaSettings settings = Media.SettingsWith("name1", 10, "playerName1", "playerID1");
      ```

* **AdSettingsWith**

   Restituisce un oggetto `MediaSettings` per l'uso con il monitoraggio di un video annuncio.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static MediaSettings AdSettingsWith ( string name, double length, 
        string playerName, string parentName, string parentPod, 
      double parentPodPosition, string CPM); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      MediaSettings adSettings = Media.AdSettingsWith ("adName1", 2, "playerName1", "name1", "podName1", 4, "CPM1"); 
      ```

* **Open**

   Apre un oggetto `ADBMediaSettings` per il monitoraggio.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void Open (MediaSettings settings, Media.IMediaCallback callback);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      MediaSettings settings = Media.SettingsWith ("name1", 10, "playerName1", "playerID1"); 
         Media.Open (settings, new MediaCallback()); 
         class MediaCallback: Java.Lang.Object, Media.IMediaCallback{ 
      public void Call (Java.Lang.Object content) 
      {
      }
      }
      ```

* **Close**

   Chiude il nome denominato dell'elemento multimediale.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void Close(string name);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      Media.Close (settings.Name); 
      ```

* **Riproduci**

   Riproduce il nome denominato dell'elemento multimediale in corrispondenza dell'offset indicato (in secondi).

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void Play ( string name, double offset); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      Media.Play (settings.Name, 0); 
      ```

* **Completa**

   Contrassegna manualmente l'elemento multimediale come completato in corrispondenza dell'offset indicato (in secondi).

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void Complete (string name, double offset); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      Media.Complete (settings.Name, 5); 
      ```

* **Stop**

   Notifica al modulo multimediale che il video è stato arrestato o messo in pausa in corrispondenza dell'offset indicato.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void Stop ( string name, double offset); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      Media.Stop (settings.Name, 3);
      ```

* **Clic**

   Notifica al modulo multimediale l'avvenuto clic sull'elemento multimediale.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void Click ( string name, double offset); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      Media.Click (settings.Name, 3); 
      ```

* **Track**

   Invia una chiamata Track Action (senza visualizzazioni pagina) per lo stato corrente dell'elemento multimediale.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void Track ( string name, NSDictionary data); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      Media.Track (settings.Name, null); 
      ```