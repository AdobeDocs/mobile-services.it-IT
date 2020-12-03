---
description: Elenco dei metodi TVJS forniti dalla libreria tvOS.
seo-description: Elenco dei metodi TVJS forniti dalla libreria tvOS.
seo-title: Metodi TVJS
solution: Experience Cloud,Analytics
title: Metodi TVJS
topic: Developer and implementation
uuid: a7bfa85a-0d6e-4f51-9a9e-70429c2a9806
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '2013'
ht-degree: 100%

---


# Metodi TVJS {#tvjs-methods}

Elenco dei metodi TVJS forniti dalla libreria tvOS.

## Metodi di configurazione {#section_5F82FD2F6A0546B3B4E80DF832E11634}

* **versione**

   Restituisce la versione corrente della libreria Adobe Mobile.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      version()
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      var sdkVersion = ADBMobile.version();
      ```

   * Restituisce: `String`

* **privacyStatus**

   Restituisce la rappresentazione NSUInteger dello stato di privacy enum per l’utente corrente.

   Di seguito sono riportate le opzioni disponibili:

   * `ADBMobilePrivacyStatusOptIn`: gli hit vengono inviati immediatamente.
   * `ADBMobilePrivacyStatusOptOut`: gli hit vengono scartati.
   * `ADBMobilePrivacyStatusUnknown`: se è abilitato il tracciamento offline, gli hit vengono salvati finché lo stato di privacy non cambia in optedin (gli hit vengono inviati) o in optedout (gli hit vengono scartati).

      Se il tracciamento offline non è abilitato, gli hit vengono scartati finché lo stato di privacy non cambia in optedin. Il valore predefinito è impostato nel file `ADBMobileConfig.json`.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      privacyStatus()
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      var privacyStatus = ADBMobile.privacyStatus();
      ```

   * Restituisce: `Number`

* **setPrivacyStatus**

   Imposta lo stato di privacy per l&#39;utente corrente su uno dei seguenti valori:

   * `ADBMobilePrivacyStatusOptIn`: gli hit vengono inviati immediatamente.
   * `ADBMobilePrivacyStatusOptOut`: gli hit vengono scartati.
   * `ADBMobilePrivacyStatusUnknown`: se è abilitato il tracciamento offline, gli hit vengono salvati finché lo stato di privacy non cambia in optedin (gli hit vengono inviati) o in optedout (gli hit vengono scartati).

   Se il tracciamento offline non è abilitato, gli hit vengono scartati finché lo stato di privacy non cambia in optedin.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      setPrivacyStatus(privacyStatus)
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      ADBMobile.setPrivacyStatus(ADBMobilePrivacyStatusOptIn);
      ```


* **lifetimeValue**

   Restituisce il valore &quot;lifetime&quot; del ciclo di vita dell&#39;utente corrente. Il valore predefinito è `0`.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      lifetimeValue()
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      var ltv = ADBMobile.lifetimeValue();
      ```

   * Restituisce: `Number`

