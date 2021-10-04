---
description: Metodi Android per i componenti Xamarin per l'SDK 4.x delle soluzioni Experience Cloud.
keywords: Xamarina
solution: Experience Cloud
title: Metodi per Android
uuid: 860af1c4-f57e-4bcb-8308-4e316da9a27b
exl-id: 0de1fa11-37e9-49be-8d42-a13cb4a3f0e3
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '1755'
ht-degree: 68%

---

# Metodi per Android{#android-methods}

Metodi Android per i componenti Xamarin per l&#39;SDK 4.x delle soluzioni Experience Cloud.

## Metodi di configurazione {#section_405AA09390E346E5BB7B1F4E0F65F51E}

* **DebugLogging**

   Restituisce l&#39;attuale preferenza di accesso di debug e l&#39;impostazione predefinita è false.

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

   Restituisce il valore &quot;lifetime&quot; del ciclo di vita dell&#39;utente corrente.

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
   * `ADBMobilePrivacyStatus.Unknown` - se è abilitato il tracciamento offline, gli hit vengono salvati finché lo stato di privacy non cambia quando l&#39;utente acconsente (opt in, gli hit vengono inviati) o rinuncia (opt out, gli hit vengono eliminati). Se il tracciamento offline non è abilitato, gli hit vengono eliminati finché lo stato di privacy non cambia quando l&#39;utente acconsente.

   Il valore predefinito è impostato nel file [ADBMobileConfig.json](/help/android/configuration/json-config/json-config.md) .

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

   Se è stato impostato un identificatore personalizzato, restituisce questo identificatore. Se non è impostato un identificatore personalizzato, restituisce null. Il valore predefinito è `null`.

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

   Indica all&#39;SDK che l&#39;applicazione è in pausa, in modo che le metriche del ciclo di vita vengano calcolate correttamente. Ad esempio, al momento della pausa recupera una marca temporale per determinare la lunghezza della sessione precedente. Inoltre, imposta un flag in modo che il ciclo di vita acquisisca correttamente che l&#39;app non si è bloccata. Per ulteriori informazioni, vedi [Metriche del ciclo di vita](/help/android/metrics.md).

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void PauseCollectingLifecycleData (); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      Config.PauseCollectingLifecycleData();
      ```

* **CollectLifecycleData (attività Activity)**

   (4.2 o versioni successive) Indica all&#39;SDK che i dati del ciclo di vita devono essere raccolti per l&#39;utilizzo in tutte le soluzioni nell&#39;SDK. Per ulteriori informazioni, vedi [Metriche del ciclo di vita](/help/android/metrics.md).

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void collectLifecycleData(Activity activity); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      Config.CollectLifecycleData (this);
      ```

* **CollectLifecycleData (attività Activity)**

   (4.2 o versioni successive) Indica all&#39;SDK che i dati del ciclo di vita devono essere raccolti per l&#39;utilizzo in tutte le soluzioni nell&#39;SDK. Per ulteriori informazioni, vedi [Metriche del ciclo di vita](/help/android/metrics.md).

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

   (4.2 o versioni successive) Consente di caricare un file di configurazione diverso `ADBMobile JSON` all&#39;avvio dell&#39;applicazione. La configurazione diversa viene utilizzata fino alla chiusura dell’applicazione.

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

   (4.2 o versioni successive) Imposta l’icona grande utilizzata per le notifiche create dall’SDK. Questa icona è l&#39;immagine principale visualizzata dall&#39;utente nella notifica completa all&#39;interno del Centro notifiche.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void SetLargeIconResourceId( int resourceId);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      Config.SetLargeIconResourceId(R.drawable.appIcon);
      ```

* **SetSmallIconResourceId(int resourceId)**

   (4.2 o versioni successive) Imposta l’icona piccola utilizzata per le notifiche create dall’SDK. Questa icona viene visualizzata nella barra di stato e rappresenta l’immagine secondaria mostrata quando l’utente visualizza la notifica completa nel centro notifiche.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void SetSmallIconResourceId( int resourceId); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
       Config.SetSmallIconResourceId(R.drawable.appIcon);
      ```

## Metodi di Analytics {#section_63CF636104EF41F790C3E4190D755BBA}

