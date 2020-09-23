---
description: Metodi iOS per componenti Xamarin per  soluzioni SDK 4.x per Experienci Cloud.
keywords: Xamarin
seo-description: Metodi iOS per componenti Xamarin per  soluzioni SDK 4.x per Experienci Cloud.
seo-title: Metodi per iOS
solution: Experience Cloud
title: Metodi per iOS
uuid: d6a056db-80c1-44d0-970f-c961ad01b0bc
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '1749'
ht-degree: 70%

---


# Metodi per iOS{#ios-methods}

Metodi iOS per componenti Xamarin per  soluzioni SDK 4.x per Experienci Cloud.

## Metodi di configurazione {#section_405AA09390E346E5BB7B1F4E0F65F51E}

* **CollectLifecycleData**

   Indica all&#39;SDK che i dati del ciclo di vita devono essere raccolti per l&#39;utilizzo in tutte le soluzioni dell&#39;SDK. Per ulteriori informazioni, vedi [Metriche del ciclo di vita](/help/ios/metrics.md).

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      public static void CollectLifecycleData();
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      ADBMobile.CollectLifecycleData();
      ```

* **DebugLogging**

   Restituisce l&#39;attuale preferenza di accesso di debug. Il valore predefinito è `false`.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      public static bool DebugLogging(); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      var debugEnabled = ADBMobile.DebugLogging();
      ```

* **SetDebugLogging**

   Imposta la preferenza di accesso di debug su enabled.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      public static void SetDebugLogging(bool enabled);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      ADBMobile.SetDebugLogging(true);
      ```

* **LifetimeValue**

   Restituisce il valore &quot;lifetime&quot; del ciclo di vita dell&#39;utente corrente.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      public static double LifetimeValue();
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      var lifetimeValue = ADBMobile.LifetimeValue();
      ```

* **PrivacyStatus**

   Restituisce la rappresentazione enum dello stato di privacy per l’utente corrente.
   * `ADBMobilePrivacyStatus.OptIn` - gli hit vengono inviati immediatamente.
   * `ADBMobilePrivacyStatus.OptOut` - gli hit vengono eliminati.
   * ADBMobilePrivacyStatus.Unknown - Se è abilitato il tracciamento offline, gli hit vengono salvati fino alla modifica dello stato di privacy, quando l’utente acconsente (opt in, gli hit vengono inviati) o rinuncia (opt out, gli hit vengono scartati). Se il tracciamento offline è disattivato, gli hit vengono scartati fino a quando lo stato di privacy non cambia quando l’utente acconsente.

   The default value is set in the [ADBMobileConfig.json](/help/ios/configuration/json-config/json-config.md).

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      public static ADBPrivacyStatus PrivacyStatus();
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      var privacyStatus = ADBMobile.PrivacyStatus();
      ```


* **SetPrivacyStatus**

   Imposta lo stato di privacy per l’utente corrente su status. Imposta uno dei valori seguenti:
   * `ADBMobilePrivacyStatus.OptIn` - gli hit vengono inviati immediatamente.
   * `ADBMobilePrivacyStatus.OptOut` - gli hit vengono eliminati.
   * `ADBMobilePrivacyStatus.Unknown`  - se è abilitato il tracciamento offline, gli hit vengono salvati finché lo stato di privacy non cambia quando l&#39;utente acconsente (opt in, gli hit vengono inviati) o rinuncia (opt out, gli hit vengono eliminati). Se il tracciamento offline non è abilitato, gli hit vengono eliminati finché lo stato di privacy non cambia quando l&#39;utente acconsente.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      public static void SetPrivacyStatus(ADBPrivacyStatus status) 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      ADBMobile.SetPrivacyStatus(ADBMobilePrivacyStatus.OptIn); 
      ```