* **userIdentifier**

   Restituisce l&#39;identificatore utente se è stato impostato un identificatore personalizzato. Restituisce nil se non è impostato alcun identificatore personalizzato. Il valore predefinito è `nil`.

   >[!IMPORTANT]
   >
   >Se l&#39;app viene aggiornata dall&#39;SDK di Experience Cloud 3.x alla versione 4.x, l&#39;ID visitatore precedente (personalizzato o generato in automatico) viene recuperato e memorizzato come identificatore utente personalizzato. In tal modo i dati del visitatore vengono mantenuti da un aggiornamento all&#39;altro dell&#39;SDK. Per le nuove installazioni con l&#39;SDK 4.x, l&#39;identificatore dell&#39;utente è nil finché non viene impostato.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      userIdentifier()
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      var uid = ADBMobile.userIdentifier();
      ```

   * Restituisce: `String`

* **setUserIdentifier**

   Imposta l&#39;identificatore dell&#39;utente.

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

      * Tipo: string
      * Nuovo identificatore per questo utente.

* **setAdvertisingIdentifier**

   Imposta l’identificatore IDFA nell’SDK e, se è stato impostato nell’SDK, l’identificatore IDFA viene inviato nel ciclo di vita. È inoltre possibile accedervi in Segnali (Postback).

   >[!IMPORTANT]
   >
   >Recupera l&#39;identificatore IDFA dall&#39;API di Apple solo se utilizzi un servizio di annunci. Se recuperi l&#39;identificatore IDFA e non lo utilizzi correttamente, l&#39;app potrebbe venire rifiutata.

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
      * IDFA recuperato dell&#39;API di Apple.

* **setDebugLogging**

   Restituisce la preferenza di accesso di debug.

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


## Metodi di Analytics {#section_F3DB9BE225F84F86BE5F8D15164C0379}

* **trackStateData**

   Tiene traccia dello stato di un&#39;app con dati contestuali facoltativi. Gli stati sono le visualizzazioni disponibili nell&#39;app, ad esempio dashboard iniziale, impostazioni dell&#39;app, carrello e così via. Questi stati sono simili alle pagine di un sito Web e le chiamate trackState incrementano le visualizzazioni di pagina.

   Se lo stato è vuoto, nei rapporti viene visualizzato come app name app version (build). Se trovi questo valore nei rapporti, assicurati che in ogni chiamata trackState sia impostato il valore state.

   >[!TIP]
   >
   >Questa è l&#39;unica chiamata di tracciamento che incrementa le visualizzazioni pagina.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      trackStateData(stateName [, contextData])
      ```

      * Restituisce: N/D
      * Parametro: `stateName`
         * Tipo: `String`
         * Nome dello stato della pagina
      * Parametro: `contextData`
         * Tipo: oggetto
         * Dati contestuali aggiuntivi per l’hit.
   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      ADBMobile.trackStateData(‘homepage’, {‘userid’:12345});
      ```




* **trackActionData**

   Tiene traccia di un&#39;azione nell&#39;applicazione. Le azioni sono gli eventi che avvengono nell&#39;applicazione e che desideri misurare, come accessi, tap sui banner, abbonamenti ai feed e altre metriche.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      trackActionData(actionName [, contextData])
      ```

      * Restituisce: N/D
      * Parametri: `actionName`
         * Tipo: string
         * Nome dell’azione da tracciare.
      * Parametro: `contextData`
         * Tipo: oggetto
         * Dati contestuali aggiuntivi per l’hit.
   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      ADBMobile.trackActionData(‘likeClicked’, {‘imageName’:’funnyKitty’});
      ```



* **trackLocationWithLatLonData**

   Invia le coordinate di latitudine e longitudine correnti.

   Utilizza anche i punti di interesse (POI) definiti nel file `ADBMobileConfig.json` per determinare se la posizione fornita come parametro si trova all&#39;interno di un POI. Se le coordinate correnti si trovano in un POI definito, una variabile di dati di contesto viene compilata e inviata insieme alla chiamata `trackLocation`.

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
         * Tipo: oggetto
         * Dati contestuali aggiuntivi per l’hit.
   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      ADBMobile.trackLocationWithLatLonData(43.36, -116.12, null);
      ```




* **trackLifetimeValueIncreaseJsData**

   Aggiunge un incremento al valore &quot;lifetime&quot; del ciclo di vita dell&#39;utente.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      trackLifetimeValueIncreaseJsData(increaseAmount)
      ```

      * Restituisce: N/D
      * Parametro: `increaseAmount`
         * Tipo: numero
         * Importo da aggiungere al valore del ciclo di vita corrente dell’utente.
   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      ADBMobile.trackLifetimeValueIncreaseJsData(5);
      ```


