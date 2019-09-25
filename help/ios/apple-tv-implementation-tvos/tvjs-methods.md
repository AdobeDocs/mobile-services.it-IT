---
description: Elenco dei metodi TVJS forniti dalla libreria tvOS.
seo-description: Elenco dei metodi TVJS forniti dalla libreria tvOS.
seo-title: Metodi TVJS
solution: Marketing Cloud,Analytics
title: Metodi TVJS
topic: Sviluppatore e implementazione
uuid: a7bfa85a-0d6e-4f51-9a9e-70429c2a9806
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# TVJS methods {#tvjs-methods}

Elenco dei metodi TVJS forniti dalla libreria tvOS.

## Configuration methods {#section_5F82FD2F6A0546B3B4E80DF832E11634}

* **version**

   Restituisce la versione corrente della libreria Adobe Mobile.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      version()
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      var sdkVersion = ADBMobile.version();
      ```

   * Returns: `String`

* **privacyStatus**

   Restituisce la rappresentazione NSUInteger dello stato di privacy enum per l'utente corrente.

   Sono disponibili le seguenti opzioni:

   * `ADBMobilePrivacyStatusOptIn`: Gli hit vengono inviati immediatamente.
   * `ADBMobilePrivacyStatusOptOut`: Hits are discarded.
   * `ADBMobilePrivacyStatusUnknown`: se è abilitato il tracciamento offline, gli hit vengono salvati finché lo stato di privacy non cambia in optedin (gli hit vengono inviati) o in optedout (gli hit vengono scartati).

      Se il tracciamento offline non è abilitato, gli hit vengono eliminati finché lo stato di privacy non cambia quando l'utente acconsente. THe default value is set in the `ADBMobileConfig.json` file.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      privacyStatus()
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      var privacyStatus = ADBMobile.privacyStatus();
      ```

   * Returns: `Number`

* Il metodo **setPrivacyStatus**

   Imposta lo stato di privacy per l'utente corrente su uno dei seguenti valori:

   * `ADBMobilePrivacyStatusOptIn`: Gli hit vengono inviati immediatamente.
   * `ADBMobilePrivacyStatusOptOut`: Gli hit vengono scartati.
   * `ADBMobilePrivacyStatusUnknown`: Se il tracciamento offline è abilitato, gli hit vengono salvati fino alla modifica dello stato di privacy, quando l’utente acconsente (opt in, gli hit vengono inviati) o rinuncia (opt out, gli hit vengono scartati).
   Se il tracciamento offline non è abilitato, gli hit vengono eliminati finché lo stato di privacy non cambia quando l'utente acconsente.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      setPrivacyStatus(privacyStatus)
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      ADBMobile.setPrivacyStatus(ADBMobilePrivacyStatusOptIn);
      ```


* **lifetimeValue**

   Restituisce il valore "lifetime" del ciclo di vita dell'utente corrente. Il valore predefinito è `0`.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      lifetimeValue()
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      var ltv = ADBMobile.lifetimeValue();
      ```

   * Returns: `Number`

* **userIdentifier**

   Restituisce l'identificatore utente se è stato impostato un identificatore personalizzato. Restituisce nil se non è impostato alcun identificatore personalizzato. The default is `nil`.

   >[!IMPORTANT]
   >
   >If your app upgrades from the Experience Cloud 3.x to 4.x SDK, the previous custom or automatically generated visitor ID is retrieved and stored as the custom user identifier. In tal modo i dati del visitatore vengono mantenuti da un aggiornamento all'altro dell'SDK. Per le nuove installazioni con l'SDK 4.x, l'identificatore dell'utente è nil finché non viene impostato.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      userIdentifier()
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      var uid = ADBMobile.userIdentifier();
      ```

   * Returns: `String`

* **setUserIdentifier**

   Imposta l'identificatore dell'utente.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      setUserIdentifier(userId)
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      ADBMobile.setUserIdentifier(‘myUserId’);
      ```

   * Restituisce: N/D

   * Parametro:  `userID`

      * Tipo: String
      * Nuovo identificatore per l'utente corrente.