* **UserIdentifier**

   Restituisce l’identificatore utente personalizzato se è stato impostato un identificatore personalizzato. Restituisce null se non è impostato un identificatore personalizzato. Il valore predefinito è `null`.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      public static string UserIdentifier(); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      var userId = ADBMobile.UserIdentifier(); 
      ```

* **SetUserIdentifier**

   Restituisce l’identificatore utente personalizzato se è stato impostato un identificatore personalizzato. Restituisce null se non è impostato un identificatore personalizzato. Il valore predefinito è `null`.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      public static string UserIdentifier();
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      ADBMobile.SetUserIdentifier ("customUserIdentifier”); 
      ```

* **GetVersion**

   Ottiene la versione della libreria.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      public static string Version();
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      var version = ADBMobile.Version();
      ```

* **KeepLifecycleSessionAlive (solo iOS)**

   Indica all&#39;SDK che la prossima ripresa dal background non rappresenta l&#39;avvio di una nuova sessione, indipendentemente dal valore di timeout della sessione del ciclo di vita nel file di configurazione.

   >[!TIP]
   >
   >Questo metodo è destinato alle app che si registrano per le notifiche mentre sono in background e dovrebbe essere invocato solo dal codice in esecuzione mentre l’app è in background.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      public static void KeepLifecycleSessionAlive();
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      ADBMobile.KeepLifecycleSessionAlive();
      ```

## Metodi di Analytics {#section_63CF636104EF41F790C3E4190D755BBA}

* **TrackingIdentifier**

   Recupera l&#39;identificativo di monitoraggio di Analytics.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      public static string TrackingIdentifier();
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      var trackingId = ADBMobile.TrackingIdentifier();
      ```

* **TrackState**

   Tiene traccia dello stato di un&#39;app con dati contestuali facoltativi. Gli stati sono le visualizzazioni disponibili nell’app, ad esempio &quot;schermata del titolo&quot;, &quot;livello 1&quot;, &quot;pausa&quot; e così via. Questi stati sono simili alle pagine di un sito Web e `TrackState` le chiamate incrementano le visualizzazioni di pagina. Se state è vuoto, nei rapporti viene visualizzato come &quot;app name app version (build)&quot;. If you see this value in reports, make sure you are setting state in each `TrackState` call.

   >[!TIP]
   >
   >Questa è l&#39;unica chiamata di tracciamento che incrementa le visualizzazioni pagina.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      public static void TrackState(string state, NSDictionary cdata); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      NSDictionary contextData; 
       contextData = NSDictionary.FromObjectAndKey (NSObject.FromObject("val"),NSObject.FromObject("key")); 
        ADBMobile.TrackState("title screen", contextData); 
      ```

* **TrackAction**

   Tiene traccia di un&#39;azione nell&#39;applicazione. Le azioni sono gli eventi che avvengono nell&#39;app e che desideri misurare, come &quot;morti&quot;, &quot;livello acquisito&quot;, &quot;abbonamenti ai feed&quot; e altre metriche.

   >[!TIP]
   >
   >In presenza di codice che potrebbe essere eseguito mentre l&#39;applicazione è in background (ad esempio, un recupero di dati in background), utilizza piuttosto `trackActionFromBackground`.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      public static void TrackAction(string action, NSDictionary cdata); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      ADBMobile.TrackAction("level gained", null); 
      ```

* **TrackActionFromBackground (solo iOS)**

   Traccia un’azione che si è verificata nel background. In questo modo gli eventi del ciclo di vita non vengono attivati in determinati scenari.

   >[!TIP]
   >
   > Questo metodo dovrebbe essere invocato solo dal codice in esecuzione mentre l&#39;applicazione è in background.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      public static void TrackActionFromBackground(string action, NSDictionary cdata); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      ADBMobile.TrackActionFromBackground("majorLocationChange", null);
      ```