* **trackTimedActionStartData**

   Avvia un&#39;azione temporizzata con il nome action. Se invochi questo metodo per un&#39;azione già avviata, l&#39;azione temporizzata precedente viene sovrascritta.

   >[!TIP]
   >
   >Questa chiamata non invia un hit.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      trackTimedActionStartData(name [, contextData])
      ```

      * Restituisce: N/D
      * Parametro: `name`
         * Tipo: string
         * Nome dell’azione temporizzata da avviare.
      * Parametro: `contextData`
         * Tipo: oggetto
         * Dati contestuali aggiuntivi per l’hit.
   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      ADBMobile.trackTimedActionStartData(‘level1’, {‘userId’:42423});
      ```


* **trackTimedActionUpdateData**

   Passa i dati per aggiornare i dati contestuali associati all’azione in questione.

   I dati passati vengono aggiunti alla fine dei dati esistenti per l’azione in questione e li sovrascrivono se per l’azione è già definita la stessa chiave.

   >[!TIP]
   >
   >Questa chiamata non invia un hit.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      trackTimedActionUpdateData(name [, contextData])
      ```

      * Restituisce: N/D
      * Parametro: `name`
         * Tipo: string
         * Nome dell’azione temporizzata da aggiornare.
      * Parametro: `contextData`
         * Tipo: oggetto
         * Dati contestuali aggiuntivi per l’hit.
   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      ADBMobile.trackTimedActionUpdateData(‘level1’);
      ```



* **trackTimedActionEndJsLogic**

   Termina un&#39;azione temporizzata.

   Se fornisci una funzione di callback, puoi accedere ai valori temporali finali. Se non viene fornito alcun callback, o se il callback restituisce true, l’SDK di Adobe invia automaticamente un hit. Se restituisce false, l&#39;hit dell&#39;azione temporizzata viene eliminato.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      trackTimedActionEndJsLogic(name [, callback])
      ```

      * Restituisce: N/D
      * Parametri: `name`
         * Tipo: string
         * Nome dell’azione temporizzata da terminare
      * Parametro: `callback`
         * Tipo: `function(inAppDuration, totalDuration, data)`
         * Metodo di callback i cui parametri conterranno il `inAppDuration` (numero), il `totalDuration` (numero) e `data` (oggetto di dati contestuali).

            Se la funzione di callback restituisce `false`, verrà impedito l&#39;invio dell&#39;hit finale da parte dell&#39;SDK.
      * Di seguito è riportato un esempio di codice per questo metodo:

         ```objective-c
         ADBMobile.trackTimedActionEndJsLogic(‘level1’, 
         function(inAppDuration, totalDuration, data) {
             // do something with final values
             return true;
             });
         ```



* **trackingTimedActionExistsJs**

   Restituisce un valore che indica se un&#39;azione temporizzata è in corso o meno.

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

   Restituisce l&#39;identificatore visitatore generato automaticamente.

   Si tratta di un ID visitatore univoco specifico per l’app, generato dai server Adobe. Se non è possibile raggiungere i server Adobe al momento della generazione, l’ID viene generato utilizzando CFUUID di Apple. Il valore viene generato al primo avvio e memorizzato e utilizzato da tale momento in poi. Questo ID viene mantenuto nei successivi aggiornamenti dell’app, viene salvato e ripristinato durante il processo standard di backup dell’applicazione e viene rimosso quando l’app viene disinstallata.

   >[!TIP]
   >
   >Se l&#39;app viene aggiornata dall&#39;SDK di Experience Cloud 3.x alla versione 4.x, l&#39;ID visitatore precedente (personalizzato o generato in automatico) viene recuperato e memorizzato come identificatore utente personalizzato. In tal modo i dati del visitatore vengono mantenuti da un aggiornamento all&#39;altro dell&#39;SDK. Per le nuove installazioni con l&#39;SDK 4.x, l&#39;identificatore dell&#39;utente è `nil` e viene utilizzato l&#39;identificatore di tracciamento. Per ulteriori informazioni, consulta la riga userIdentifier di seguito.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      trackingIdentifier()
      ```

      * Restituisce: `String`
      * Parametri: nessuno
   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      var trackingId = ADBMobile.trackingIdentifier();
      ```


* **trackingSendQueuedHits**

   Forza l&#39;invio da parte della libreria di tutti gli hit nella coda, indipendentemente dal numero di hit attualmente presenti nella coda.

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


## Metodi di Audience Manager {#section_0155C4DF04644EDAAF6159C420A158DE}

* **audienceVisitorProfile**

   Restituisce il profilo del visitatore ottenuto più di recente.

   Restituisce null se non è stato ancora inviato alcun segnale. Il profilo del visitatore viene salvato in `NSUserDefaults` in modo da essere facilmente accessibile per diversi avvii dell&#39;applicazione.

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

      * Restituisce: `String`
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
         * Tipo: oggetto
         * Dizionario delle caratteristiche per questo utente.
      * Parametro: `callback`
         * Tipo: function(profile)
         * Il profilo restituito da Audience Manager nel parametro per la funzione di callback.
   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      ADBMobile.audienceSignalWithDataJsCallback({‘trait’:’something’}, 
      function(profile) {
          //do something with the user’s segments found in profile
           });
      ```