* **setAdvertisingIdentifier**

   Imposta l’identificatore IDFA nell’SDK e, se è stato impostato nell’SDK, l’identificatore IDFA viene inviato nel ciclo di vita. È inoltre possibile accedervi in Segnali (Postback).

   >[!IMPORTANT]
   >
   >Recupera l’identificatore IDFA dalle API Apple solo se utilizzi un servizio di annunci. Se recuperi l'identificatore IDFA e non lo utilizzi correttamente, l'app potrebbe venire rifiutata.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      setAdvertisingIdentifier(idfa)
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      ADBMobile.setAdvertisingIdentifier(‘myIdfa’);
      ```

   * Restituisce: N/D
   * Parametro: `idfa`
      * Tipo: `String`
      * IDFA recuperato dell'API di Apple.

* **setDebugLogging**

   Restituisce l'attuale preferenza di accesso di debug.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      setDebugLogging(logging)
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      `ADBMobile.setDebugLogging(true);
      ```

   * Restituisce: N/D
   * Parametri: `logging`
      * Tipo: `Bool`
      * Valore che indica se Adobe SDK dovrebbe registrare nella console di debug.


## Analytics methods {#section_F3DB9BE225F84F86BE5F8D15164C0379}

* **trackStateData**

   Tiene traccia dello stato di un'app con dati contestuali facoltativi. Gli stati sono le visualizzazioni disponibili nell'app, ad esempio dashboard iniziale, impostazioni dell'app, carrello e così via. Questi stati sono simili alle pagine di un sito Web e le chiamate trackState incrementano le visualizzazioni di pagina.

   Se lo stato è vuoto, nei rapporti viene visualizzato come app name app version (build). Se trovi questo valore nei rapporti, assicurati che in ogni chiamata trackState sia impostato il valore state.

   >[!TIP]
   >
   >Questa è l'unica chiamata di tracciamento che incrementa le visualizzazioni di pagina.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      trackStateData(stateName [, contextData])
      ```

      * Restituisce: N/D
      * Parametro: `stateName`
         * Tipo: `String`
         * Nome dello stato della pagina
      * Parametro: `contextData`
         * Tipo: Object
         * Dati di contesto aggiuntivi per questo hit.
   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      ADBMobile.trackStateData(‘homepage’, {‘userid’:12345});
      ```




* **trackActionData**

   Tiene traccia di un'azione nell'applicazione. Le azioni sono gli eventi che avvengono nell'applicazione e che desideri misurare, come accessi, tap sui banner, abbonamenti ai feed e altre metriche.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      trackActionData(actionName [, contextData])
      ```

      * Restituisce: N/D
      * Parametri: `actionName`
         * Tipo: String
         * Nome dell'azione di cui tenere traccia.
      * Parametro: `contextData`
         * Tipo: Object
         * Dati di contesto aggiuntivi per questo hit.
   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      ADBMobile.trackActionData(‘likeClicked’, {‘imageName’:’funnyKitty’});
      ```



* **trackLocationWithLatLonData**

   Invia le coordinate di latitudine e longitudine correnti.

   Also uses points of interest (POI) that are defined in the `ADBMobileConfig.json` file to determine whether the location that you entered as a parameter is in any of your POIs. Se le coordinate correnti si trovano in un POI definito, una variabile di dati di contesto viene compilata e inviata insieme alla chiamata `trackLocation`.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      trackLocationWithLatLonData(lat, lon [, contextData]);
      ```

      * Restituisce: N/D
      * Parametro: `lat`
         * Tipo: numero
         * Latitudine della posizione.
      * Parametro: `lon`
         * Tipo: numero
         * Longitudine della posizione.
      * Parametro: `contextData`
         * Tipo: Object
         * Dati di contesto aggiuntivi per questo hit.
   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      ADBMobile.trackLocationWithLatLonData(43.36, -116.12, null);
      ```




* **trackLifetimeValueIncreaseJsData**

   Aggiunge un incremento al valore "lifetime" del ciclo di vita dell'utente.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      trackLifetimeValueIncreaseJsData(increaseAmount)
      ```

      * Restituisce: N/D
      * Parametro: `increaseAmount`
         * Tipo: numero
         * Incremento da aggiungere al valore "lifetime" del ciclo di vita dell'utente.
   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      ADBMobile.trackLifetimeValueIncreaseJsData(5);
      ```


* **trackTimedActionStartData**

   Avvia un'azione temporizzata con il nome action. Se invochi questo metodo per un'azione già avviata, l'azione temporizzata precedente viene sovrascritta.

   >[!TIP]
   >
   >Questa chiamata non invia un hit.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      trackTimedActionStartData(name [, contextData])
      ```

      * Restituisce: N/D
      * Parametro: `name`
         * Tipo: String
         * Nome dell'azione temporizzata di cui tenere traccia.
      * Parametro: `contextData`
         * Tipo: Object
         * Dati di contesto aggiuntivi per questo hit.
   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      ADBMobile.trackTimedActionStartData(‘level1’, {‘userId’:42423});
      ```


* **trackTimedActionUpdateData**

   Passa i dati con cui aggiornare i dati contestuali associati all'azione.

   I dati passati vengono aggiunti alla fine dei dati esistenti per l'azione e li sovrascrivono se per l'azione è già definita la stessa chiave.

   >[!TIP]
   >
   >Questa chiamata non invia un hit.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      trackTimedActionUpdateData(name [, contextData])
      ```

      * Restituisce: N/D
      * Parametro: `name`
         * Tipo: String
         * Nome dell'azione temporizzata che viene aggiornata.
      * Parametro: `contextData`
         * Tipo: Object
         * Dati di contesto aggiuntivi per questo hit.
   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      ADBMobile.trackTimedActionUpdateData(‘level1’);
      ```



* **trackTimedActionEndJsLogic**

   Termina un'azione temporizzata.

   Se fornisci una funzione di callback, puoi accedere al valori temporali finali. In assenza di callback, o se il callback restituisce "true", Adobe SDK invia automaticamente un hit. Quando viene restituito un valore false dal callback, l’hit dell’azione temporizzata viene eliminato.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      trackTimedActionEndJsLogic(name [, callback])
      ```

      * Restituisce: N/D
      * Parametri: `name`
         * Tipo: String
         * Nome dell'azione temporizzata che viene terminata.
      * Parametro: `callback`
         * Tipo: `function(inAppDuration, totalDuration, data)`
         * Callback method that will have `inAppDuration` (number), `totalDuration` (number), and `data` (context data object) in its parameters.

            You can suppress the final hit from being sent by the SDK by returning `false` in your callback function.
      * Di seguito è riportato un esempio di codice per questo metodo:

         ```objective-c
         ADBMobile.trackTimedActionEndJsLogic(‘level1’, 
         function(inAppDuration, totalDuration, data) {
             // do something with final values
             return true;
             });
         ```



