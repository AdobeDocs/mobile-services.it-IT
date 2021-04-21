---
description: Metodi di configurazione ADBMobile.cs
keywords: Unity
solution: Experience Cloud
title: Metodi ADBMobile.cs
uuid: af504934-febd-45d9-81e2-2a310f4c65dc
exl-id: d12c16f1-c25c-4698-8943-a660d9c08faf
translation-type: tm+mt
source-git-commit: b9ee49ba26d4726b1f97ef36f5c2e9923361b1ee
workflow-type: tm+mt
source-wordcount: '1324'
ht-degree: 70%

---

# Metodi ADBMobile.cs {#adbmobile-cs-methods}

## Metodi di configurazione

* **CollectLifecycleData**

   Indica all&#39;SDK che i dati del ciclo di vita devono essere raccolti per l&#39;utilizzo in tutte le soluzioni dell&#39;SDK. Per ulteriori informazioni, vedi [Metriche del ciclo di vita](/help/ios/metrics.md).

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void CollectLifecycleData();
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      ADBMobile.CollectLifecycleData();
      ```

* **EnableLocalNotifications (solo iOS)**

   Abilita le notifiche locali nell&#39;app.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void EnableLocalNotifications();
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      ADBMobile.EnableLocalNotifications();
      ```

* **GetDebugLogging**

   Restituisce l&#39;attuale preferenza di accesso di debug. Il valore predefinito è `false`.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static bool GetDebugLogging();
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      var debugEnabled = ADBMobile.GetDebugLogging();
      ```

* **GetLifetimeValue**

   Restituisce il valore &quot;lifetime&quot; del ciclo di vita dell&#39;utente corrente.

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
   * `MOBILE_PRIVACY_STATUS_OPT_IN`: gli hit vengono inviati immediatamente.
   * `MOBILE_PRIVACY_STATUS_OPT_OUT`: gli hit vengono scartati.
   * `MOBILE_PRIVACY_STATUS_UNKNOWN`: se è abilitato il tracciamento offline, gli hit vengono salvati finché lo stato di privacy non cambia quando l&#39;utente acconsente (opt in, gli hit vengono inviati) o rinuncia (opt out, gli hit vengono eliminati).

      Se il tracciamento offline non è abilitato, gli hit vengono eliminati finché lo stato di privacy non cambia quando l&#39;utente acconsente. Il valore predefinito è impostato nel file [ADBMobileConfig.json](/help/ios/configuration/json-config/json-config.md) .

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static ADBPrivacyStatus GetPrivacyStatus();
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      var privacyStatus = ADBMobile.GetPrivacyStatus();
      ```

* **GetUserIdentifier**

   Restituisce l&#39;identificatore utente personalizzato se è stato impostato un identificatore personalizzato. Restituisce null se non è impostato un identificatore personalizzato. Il valore predefinito è `null`.

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

   Indica all&#39;SDK che la prossima ripresa dal background non rappresenta l&#39;avvio di una nuova sessione, indipendentemente dal valore di timeout della sessione del ciclo di vita nel file di configurazione.

   >[!TIP]
   >
   >Questo metodo è destinato alle app che si registrano per le notifiche mentre sono in background, e dovrebbe essere invocato solo dal codice in esecuzione mentre l&#39;app è in background.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void KeepLifecycleSessionAlive();
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      ADBMobile.KeepLifecycleSessionAlive();
      ```

* **PauseCollectingLifecycleData (solo Android)**

   Indica all&#39;SDK che l&#39;applicazione è in pausa, in modo che le metriche del ciclo di vita vengano calcolate correttamente. Ad esempio, al momento della pausa recupera una marca temporale per determinare la lunghezza della sessione precedente. Inoltre, imposta un flag in modo che il ciclo di vita acquisisca correttamente che l&#39;app non si è bloccata. Per ulteriori informazioni, vedi [Metriche del ciclo di vita](/help/android/metrics.md).

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void PauseCollectingLifecycleData();
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      ADBMobile.PauseCollectingLifecycleData();
      ```

* **SetContext (solo Android)**

   Indica all&#39;SDK di impostare il contesto dell&#39;applicazione dall&#39;attività corrente di UnityPlayer.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void SetContext();
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      ADBMobile.SetContext();
      ```

* **SetDebugLogging**

   Imposta l&#39;abilitazione della preferenza di accesso di debug.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void SetDebugLogging (bool enabled);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      ADBMobile.SetDebugLogging(true);
      ```

* **SetPrivacyStatus**

   Imposta lo stato di privacy per l&#39;utente corrente su status. Imposta uno dei valori seguenti:

   * `MOBILE_PRIVACY_STATUS_OPT_IN`: gli hit vengono inviati immediatamente.
   * `MOBILE_PRIVACY_STATUS_OPT_OUT`: gli hit vengono scartati.
   * `MOBILE_PRIVACY_STATUS_UNKNOWN`: se è abilitato il tracciamento offline, gli hit vengono salvati finché lo stato di privacy non cambia quando l&#39;utente acconsente (opt in, gli hit vengono inviati) o rinuncia (opt out, gli hit vengono eliminati). Se il tracciamento offline non è abilitato, gli hit vengono eliminati finché lo stato di privacy non cambia quando l&#39;utente acconsente.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void SetPrivacyStatus(ADBPrivacyStatusstatus);
      ```

   * Di seguito è riportato un esempio di codice per questa sintassi:

      ```java
      ADBMobile.SetPrivacyStatus(ADBMobile.ADBPrivacyStatus.MOBILE_PRIVACY_STATUS_OPT_IN);
      ```

* **SetUserIdentifier**

   Imposta l&#39;identificatore utente su userId.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void SetUserIdentifier(string userId);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      ADBMobile.SetUserIdentifier("myCustomUserId");
      ```

