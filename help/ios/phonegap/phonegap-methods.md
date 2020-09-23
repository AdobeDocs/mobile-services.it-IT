---
description: Puoi usare i metodi di plug-in di PhoneGap iOS per eseguire diverse attività.
keywords: phonegap
seo-description: Puoi usare i metodi di plug-in di PhoneGap iOS per eseguire diverse attività.
seo-title: Metodi del plug-in PhoneGap
solution: Experience Cloud,Analytics
title: Metodi del plug-in PhoneGap
topic: Developer and implementation
uuid: bd830fe5-804a-4d0a-bbb6-99a6d8da6a03
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '1730'
ht-degree: 100%

---


# Metodi del plug-in PhoneGap {#phonegap-plug-in-methods}

Puoi usare i metodi di plug-in di PhoneGap iOS per eseguire diverse attività.

Nei file `html` in cui desideri usare il tracciamento, aggiungi quanto segue al tag `<head>`:

```html
<script type="text/javascript" charset="utf-8" src="ADB_Helper.js"></script>
```

## Metodi di configurazione {#section_CC429F68292D4601AEEF0A91445E1185}

* **getPrivacyStatus**

   Restituisce lo stato di privacy per l&#39;utente corrente. Gli stati disponibili sono:

   * `ADB.optedIn`: gli hit vengono inviati immediatamente.
   * `ADB.optedOut`: gli hit vengono scartati.
   * `ADB.optUnknown`Se le marche temporali **sono** abilitate nella suite di rapporti, gli hit vengono salvati fino a quando lo stato di privacy non cambia in optedin (gli hit vengono inviati) o optedout (gli hit vengono scartati). Se le marche temporali **non sono** abilitate nella suite di rapporti, gli hit vengono eliminati fino alla modifica dello stato di privacy, quando l&#39;utente acconsente (optedin).\
      Il valore predefinito è impostato nel file `ADBMobileConfig.json`.

      * Di seguito è riportato un esempio di codice per questo metodo:

         ```javascript
         getPrivacyStatus(function (value){myTempVal = value;},function(){myTempVal = null;});
         ```

* **setPrivacyStatus**

   Imposta lo stato di privacy per l&#39;utente corrente su `status`. Puoi impostare uno dei valori seguenti:
   * `ADB.optedIn`: gli hit vengono inviati immediatamente.
   * `ADB.optedOut`: gli hit vengono scartati.
   * `ADB.optUnknown` - Se le marche temporali **sono** abilitate nella suite di rapporti, gli hit vengono salvati fino a quando lo stato di privacy non cambia in optedin (gli hit vengono inviati) o optedout (gli hit vengono scartati).

      Se le marche temporali **non sono** abilitate nella suite di rapporti, gli hit vengono eliminati fino alla modifica dello stato di privacy, quando l&#39;utente acconsente (optedin).

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```javascript
        ADB.setPrivacyStatus('ADB.optedIn'); 
      ```

* **getLifetimeValue**

   Restituisce il valore &quot;lifetime&quot; del ciclo di vita dell&#39;utente corrente. Il valore predefinito è 0.

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```javascript
      ADB.getLifetimeValue(function(value){myTempVal = value;},function(){myTempVal = null;});
      ```

* **setDebugLogging**

   Abilita (`true`) o disabilita (`false`) la visualizzazione delle informazioni di debug. Per impostazione predefinita, questa variabile è impostata su `false`.

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```javascript
      ADB.setDebugLogging(true);
      ```

* **getVersion**

   Ottiene la versione della libreria.

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```javascript
      ADB.getVersion(function(value){versionNum = value;},function(){versionNum=1.0;}); 
      ```

* **trackingIdentifier**

   Restituisce l&#39;identificatore visitatore generato automaticamente. Si tratta di un ID visitatore univoco specifico per l’app, generato all’avvio iniziale dell’app e quindi memorizzato e utilizzato da quel momento in poi. L’ID viene mantenuto nei successivi aggiornamenti dell’app e rimosso quando l’app viene disinstallata.

   >[!TIP]
   >
   >Se l&#39;app viene aggiornata dall&#39;SDK di Experience Cloud 3.x alla versione 4.x, l&#39;ID visitatore precedente (personalizzato o generato in automatico) viene recuperato e memorizzato come identificatore utente personalizzato (vedi `getUserIdentifier` qui sotto). In tal modo i dati del visitatore vengono mantenuti da un aggiornamento all’altro dell’SDK. Per le nuove installazioni con l&#39;SDK 4.x, l&#39;identificatore dell&#39;utente è `null` e viene utilizzato l&#39;identificatore di tracciamento.

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```javascript
       ADB.trackingIdentifier(function(value){myTempVal = value;},function(){myTempVal = null;}); 
      ```