* **trackingTimedActionExistsJs**

   Restituisce un valore che indica se un'azione temporizzata è in corso o meno.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      trackingTimedActionExistsJs(name)
      ```

      * Restituisce: Bool
      * Parametro: `name`
         * Tipo: `String`
         * Nome dell’azione temporizzata per la quale è necessario verificare l’esistenza.
   * Di seguito è riportato un esempio di codice per questo metodo:


      ```objective-c
      var actionExists = ADBMobile.trackTimedActionExistsJs(‘level1’);
      ```


* **trackingIdentifier**

   Restituisce l'identificatore visitatore generato automaticamente.

   Si tratta di un ID visitatore univoco specifico per l'app, generato dai server Adobe. Se i server Adobe non sono accessibili al momento della generazione, verrà utilizzato l'identificatore CFUUID di Apple. Il valore viene generato al primo avvio, memorizzato e utilizzato da tale momento in poi. Questo ID viene mantenuto nei successivi aggiornamenti dell'app, salvato e ripristinato durante il processo standard di backup dell'applicazione, e rimosso con la disinstallazione dell'app.

   >[!TIP]
   >
   >If your app upgrades from the Experience Cloud 3.x to 4.x SDK, the previous custom or automatically generated visitor ID is retrieved and stored as the custom user identifier. In tal modo i dati del visitatore vengono mantenuti da un aggiornamento all'altro dell'SDK. Per le nuove installazioni con l'SDK 4.x, l'identificatore dell'utente è `nil` e viene utilizzato l'identificatore di tracciamento. Per ulteriori informazioni, consulta la riga userIdentifier di seguito.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      trackingIdentifier()
      ```

      * Returns: `String`
      * Parametri: nessuno
   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      var trackingId = ADBMobile.trackingIdentifier();
      ```


* **trackingSendQueuedHits**

   Forza l'invio da parte della libreria di tutti gli hit nella coda, indipendentemente dal numero di hit attualmente presenti nella coda.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      trackingSendQueuedHits()
      ```

      * Restituisce: N/D
      * Parametri: nessuno
   * Di seguito è riportato un esempio di codice per questo metodo:


      ```objective-c
      ADBMobile.trackingSendQueuedHits();
      ```


