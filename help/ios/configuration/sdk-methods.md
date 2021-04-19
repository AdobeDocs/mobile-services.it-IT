---
description: Elenco di metodi forniti dalla libreria iOS.
seo-description: Elenco di metodi forniti dalla libreria iOS.
seo-title: Metodi di configurazione
solution: Experience Cloud,Analytics
title: Metodi di configurazione
topic-fix: Developer and implementation
uuid: 623c7b07-fbb3-4d39-a5c4-e64faec4ca29
exl-id: b6841808-8fa8-4090-8cb3-ce647a3d5d08
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '1198'
ht-degree: 100%

---

# Metodi di configurazione {#configuration-methods}

Elenco di metodi forniti dalla libreria iOS.

L&#39;SDK supporta attualmente più soluzioni Adobe Experience Cloud, tra cui Analytics, Target, Audience Manager e il servizio Adobe Experience Platform Identity.

* **setAppExtensionType**

   Configura l’impostazione Adobe Mobile SDK per determinare il tipo di estensione attualmente in esecuzione.

   Imposta uno dei valori seguenti:
   * `ADBMobileAppExtensionTypeRegular` - l&#39;estensione è inclusa in un pacchetto con un&#39;app contenitore.
   * `ADBMobileAppExtensionTypeStandAlone` - l&#39;estensione non è inclusa in un pacchetto con un&#39;app contenitore.

   >[!TIP]
   >
   >Usa questo metodo **solo** se l&#39;app ha un&#39;estensione o se si tratta di un&#39;estensione autonoma. Per ulteriori informazioni, consulta *ADBMobileAppExtensionType*, di seguito.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      + (void) setAppExtensionType:(ADBMobileAppExtensionType)type;
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      [ADBMobile setAppExtensionType:ADBMobileAppExtensionTypeStandAlone]; 
      ```



* **version**

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

   Restituisce la rappresentazione enum dello stato di privacy per l&#39;utente corrente:

   * `ADBMobilePrivacyStatusOptIn` - gli hit vengono inviati immediatamente.
   * `ADBMobilePrivacyStatusOptOut` - gli hit vengono eliminati.
   * `ADBMobilePrivacyStatusUnknown` - se è abilitato il tracciamento offline, gli hit vengono salvati finché lo stato di privacy non cambia quando l&#39;utente acconsente (opt in, gli hit vengono inviati) o rinuncia (opt out, gli hit vengono eliminati). Se il tracciamento offline non è abilitato, gli hit vengono eliminati finché lo stato di privacy non cambia quando l&#39;utente acconsente.
Il valore predefinito è impostato nel file `ADBMobileConfig.json`.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      + (ADBMobilePrivacyStatus) privacyStatus;
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      ADBMobilePrivacyStatus privacyStatus = [ADBMobileprivacyStatus];
      ```

* **setPrivacyStatus**

   Imposta lo stato di privacy per l&#39;utente corrente su `status`.

   Imposta uno dei valori seguenti:

   * `ADBMobilePrivacyStatusOptIn` - gli hit vengono inviati immediatamente.
   * `ADBMobilePrivacyStatusOptOut` - gli hit vengono eliminati.
   * `ADBMobilePrivacyStatusUnknown` - se è abilitato il tracciamento offline, gli hit vengono salvati finché lo stato di privacy non cambia quando l&#39;utente acconsente (opt in, gli hit vengono inviati) o rinuncia (opt out, gli hit vengono eliminati). Se il tracciamento offline non è abilitato, gli hit vengono eliminati finché lo stato di privacy non cambia quando l&#39;utente acconsente.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      + (void) setPrivacyStatus:(ADBMobilePrivacyStatus)status;
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      [ADBMobile setPrivacyStatus:ADBMobilePrivacyStatusOptIn];
      ```

* **lifetimeValue**

   Restituisce il valore &quot;lifetime&quot; del ciclo di vita dell&#39;utente corrente. Il valore predefinito è `0`.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      + (NSDecimalNumber *) lifetimeValue;
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      NSDecimalNumber *lifeValue = [ADBMobile lifetimeValue];
      ```