* **getUserIdentifier**

   Se è stato impostato un identificatore personalizzato, restituisce l&#39;identificatore utente personalizzato. In caso contrario restituisce `null`. Il valore predefinito è `null`.

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```javascript
      getUserIdentifier(function(value){myTempVal = value;},function(){myTempVal = null;}); 
      ```

* **setUserIdentifier**

   Imposta l&#39;identificatore utente su `identifier`.

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```javascript
      ADB.setUserIdentifier('testUser');
      ```

* **setPushIdentifier**

   Imposta il token dispositivo per le notifiche push.

   * Di seguito è riportata la sintassi per questo metodo:

      ```javascript
      ADB.setPushIdentifier(pushIdentifier,success,fail);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```javascript
      ADB.setPushIdentifier('test_push_identifier',function(value){alert('success');},function(value){alert('fail');
      ```

* **keepLifecycleSessionAlive**

   Imposta la preferenza per mantenere valida la sessione del ciclo di vita.

   >[!IMPORTANT]
   >
   >Una chiamata `keepLifecycleSessionAlive` impedisce che l&#39;app avvii una nuova sessione in seguito alla ripresa dopo l&#39;esecuzione in background. Usa questo metodo solo se l&#39;app si registra per le notifiche in background.

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```javascript
      ADB.keepLifecycleSessionAlive();
      ```

* **trackingSendQueuedHits**

   Fa sì che la libreria invii tutti gli hit presenti in coda, a prescindere dalle opzioni di batch correnti.

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```javascript
      ADB.trackingSendQueuedHits();
      ```

* **trackingGetQueueSize**

   Ottiene o imposta il numero di chiamate di tracciamento in attesa nella coda offline.

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```javascript
      ADB.trackingGetQueueSize(function(value){myTempVal = value;},function(){myTempVal = null;}); 
      ```

* **trackingClearQueue**

   Rimuove dalla coda offline tutte le chiamate di tracciamento memorizzate.

   >[!CAUTION]
   >
   >Da usare con cautela quando si cancella la coda manualmente; questa operazione non può essere annullata.

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```javascript
      ADB.trackingClearQueue(function(value){myTempVal = value;},function(){myTempVal = null;}); 
      ```

* **keepLifecycleSessionAlive**

   Indica all&#39;SDK che la prossima ripresa dal background non rappresenta l&#39;avvio di una nuova sessione, indipendentemente dal valore di timeout della sessione del ciclo di vita nel file di configurazione.

   >[!IMPORTANT]
   >
   >Nota: questo metodo è destinato alle app che si registrano per le notifiche mentre sono in background, e dovrebbe essere invocato solo dal codice in esecuzione mentre l&#39;app è in background.

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```javascript
      ADB.keepLifecycleSessionAlive();
      ```

* **collectLifecycleData**

   Indica all&#39;SDK che i dati del ciclo di vita devono essere raccolti per l&#39;utilizzo in tutte le soluzioni dell&#39;SDK. Per ulteriori informazioni, vedi [Metriche del ciclo di vita](/help/ios/metrics.md).

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```javascript
      ADB.collectLifecycleData(); 
      ```


## Metodi PII {#section_DB27270D2CEB4D369E0090FD9D1A7F81}

* **collectPII**

   Invia una richiesta di raccolta PII.

   * Di seguito è riportata la sintassi per questo metodo:

      ```javascript
      ADB.collectPII(piiData,success,fail); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```javascript
      ADB.collectPII({'k1':'v1','k2':'v2','k3':'v3'}, function (value) { alert('success'); },function (value) { alert('fail'); });
      ```

## Metodi di tracciamento {#section_7946BB753A4446FE8A3ED728AEF97D04}

* **trackAdobeDeepLink**

   Tiene traccia del click-through di un collegamento profondo (deep link) di Adobe.

   >[!TIP]
   >
   >Se la chiamata del ciclo di vita è un evento di avvio, i dati del collegamento Adobe verranno aggiunti; in caso contrario viene inviata una chiamata aggiuntiva.

   * Di seguito è riportata la sintassi per questo metodo:

      ```javascript
      ADB.trackAdobeDeepLink(deeplinkURL,success,fail);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```javascript
      ADB.trackAdobeDeepLink('xyz-deeplink-url',function(value){alert('success');},function(value){alert('fail');}); 
      ```

* **trackPushMessageClickthrough**

   Tiene traccia del click-through di un messaggio push.

   * Di seguito è riportata la sintassi per questo metodo:

      ```javascrpt
      ADB.trackPushMessageClickthrough(userInfo,success,fail); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```javascript
      ADB.trackPushMessageClickthrough({'k1':'v1','k2':'v2','k3':'v3'},function(value){alert('success');},function(value){alert('fail');}); 
      ```

* **trackLocalNotificationClickThrough**

   Tiene traccia del click-through di un messaggio di notifica locale.

   * Di seguito è riportata la sintassi per questo metodo:

      ```javascript
      ADB.trackLocalNotificationClickThrough(userInfo,success,fail); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```javascript
      ADB.trackLocalNotificationClickThrough({'k1':'v1','k2':'v2','k3':'v3'},function(value){alert('success');},function(value){alert('fail');}); 
      ```

* **trackState**

   Tiene traccia dello stato di un&#39;app con dati contestuali facoltativi. Gli stati sono le visualizzazioni disponibili nell&#39;app, ad esempio `home dashboard`, `app settings`, `cart` e così via. Questi stati sono simili alle pagine di un sito Web e le chiamate `trackState` incrementano le visualizzazioni di pagina. cData è un oggetto JSON con coppie chiave-valore da inviare nei dati contestuali.

   * Di seguito è riportata la sintassi per questo metodo:

      ```javascript
      ADB.trackState(stringstateName[,JSONcData]); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```javascript
      ADB.trackState("loginpage");
      ```

      ```javascript
        ADB.trackState("loginpage",{"user":"john","remember":"true"});
      ```

* **trackAction**

   Tiene traccia di un&#39;azione nell&#39;applicazione. Le azioni sono gli eventi che avvengono nell&#39;applicazione e che desideri misurare, come `logins`, `banner taps`, `feed subscriptions` e altre metriche.

   * Di seguito è riportata la sintassi per questo metodo:

      ```javascript
      ADB.trackAction(stringaction[,JSONcData]);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```javascript
      ADB.trackAction("login");
      ```

      ```javascript
      ADB.trackAction("login",{"user":"john","remember":"true"})
      ```

* **trackActionFromBackground**

   Traccia un’azione che si è verificata nel background. In questo modo gli eventi del ciclo di vita non vengono attivati in determinati scenari.

   * Di seguito è riportata la sintassi per questo metodo:

      ```javascript
      ADB.trackActionFromBackground(stringaction[,JSONcData]); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```javascript
      ADB.trackActionFromBackground("login");
      ```

      ```javascript
      ADB.trackActionFromBackground("login",{"user":"john","remember":"true"});
      ```

* **trackLocation**

   Invia le coordinate x e y correnti. Utilizza anche i punti di interesse definiti nel file `ADBMobileConfig.json` per determinare se la posizione fornita come parametro si trova nel raggio di riferimento di un POI. Se le coordinate correnti si trovano all&#39;interno di un POI definito, una variabile di dati di contesto viene compilata e inviata insieme alla chiamata `trackLocation`.

   * Di seguito è riportata la sintassi per questo metodo:

      ```javascript
       ADB.trackLocation(x,y[,JSONcData]);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```javascript
      ADB.trackLocation('40.431596','-111.893713');
      ```

* **trackLifetime&#x200B;ValueIncrease**

   Aggiunge al valore &quot;lifetime&quot; del ciclo di vita dell&#39;utente un incremento pari a `amount`.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      ADB.trackLifetimeValueIncrease(amount[,JSONcData]);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      ADB.trackLifetimeValueIncrease('10.01');
      ```

* **trackTimed&#x200B;ActionStart**

   Avvia un&#39;azione temporizzata con il nome `action`. Se invochi questo metodo per un&#39;azione già avviata, l&#39;azione temporizzata precedente viene sovrascritta.

   >[!TIP]
   >
   >Questa chiamata non invia un hit.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      ADB.trackTimedActionStart(action[,JSONcData]);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      ADB.trackTimedActionStart("cartToCheckout"); 
      ```

* **trackTimed&#x200B;ActionUpdate**

   Passa i dati `cData` per aggiornare i dati contestuali associati all&#39;azione `action`. I dati `cData` passati vengono aggiunti alla fine dei dati esistenti per l&#39;azione, e li sovrascrivono se per l&#39;azione è già definita la stessa chiave per `action`.

   >[!TIP]
   >
   >Questa chiamata non invia un hit.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      ADB.trackTimedActionUpdate(Stringaction[,JSONcData]);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      ADB.trackTimedActionUpdate("cartToCheckout",{'SampleContextDataKey3':'SampleContextDataVal3','SampleContextDataKey4':'SampleContextDataVal4'}); 
      ```

* **trackTimed&#x200B;ActionEnd**

   Termina un&#39;azione temporizzata.

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      ADB.trackTimedActionEnd("cartToCheckout");
      ```

* **trackingTimedActionExists**

   Restituisce un valore che indica se un&#39;azione temporizzata è in corso o meno.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      ADB.trackingTimedActionExists(function(value){myTempVal = value;},function(){myTempVal = null;});
      ```


## Metodi di Target {#section_C45D2FE54AE04EB5BD24D3508F8A3212}

* **targetLoadRequest**

   Invia una richiesta al server di `Target` configurato e restituisce il valore stringa dell&#39;offerta.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      ADB.targetLoadRequest(success,fail,name,defaultContent,parameters); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      ADB.targetLoadRequest(function (value)
      {myTempVal = value;},function() {myTempVal = null;},'bannerOffer','none',{'hp':'hp_val_new','hp.company':'adobe','hp.val2':'hp_val2'}); 
      ```

* **targetLoadOrderConfirmRequest**

   Invia una richiesta al server Target configurato.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      ADB.targetLoadOrderConfirmRequest(success,fail,name,orderId,orderTotal,productPurchaseId,parameters); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      ADB.targetLoadRequest(function(value){myTempVal=value;}
      ,function()
      {myTempVal = null; }
      ,'name','orderId','total','purchaseId'
      ,{'hp':'hp_val_new','hp.company':'adobe','hp.val2':'hp_val2'}
      ); 
      ```

* **targetClearCookies**

   Cancella i cookie di Target dall&#39;archiviazione dei cookie condivisi.

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      ADB.targetClearCookies();
      ```

* **targetLoadRequestWithNameWithLocationParameters**

   Elabora la richiesta di un servizio Target.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      ADB.targetLoadRequestWithNameWithLocationParameters(success,fail,name,defaultContent,profileParameters,orderParameters,mboxParameters,requestLocationParameters
      ); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      ADB.targetLoadRequestWithNameWithLocationParameters(function(){alert('success');},function(){alert('fail');},'bannerOffer','none',{'hp':'hp_val_new','hp.company':'adobe','hp.val2':'hp_val2'},{'hp':'hp_val_new','hp.company':'adobe','hp.val2':'hp_val2'},{'hp':'hp_val_new','hp.company':'adobe','hp.val2':'hp_val2'},{'hp':'hp_val_new','hp.company':'adobe','hp.val2':'hp_val2'}); 
      ```

* **targetLoadRequestWithName**

   Elabora la richiesta di un servizio Target.

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
      ADB.targetSessionID(success,fail); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
        ADB.targetSessionID(function(value){alert(value);},function(value){alert('fail');}); 
      ```

* **targetPcID**

   Ottiene il valore del cookie `PcID` restituito dal server Target per il visitatore corrente.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      ADB.targetPcID(success,fail);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      ADB.targetPcID(function(value){alert(value);},function(value){alert('fail');});
      ```

* **targetSetThirdPartyID**

   Imposta l&#39;ID visitatore personalizzato per Target.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      ADB.targetSetThirdPartyID(thirdPartyID,success,fail); 
      ```

   * Di seguito è riportato un esempio di codice per questo gruppo:

      ```java
      ADB.targetSetThirdPartyID('test-third-party-id',function(value){alert('success');},function(value){alert('fail');}); 
      ```

* **targetThirdPartyID**

   Ottiene l&#39;ID visitatore personalizzato per Target.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      ADB.targetThirdPartyID(success,fail); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      ADB.targetThirdPartyID(function(value){alert(value);},function(value){alert('fail');}); 
      ```

## Metodi di acquisizione {#section_EDEA25C4B2884487827069E9257A0BA6}

* **acquisitionCampaignStartForApp**

   Consente agli sviluppatori di avviare una campagna di acquisizione app, come se l&#39;utente avesse fatto clic su un collegamento. È utile per creare collegamenti di acquisizione manuali e per gestire direttamente il reindirizzamento all&#39;App Store (ad esempio con `SKStoreView`).

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      ADB.acquisitionCampaignStartForApp(appId,data,success,fail); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      ADB.acquisitionCampaignStartForApp('0652024f-adcd-49f9-9bd7-2552a4564d2f',{'extraDataKey':'extraDataValue'},success,fail); 
      ```


## Identificatore pubblicitario {#section_194607D101B047A19C51B19E176E1500}

Nel `AppDelegate` generato da Cordova, invoca `[ADBMobile setAdvertisingIdentifier:]` nel metodo delegate `application:didFinishLaunchingWithOptions:`. Per ulteriori informazioni, consulta [Metodi di configurazione](/help/ios/configuration/sdk-methods.md).

## Metodi di Audience Manager {#section_1FD12B29A0AF41D3BEACBB3D624EA0E4}

* **audienceGetVisitorProfile**

   Ottiene il profilo del visitatore.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      ADB.audienceGetVisitorProfile();
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      ADB.audienceGetVisitorProfile(function(value){profile = value;},function(){profile = null;}); 
      ```

* **audienceGetDpuuid**

   Restituisce l&#39;identificatore DPUUID.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      ADB.audienceGetDpuuid(success,fail);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
       ADB.audienceGetDpuuid(function(value){dpuuid=value;},function(){dpuuid=null;}); 
      ```

* **audienceGetDpid**

   Restituisce l&#39;identificatore DPID.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
       ADB.audienceGetDpid(success,fail);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      ADB.audienceGetDpid(function(value){dpid = value;},function(){dpid = null;}); 
      ```

* **audienceSetDpidAndDpuuid**

   Imposta gli identificatori DPID e DPUUID.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      ADB.audienceSetDpidAndDpuuid(dpid,dpuuid,success,fail);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      ADB.audienceSetDpidAndDpuuid(‘dpid’,‘dpuuid’,function(){…},function(){…});
      ```

      ```java
      ADB.audienceSetDpidAndDpuuid(‘dpid’,‘dpuuid’);
      ```

* **audienceSignalWithData**

   Elabora una richiesta del servizio Audience Manager.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      ADB.audienceSignalWithData(success,fail,data);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      ADB.audienceSignalWithData(function(){},function(){},{‘key1’:’value1’,‘key2’:‘value2’});
      ```

      ```java
      ADB.audienceSignalWithData({‘key1’:’value1’,‘key2’:‘value2’}); 
      ```

* **audienceReset**

   Ripristina l&#39;identificatore UUID di Audience Manager ed elimina il profilo del visitatore corrente.

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      ADB.audienceReset(); 
      ```

## Metodi del servizio ID {#section_840B4FAEA55B466F9754148ABA15EBDA}

* **visitorGetMarketingCloudId**

   Restituisce l&#39;Experience Cloud ID dal servizio ID.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      ADB.visitorGetMarketingCloudId(success,fail);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      ADB.visitorGetMarketingCloudId(function(value){mcid=value;},function(){mcid=null;}); 
      ```

* **visitorSyncIdentifiers**

   Sincronizza gli identificatori forniti con il servizio ID.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      ADB.visitorSyncIdentifiers(identifiers,success,fail);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      ADB.visitorSyncIdentifiers({‘key_id_1’:’value_id_1’},function(){…},function(){…})) 
      ```

      ```java
      ADB.visitorSyncIdentifiers({‘key_id_1’:‘value_id_1’});
      ```

* **visitorSyncIdentifiersWithAuthenticationState**

   Sincronizza gli identificatori forniti con il servizio ID visitatori.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      ADB.visitorSyncIdentifiersWithAuthenticationState(identifiers,authenticationState,success,fail); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      ADB.visitorSyncIdentifiersWithAuthenticationState({'k1':'v1','k2':'v2','k3':'v3'},ADB.mobileVisitorAuthenticationStateAuthenticated,function(value){alert('success');},function(value){alert('fail');});
      ```

* **visitorSyncIdentifierWithType**

   Sincronizza con il servizio ID visitatori l&#39;identificatore fornito.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      ADB.visitorSyncIdentifierWithType(identifierType,identifier,authenticationState,success,fail); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      ADB.visitorSyncIdentifierWithType('test-identifier-type','test-identifier',ADB.mobileVisitorAuthenticationStateAuthenticated,function(value){alert('success');},function(value){alert('fail');}); 
      ```

* **visitorAppendToURL**

   Aggiunge gli identificatori dei visitatori alla fine di un determinato URL.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      ADB.visitorAppendToURL(urlToAppend,success,fail);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      ADB.visitorAppendToURL('test_visitor_url',function(value){alert(value);},'');
      ```

* **visitorGetIDs**

   Restituisce tutti gli identificatori `visitorIDs` che sono stati sincronizzati.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      ADB.visitorGetIDs(success,fail)
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      ADB.visitorGetIDs(function(value){alert(value);},function(value){alert('fail');}); 
      ```