* **TrackingIdentifier**

   Restituisce l&#39;ID generato automaticamente per Analytics. Si tratta di un ID univoco specifico per l’app, generato all’avvio iniziale e quindi memorizzato e utilizzato da quel momento in poi. Questo ID viene mantenuto nei successivi aggiornamenti dell’app e rimosso al momento della disinstallazione.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static string TrackingIdentifier;
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      Var trackingId = Analytics.TrackingIdentifier
      ```

* **TrackState**

   Tiene traccia dello stato di un&#39;app con dati contestuali facoltativi. `States` sono le visualizzazioni disponibili nell’app, ad esempio &quot;schermata del titolo&quot;, &quot;livello 1&quot;, &quot;pausa&quot; e così via. Questi stati sono simili alle pagine di un sito Web e le chiamate `TrackState` incrementano le visualizzazioni di pagina. Se state è vuoto, nei rapporti viene visualizzato come &quot;app name app version (build)&quot;. Se trovi questo valore nei rapporti, assicurati che in ogni chiamata `TrackState` sia impostato lo stato .

   >[!TIP]
   >
   >Questa è l&#39;unica chiamata di tracciamento che incrementa le visualizzazioni pagina.

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

   Tiene traccia di un&#39;azione nell&#39;applicazione. Le azioni sono gli eventi che avvengono nell’app e che desideri misurare, come &quot;morti&quot;, &quot;livello acquisito&quot;, &quot;abbonamenti ai feed&quot; e altre metriche.

   >[!TIP]
   >
   >
   >In presenza di codice che potrebbe essere eseguito mentre l&#39;applicazione è in background (ad esempio, un recupero di dati in background), utilizza piuttosto `trackActionFromBackground`.

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

   Invia le coordinate di latitudine e longitudine correnti. Utilizza anche i punti di interesse definiti nel file `ADBMobileConfig.json` per determinare se la posizione fornita come parametro si trova nel raggio di riferimento di un POI. Se le coordinate correnti si trovano in un POI definito, una variabile di dati di contesto viene compilata e inviata insieme alla chiamata `TrackLocation`.

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

   Aggiunge un incremento al valore &quot;lifetime&quot; del ciclo di vita dell&#39;utente.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void TrackLifetimeValueIncrease (double amount, IDictionary<string,Object> cdata); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      Analytics.TrackLifetimeValueIncrease(5,null);
      ```

* **TrackTimedActionStart**

   Avvia un&#39;azione temporizzata con il nome action. Se invochi questo metodo per un&#39;azione già avviata, l&#39;azione temporizzata precedente viene sovrascritta.

   >[!TIP]
   >
   > Questa chiamata non invia un hit.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void TrackTimedActionStart(string action,IDictionary<string, Object> cdata); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      Analytics.TrackTimedActionStart("level2", null);
      ```

* **TrackTimedActionUpdate**

   Passa i dati per aggiornare i dati contestuali associati all’azione in questione. I dati passati vengono aggiunti alla fine dei dati esistenti per l&#39;azione, e li sovrascrivono se per l&#39;azione è già definita la stessa chiave.

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

   Termina un&#39;azione temporizzata.

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

   Restituisce un valore che indica se un&#39;azione temporizzata è in corso o meno.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static bool TrackingTimedActionExists(string action); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      var level2InProgress = Analytics.TrackingTimedActionExists("level2"); 
      ```

* **SendQueuedHits**

   Forza l&#39;invio da parte della libreria di tutti gli hit nella coda offline, indipendentemente dal numero di hit attualmente presenti nella coda.

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

* **DimensioneCoda**

   Recupera il numero di hit attualmente presenti nella coda offline.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static long QueueSize(); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      var queueSize = Analytics.QueueSize();
      ```

## Metodi Experience Cloud ID {#section_157919E46030443DBB5CED60D656AD9F}

* **MarketingCloudId**

   Recupera l&#39;Experience Cloud ID dal servizio ID.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static string MarketingCloudId;
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      var mcid = Visitor.MarketingCloudId;
      ```