* **trackingIdentifier**

   Restituisce l&#39;identificatore visitatore generato automaticamente. Si tratta di un ID visitatore univoco specifico per l’app, generato dai server Adobe. Se non è possibile raggiungere i server Adobe al momento della generazione, l’ID viene generato utilizzando l’identificatore CFUUID di Apple. Il valore viene generato al primo avvio, quindi viene memorizzato e utilizzato da tale momento in poi. Questo ID viene mantenuto nei successivi aggiornamenti dell’app, viene salvato e ripristinato durante il processo standard di backup dell’applicazione e viene rimosso al momento della disinstallazione.

   >[!TIP]
   >
   >Se l&#39;app viene aggiornata dall&#39;SDK di Experience Cloud 3.x alla versione 4.x, l&#39;ID precedente (personalizzato o generato in automatico) viene recuperato e memorizzato come identificatore utente personalizzato. Per ulteriori informazioni, consulta la riga `userIdentifier` di seguito. In tal modo i dati del visitatore vengono mantenuti da un aggiornamento all&#39;altro dell&#39;SDK. Per le nuove installazioni con l&#39;SDK 4.x, l&#39;identificatore dell&#39;utente è `nil` e viene utilizzato l&#39;identificatore di tracciamento.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      + (NSString *) trackingIdentifier;
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      NSString *tid = [ADBMobile trackingIdentifier];
      ```

* **userIdentifier**

   Se è stato impostato un identificatore personalizzato, viene restituito l&#39;identificatore utente. Se non è stato impostato un identificatore personalizzato, viene restituito `nil`. Il valore predefinito è `nil`.

   >[!TIP]
   >
   >Se l&#39;app viene aggiornata dall&#39;SDK di Experience Cloud 3.x alla versione 4.x, l&#39;ID visitatore precedente (personalizzato o generato in automatico) viene recuperato e memorizzato come identificatore utente personalizzato. In tal modo i dati del visitatore vengono mantenuti da un aggiornamento all’altro dell’SDK.

   Per le nuove installazioni con l&#39;SDK 4.x, l&#39;identificatore dell&#39;utente è `nil` finché non viene impostato.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      +(NSString *) userIdentifier;
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      NSString *uid = [ADBMobileuserIdentifier];
      ```

* **setUserIdentifier**

   Imposta l&#39;identificatore utente su `identifier`.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      +(void)setUserIdentifier:(NSString*)identifier;
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      [ADBMobile setUserIdentifier:@"billybob"]; 
      ```

* **debugLogging**

   Restituisce l&#39;attuale preferenza di accesso di debug. Il valore predefinito è `NO`.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      + (BOOL) debugLogging;
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      BOOL debugging = [ADBMobile debugLogging];
      ```

* **setDebugLogging**

   Imposta la preferenza per l&#39;accesso di su `debug` debug.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      + (void) setDebugLogging:(BOOL)debug;
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      [ADBMobile setDebugLogging:YES];
      ```

* **keepLifecycleSessionAlive**

   Indica all&#39;SDK che la prossima ripresa dal background non rappresenta l&#39;avvio di una nuova sessione, indipendentemente dal valore di timeout della sessione del ciclo di vita nel file di configurazione.

   >[!TIP]
   >
   >Questo metodo è destinato alle app che si registrano per le notifiche mentre sono in background e dovrebbe essere invocato solo dal codice in esecuzione mentre l&#39;app è in background.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      + (void) keepLifecycleSessionAlive;
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      [ADBMobile keepLifecycleSessionAlive]; 
      ```

