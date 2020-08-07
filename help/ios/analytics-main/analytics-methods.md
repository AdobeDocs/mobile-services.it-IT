---
description: Elenco dei metodi di Adobe Analytics forniti dalla libreria iOS.
seo-description: Elenco dei metodi di Adobe Analytics forniti dalla libreria iOS.
seo-title: Metodi di Analytics
solution: Marketing Cloud,Analytics
title: Metodi di Analytics
topic: Developer and implementation
uuid: d49fe6de-cb32-4b96-9891-c567310e59a6
translation-type: tm+mt
source-git-commit: c64e2fa7cee3cd35c4574e5007406b7604c99499
workflow-type: tm+mt
source-wordcount: '784'
ht-degree: 100%

---


# Metodi di Analytics {#analytics-methods}

Elenco dei metodi di Adobe Analytics forniti dalla libreria iOS.

L&#39;SDK supporta attualmente più soluzioni Adobe Experience Cloud, tra cui Analytics, Target, Audience Manager e il servizio Adobe Experience Platform Identity. I metodi sono contraddistinti dal prefisso della relativa soluzione. I metodi di Experience Cloud ID hanno il prefisso `track`.

Ciascuno di questi metodi viene usato per inviare dati alla suite di rapporti di Adobe Analytics.

* **trackState:&#x200B;data:**

   Gli stati sono le visualizzazioni disponibili nell&#39;app, ad esempio `home dashboard`, `app settings`, `cart` e così via. Questi stati sono simili alle pagine di un sito Web e le chiamate `trackState` incrementano le visualizzazioni di pagina. Se `state` è vuoto, nei rapporti viene visualizzato come *app name app version (build)*. Se trovi questo valore nei rapporti, assicurati che in ogni chiamata `state` sia impostato il valore `trackState`.

   >[!TIP]
   >
   >Questa è l&#39;unica chiamata di tracciamento che incrementa le visualizzazioni pagina.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      + (void)  trackState:(NSString  *)state
                      data:(NSDictionary  *)data;
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      [ADBMobile  trackState:@"loginScreen"
                        data:nil]; 
      ```

* **trackAction:&#x200B;data:**

   Tiene traccia di un&#39;azione nell&#39;applicazione. Le azioni che desideri misurare, come `logons`, `banner taps`, `feed subscriptions` e altre metriche, si verificano nell&#39;app.

   >[!TIP]
   >
   >In presenza di codice che potrebbe essere eseguito mentre l&#39;applicazione è in background (ad esempio, un recupero di dati in background), utilizza piuttosto `trackActionFromBackground`.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      +  (void)  trackAction:(NSString  *)action
                        data:(NSDictionary  *)data; 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      [ADBMobile  trackAction:@"heroBannerTouched"
                         data:nil]; 
      ```

* **trackingIdentifier**

   Recupera l&#39;identificativo di monitoraggio di Analytics.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      + (NSString *) trackingIdentifier; 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      NSString *trackingId = [ADBMobile trackingIdentifier];
      ```

* **trackActionFromBackground:&#x200B;data:**

   Tiene traccia di un&#39;azione eseguita in background, che in alcuni scenari impedisce l&#39;attivazione di eventi di ciclo di vita.

   >[!TIP]
   >
   >Questo metodo dovrebbe essere invocato solo dal codice in esecuzione mentre l&#39;applicazione è in background.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
       +  (void)  trackActionFromBackground:(NSString  *)action
                                       data:(NSDictionary  *)data; 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      [ADBMobile  trackActionFromBackground:@"downloadedUpdate"
                                       data:nil];
      ```

* **trackLocation:&#x200B;data:**

   Invia le coordinate x,y correnti. Utilizza anche i punti di interesse definiti nel file `ADBMobileConfig.json` per determinare se la posizione fornita come parametro si trova nel raggio di riferimento di un POI. Se le coordinate correnti si trovano in un POI definito, una variabile di dati di contesto viene compilata e inviata insieme alla chiamata `trackLocation`.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      +  (void)  trackLocation:(CLLocation  *)location
                          data:(NSDictionary  *)data; 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      [ADBMobile  trackLocation:userLocation
                           data:nil]; 
      ```

* **trackBeacon:&#x200B;data:**

   Monitora quando un utente arriva in prossimità di un beacon.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      +  (void)  trackLocation:(CLBeacon  *)beacon
                          data:(NSDictionary  *)data;
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      [ADBMobile  trackBeacon:beacon
                         data:nil];
      ```