* **SyncIdentifiers**

   Con l’ID Experience Cloud, puoi impostare ID cliente aggiuntivi da associare a ogni visitatore. L’API visitatore accetta più ID cliente per lo stesso visitatore, con un identificatore del tipo di cliente per separare l’ambito dei diversi ID cliente. Questo metodo corrisponde a `setCustomerIDs` nella libreria JavaScript.

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

## Metodi di Target {#section_C1E4121CAF9D43538511D857A1F549A7}

* **LoadRequest**

   Invia una richiesta al server di Target configurato e restituisce il valore stringa dell&#39;offerta generata in un callback `Action<NSDictionary>`.

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

   Costruttore di convenienza per creare un oggetto `ADBTargetLocationRequest` con i parametri specificati.

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

   Crea una `ADBTargetLocationRequest`.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static TargetLocationRequest TargetCreateRequest (string name, string defaultContent, IDictionary<;string, string> parameters);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      var orderConfirm = Target.CreateOrderConfirmRequest ("myOrder", "12345", "29.41", "cool stuff", null); 
      ```

* **ClearCookies**

   Elimina i cookie di Target dall’app.

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

   Restituisce il profilo del visitatore ottenuto più di recente. Restituisce nil se non è stato ancora inviato alcun segnale. Il profilo del visitatore viene salvato in `NSUserDefaults` in modo da essere facilmente accessibile per diversi avvii dell&#39;applicazione.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static IDictionary<string, Object> VisitorProfile; 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      NSDictionary profile = AudienceManager.VisitorProfile; 
      ```

* **Dpid**

   Restituisce il `DPID` corrente.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static string Dpuuid; 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      string currentDpid = AudienceManager.Dpid;
      ```

* **Dpuuid**

   Restituisce il `DPUUID` corrente.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static string AudienceDpuuid; 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      string currentDpuuid = AudienceManager.Dpuuid;
      ```

* **AudienceSetDpidAndDpuuid**

   Imposta i valori `dpid` e `dpuuid`. Se sono impostati `dpid` e `dpuuid`, questi vengono inviati con ciascun segnale.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void AudienceSetDpidAndDpuuid (string Dpid, String Dpuuid);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      AudienceManager.SetDpidAndDpuuid ("testDpid", "testDpuuid");
      ```

* **SignalWithData**

   Invia a Gestione dell&#39;audience un segnale con caratteristiche e fa sì che i segmenti corrispondenti vengano restituiti in un callback `Action<NSDictionary>`.

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

* **Ripristino**

   Ripristina audience manager `UUID` ed elimina il profilo del visitatore corrente.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void Reset ();
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
       AudienceManager.Reset ();
      ```

## Video {#section_CBCE1951CE204A108AD4CA7BB07C7F98}

Per ulteriori informazioni su Video Analytics, consulta [Video Analytics](/help/android/analytics-main/video-qs.md).

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

   Restituisce un oggetto `MediaSettings` per l&#39;uso con il monitoraggio di un video annuncio.

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

* **Chiudi**

   Chiude l&#39;elemento multimediale denominato name.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void Close(string name);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      Media.Close (settings.Name); 
      ```

* **Play**

   Riproduce l&#39;elemento multimediale denominato name in corrispondenza dell&#39;offset indicato (in secondi).

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void Play ( string name, double offset); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      Media.Play (settings.Name, 0); 
      ```

* **Completa**

   Contrassegna manualmente l&#39;elemento multimediale come completato in corrispondenza dell&#39;offset indicato (in secondi).

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void Complete (string name, double offset); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      Media.Complete (settings.Name, 5); 
      ```

* **Interruzione**

   Notifica al modulo multimediale che il video è stato interrotto o messo in pausa in corrispondenza dell&#39;offset indicato.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void Stop ( string name, double offset); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      Media.Stop (settings.Name, 3);
      ```

* **Click**

   Notifica al modulo multimediale l&#39;avvenuto clic sull&#39;elemento multimediale.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void Click ( string name, double offset); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      Media.Click (settings.Name, 3); 
      ```

* **Traccia**

   Invia una chiamata Track Action (senza visualizzazioni pagina) per lo stato corrente dell&#39;elemento multimediale.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void Track ( string name, NSDictionary data); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      Media.Track (settings.Name, null); 
      ```