* **collectLifecycleData**

   Indica all&#39;SDK che i dati del ciclo di vita devono essere raccolti per l&#39;utilizzo in tutte le soluzioni dell&#39;SDK. Per ulteriori informazioni, vedi [Metriche del ciclo di vita](/help/ios/metrics.md).

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

   Consente di passare dati aggiuntivi durante la raccolta delle metriche &quot;lifecycle&quot; sul ciclo di vita.

   Questo metodo deve essere invocato dal punto di ingresso dell&#39;app. Se applicabile, potrebbe includere i metodi `application:didFinishLaunchingWithOptions:` e/o `applicationWillEnterForeground:` nella classe AppDelegate.

   >[!IMPORTANT]
   >
   >I dati passati all&#39;SDK tramite `collectLifecycleDataWithAdditionalData:` verranno memorizzati dall&#39;SDK in `NSUserDefaults`. L&#39;SDK eliminerà dal parametro `NSDictionary` i valori che non sono di tipo `NSString` o `NSNumber`. Per usare `collectLifecycleDataWithAdditionalData:`, devi disporre della versione SDK **4.4** o successiva.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      + (void) collectLifecycleDataWithAdditionalData:(nullableNSDictionary*)data; 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      [ADBMobile collectLifecycleDataWithAdditionalData:@{@"entryType":@"appShortcutIcon"}]; 
      ```

* **pauseCollectingLifecycleData**

   Utilizza questa API per mettere in pausa la raccolta dati del ciclo di vita. Per ulteriori informazioni, vedi [Metriche del ciclo di vita](/help/ios/metrics.md).

   >[!IMPORTANT]
   >
   >Nel metodo delegato `applicationDidEnterBackground` devi prima chiamare il metodo `pauseCollectingLifecycleData`.
   >
   >L&#39;API attenua il problema su iPhone 7/7s o dispositivi precedenti con iOS 13, in cui la metrica della lunghezza di sessione era anormale. La causa è riconducibile ad alcune modifiche non note in iOS 13, per cui iOS non lascia abbastanza tempo per il completamento dell&#39;attività quando l&#39;app viene mantenuta in background.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      + (void) pauseCollectingLifecycleData;
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      - (void)applicationDidEnterBackground:(UIApplication *)application{
          // manually stop the lifecycle of SDK
          // important: do NOT call any track state or track action after this line
          [ADBMobile pauseCollectingLifecycleData];   
      
      
          // the following code is optional, may help to mitigate the issue a bit more. If you have other logic to run here that probably takes more than 10ms, then there is no need to add this line of code.
          [NSThread sleepForTimeInterval:0.01];
      
      
          // app's code to handle applicationDidEnterBackground
      }
      ```


* **overrideConfigPath**

   Consente di caricare un diverso file di configurazione ADBMobile JSON all’avvio dell’applicazione. La configurazione diversa viene utilizzata fino alla chiusura dell’applicazione.

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

   Imposta l’identificatore IDFA nell’SDK. Se l’identificatore IDFA è stato impostato nell’SDK, verrà inviato nel ciclo di vita. È inoltre possibile accedervi in Segnali (Postback).

   >[!TIP]
   >
   >Recupera l&#39;identificatore IDFA dall&#39;API di Apple **solo** se utilizzi un servizio di annunci. Se recuperi l&#39;identificatore IDFA e non lo utilizzi correttamente, l&#39;app potrebbe venire rifiutata.
   >
   >Se l’applicazione richiede l’identificatore IDFA, consulta la [documentazione di Apple](https://developer.apple.com/documentation/adsupport) per informazioni sulle preferenze dell’utente in merito al tracciamento degli annunci e per ottenere il valore IDFA.
   >
   >Per iOS 14 e versioni successive, per consentire il corretto recupero del valore IDFA è necessario implementare il nuovo [framework App Tracking Transparency](https://developer.apple.com/documentation/apptrackingtransparency).
   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      +(void) setAdvertisingIdentifier:(NSString*)identifier;
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      NSString *idfa = // retrieve IDFA using AdSupport (before iOS 14.0) and/or AppTrackingTransparency (iOS 14.0+)
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
