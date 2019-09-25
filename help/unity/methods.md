---
description: nulle
keywords: Unity
seo-description: nulle
seo-title: Metodi ADBMobile.cs
solution: Marketing Cloud,Developer
title: Metodi ADBMobile.cs
uuid: af504934-febd-45d9-81e2-2a310f4c65dc
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# ADBMobile.cs methods {#adbmobile-cs-methods}

## Metodi di configurazione

* **CollectLifecycleData**

   Indica all'SDK che i dati del ciclo di vita devono essere raccolti per l'utilizzo in tutte le soluzioni dell'SDK. Per ulteriori informazioni, vedi [Metriche del ciclo di vita](/help/ios/metrics.md).

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void CollectLifecycleData();
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      ADBMobile.CollectLifecycleData(); 
      ```

* **EnableLocalNotifications (solo iOS)**

   Attiva le notifiche locali nell'applicazione.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void EnableLocalNotifications();
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      ADBMobile.EnableLocalNotifications(); 
      ```

* **GetDebugLogging**

   Restituisce l'attuale preferenza di accesso di debug. Il valore predefinito è `false`.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static bool GetDebugLogging();
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      var debugEnabled = ADBMobile.GetDebugLogging();
      ```

* **GetLifetimeValue**

   Restituisce il valore "lifetime" del ciclo di vita dell'utente corrente.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static double GetLifetimeValue();
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      var lifetimeValuea = ADBMobile.GetLifetimeValue();
      ```

* **GetPrivacyStatus**

   Restituisce la rappresentazione enum dello stato di privacy per l’utente corrente.
   * `MOBILE_PRIVACY_STATUS_OPT_IN`: Gli hit vengono inviati immediatamente.
   * `MOBILE_PRIVACY_STATUS_OPT_OUT`: Gli hit vengono scartati.
   * `MOBILE_PRIVACY_STATUS_UNKNOWN`: se è abilitato il tracciamento offline, gli hit vengono salvati finché lo stato di privacy non cambia quando l'utente acconsente (opt in, gli hit vengono inviati) o rinuncia (opt out, gli hit vengono eliminati).

      Se il tracciamento offline non è abilitato, gli hit vengono eliminati finché lo stato di privacy non cambia quando l'utente acconsente. Il valore predefinito è impostato nel file [ADBMobileConfig.json](/help/ios/configuration/json-config/json-config.md).

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static ADBPrivacyStatus GetPrivacyStatus();
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      var privacyStatus = ADBMobile.GetPrivacyStatus();
      ```

* **GetUserIdentifier**

   Restituisce l'identificativo utente personalizzato se un identificatore personalizzato è stato impostato. Restituisce null se non è impostato un identificatore personalizzato. Il valore predefinito è `null`.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static string GetUserIdentifier();
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      var userId = ADBMobile.GetUserIdentifier(); 
      ```

* **GetVersion**

   Ottiene la versione della libreria.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static string GetVersion();
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      var version = ADBMobile.GetVersion();
      ```

* **KeepLifecycleSessionAlive (solo iOS)**

   Indica all'SDK che la prossima ripresa dal background non rappresenta l'avvio di una nuova sessione, indipendentemente dal valore di timeout della sessione del ciclo di vita nel file di configurazione.

   >[!TIP]
   >
   >This method is intended to be used for apps that register for notifications while in the background and should only be called from your code that runs while your app is in the background.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void KeepLifecycleSessionAlive(); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      ADBMobile.KeepLifecycleSessionAlive(); 
      ```

* **PauseCollectingLifecycleData (solo Android)**

   Indica all’SDK che l’applicazione è in pausa, in modo che le metriche del ciclo di vita vengano calcolate correttamente. Ad esempio, all'avvio della pausa recupera un timestamp per determinare la durata della sessione precedente. Inoltre, questo imposta un flag in modo che il ciclo di vita acquisisca correttamente che l'applicazione non si è bloccata. Per ulteriori informazioni, vedi [Metriche del ciclo di vita](/help/android/metrics.md).

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void PauseCollectingLifecycleData();
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      ADBMobile.PauseCollectingLifecycleData(); 
      ```

* **SetContext (solo Android)**

   Indica all'SDK di impostare il proprio contesto dell'applicazione dall'attività corrente di UnityPlayer.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void SetContext();
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      ADBMobile.SetContext(); 
      ```

