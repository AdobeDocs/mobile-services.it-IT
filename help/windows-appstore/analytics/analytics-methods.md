---
description: Informazioni di supporto per utilizzare l’SDK Windows 8.1 Universal App Store con Adobe Analytics.
seo-description: Informazioni di supporto per utilizzare l’SDK Windows 8.1 Universal App Store con Adobe Analytics.
seo-title: Metodi di Analytics
solution: Marketing Cloud, Analytics
title: Metodi di Analytics
topic: Sviluppatore e implementazione
uuid: 79 db 105 c -216 c -4061-97 f 3-a 55954995 e 67
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Analytics methods {#analytics-methods}

Informazioni di supporto per utilizzare l’SDK Windows 8.1 Universal App Store con Adobe Analytics.

L'SDK supporta attualmente più soluzioni Adobe Experience Cloud], tra cui Analytics], Target] e Audience Manager]. Ai metodi è applicato il prefisso della relativa soluzione. I metodi di Analytics hanno il prefisso "Analytics".

Ciascuno di questi metodi viene usato per inviare dati alla suite di rapporti di Adobe Analytics.

>[!TIP]
>
>When you consume `winmd` methods from winJS (JavaScript), all methods automatically have their first letter lowercased.

* **Trackstate (winjs: Trackstate)**

   Tiene traccia dello stato di un'app con dati contestuali facoltativi. Gli stati sono le visualizzazioni disponibili nell'app, ad esempio “dashboard iniziale”, “impostazioni dell'app”, “carrello” e così via. Questi stati sono simili alle pagine di un sito Web e le chiamate `TrackState` incrementano le visualizzazioni di pagina. Se `state` è vuoto, nei rapporti viene visualizzato come “app name app version (build)”. Se vedi questo valore nei rapporti, assicurati che `state` sia impostato in ogni chiamata `TrackState`.

   >[!TIP]
   >
   >Questa è l'unica chiamata di tracciamento che incrementa le visualizzazioni di pagina.

   * Di seguito è riportata la sintassi per questo metodo:

      ```csharp
      static void TrackState(Platform::String ^state, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> ^contextData); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```js
      var ADB = ADBMobile;
      ADB.Analytics.trackState("loginScreen", null);
      ```

* **Trackaction (winjs: Trackaction)**

   Tiene traccia di un'azione nell'applicazione. Le azioni sono gli eventi che avvengono nell’applicazione e che desideri misurare, come “accessi”, “tap sui banner”, “abbonamenti ai feed” e altre metriche.

   * Di seguito è riportata la sintassi per questo metodo:

      ```csharp
      static void TrackAction(Platform::String ^action, Windows::Foundation::Collections::IMap <Platform::String^, Platform::Object> ^contextData);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```js
      var ADB = ADBMobile; 
      ADB.Analytics.trackAction("Button Click", null); 
      ```

* **Gettrackingidentifierasync (winjs: Gettrackingidentifierasync)**

   Restituisce l’identificatore visitatore generato automaticamente per Analytics. Si tratta di un ID visitatore univoco specifico per l’app, che viene generato all’avvio iniziale e quindi memorizzato e utilizzato da quel momento in poi. Questo ID viene conservato tra un aggiornamento e l’altro dell’applicazione, e rimosso alla disinstallazione.

   * Di seguito è riportata la sintassi per questo metodo:

      ```csharp
      static Windows::Foundation::IAsyncOperation<Platform::String^> ^GetTrackingIdentifierAsync(); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```js
      var trackingIdentifier; 
      ADBMobile.Analytics.getTrackingIdentifierAsync().then(function (trackingid) { 
         trackingIdentifier = trackingid; 
      });
      ```

* **Tracklocation (winjs: Tracklocation)**

   Invia le coordinate x,y correnti. Utilizza anche i punti di interesse definiti nel file `ADBMobileConfig.json` per determinare se la posizione fornita come parametro si trova all'interno di un POI. Se le coordinate correnti si trovano all'interno di un POI definito, una variabile di dati di contesto viene compilata e inviata insieme alla chiamata `trackLocation`.

   * Di seguito è riportata la sintassi per questo metodo:

      ```csharp
      static void TrackLocation(double lat, double lon, double accuracy, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^contextData);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```js
      var ADB = ADBMobile; 
      ADB.Analytics.trackLocation(47.60621, -122.33207, null);
      ```

* **Tracklifetimevalueincrease (winjs: Tracklifetimevalueincrease)**

   Aggiunge al valore "lifetime" del ciclo di vita dell'utente un incremento pari a `amount`.

   * Di seguito è riportata la sintassi per questo metodo:

      ```csharp
      static void TrackLifetimeValueIncrease(float amount, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^contextData); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```js
      var ADB = ADBMobile; 
      ADB.Analytics.trackLifetimeValueIncrease(10, null); 
      ```

* **Tracktimedactionstart (winjs: Tracktimedactionstart)**

   Avvia un'azione temporizzata con il nome `action`. Se invochi questo metodo per un'azione già avviata, l'azione temporizzata precedente viene sovrascritta.

   >[!TIP]
   >
   >Questa chiamata non invia un hit.

   * Di seguito è riportata la sintassi per questo metodo:

      ```csharp
      static void TrackTimedActionStart(Platform::String ^action, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^contextData);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```js
      var ADB = ADBMobile; 
      ADB.Analytics.trackTimedActionStart("cartToCheckout", null); 
      ```

* **Tracktimedactionupdate (winjs: Tracktimedactionupdate)**

   Passa i dati `contextData` per aggiornare i dati contestuali associati all'azione `action`. The `data` passed is appended to the existing data for the given action, and overwrites the data if the same key is already defined for `action`.

   >[!TIP]
   >
   >Questa chiamata non invia un hit.

   * Di seguito è riportata la sintassi per questo metodo:

      ```csharp
      static void TrackTimedActionUpdate(Platform::String ^action, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^contextData); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```js
      var ADB = ADBMobile; 
      var contextData = new Windows.Foundation.Collections.PropertySet(); 
      contextData["quantity"] = 3; 
      ADB.Analytics.trackTimedActionUpdate("cartToCheckout", contextData); 
      ```

* **Tracktimedactionexistsasync (winjs: Tracktimedactionexistsasync)**

   Restituisce true se una determinata azione temporizzata esiste e false se non esiste.

   * Di seguito è riportata la sintassi per questo metodo:

      ```csharp
      static Windows::Foundation::IAsyncOperation<bool> ^TrackTimedActionExistsAsync(Platform::String ^action); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```js
      ADBMobile.Analytics.trackTimedActionExistsAsync("signUp").then(function (exists) { 
          actionExists = exists; 
      });
      ```

* **Tracktimedactionend (winjs: Tracktimedactionend)**

   Termina un'azione temporizzata.

   * Di seguito è riportata la sintassi per questo metodo:

      ```csharp
      static void TrackTimedActionEnd(Platform::String ^action);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```js
      var ADB = ADBMobile; 
      ADB.Analytics.trackTimedActionEnd("cartToCheckout"); 
      ```

* **Cleartrackingqueue (winjs: Cleartrackingqueue)**

   Cancella tutti gli hit memorizzati dalla coda di tracciamento di Analytics.

   * Di seguito è riportata la sintassi per il messaggio:

      ```csharp
      static void ClearTrackingQueue();
      ```

   * Esempio di esempio:

      ```js
      ADBMobile.Analytics.clearTrackingQueue();
      ```

* **Getqueuesizeasync (winjs: Getqueuesizeasync)**

   Restituisce il numero di hit attualmente memorizzati nella coda di Analytics.

   * Di seguito è riportata la sintassi per questo metodo:

      ```csharp
      static Windows::Foundation::IAsyncOperation<int> ^GetQueueSizeAsync();
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```js
      var queueSize; 
      ADBMobile.Analytics.getQueueSizeAsync().then(function (size) { 
          queueSize = size; 
      });
      ```