* **TrackLocation**

   Invia le coordinate di latitudine e longitudine correnti. Utilizza anche i punti di interesse definiti nel file `ADBMobileConfig.json` per determinare se la posizione fornita come parametro si trova all&#39;interno di un POI. Se le coordinate correnti si trovano all&#39;interno di un POI definito, una variabile di dati di contesto viene compilata e inviata insieme alla chiamata `TrackLocation`.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      public static void TrackLocation(CLLocation location, NSDictionary cdata); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      CoreLocation.CLLocation l = new CoreLocation.CLLocation  (111.111, 44.156);
      ADBMobile.TrackLocation (l, null);
      ```

* **TrackBeacon**

   Monitora quando un utente arriva in prossimità di un beacon.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      public static void TrackBeacon( CLBeacon beacon, NSDictionary cdata);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      CoreLocation.CLBeacon beacon = new CoreLocation.CLBeacon (); 
      ADBMobile.TrackBeacon (beacon, null);
      ```

* **TrackingClearCurrentBeacon**

   Elimina i dati del beacon dopo che un utente si allontana dalle vicinanze del beacon.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      public static void TrackingClearCurrentBeacon();
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      ADBMobile.TrackingClearCurrentBeacon();
      ```

* **TrackLifetimeValueIncrease**

   Aggiunge un importo al valore &quot;lifetime&quot; del ciclo di vita dell’utente.

   * Di seguito è riportata la sintassi per questo metodo:

      public nbsp;static void TrackLifetimeValueIncrease(double amount, NSDictionary data);

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      ADBMobile.TrackLifetimeValueIncrease(5, null); 
      ```

* **TrackTimedActionStart**

   Avvia un&#39;azione temporizzata con il nome action. Se invochi questo metodo per un&#39;azione già avviata, l&#39;azione temporizzata precedente viene sovrascritta.

   >[!TIP]
   >
   >Questa chiamata non invia un hit.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      public static void TrackTimedActionStart(string action, NSDictionary cdata); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      ADBMobile.TrackTimedActionStart("level2", null);
      ```

* **TrackTimedActionUpdate**

   Passa i dati per aggiornare i dati contestuali associati all’azione action. I dati passati vengono aggiunti in coda ai dati esistenti per l’azione, e li sovrascrivono se per l’azione è già definita la stessa chiave.

   >[!TIP]
   >
   >Questa chiamata non invia un hit.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      public static void TrackTimedActionUpdate(string action, NSDictionary cdata); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      NSDictionary updatedData = NSDictionary.FromObjectAndKey (NSObject.FromObject("val2"), NSObject.FromObject ("key2")); 
        ADBMobile.TrackTimedActionUpdate("level2", updatedData); 
      ```

* **TrackTimedActionEnd**

   Termina un&#39;azione temporizzata.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      public static void TrackTimedActionEnd(string action, Func<double, double, NSMutableDictionary, sbyte> block); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      ADBMobile.TrackTimedActionEnd  ("level2", (double  arg1,  double  arg2,  NSMutableDictionary  arg3)  =>  { 
      return  Convert.ToSByte(true); 
      });
      ```

* **TrackingTimedActionExists**

   Restituisce un valore che indica se un’azione temporizzata è in corso o meno.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      public static bool TrackingTimedActionExists(string action); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      ADBMobile.TrackTimedActionEnd  ("timedAction",  (double  inAppDuration, 
      double  totalDuration,  NSMutableDictionary  data)  =>  { 
                   return  true; 
      });
      ```

* **TrackingSendQueuedHits**

   Forza l&#39;invio da parte della libreria di tutti gli hit nella coda, indipendentemente dal numero di hit attualmente presenti nella coda.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      public static void TrackingSendQueuedHits();
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      ADBMobile.TrackingSendQueuedHits(); 
      ```

* **TrackingClearQueue**

   Elimina tutti gli hit dalla coda offline.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      public static void TrackingClearQueue(); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
       ADBMobile.TrackingClearQueue();
      ```

* **TrackingGetQueueSize**

   Recupera il numero di hit attualmente presenti nella coda offline.

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      public static int TrackingGetQueueSize();
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      var queueSize = ADBMobile.TrackingGetQueueSize(); 
      ```

## Experience Cloud ID methods {#section_157919E46030443DBB5CED60D656AD9F}

* **GetMarketingCloudID**

   Recupera l&#39;Experience Cloud ID dal servizio ID.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      public static string GetMarketingCloudID(); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      var mcid = ADBMobile.GetMarketingCloudID();
      ```