* **SetDebugLogging**

   Imposta l'abilitazione della preferenza di accesso di debug.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void SetDebugLogging (bool enabled); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      ADBMobile.SetDebugLogging(true); 
      ```

* **SetPrivacyStatus**

   Imposta lo stato di privacy per l'utente corrente sullo stato. Imposta uno dei valori seguenti:

   * `MOBILE_PRIVACY_STATUS_OPT_IN`: Gli hit vengono inviati immediatamente.
   * `MOBILE_PRIVACY_STATUS_OPT_OUT`: Hits are discarded.
   * `MOBILE_PRIVACY_STATUS_UNKNOWN`: se è abilitato il tracciamento offline, gli hit vengono salvati finché lo stato di privacy non cambia quando l'utente acconsente (opt in, gli hit vengono inviati) o rinuncia (opt out, gli hit vengono eliminati). Se il tracciamento offline non è abilitato, gli hit vengono eliminati finché lo stato di privacy non cambia quando l'utente acconsente.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void SetPrivacyStatus(ADBPrivacyStatusstatus); 
      ```

   * Here is the code sample for this syntax:

      ```java
      ADBMobile.SetPrivacyStatus(ADBMobile.ADBPrivacyStatus.MOBILE_PRIVACY_STATUS_OPT_IN);
      ```

* **SetUserIdentifier**

   Imposta l'identificativo utente su userId.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void SetUserIdentifier(string userId); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      ADBMobile.SetUserIdentifier("myCustomUserId"); 
      ```

## Metodi di analisi

* **GetTrackingIdentifier**

   Recupera l'identificativo di monitoraggio di Analytics.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static string GetTrackingIdentifier();
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      var trackingId = ADBMobile.GetTrackingIdentifier(); 
      ```

* **TrackState**

   Monitora lo stato di un'app con dati di contesto facoltativi. Gli stati sono le visualizzazioni disponibili nell'applicazione, come "schermata del titolo", "livello 1", "pausa" e così via. Questi stati sono simili alle pagine di un sito Web e le chiamate `TrackState` incrementano le visualizzazioni di pagina.

   If state is empty, it displays as *`app name app version (build)`* in reports. Se visualizzi questo valore nel report, assicurati che lo stato in ogni chiamata sia impostato su `TrackState`.

   >[!TIP]
   >
   >Questa è l'unica chiamata di tracciamento che incrementa le visualizzazioni di pagina.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void TrackState(string state, Dictionary<string, object> cdata);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      var contextData = new Dictionary<string, object>); 
      contextData.Add ("user", "jim");
      ADBMobile.TrackState("title screen", contextData);
      ```

* **TrackAction**

   Monitora un'azione nell'applicazione. Le azioni sono gli eventi che avvengono nell'applicazione e che desideri misurare, come "morti", "livello acquisito", "iscrizioni al feed" e altri parametri.

   >[!TIP]
   >
   >If you have code that might run while the app is in the background (for example, a background data retrieval), use `trackActionFromBackground` instead.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void TrackAction(string action, Dictionary<string, object> cdata); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      ADBMobile.TrackAction("level gained", null); 
      ```

* **TrackActionFromBackground (solo iOS)**

   Monitora un'azione che si è verificata in background. Questo impedisce l'attivazione degli eventi del ciclo di vita in determinati scenari.

   >[!TIP]
   >
   >This method should only be called in code that runs while your app is in the background.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void TrackActionFromBackground(string action, Dictionary<string,object> cdata); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      ADBMobile.TrackActionFromBackground("majorLocationChange", null);
      ```

* **TrackLocation**

   Invia le coordinate di latitudine e longitudine correnti. Utilizza anche i punti di interesse definiti nel file `ADBMobileConfig.json` per determinare se la posizione fornita come parametro si trova all'interno di un POI. Se le coordinate correnti si trovano all'interno di un POI definito, una variabile di dati di contesto viene compilata e inviata insieme alla chiamata a TrackLocation.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void TrackLocation(float latValue, float lonValue, Dictionary<string, object> cdata); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      ADBMobile.TrackLocation(28.418649, -81.581324, null); 
      ```

