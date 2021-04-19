---
description: Informazioni utili per usare l’SDK della piattaforma UWP (Universal Windows Platform) con Adobe Analytics.
seo-description: Informazioni utili per usare l’SDK della piattaforma UWP (Universal Windows Platform) con Adobe Analytics.
seo-title: Metodi di Analytics
solution: Experience Cloud,Analytics
title: Metodi di Analytics
topic-fix: Developer and implementation
uuid: cc299bb5-ec61-49bf-869a-f3c3bc83359f
exl-id: 3ceaedfa-274f-4dc7-9e4c-15233d09f935
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '632'
ht-degree: 57%

---

# Metodi di Analytics {#analytics-methods}

Informazioni utili per usare l’SDK della piattaforma UWP (Universal Windows Platform) con Adobe Analytics.

L&#39;SDK supporta attualmente più soluzioni Adobe Experience Cloud, tra cui Analytics, Target e Audience Manager. Ai metodi è applicato il prefisso della relativa soluzione. I metodi di Analytics hanno il prefisso &quot;Analytics&quot;.

Ciascuno di questi metodi viene usato per inviare dati alla suite di rapporti di Adobe Analytics.

>[!TIP]
>
>Quando utilizzi metodi `winmd` da winJS (JavaScript), tutti i metodi presentano automaticamente la prima lettera minuscola.

* **TrackState (winJS: trackState)**

   Tiene traccia dello stato di un&#39;app con dati contestuali facoltativi. Gli stati sono le visualizzazioni disponibili nell&#39;app, ad esempio &quot;dashboard iniziale&quot;, &quot;impostazioni app&quot;, &quot;carrello&quot; e così via. Questi stati sono simili alle pagine di un sito Web e le chiamate `TrackState` incrementano le visualizzazioni di pagina.
Se `state` è vuoto, nei rapporti viene visualizzato come &quot;app name app version (build)&quot;. Se trovi questo valore nei rapporti, assicurati che in ogni chiamata `TrackState` sia impostato `state`.

   >[!TIP]
   >
   >Questa è l&#39;unica chiamata di tracciamento che incrementa le visualizzazioni pagina.

   * Di seguito è riportata la sintassi per questo metodo:

      ```csharp
      static void TrackState(Platform::String ^state, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> ^contextData); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```js
      var ADB = ADBMobile
      ADB.Analytics.trackState("loginScreen", null);
      ```

* **TrackAction (winJS: trackAction)**

   Tiene traccia di un&#39;azione nell&#39;applicazione. Le azioni sono gli eventi che avvengono nell’app e che desideri misurare, come &quot;accessi&quot;, &quot;tap sui banner&quot;, &quot;abbonamenti ai feed&quot; e altre metriche.

   * Di seguito è riportata la sintassi per questo metodo:

      ```csharp
      static void TrackAction(Platform::String ^action, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> ^contextData); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```js
      varADB=ADBMobile; 
      ADB.Analytics.trackAction("ButtonClick",null); 
      ```

* **GetTrackingIdentifierAsync (winJS: getTrackingIdentifierAsync)**

   Restituisce l&#39;ID visitatore generato automaticamente per Analytics. Si tratta di un ID visitatore univoco specifico per l’app, che viene generato all’avvio iniziale e quindi memorizzato e utilizzato da quel momento in poi. Questo ID viene mantenuto nei successivi aggiornamenti dell’app e rimosso al momento della disinstallazione.

   * Di seguito è riportata la sintassi per questo metodo:

      ```csharp
      static Windows::Foundation::IAsyncOperation<Platform::String> ^GetTrackingIdentifierAsync(); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```js
      vartrackingIdentifier; 
      ADBMobile.Analytics.getTrackingIdentifierAsync().then(function(trackingid){
      trackingIdentifier=trackingid;
      });
      ```

* **TrackLocation (winJS: trackLocation)**

   Invia le coordinate x,y correnti. Utilizza anche i punti di interesse definiti nel file `ADBMobileConfig.json` per determinare se la posizione fornita come parametro si trova all&#39;interno di un POI. Se le coordinate correnti si trovano all&#39;interno di un POI definito, una variabile di dati di contesto viene compilata e inviata insieme alla chiamata `trackLocation`.

   * Di seguito è riportata la sintassi per questo metodo:

      ```csharp
      static void TrackLocation(double lat, double lon, double accuracy, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> ^contextData);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```js
      varADB=ADBMobile; 
      ADB.Analytics.trackLocation(47.60621,-122.33207,null);
      ```