* **trackingClearQueue**

   Elimina tutti gli hit dalla coda offline.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      trackingClearQueue()
      ```

      * Restituisce: N/D
      * Parametri: nessuno
   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      ADBMobile.trackingClearQueue();
      ```


* **trackingGetQueueSize**

   Recupera il numero di hit attualmente presenti nella coda offline.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      trackingGetQueueSize()
      ```

      * Restituisce: numero
      * Parametri: nessuno
   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      var queueSize = ADBMobile.trackingGetQueueSize();
      ```


## Audience Manager methods {#section_0155C4DF04644EDAAF6159C420A158DE}

* **audienceVisitorProfile**

   Restituisce il profilo del visitatore ottenuto più di recente.

   Restituisce null se non è stato ancora inviato alcun segnale. Il profilo del visitatore viene salvato in `NSUserDefaults` in modo da essere facilmente accessibile per diversi avvii dell'applicazione.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      audienceVisitorProfile()
      ```

      * Restituisce: oggetto
      * Parametri: nessuno
   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      var profile = ADBMobile.audienceVisitorProfile();
      ```


* **audienceDpid**

   Restituisce il DPID corrente.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      audienceDpid()
      ```

      * Restituisce: String
      * Parametri: nessuno
   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      var dpid = ADBMobile.audienceDpid();
      ```


* **audienceDpuuid**

   Restituisce il DPUUID corrente.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      audienceDpuuid()
      ```

      * Returns: `String`
      * Parametri: nessuno
   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      var dpuuid = ADBMobile.audienceDpuuid();
      ```


* **audienceSetDpidDpuuid**

   Imposta il dpid e il dpuuid e, se sono impostati, saranno inviati con ciascun segnale.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      audienceSetDpidDpuuid(dpid, dpuuid)
      ```

      * Restituisce: N/D
      * Parametro: `dpid`
         * Tipo: `String`
         * ID del provider di dati Audience Manager.
      * Parametro: `dpuuid`
         * Tipo: `String`
         * Identificatore per la combinazione utente-provider dati.
   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      ADBMobile.audienceSetDpidDpuuid(‘myDpid’, ‘userDpuuid’);
      ```


* **audienceSignalWithDataJsCallback**

   Invia a Audience Manager un segnale con caratteristiche e riceve i segmenti corrispondenti restituiti in una funzione di callback.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      audienceSignalWithDataJsCallback(traits [, callback])
      ```

      * Parametro: `traits`
         * Tipo: Object
         * Dizionario delle caratteristiche per l'utente corrente.
      * Parametro: `callback`
         * Tipo: function(profile)
         * Profilo restituito da Audience Manager nel parametro della funzione di callback.
   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      ADBMobile.audienceSignalWithDataJsCallback({‘trait’:’something’}, 
      function(profile) {
          //do something with the user’s segments found in profile
           });
      ```



* **audienceReset**

   Ripristina l'identificatore UUID di Audience Manager e svuota il profilo visitatore corrente.

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      audienceReset()
      ```

      * Restituisce: N/D
      * Parametro: None
   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      ADBMobile.audienceReset();
      ```


## ID Service methods {#section_BEB6DA612EA4423FB354B65ECC941335}

* **visitorMarketingCloudID**

   Recupera l'Experience Cloud ID dal servizio ID.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      visitorMarketingCloudID()
      ```

      * Restituisce: String
      * Parametri: nessuno
   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      var mcid = ADBMobile.visitorMarketingCloudID();
      ```


