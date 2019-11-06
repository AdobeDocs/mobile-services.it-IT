---
description: Puoi usare i metodi di plug-in di PhoneGap iOS per eseguire diverse attività.
keywords: android,libreria,mobile,sdk
seo-description: Puoi usare i metodi di plug-in di PhoneGap iOS per eseguire diverse attività.
seo-title: Metodi del plug-in PhoneGap
solution: Experience Cloud,Analytics
title: Metodi del plug-in PhoneGap
topic: Sviluppatore e implementazione
uuid: bc3db9ce-81b7-45ec-88aa-6020c1db5d9c
translation-type: ht
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Metodi del plug-in PhoneGap{#phonegap-plug-in-methods}

Puoi usare i metodi del plug-in PhoneGap per Android per completare diverse attività.

Nei file `html` in cui desideri usare il tracciamento, aggiungi quanto segue al tag `<head>`:

```js
<script type="text/javascript" charset="utf-8" src="ADB_Helper.js"></script>
```

## Metodi di configurazione {#section_CC429F68292D4601AEEF0A91445E1185}

* **getPrivacyStatus**

   Restituisce lo stato di privacy per l'utente corrente.

   Gli stati disponibili sono:

   * `ADB.optedIn`: Gli hit vengono inviati immediatamente.
   * `ADB.optedOut`: Gli hit vengono scartati.
   * `ADB.optUnknown`: Se le marche temporali **sono** abilitate nella suite di rapporti, gli hit vengono salvati fino a quando lo stato di privacy non cambia in optedin (gli hit vengono inviati) o optedout (gli hit vengono scartati). Se le marche temporali **non sono** abilitate nella suite di rapporti, gli hit vengono eliminati fino alla modifica dello stato di privacy, quando l'utente acconsente (optedin).

      Il valore predefinito è impostato nel file `ADBMobileConfig.json`.

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      getPrivacyStatus(function (value) { myTempVal = value; }, function () {myTempVal = null;}); 
      ```

* Il metodo **setPrivacyStatus**

   Imposta lo stato di privacy per l'utente corrente su `status`.

   Puoi impostare uno dei valori seguenti:

   * `ADB.optedIn`: Gli hit vengono inviati immediatamente.
   * `ADB.optedOut`: Gli hit vengono scartati.
   * `ADB.optUnknown`: Se le marche temporali **sono** abilitate nella suite di rapporti, gli hit vengono salvati fino a quando lo stato di privacy non cambia in optedin (gli hit vengono inviati) o optedout (gli hit vengono scartati). Se le marche temporali **non sono** abilitate nella suite di rapporti, gli hit vengono eliminati fino alla modifica dello stato di privacy, quando l'utente acconsente (optedin).

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      ADB.setPrivacyStatus('ADB.optedIn');
      ```

* **getLifetimeValue**

   Restituisce il valore "lifetime" del ciclo di vita dell'utente corrente. Il valore predefinito è 0.

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      ADB.getLifetimeValue(function (value) { myTempVal = value }, function () { myTempVal = null; }); 
      ```

* **setDebugLogging**

   Abilita (`true`) o disabilita (`false`) la visualizzazione delle informazioni di debug. Per impostazione predefinita, questa variabile è impostata su `false`.

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      ADB.setDebugLogging(true);
      ```

* **getVersion**

   Ottiene la versione della libreria.

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      ADB.getVersion(function (value) { versionNum = value }, function () { versionNum = 1.0;});
      ```

* **trackingIdentifier**

   Restituisce l'identificatore visitatore generato automaticamente.

   Si tratta di un ID visitatore univoco specifico per l'app, che viene generato all'avvio iniziale dell'app e quindi memorizzato e utilizzato da quel momento in poi. L'ID viene conservato durante gli aggiornamenti dell'app e rimosso quando l'app viene disinstallata.

   >[!TIP]
   >
   >Se l'app viene aggiornata dall'SDK Experience Cloud 3.x alla versione 4.x, l'ID visitatore precedente (generato in modo personalizzato o automatico) viene recuperato e memorizzato come identificatore utente personalizzato. Per ulteriori informazioni, consulta `getUserIdentifier`, di seguito. Questo ID conserva i dati del visitatore tra gli aggiornamenti dell'SDK.

   Per le nuove installazioni con l'SDK 4.x, l'identificatore dell'utente è `null` e viene utilizzato l'identificatore di tracciamento.

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      ADB.trackingIdentifier(function (value) { myTempVal = value; }, function () { myTempVal = null; }); 
      ```

* **getUserIdentifier**

   Se è stato impostato un identificatore utente personalizzato, restituisce tale identificatore. In caso contrario restituisce `null`. Il valore predefinito è `null`.

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      getUserIdentifier(function(value) { myTempVal = value; }, function () { myTempVal = null; });
      ```

* **setUserIdentifier**

   Imposta l'identificatore utente su `identifier`.

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      ADB.setUserIdentifier('testUser');
      ```

* **setPushIdentifier**

   Imposta il token dispositivo per le notifiche push.

   ```java
   getUserIdentifier(function (value) { myTempVal = value; }, function () { myTempVal = null; });
   ```

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      ADB.setPushIdentifier(pushIdentifier, success, fail);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      ADB.setPushIdentifier('test_push_identifier',function (value) { alert('success'); },function (value) { alert('fail'); }); 
      ```

* **keepLifecycleSessionAlive**

   Imposta la preferenza per mantenere valida la sessione del ciclo di vita.

   >[!IMPORTANT]
   >
   >Una chiamata `keepLifecycleSessionAlive` impedisce che l'app avvii una nuova sessione in seguito alla ripresa dopo l'esecuzione in background. Usa questo metodo solo se l'app si registra per le notifiche in background.

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```js
      ADB.keepLifecycleSessionAlive(); 
      ```

* **trackingSendQueuedHits**

   Fa sì che la libreria invii tutti gli hit presenti in coda, a prescindere dalle opzioni di batch correnti.

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```js
      ADB.trackingSendQueuedHits();
      ```

* **trackingGetQueueSize**

   Ottiene o imposta il numero di chiamate di tracciamento in attesa nella coda offline.

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```js
      ADB.trackingGetQueueSize(function (value) { myTempVal = value;}, function () { myTempVal = null;}); 
      ```

* **trackingClearQueue**

   Rimuove dalla coda offline tutte le chiamate di tracciamento memorizzate.

   >[!WARNING]
   >
   >Quando cancelli la coda manualmente, presta particolare attenzione poiché l'azione non può essere annullata.

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```js
      ADB.trackingClearQueue(function (value) { myTempVal = value; }, function () { myTempVal = null; }); 
      ```

## Metodi PII {#section_DB27270D2CEB4D369E0090FD9D1A7F81}

* **collectPII**

   Invia una richiesta di raccolta PII.

   * Di seguito è riportata la sintassi per questo metodo:

   ```javascript
   ADB.collectPII(piiData,success, fail);
   ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```javascript
      ADB.collectPII({'k1':'v1','k2':'v2','k3':'v3'}, function (value) { alert('success') },function (value) { alert('fail') ;});
      ```


## Metodi di tracciamento {#section_7946BB753A4446FE8A3ED728AEF97D04}

* **trackAdobeDeepLink**

   Tiene traccia del click-through di un collegamento profondo (deep link) di Adobe.

   >[!TIP]
   >
   >Se la chiamata del ciclo di vita è un evento di avvio, i dati del collegamento Adobe verranno aggiunti; in caso contrario viene inviata una chiamata aggiuntiva.

   * Di seguito è riportata la sintassi per questo metodo:

      ```js
      ADB.trackAdobeDeepLink(deeplinkURL, success, fail); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```js
      ADB.trackAdobeDeepLink('xyz-deeplink-url',function (value) { alert('success'); },function (value) { alert('fail') }); 
      ```

* **trackState**

   Tiene traccia dello stato di un'app con dati contestuali facoltativi. Gli stati sono le visualizzazioni disponibili nell'app, ad esempio `home dashboard`, `app settings`, `cart` e così via. Questi stati sono simili alle pagine di un sito Web e le chiamate `trackState` incrementano le visualizzazioni di pagina.

   `cData`: oggetto JSON con coppie chiave-valore da inviare nei dati contestuali.

   * Di seguito è riportata la sintassi per questo metodo:

      ```js
      ADB.trackState(string stateName[,JSON cData]);
      ```

   * Di seguito sono riportati alcuni esempi di codice per questo metodo:

      ```js
        ADB.trackState("login&amp;nbsp;page"); 
      ```

      ```js
        ADB.trackState("login page", {"user":"john","remember":"true"});
      ```

* **trackAction**

   Tiene traccia di un'azione nell'applicazione. Azioni, come `logins`, `banner taps`, `feed subscriptions` e altre metriche che si verificano nell'app e che desideri misurare.

   * Di seguito è riportata la sintassi per questo metodo:

      ```js
      ADB.trackAction(string action[,JSON cData]); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```js
        ADB.trackAction("login");
      ```

      ```js
        ADB.trackAction("login", {"user":"john","remember":"true"}); 
      ```

* **trackLocation**

   Invia le coordinate x,y correnti. Utilizza anche i punti di interesse definiti nel file `ADBMobileConfig.json` per determinare se la posizione fornita come parametro si trova all'interno di un POI. Se le coordinate correnti si trovano all'interno di un POI definito, una variabile di dati di contesto viene compilata e inviata insieme alla chiamata `trackLocation`.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      ADB.trackLocation(x, y[,JSON cData]); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      ADB.trackLocation('40.431596', '-111.893713'); 
      ```

* **trackLifetime&#x200B;ValueIncrease**

   Aggiunge al valore "lifetime" del ciclo di vita dell'utente un incremento pari a `amount`.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      ADB.trackLifetimeValueIncrease(amount[,JSON cData]); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      ADB.trackLifetimeValueIncrease('10.01'); 
      ```

* **trackTimed&#x200B;ActionStart**

   Avvia un'azione temporizzata con il nome `action`.

   Se invochi questo metodo per un'azione già avviata, l'azione temporizzata precedente viene sovrascritta.

   >[!TIP]
   >
   >Questa chiamata non invia un hit.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      ADB.trackTimedActionStart(action[,JSON cData]);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      ADB.trackTimedActionStart("cartToCheckout"); 
      ```

* **trackTimed&#x200B;ActionUpdate**

   Passa in `cData` per aggiornare i dati contestuali associati all'azione `action`.

   I dati `cData` passati vengono aggiunti alla fine dei dati esistenti per l'azione, e li sovrascrivono se per l'azione `action`, è già definita la stessa chiave.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      ADB.trackTimedActionUpdate(String action[,JSON cData]);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      ADB.trackTimedActionUpdate("cartToCheckout",{'SampleContextDataKey3':'SampleContextDataVal3','SampleContextDataKey4':'SampleContextDataVal4'});
      ```

* **trackTimed&#x200B;ActionEnd**

   Termina un'azione temporizzata.

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      ADB.trackTimedActionEnd("cartToCheckout"); 
      ```

* **trackingTimedActionExists**

   Restituisce un valore che indica se un'azione temporizzata è in corso o meno.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      ADB.trackingTimedActionExists(function (value) { myTempVal = value }, function () { myTempVal = null; }); 
      ```

## Metodi Beacon {#section_F9500D6BD95348E08E283C02B657019D}

* **trackBeacon**

   Monitora quando un utente arriva in prossimità di un beacon.

   * Di seguito è riportata la sintassi per questo metodo:

      ```js
      ADB.trackBeacon(uuid, major, minor, proximity, cData) 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```js
      ADB.trackBeacon('2F234454-CF6D-4A0F-ADF2-F4911BA9FFA6', 1, 2, 
      ADB.beaconUnknown, {'hp':'hp_val','hp.company':'adobe'}
      ```

* **clearCurrentBeacon**

   Elimina i dati del beacon dopo che un utente si allontana dalle vicinanze del beacon.

   * Di seguito è riportata la sintassi per questo metodo:

      ```js
      ADB.clearCurrentBeacon(success, fail)
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```js
      ADB.clearCurrentBeacon(); 
      ```

## Metodi di Target {#section_8670140C5A3F455E887830AFFDF91D59}

* **targetLoadRequest**

   Invia una richiesta al server di `Target` configurato e restituisce il valore stringa dell'offerta.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      ADB.targetLoadRequest(success, fail, name, defaultContent, parameters);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      ADB.targetLoadRequest(function&nbsp;(value)
      {myTempVal = value }, function () { myTempVal = null;},'bannerOffer', 'none', {'hp':'hp_val_new','hp.company':'adobe', 'hp.val2':'hp_val2'}); 
      ```

* **targetLoadOrderConfirmRequest**

   Invia una richiesta al server `Target` configurato.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      ADB.targetLoadOrderConfirmRequest(success, fail name orderId, orderTotal, productPurchaseId, parameters); 
      ```

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      ADB.targetLoadRequest(function (value) { myTempVal = value }
      , function ()
      { myTempVal = null; } 
      , 'name' 'orderId' 'total', 'purchaseId',
      {'hp':'hp_val_new','hp.company':'adobe', 'hp.val2':'hp_val2'}
      ); 
      ```

* **targetClearCookies**

   Cancella i cookie di `Target` dall'archiviazione dei cookie condivisi.

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      ADB.targetClearCookies(); 
      ```

* **targetLoadRequestWithNameWithLocationParameters**

   Elabora la richiesta di un servizio `Target`.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      ADB.targetLoadRequestWithNameWithLocationParameters(
        success, fail, name, defaultContent, profileParameters, orderParameters, mboxParameters requestLocationParameters
        ); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      ADB.targetLoadRequestWithNameWithLocationParameters  (function () { alert('success'); }, function () { alert('fail'); }, ;'bannerOffer', 'none', {'hp':'hp_val_new','hp.company':'adobe', 'hp.val2':'hp_val2'}, {'hp':'hp_val_new','hp.company':'adobe', 'hp.val2':'hp_val2'},{'hp':'hp_val_new','hp.company':'adobe', 'hp.val2':'hp_val2'},{'hp':'hp_val_new','hp.company':'adobe', 'hp.val2':'hp_val2'});
      ```

* **targetLoadRequestWithName**

   Elabora la richiesta di un servizio `Target`.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      ADB.targetLoadRequestWithRequestName(success, fail, name, defaultContent, profileParameters, orderParameters, mboxParameters);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      ADB.targetLoadRequestWithName(
      function (value){ // handle target success} ,
      function() { // handle target failure }, 
      "mboxName",
      "defaultContent",
      {"profileParameters":"profileParametervalues"}
      {"orderId" : "32FGJ4XK" , "orderTotal" : "123.33" , "purchasedProductIds":"[46,34]" }
      {"mboxParameters":"mboxParametersvalues"}
      );
      ```

* **targetSessionID**

   Ottiene il valore del cookie `SessionID` restituito dal server Target per il visitatore corrente.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      ADB.targetSessionID (success, fail); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      ADB.targetSessionID(function (value) { alert(value) },function (value){ alert('fail'); });  
      ```

* **targetPcID**

   Ottiene il valore del cookie `PcID` restituito per questo visitatore dal server di `Target`.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      ADB.targetPcID (success, fail); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      ADB.targetPcID(function  (value) { alert(value) },function (value) { alert('fail'); });
      ```

* **targetSetThirdPartyID**

   Imposta l'ID visitatore personalizzato per Target.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      ADB.targetSetThirdPartyID(thirdPartyID, success, fail); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      ADB.targetSetThirdPartyID('test-third-party-id' function (value) { alert('success'); },function (value) { alert('fail'); }); 
      ```

* **targetThirdPartyID**

   Ottiene l'ID visitatore personalizzato per Target.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      ADB.targetThirdPartyID(success, fail);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
       ADB.targetThirdPartyID(function (value) { alert(value); },function (value) { alert('fail')__;});
      ```

## Metodi di acquisizione {#section_EDEA25C4B2884487827069E9257A0BA6}

* **acquisitionCampaignStartForApp**

   Invia una richiesta al server di Target configurato e restituisce il valore stringa dell'offerta.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      ADB.acquisitionCampaignStartForApp(appId, data, success, fail); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      ADB.acquisitionCampaignStartForApp(“appId”, {‘key’:‘value’}, function() {…}, function() {…}));
      ```

      ```java
      ADB.acquisitionCampaignStartForApp(“appId”, {‘key’:‘value’});  
      ```

## Identificatore pubblicitario {#section_194607D101B047A19C51B19E176E1500}

Nell'attività principale generata da Cordova, chiama `Config.submitAdvertisingIdentifierTask()` nel metodo `onResume()`. Per ulteriori informazioni, consulta [Metodi di configurazione](/help/android/configuration/methods.md).

## Metodi di Audience Manager {#section_1FD12B29A0AF41D3BEACBB3D624EA0E4}

* **audienceGetVisitorProfile**

   Ottiene il profilo del visitatore.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      ADB.audienceGetVisitorProfile(); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      ADB.audienceGetVisitorProfile(function(value) { profile = value;}, function() { profile = null; }); 
      ```

* **audienceGetDpuuid**

   Restituisce l'identificatore DPUUID.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      ADB.audienceGetDpuuid(success fail);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      ADB.audienceGetDpuuid(function(value) { dpuuid = value;}, function(){dpuuid = null; }); 
      ```

* **audienceGetDpid**

   Restituisce l'identificatore DPID.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      ADB.audienceGetDpid(success, fail);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      ADB.audienceGetDpid(function(value){dpid = value;}, function() {dpid =  null;}); 
      ```

* **audienceSetDpidAndDpuuid**

   Imposta gli identificatori DPID e DPUUID.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      ADB.audienceSetDpidAndDpuuid(dpid, dpuuid, success, fail); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      ADB.audienceSetDpidAndDpuuid(‘dpid’, ‘dpuuid’, function() {…}, function(){…};
      ```

      ```java
      ADB.audienceSetDpidAndDpuuid(‘dpid’, ‘dpuuid’); 
      ```

* **audienceSignalWithData**

   Elabora una richiesta del servizio Audience Manager.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      ADB.audienceSignalWithData(success, fail, data);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
       ADB.audienceSignalWithData(function() {}, function() {} {‘key1’: ’value1’ ‘key2’: ‘value2’}); 
      ```

      ```java
      ADB.audienceSignalWithData({‘key1’: ’value1’, ‘key2’:‘value2’}); 
      ```

* **audienceReset**

   UUID di Audience Manager ed elimina il profilo del visitatore corrente.

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      ADB.audienceReset();
      ```

## Metodi del servizio ID {#section_840B4FAEA55B466F9754148ABA15EBDA}

* **visitorGetMarketingCloudId**

   Restituisce l'Experience Cloud ID dal servizio ID.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      ADB.visitorGetMarketingCloudId(success, fail); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      ADB.visitorGetMarketingCloudId(function (value) { mcid = value;},function (){ mcid = null;});
      ```

* **visitorSyncIdentifiers**

   Sincronizza gli identificatori forniti con il servizio ID.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      ADB.visitorSyncIdentifiers(identifiers, success, fail); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      ADB.visitorSyncIdentifiers({‘key_id_1’:’value_id_1’}, function() {…}, function() {…}));
      ```

      ```java
      ADB.visitorSyncIdentifiers({‘key_id_1’: ‘value_id_1’});  
      ```

* **visitorSyncIdentifiersWithAuthenticationState**

   Sincronizza gli identificatori forniti con il servizio ID.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      ADB.visitorSyncIdentifiersWithAuthenticationState
      (identifiers, authenticationState, success, fail); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      ADB.visitorSyncIdentifiersWithAuthenticationState({'k1':'v1','k2':'v2','k3':'v3'}, ADB.mobileVisitorAuthenticationStateAuthenticated, function (value) { alert('success'); },function (value) { alert('fail'); }); 
      ```

* **visitorSyncIdentifierWithType**

   Sincronizza l'identificatore fornito con il servizio ID.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      ADB.visitorSyncIdentifierWithType(identifierType, identifier authenticationState, success, fail); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      ADB.visitorSyncIdentifierWithType('test-identifier-type', 'test-identifier', ADB.mobileVisitorAuthenticationStateAuthenticated, function (value) { alert('success') },function (value) { alert('fail'); }); 
      ```

* **visitorAppendToURL**

   Aggiunge gli identificatori dei visitatori alla fine di un determinato URL.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
       ADB.visitorAppendToURL(urlToAppend, success, fail); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      ADB.visitorAppendToURL('test_visitor_url', function (value) alert(value);},'');
      ```

* **visitorGetIDs**

   Restituisce tutti gli `visitorID` che sono stati sincronizzati.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      ADB.visitorGetIDs (success, fail);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      ADB.visitorGetIDs(function (value) { alert(value); },function (value) { alert('fail') ;}); 
      ```