* **TrackBeacon**

   Monitora quando un utente arriva in prossimità di un beacon.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void TrackBeacon(int major, int minor, string uuid, ADBBeaconProximity proximity, Dictionary<string, object> cdata); 
      ```

* **TrackingClearCurrentBeacon**

   Elimina i dati del beacon dopo che un utente si allontana dalle vicinanze del beacon.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void TrackingClearCurrentBeacon(); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      ADBMobile.TrackingClearCurrentBeacon();
      ```

* **TrackLifetimeValueIncrease**

   Incrementa la durata di vita dell'utente.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void TrackLifetimeValueIncrease(double amount, Dictionary<string, object> cdata);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      ADBMobile.TrackLifetimeValueIncrease(5, null); 
      ```

* **TrackTimedActionStart**

   Avvia un'azione temporizzata con il nome action. Se invochi questo metodo per un'azione già avviata, l'azione temporizzata precedente viene sovrascritta.

   >[!TIP]
   >
   >Questa chiamata non invia un hit.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void TrackTimedActionStart(string action, Dictionary<string,object> cdata); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      ADBMobile.TrackTimedActionStart("level2", null);
      ```

* **TrackTimedActionUpdate**

   Trasmette i dati per aggiornare i dati di contesto associati all'azione in questione. I dati trasmessi vengono aggiunti in coda ai dati esistenti per l'azione, e li sovrascrivono se per l'azione è già definita la stessa chiave.

   >[!TIP]
   >
   >Questa chiamata non invia un hit.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void TrackTimedActionUpdate(string action, Dictionary<string, object> cdata); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      var contextData = new Dictionary<string, object>; 
      contextData.Add("checkpoint", "1:32"); 
         ADBMobile.TrackTimedActionUpdate("level2", contextData);
      ```

* **TrackTimedActionEnd**

   Termina un'azione temporizzata.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void TrackTimedActionEnd(string action); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      ADBMobile.TrackTimedActionEnd("level2"); 
      ```

* **TrackingTimedActionExists**

   Restituisce un valore che indica se un'azione temporizzata è in corso o meno.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static bool TrackingTimedActionExists(string action); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
       var level2InProgress = ADBMobile.TrackingTimedActionExists("level2"); 
      ```

* **TrackingSendQueuedHits**

   Forza l'invio da parte della libreria di tutti gli hit nella coda, indipendentemente dal numero di hit attualmente presenti nella coda.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void TrackingSendQueuedHits();
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      ADBMobile.TrackingSendQueuedHits(); 
      ```

* **TrackingClearQueue**

   Elimina tutti gli hit dalla coda offline.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void TrackingClearQueue();
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      ADBMobile.TrackingClearQueue(); 
      ```

* **TrackingGetQueueSize**

   Recupera il numero di hit attualmente presenti nella coda offline.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static int TrackingGetQueueSize();
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      var queueSize = ADBMobile.TrackingGetQueueSize();
      ```

## Metodi Experience Cloud ID

* **GetMarketingCloudID**

   Recupera l'Experience Cloud ID dal servizio ID.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static string GetMarketingCloudID(); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      var mcid = ADBMobile.GetMarketingCloudID();
      ```

* **VisitorSyncIdentifiers**

   Utilizzando l’ID Experience Cloud, è possibile impostare ID cliente aggiuntivi da associare a ciascun visitatore. L'API Visitor accetta più ID cliente per lo stesso visitatore, insieme a un identificatore del tipo di cliente per separare l'ambito dei diversi ID cliente. Questo metodo corrisponde a setCustomerIDs nella libreria JavaScript.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void VisitorSyncIdentifiers(Dictionary<string, object> identifiers); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      var ids = new Dictionary<string, object> (); 
      ids.Add ("player1", "jimbob"); 
      ADBMobile.VisitorSyncIdentifiers(ids);
      ```