* **audienceReset**

   Ripristina l&#39;identificatore UUID di Audience Manager e svuota il profilo visitatore corrente.

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      audienceReset()
      ```

      * Restituisce: N/D
      * Parametro: nessuno
   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      ADBMobile.audienceReset();
      ```


## Metodi del servizio ID {#section_BEB6DA612EA4423FB354B65ECC941335}

* **visitorMarketingCloudID**

   Recupera l&#39;Experience Cloud ID dal servizio ID.

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

   Oltre a Experience Cloud ID, puoi impostare ID cliente aggiuntivi da associare a ogni visitatore. L’API visitatore accetta più ID cliente per lo stesso visitatore, con un identificatore del tipo di cliente per separare l’ambito dei diversi ID cliente. Questo metodo corrisponde a setCustomerIDs nella libreria JavaScript.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      visitorSyncIdentifiers(identifiers)
      ```

      * Restituisce: N/D
      * Parametro: `identifiers`

         * Tipo: `Object`
         * Identificatori da sincronizzare con il servizio ID per l&#39;utente corrente.
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
         * Identificatori da sincronizzare con il servizio ID per l&#39;utente corrente.
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

   Sincronizza con il servizio ID il tipo e il valore dell&#39;identificatore fornito.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      visitorSyncIdentifierWithTypeIdentifierAuthenticationState(idType, identifier, authState)
      ```

      * Restituisce: N/D
      * Parametro: `idType`
         * Tipo: `String`
         * Tipo dell&#39;identificatore da sincronizzare.
      * Parametro: `identifier`
         * Tipo: `String`
         * Valore dell&#39;identificatore da sincronizzare.
      * Parametro: `authState`
         * Tipo: ADBMobileVisitorAuthenticationState
Stato di autenticazione dell’utente. Possibili valori:
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

      * Restituisce: `Array [Object]`

      * Parametri: nessuno
   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      var myVisitorIds = ADBMobile.visitorGetIDsJs();
      ```


## Metodi di Target {#section_F9F7EC2B9B7C41AFBCA2458F9F138634}

* **targetThirdPartyID**

   Restituisce l&#39;ID di terze parti.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      targetThirdPartyID()
      ```

      * Restituisce: `String`
      * Parametri: nessuno
   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      var thirdPartyID = ADBMobile.targetThirdPartyID();
      ```


* **targetSetThirdPartyID**

   Imposta l&#39;ID di terze parti.

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

      * Restituisce: `String`
      * Parametri: nessuno
   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      var pcID = ADBMobile.targetPcID();
      ```


* **targetSessionID**

   Restituisce l&#39;ID della sessione.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      targetSessionID()
      ```

      * Restituisce: `String`
      * Parametri: nessuno
   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      var sessionID = ADBMobile.targetSessionID();
      ```