* **VisitorSyncIdentifiers**

   Con l&#39;ID Experience Cloud , puoi impostare ID cliente aggiuntivi da associare a ogni visitatore. L&#39;API Visitor accetta più ID cliente per lo stesso visitatore, insieme a un identificatore del tipo di cliente per separare l&#39;ambito dei diversi ID cliente. Questo metodo corrisponde a setCustomerIDs nella libreria JavaScript.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      public static void VisitorSyncIdentifiers(NSDictionary identifiers);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      NSDictionary  ids  =  NSDictionary.FromObjectAndKey  (NSObject.FromObject  ("value2"),  NSObject.FromObject  ("pushID")); 
      ADBMobile.VisitorSyncIdentifiers(ids); 
      ```

## Metodi di Target {#section_C1E4121CAF9D43538511D857A1F549A7}

* **TargetLoadRequest**

   Sends request to your configured Target server and returns the string value of the offer generated in a `Action<NSDictionary>` callback.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      public static void TargetLoadRequest (ADBTargetLocationRequest request, Action<NSString> callback); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      NSDictionary  dict  =  NSDictionary.FromObjectAndKey  (NSObject.FromObject  ("value2"),  NSObject.FromObject  ("key1")); 
      ADBTargetLocationRequest  req  =  ADBMobile.TargetCreateRequest  ("iOSTest",  "defGal",  dict); 
      ADBMobile.TargetLoadRequest(req,    (context)  =>  { 
      Console.WriteLine  (context); 
      });
      ```

* **TargetCreateRequest**

   Convenience constructor to create an `ADBTargetLocationRequest` object with the given parameters.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      public static ADBTargetLocationRequest ADBTargetLocationRequest TargetCreateRequest (string name, string defaultContent, NSDictionary parameters); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      NSDictionary  dict  =  NSDictionary.FromObjectAndKey  (NSObject.FromObject  ("value2"),  NSObject.FromObject  ("key1")); 
      ADBTargetLocationRequest  req  =  ADBMobile.TargetCreateRequest  ("iOSTest",  "defGal",  dict); 
      ```

* **TargetCreateOrderConfirmRequest**

   Crea una `ADBTargetLocationRequest`.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      public static ADBTargetLocationRequest ADBTargetLocationRequest TargetCreateRequest (string name, string defaultContent, NSDictionary parameters);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      ADBMobile.TargetCreateOrderConfirmRequest ("myOrder", "12345", "29.41", "cool stuff", null); 
      ```

* **TargetClearCookies**

   Elimina tutti i cookie di Target dall&#39;applicazione.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      public static void TargetClearCookies(); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      ADBMobile.TargetClearCookies(); 
      ```

## Audience Manager {#section_862C4202B6294B978DEEBB15C5CD5C01}

* **AudienceVisitorProfile**

   Restituisce il profilo del visitatore ottenuto più di recente. Restituisce nil se non è stato ancora inviato alcun segnale. Visitor profile is saved in `NSUserDefaults` for easy access across multiple launches of your app.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      public static NSDictionary AudienceVisitorProfile (); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      NSDictionary profile = ADBMobile.AudienceVisitorProfile();
      ```

* **AudienceDpid**

   Restituisce il DPID corrente.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      public static string AudienceDpid ();
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      string currentDpid = ADBMobile.AudienceDpid();
      ```

* **AudienceDpuuid**

   Restituisce il DPUUID corrente.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      public static string AudienceDpuuid ();
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      string currentDpuuid = ADBMobile.AudienceDpuuid(); 
      ```