* **TrackLifetime &#x200B; ValueIncrease (winJS: trackLifetime &#x200B; ValueIncrease)**

   Aggiunge al valore “lifetime” del ciclo di vita dell&#39;utente un incremento pari a `amount`.

   * Di seguito è riportata la sintassi per questo metodo:

      ```csharp
      static void TrackLifetimeValueIncrease(float amount, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> ^contextData); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```js
      varADB=ADBMobile;
      ADB.Analytics.trackLifetimeValueIncrease(10,null);
      ```

* **TrackTimed &#x200B; ActionStart (winJS: trackTimed &#x200B; ActionStart)**

   Avvia un&#39;azione temporizzata con il nome `action`. Se invochi questo metodo per un&#39;azione già avviata, l&#39;azione temporizzata precedente viene sovrascritta.

   >[!TIP]
   >
   >Questa chiamata non invia un hit.

   * Di seguito è riportata la sintassi per questo metodo:

      ```csharp
      static void TrackTimedActionStart(Platform::String ^action, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^contextData); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```js
      varADB=ADBMobile;
      ADB.Analytics.trackTimedActionStart("cartToCheckout",null); 
      ```

* **TrackTimed &#x200B; ActionUpdate (winJS: trackTimed &#x200B; ActionUpdate)**

   Passa i dati `contextData` per aggiornare i dati contestuali associati all&#39;azione `action`. I dati `data` passati vengono aggiunti alla fine dei dati esistenti per l&#39;azione, e li sovrascrivono se per l&#39;azione è già definita la stessa chiave per `action`.

   >[!TIP]
   >
   >Questa chiamata non invia un hit.

   * Di seguito è riportata la sintassi per questo metodo:

      ```csharp
      static void TrackTimedActionUpdate(Platform::String ^action, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> ^contextData); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```js
      varADB = ADBMobile;
      varcontextData = newWindows.Foundation.Collections.PropertySet();
      contextData["quantity"]=3; 
      ADB.Analytics.trackTimedActionUpdate("cartToCheckout",contextData);
      ```

* **TrackTimedActionExistsAsync (winJS: trackTimedActionExistsAsync)**

   Restituisce true se l&#39;azione temporizzata specificata esiste e false se non esiste.

   * Di seguito è riportata la sintassi per questo metodo:

      ```csharp
      static Windows::Foundation::IAsyncOperation<bool> ^TrackTimedActionExistsAsync(Platform::String ^action); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```js
      ADBMobile.Analytics.trackTimedActionExistsAsync("signUp").then(function(exists){ 
          actionExists = exists; 
      });
      ```

* **TrackTimed &#x200B; ActionEnd (winJS: trackTimed &#x200B; ActionEnd)**

   Termina un&#39;azione temporizzata.

   * Di seguito è riportata la sintassi per questo metodo:

      ```csharp
      static void TrackTimedActionEnd(Platform::String ^action);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```js
      varADB = ADBMobile; 
      ADB.Analytics.trackTimedActionEnd("cartToCheckout"); 
      ```

* **ClearTrackingQueue (winJS: clearTrackingQueue)**

   Cancella tutti gli hit memorizzati dalla coda di tracciamento di Analytics.

   * Di seguito è riportata la sintassi per questo metodo:

      ```csharp
      static void ClearTrackingQueue();
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```js
      ADBMobile.Analytics.clearTrackingQueue();
      ```

* **GetQueueSizeAsync (winJS: getQueueSizeAsync)**

   Restituisce il numero di hit attualmente memorizzati nella coda di Analytics.

   * Di seguito è riportata la sintassi per questo metodo:

      ```csharp
      static Windows::Foundation::IAsyncOperation<int> ^GetQueueSizeAsync();
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```js
      varqueueSize;
      ADBMobile.Analytics.getQueueSizeAsync().then(function(size){ 
          queueSize=size;
      });
      ```
