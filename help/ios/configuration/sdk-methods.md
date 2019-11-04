---
description: Elenco di metodi forniti dalla libreria iOS.
seo-description: Elenco di metodi forniti dalla libreria iOS.
seo-title: Metodi di configurazione
solution: Experience Cloud,Analytics
title: Metodi di configurazione
topic: Sviluppatore e implementazione
uuid: 623c7b07-fbb3-4d39-a5c4-e64faec4ca29
translation-type: ht
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Metodi di configurazione {#configuration-methods}

Elenco di metodi forniti dalla libreria iOS.

L'SDK supporta attualmente più soluzioni Adobe Experience Cloud, tra cui Analytics, Target, Audience Manager e il servizio Adobe Experience Platform Identity.

* **setAppExtensionType**

   Configura l'impostazione SDK di Adobe Mobile per determinare quale tipo di estensione viene attualmente eseguito.

   Imposta uno dei valori seguenti:
   * `ADBMobileAppExtensionTypeRegular`: l'estensione è inclusa in un pacchetto con un'app contenitore.
   * `ADBMobileAppExtensionTypeStandAlone`: l'estensione non è inclusa in un pacchetto con un'app contenitore.
   >[!TIP]
   >
   >Usa questo metodo **solo** se l'app ha un'estensione o se si tratta di un'estensione autonoma. Per ulteriori informazioni, consulta *ADBMobileAppExtensionType*, di seguito.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      + (void) setAppExtensionType:(ADBMobileAppExtensionType)type;
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      [ADBMobile setAppExtensionType:ADBMobileAppExtensionTypeStandAlone]; 
      ```



* **versione**

   Restituisce la versione corrente della libreria Adobe Mobile.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      +(NSString*) version;
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      NSString*libraryVersion = [ADBMobileversion];
      ```

* **privacyStatus**

   Restituisce la rappresentazione enum dello stato di privacy per l'utente corrente:

   * `ADBMobilePrivacyStatusOptIn` - gli hit vengono inviati immediatamente.
   * `ADBMobilePrivacyStatusOptOut` - gli hit vengono eliminati.
   * `ADBMobilePrivacyStatusUnknown` - se è abilitato il tracciamento offline, gli hit vengono salvati finché lo stato di privacy non cambia quando l'utente acconsente (opt in, gli hit vengono inviati) o rinuncia (opt out, gli hit vengono eliminati). Se il tracciamento offline non è abilitato, gli hit vengono eliminati finché lo stato di privacy non cambia quando l'utente acconsente. 
Il valore predefinito è impostato nel file `ADBMobileConfig.json`.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      + (ADBMobilePrivacyStatus) privacyStatus;
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      ADBMobilePrivacyStatus privacyStatus = [ADBMobileprivacyStatus];
      ```

* Il metodo **setPrivacyStatus**

   Imposta lo stato di privacy per l'utente corrente su `status`.

   Imposta uno dei valori seguenti:

   * `ADBMobilePrivacyStatusOptIn` - gli hit vengono inviati immediatamente.
   * `ADBMobilePrivacyStatusOptOut` - gli hit vengono eliminati.
   * `ADBMobilePrivacyStatusUnknown` - se è abilitato il tracciamento offline, gli hit vengono salvati finché lo stato di privacy non cambia quando l'utente acconsente (opt in, gli hit vengono inviati) o rinuncia (opt out, gli hit vengono eliminati). Se il tracciamento offline non è abilitato, gli hit vengono eliminati finché lo stato di privacy non cambia quando l'utente acconsente.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      + (void) setPrivacyStatus:(ADBMobilePrivacyStatus)status;
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      [ADBMobile setPrivacyStatus:ADBMobilePrivacyStatusOptIn];
      ```

* **lifetimeValue**

   Restituisce il valore "lifetime" del ciclo di vita dell'utente corrente. Il valore predefinito è `0`.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      + (NSDecimalNumber *) lifetimeValue;
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      NSDecimalNumber *lifeValue = [ADBMobile lifetimeValue];
      ```

* **trackingIdentifier**

   Restituisce l'identificatore visitatore generato automaticamente. Si tratta di un ID visitatore univoco specifico per l'app, generato dai server Adobe. Se i server Adobe non sono accessibili al momento della generazione di questo ID, verrà utilizzato l'identificatore CFUUID di Apple. Il valore viene generato al primo avvio, memorizzato e utilizzato da tale momento in poi. Questo ID viene mantenuto nei successivi aggiornamenti dell'app, viene salvato e ripristinato durante il processo standard di backup dell'applicazione, e viene rimosso con la disinstallazione dell'app.

   >[!TIP]
   >
   >Se l'app viene aggiornata dall'SDK di Experience Cloud 3.x alla versione 4.x, l'ID precedente (personalizzato o generato in automatico) viene recuperato e memorizzato come identificatore utente personalizzato. Per ulteriori informazioni, consulta la riga `userIdentifier` di seguito. In tal modo i dati del visitatore vengono mantenuti da un aggiornamento all'altro dell'SDK. Per le nuove installazioni con l'SDK 4.x, l'identificatore dell'utente è `nil` e viene utilizzato l'identificatore di tracciamento.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      + (NSString *) trackingIdentifier;
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      NSString *tid = [ADBMobile trackingIdentifier];
      ```

* **userIdentifier**

   Se è stato impostato un identificatore personalizzato, viene restituito l'identificatore utente. Se non è stato impostato un identificatore personalizzato, viene restituito `nil`. Il valore predefinito è `nil`.

   >[!TIP]
   >
   >Se l'app viene aggiornata dall'SDK di Experience Cloud 3.x alla versione 4.x, l'ID visitatore precedente (personalizzato o generato in automatico) viene recuperato e memorizzato come identificatore utente personalizzato. In tal modo i dati del visitatore vengono mantenuti da un aggiornamento all'altro dell'SDK.

   Per le nuove installazioni con l'SDK 4.x, l'identificatore dell'utente è `nil` finché non viene impostato.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      +(NSString *) userIdentifier;
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      NSString *uid = [ADBMobileuserIdentifier];
      ```

* **setUserIdentifier**

   Imposta l'identificatore utente su `identifier`.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      +(void)setUserIdentifier:(NSString*)identifier;
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      [ADBMobile setUserIdentifier:@"billybob"]; 
      ```

* **debugLogging**

   Restituisce l'attuale preferenza di accesso di debug. Il valore predefinito è `NO`.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      + (BOOL) debugLogging;
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      BOOL debugging = [ADBMobile debugLogging];
      ```

* **setDebugLogging**

   Imposta la preferenza per l'accesso di su `debug`debug.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      + (void) setDebugLogging:(BOOL)debug;
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      [ADBMobile setDebugLogging:YES];
      ```

* **keepLifecycleSessionAlive**

   Indica all'SDK che la prossima ripresa dal background non rappresenta l'avvio di una nuova sessione, indipendentemente dal valore di timeout della sessione del ciclo di vita nel file di configurazione.

   >[!TIP]
   >
   >Questo metodo è destinato alle app che si registrano per le notifiche mentre sono in background e dovrebbe essere invocato solo dal codice in esecuzione mentre l'app è in background.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      + (void) keepLifecycleSessionAlive;
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      [ADBMobile keepLifecycleSessionAlive]; 
      ```

* **collectLifecycleData**

   Indica all'SDK che i dati del ciclo di vita devono essere raccolti per l'utilizzo in tutte le soluzioni dell'SDK. Per ulteriori informazioni, vedi [Metriche del ciclo di vita](/help/ios/metrics.md).

   >[!TIP]
   >
   >La posizione preferita da cui invocare questo metodo è in `application:didFinishLaunchingWithOptions:`.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      + (void) collectLifecycleData;
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      [ADBMobile collectLifecycleData];
      ```

* **collectLifecycleDataWithAdditionalData:**

   Consente di passare dati aggiuntivi durante la raccolta delle metriche "lifecycle" sul ciclo di vita.

   Questo metodo deve essere invocato dal punto di ingresso dell'app. Se applicabile, potrebbe includere i metodi `application:didFinishLaunchingWithOptions:` e/o `applicationWillEnterForeground:` nella classe AppDelegate.

   >[!IMPORTANT]
   >
   >I dati passati all'SDK tramite `collectLifecycleDataWithAdditionalData:` verranno memorizzati dall'SDK in `NSUserDefaults`. L'SDK eliminerà dal parametro `NSDictionary` i valori che non sono di tipo `NSString` o `NSNumber`. Per usare `collectLifecycleDataWithAdditionalData:`, devi disporre della versione SDK **4.4** o successiva.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      + (void) collectLifecycleDataWithAdditionalData:(nullableNSDictionary*)data; 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      [ADBMobile collectLifecycleDataWithAdditionalData:@{@"entryType":@"appShortcutIcon"}]; 
      ```

* **overrideConfigPath**

   Consente di caricare un diverso file di configurazione ADBMobile JSON all'avvio dell'applicazione. La diversa configurazione viene utilizzata fino alla chiusura dell'applicazione.

   >[!IMPORTANT]
   >
   >Per usare `overrideConfigPath`, devi disporre della versione SDK 4.2 o successiva.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
       + (void) overrideConfigPath: (nullableNSString *) path;
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      NSString *filePath = [[NSBundle mainBundle] pathForResource:@"ExampleJSONFile" ofType:@"json"]; 
      [ADBMobile overrideConfigPath:filePath];
      ```

* **setPushIdentifier**

   Imposta il token dispositivo per le notifiche push.

   >[!IMPORTANT]
   >
   >Usa questo metodo solo nel metodo `application:didRegisterForRemoteNotificationsWithDeviceToken:`.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      + (void) setPushIdentifier:(NSData *)deviceToken;
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      - (void) application:(UIApplication *) application  didRegisterForRemoteNotificationsWithDeviceToken:(NSData *)deviceToken { 
      [ADBMobile setPushIdentifier:deviceToken];  
      }
      ```

* **setAdvertisingIdentifier**

   Imposta l'identificatore IDFA nell'SDK. Se l'identificatore IDFA è stato impostato nell'SDK sarà inviato nel ciclo di vita. È inoltre possibile accedervi in Segnali (Postback).

   >[!TIP]
   >
   >Recupera l'identificatore IDFA dall'API di Apple **solo** se utilizzi un servizio di annunci. Se recuperi l'identificatore IDFA e non lo utilizzi correttamente, l'app potrebbe venire rifiutata.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      +(void) setAdvertisingIdentifier:(NSString*)identifier;
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      NSString *idfa = [[[ASIdentifierManager sharedManager]advertisingIdentifier] UUIDString]; 
      [ADBMobile setAdvertisingIdentifier:idfa]; 
      ```

## ADBMobileAppExtensionType enum {#section_18DB491D0ABC4765BB5A467D8FEF4F1B}

```objective-c
/** 
 * @brief An enum type. 
 * The possible types of app extension you might use 
 * @see setAppExtensionType 
 */ 
typedef NS_ENUM(NSUInteger, ADBMobileAppExtensionType) { 
    ADBMobileAppExtensionTypeRegular = 0, /*!< Enum value ADBMobileAppExtensionTypeRegular. */ 
    ADBMobileAppExtensionTypeStandAlone = 1 /*!< Enum value ADBMobileAppExtensionTypeStandAlone. */ 
};
```