## Metodi di Analytics

* **GetTrackingIdentifier**

   Recupera l&#39;identificativo di monitoraggio di Analytics.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static string GetTrackingIdentifier();
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      var trackingId = ADBMobile.GetTrackingIdentifier();
      ```

* **TrackState**

   Tiene traccia dello stato di un&#39;app con dati contestuali facoltativi. Gli stati sono le visualizzazioni disponibili nell’app, ad esempio &quot;schermata del titolo&quot;, &quot;livello 1&quot;, &quot;pausa&quot; e così via. Questi stati sono simili alle pagine di un sito Web e le chiamate `TrackState` incrementano le visualizzazioni di pagina.

   Se lo stato è vuoto, nei rapporti viene visualizzato come *`app name app version (build)`* . Se trovi questo valore nei rapporti, assicurati che in ogni chiamata `TrackState` sia impostato lo stato .

   >[!TIP]
   >
   >Questa è l&#39;unica chiamata di tracciamento che incrementa le visualizzazioni pagina.

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

   Tiene traccia di un&#39;azione nell&#39;applicazione. Le azioni sono gli eventi che avvengono nell’app e che desideri misurare, come &quot;morti&quot;, &quot;livello acquisito&quot;, &quot;abbonamenti ai feed&quot; e altre metriche.

   >[!TIP]
   >
   >In presenza di codice che potrebbe essere eseguito mentre l&#39;applicazione è in background (ad esempio, un recupero di dati in background), utilizza piuttosto `trackActionFromBackground`.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void TrackAction(string action, Dictionary<string, object> cdata);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      ADBMobile.TrackAction("level gained", null);
      ```

* **TrackActionFromBackground (solo iOS)**

   Traccia un’azione che si è verificata nel background. In questo modo gli eventi del ciclo di vita non vengono attivati in determinati scenari.

   >[!TIP]
   >
   >Questo metodo dovrebbe essere invocato solo dal codice in esecuzione mentre l&#39;applicazione è in background.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void TrackActionFromBackground(string action, Dictionary<string,object> cdata);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      ADBMobile.TrackActionFromBackground("majorLocationChange", null);
      ```

* **TrackLocation**

   Invia le coordinate di latitudine e longitudine correnti. Utilizza anche i punti di interesse definiti nel file `ADBMobileConfig.json` per determinare se la posizione fornita come parametro si trova all&#39;interno di un POI. Se le coordinate correnti si trovano all&#39;interno di un POI definito, una variabile di dati di contesto viene compilata e inviata insieme alla chiamata TrackLocation .

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

   Aggiunge un incremento al valore &quot;lifetime&quot; del ciclo di vita dell&#39;utente.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void TrackLifetimeValueIncrease(double amount, Dictionary<string, object> cdata);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      ADBMobile.TrackLifetimeValueIncrease(5, null);
      ```

* **TrackTimedActionStart**

   Avvia un&#39;azione temporizzata con il nome action. Se invochi questo metodo per un&#39;azione già avviata, l&#39;azione temporizzata precedente viene sovrascritta.

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

   Passa i dati per aggiornare i dati contestuali associati all&#39;azione. I dati passati vengono aggiunti alla fine dei dati esistenti per l&#39;azione, e li sovrascrivono se per l&#39;azione è già definita la stessa chiave.

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

   Termina un&#39;azione temporizzata.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void TrackTimedActionEnd(string action);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      ADBMobile.TrackTimedActionEnd("level2");
      ```

* **TrackingTimedActionExists**

   Restituisce un valore che indica se un&#39;azione temporizzata è in corso o meno.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static bool TrackingTimedActionExists(string action);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
       var level2InProgress = ADBMobile.TrackingTimedActionExists("level2");
      ```

* **TrackingSendQueuedHits**

   Forza l&#39;invio da parte della libreria di tutti gli hit nella coda, indipendentemente dal numero di hit attualmente presenti nella coda.

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

   Recupera l&#39;Experience Cloud ID dal servizio ID.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static string GetMarketingCloudID();
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      var mcid = ADBMobile.GetMarketingCloudID();
      ```

* **VisitorSyncIdentifiers**

   Con l’ID Experience Cloud, puoi impostare ID cliente aggiuntivi da associare a ogni visitatore. L’API visitatore accetta più ID cliente per lo stesso visitatore, insieme a un identificatore del tipo di cliente per separare l’ambito dei diversi ID cliente. Questo metodo corrisponde a setCustomerIDs nella libreria JavaScript.

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

## Metodi di acquisizione 

* **ProcessGooglePlayInstallReferrerUrl** *(solo Android)*

   Passa l’URL del referente restituito da una chiamata all’API Google Play Install Referrer a questo metodo.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void ProcessGooglePlayInstallReferrerUrl(string referrerUrl);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      // in actual implementation, the referrer url should be retrieved
      // from the Google Play Install Referrer API.
      var myReferrer = "utm_source=unityTestSource&utm_content=unityTestContent&utm_campaign=unityTestCampaign";
      ADBMobile.ProcessGooglePlayInstallReferrerUrl(myReferrer);
      ```