* **AudienceSetDpidAndDpuuid**

   Imposta dpid e dpuuid. Se sono impostati dpid e dpuuid, saranno inviati con ogni segnale.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      public static void AudienceSetDpidAndDpuuid (NSDictionary data, Action<NSDictionary> callback); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      ADBMobile.AudienceSetDpidAndDpuuid ("testDppid", "testDpuuid")
      ```

* **AudienceSignalWithData**

   Sends audience management a signal with traits and get the matching segments returned in a `Action<NSDictionary>`  callback.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      public static void AudienceSignalWithData (NSDictionary data, Action<NSDictionary> callback); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      NSDictionary  audienceData  =  NSDictionary.FromObjectAndKey  (NSObject.FromObject  ("value2"),  NSObject.FromObject  ("key1")); 
      ADBMobile.AudienceSignalWithData  (audienceData,  (context)  =>  { 
      Console.WriteLine  (context); 
      }); 
      ```

* **AudienceReset**

   Ripristina l&#39;identificatore UUID di Audience Manager ed elimina il profilo del visitatore corrente.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      public static void AudienceReset ();
      ```

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      ADBMobile.AudienceReset ();
      ```

## Video {#section_CBCE1951CE204A108AD4CA7BB07C7F98}

Per ulteriori informazioni, consultate Analisi [video](/help/ios/getting-started/dev-qs.md).

* **MediaCreateSettings**

   Restituisce un oggetto `ADBMediaSettings` con i parametri specificati.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      public static ADBMediaSettings MediaCreateSettings ([string name, double length, string playerName, string playerID); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      ADBMediaSettings settings = ADBMobile.MediaCreateSettings ("name1", 10, "playerName1", "playerID1"); 
      ```

* **MediaAdCreateSettings**

   Restituisce un oggetto `ADBMediaSettings` per l&#39;uso con il monitoraggio di un video annuncio.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      public static ADBMediaSettings MediaAdCreateSettings ( string name,  double length,  string playerName,  string parentName,  string parentPod,  double parentPodPosition,  string CPM); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      ADBMediaSettings adSettings = ADBMobile.MediaAdCreateSettings("adName1", 2, "playerName1", "name1", "podName1", 4, "CPM1");
      ```

* **MediaOpenWithSettings**

   Apre un oggetto `ADBMediaSettings` per il monitoraggio.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      public static void MediaOpenWithSettings ( ADBMediaSettings settings,  Action<ADBMediaState> callback); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      ADBMediaSettings settings = ADBMobile.MediaCreateSettings  ("name1",  10,  "playerName1",  "playerID1"); 
      ADBMobile.MediaOpenWithSettings  (settings,  (state)  =>  { 
      Console.WriteLine  (state.Name); 
      }); 
      ```

* **MediaClose**

   Chiude l&#39;elemento multimediale denominato name.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      public static void MediaClose ( string name);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      ADBMobile.MediaClose  (settings.Name);
      ```

* **MediaPlay**

   Riproduce l&#39;elemento multimediale denominato name in corrispondenza dell&#39;offset indicato (in secondi).

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      public static void MediaPlay ( string name, double offset);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      ADBMobile.MediaPlay (settings.Name, 0); 
      ```

* **MediaComplete**

   Contrassegna manualmente l&#39;elemento multimediale come completato in corrispondenza dell&#39;offset indicato (in secondi).

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      public static void MediaComplete ( string name, double offset);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      ADBMobile.MediaComplete (settings.Name, 5);
      ```

* **MediaStop**

   Notifica al modulo multimediale che il video è stato interrotto o messo in pausa in corrispondenza dell&#39;offset indicato.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      public static void MediaStop ( string name, double offset);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      ADBMobile.MediaStop (settings.Name, 3);
      ```

* **MediaClick**

   Notifica al modulo multimediale l&#39;avvenuto clic sull&#39;elemento multimediale.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      public static void MediaClick ( string name, double offset); 
      ```

* **MediaTrack**

   Invia una chiamata Track Action (senza visualizzazioni pagina) per lo stato corrente dell&#39;elemento multimediale.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      public static void MediaTrack ( string name, NSDictionary data); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
       ADBMobile.MediaTrack (settings.Name, null);
      ```