* **visitorSyncIdentifiers**

   Oltre all'Experience Cloud ID, puoi impostare altri ID cliente da associare a ogni visitatore. L'API Visitor accetta più ID cliente per lo stesso visitatore, con un identificatore del tipo di cliente che consente di distinguere l'ambito dei diversi ID cliente. Questo metodo corrisponde a setCustomerIDs nella libreria JavaScript.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      visitorSyncIdentifiers(identifiers)
      ```

      * Restituisce: N/D
      * Parametro: `identifiers`

         * Tipo: `Object`
         * Identificatori da sincronizzare con il servizio ID per l'utente corrente.
   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      ADBMobile.visitorSyncIdentifiers({‘idType’:’idValue’});
      ```


* **visitorSyncIdentifiersAuthenticationState**

   Sincronizza gli identificatori forniti con il servizio ID.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      visitorSyncIdentifiersAuthenticationState(identifiers, authState)
      ```

      * Restituisce: N/D
      * Parametri: `identifiers`
         * Tipo: `Object`
         * Identificatori da sincronizzare con il servizio ID per l'utente corrente.
      * Parametro: `authState`
         * Tipo: ADBMobileVisitorAuthenticationState
         * Lo stato di autenticazione dell’utente e i valori possibili includono:
            * `ADBMobileVisitorAuthenticationStateUnknown`
            * `ADBMobileVisitorAuthenticationStateAuthenticated`
            * `ADBMobileVisitorAuthenticationStateLoggedOut`
   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      ADBMobile.visitorSyncIdentifiersAuthenticationState({'myIdType':'valueForUser'}, ADBMobileVisitorAuthenticationStateLoggedOut)
      ```



* **visitorSyncIdentifierWithTypeIdentifierAuthenticationState**

   Sincronizza con il servizio ID il tipo e il valore dell'identificatore fornito.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      visitorSyncIdentifierWithTypeIdentifierAuthenticationState(idType, identifier, authState)
      ```

      * Return: N/D
      * Parametro: `idType`
         * Tipo: `String`
         * Tipo dell'identificatore da sincronizzare.
      * Parametro: `identifier`
         * Tipo: `String`
         * Valore dell'identificatore da sincronizzare.
      * Parametro: `authState`
         * Tipo: Stato ADBMobileVisitorAuthenticationStateAuthentication dell’utente. Possibili valori:
            * `ADBMobileVisitorAuthenticationStateUnknown`
            * `ADBMobileVisitorAuthenticationStateAuthenticated`
            * `ADBMobileVisitorAuthenticationStateLoggedOut`
   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      ADBMobile.visitorSyncIdentifierWithTypeIdentifierAuthenticationState('myIdType', 'valueForUser', 
      ADBMobileVisitorAuthenticationStateAuthenticated);
      ```


* **visitorGetIDsJs**

   Recupera un array di oggetti ADBVisitorID di sola lettura. Il codice seguente è un esempio di oggetto VisitorID:

   ```js
   {
       idType: "abc",
       authenticationState: 1, 
       identifier: "123"
   }
   ```

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      visitorGetIDsJs()
      ```

      * Returns: `Array [Object]`

      * Parametri: nessuno
   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      var myVisitorIds = ADBMobile.visitorGetIDsJs();
      ```


## Target methods {#section_F9F7EC2B9B7C41AFBCA2458F9F138634}

* **targetThirdPartyID**

   Restituisce l'ID di terze parti.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      targetThirdPartyID()
      ```

      * Returns: `String`
      * Parametri: nessuno
   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      var thirdPartyID = ADBMobile.targetThirdPartyID();
      ```


* **targetSetThirdPartyID**

   Imposta l'ID di terze parti.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      targetSetThirdPartyID(thirdPartyID)
      ```

      * Restituisce: N/D
      * Parametri: `thirdPartyID`
         * Tipo: `String`
         * ID di terze parti da usare per le richieste di Target.
   * Di seguito è riportato un esempio di codice per questo metodo:
   ```objective-c
   ADBMobile.targetSetThirdPartyID(‘thirdPartyID’);
   ```

* **targetPcID**

   Restituisce il PcID.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      targetPcID()
      ```

      * Returns: `String`
      * Parametri: nessuno
   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      var pcID = ADBMobile.targetPcID();
      ```


* **targetSessionID**

   Restituisce l'ID della sessione.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      targetSessionID()
      ```

      * Returns: `String`
      * Parametri: nessuno
   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      var sessionID = ADBMobile.targetSessionID();
      ```