* **trackingClearCurrentBeacon**

   Elimina i dati del beacon dopo che un utente si allontana dalle vicinanze del beacon.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      + (void) trackingClearCurrentBeacon;
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      [ADBMobile trackingClearCurrentBeacon];
      ```

* **trackLifetimeValueIncrease:&#x200B;data:**

   Aggiunge al valore &quot;lifetime&quot; del ciclo di vita dell&#39;utente un incremento pari a `amount`.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
       +  (void)  trackLifetimeValueIncrease:(NSDecimalNumber  *)amount
                                       data:(NSDictionary  *)data; 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      [ADBMobile  trackLifetimeValueIncrease:30
                                         data:nil];
      ```

* **trackTimedActionStart:&#x200B;data:**

   Avvia un&#39;azione temporizzata con il nome `action`. Se invochi questo metodo per un&#39;azione già avviata, l&#39;azione temporizzata precedente viene sovrascritta.

   >[!TIP]
   >
   >Questa chiamata non invia un hit.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      +  (void)  trackTimedActionStart:(NSString  *)action
                                  data:(NSDictionary  *)data; 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      [ADBMobile  trackTimedActionStart:@"cartToCheckout"
                                  data:nil]; 
      ```

* **trackTimedActionUpdate:&#x200B;data:**

   Passa i dati `data` per aggiornare i dati contestuali associati all&#39;azione `action`. I dati `data` passati vengono aggiunti alla fine dei dati esistenti per l&#39;azione, e li sovrascrivono se per l&#39;azione `action`, è già definita la stessa chiave.

   >[!TIP]
   >
   >Questa chiamata non invia un hit.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
       +  (void)  trackTimedActionUpdate:(NSString  *)action
                                    data:(NSDictionary  *)data; 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      [ADBMobile  trackTimedActionUpdate:@"cartToCheckout"
                                    data:@{@"quantity":@"3"}];
      ```

* **trackTimedActionEnd:&#x200B;logic:**

   Termina un&#39;azione temporizzata. Se fornisci `block`, potrai accedere ai valori di tempo finali e manipolare i dati `data` prima di inviare l&#39;hit finale.

   >[!TIP]
   >
   >Se fornisci `block`, devi restituire `YES` per inviare un hit. Se per `nil` viene passato `block`, viene inviato l&#39;hit finale.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      +  (void)  trackTimedActionEnd:(NSString  *)action
                          logic:(BOOL  (^)  (NSTimeInterval  inAppDuration,
                                                  NSTimeInterval totalDuration,
                                                  NSMutableDictionary *data))block; 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      [ADBMobile  trackTimedActionEnd:@"cartToCheckout"
                    logic:^(NSTimeInterval inApp,
                    NSTimeInterval  total,
                    NSMutableDictionary  *data)  {
                        data[@"price"]  =  @"49.95";
                        return  YES;
                    }];
      ```

* **trackingTimedActionExists**

   Restituisce un valore che indica se un&#39;azione temporizzata è in corso o meno.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      + (BOOL) trackingTimedActionExists:(NSString *)action;
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      BOOL *actionExists = [ADBMobile trackingTimedActionExists];
      ```

* **trackingSendQueuedHits**

   Richiede SDK 4.1. A prescindere da quanti hit siano attualmente in coda, forza la libreria a inviare tutti gli hit nella coda offline.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      + (void) trackingSendQueuedHits;
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      [ADBMobile trackingSendQueuedHits]; 
      ```

* **trackingGetQueueSize**

   Recupera il numero di hit attualmente presenti nella coda offline.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
       + (NSUInteger) trackingGetQueueSize;
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      NSUInteger *queueSize = [ADBMobile trackingGetQueueSize];
      ```

* **trackingClearQueue**

   Elimina tutti gli hit dalla coda offline.

   >[!CAUTION]
   >
   >Da usare con cautela quando si cancella la coda manualmente. Questo processo non può essere annullato.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      + (void) trackingClearQueue;
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      [ADBMobile trackingClearQueue]; 
      ```



* **trackPushMessageClickThrough**

   Tiene traccia del click-through di un messaggio push.

   >[!IMPORTANT]
   >
   >Questo metodo non incrementa le visualizzazioni della pagina.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      + (void) trackPushMessageClickThrough:(NSDictionary *)userInfo;
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      -  (void)application:(UIApplication  *)application  
      didReceiveRemoteNotification:(NSDictionary  *)userInfo  
      fetchCompletionHandler:(void  (^)
      (UIBackgroundFetchResult))completionHandler  {
          // only send the hit if the app is not active
          if (application.applicationState !=  UIApplicationStateActive)  {
              [ADBMobile  trackPushMessageClickThrough:userInfo];
      
          }
          completionHandler(UIBackgroundFetchResultNoData);
      }
      ```
