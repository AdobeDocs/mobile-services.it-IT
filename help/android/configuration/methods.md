---
description: Elenco dei metodi di forniti dalla libreria Android.
keywords: android;libreria;mobile;sdk
seo-description: Elenco dei metodi di forniti dalla libreria Android.
seo-title: Metodi di Configurazione
solution: Marketing Cloud,Analytics
title: Metodi di Configurazione
topic: Sviluppatore e implementazione
uuid: 663aeb6c-1b97-4a3a-8c0e-dd4c2ec28c01
translation-type: tm+mt
source-git-commit: bf076aa8e59d5c3e634fc4ae21f0de0d4541a83f

---


# Configuration methods{#configuration-methods}

Elenco dei metodi di forniti dalla libreria Android.

## Initial configuration {#section_9169243ECC4744A899A8271F92090ECD}

Il seguente metodo deve essere chiamato una volta nel metodo `onCreate` della tua attività principale:

* `setContext`
Di seguito è riportato un esempio di codice per questo metodo:

   ```java
    @Override
    public void onCreate(BundlesavedInstanceState){
      super.onCreate(savedInstanceState)
      setContentView(R.layout.main);
      Config.setContext(this.getApplicationContext());
    }
   ````


## SDK settings (Config Class) {#section_C1EB977043C04D2B93E5A63DB72828B6}

* **registerAdobeDataCallback**

   * Registra un oggetto che implementa l'interfaccia `AdobeDataCallback`. The overwritten "call" method will be invoked with a `Config.MobileDataEvent` value and the associated data in a `Map<String, Object>` for the triggering event. Per ulteriori dettagli sugli eventi che attiveranno questo callback, vedi *MobileDataEventEnum* in fondo a questo argomento.

      >[!TIP]
      >
      >This method requires version 4.9.0 or later.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void registerAdobeDataCallback(final AdobeDataCallback&amp;nbsp;callback);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
        Config.registerAdobeDataCallback(new Config.AdobeDataCallback() {
          @Override
          public void call(Config.MobileDataEvent event, Map<String, Object> contextData) {
              // handle each event type accordingly 
              if (event == Config.MobileDataEvent.MOBILE_EVENT_ACQUISITION_INSTALL) {
                   // do something with acquisition data found in contextData parameter
                   HashMap<String, Object> acquisitionData = new HashMap<String, Object>(contextData);
              }
          }
      });
      ```

* **getVersion**

   * Restituisce la versione corrente della libreria Adobe Mobile.
   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static String getVersion();
      ```

   * Esempio di codice per questo metodo:

      ```java
      String libraryVersion = Config.getVersion(); 
      ```

* **getPrivacyStatus**

   * Restituisce la rappresentazione enum dello stato di privacy per l’utente corrente.

      I valori di stato disponibili sono:

      * `MOBILE_PRIVACY_STATUS_OPT_IN`, dove gli hit vengono inviati immediatamente.
      * `MOBILE_PRIVACY_STATUS_OPT_OUT`, in cui gli hit vengono scartati.
      * `MOBILE_PRIVACY_STATUS_UNKNOWN` - se la suite di rapporti ha la marca temporale abilitata, gli hit vengono salvati finché lo stato di privacy non cambia in optedin (gli hit vengono inviati) o in optedout (gli hit vengono scartati).

         Se le marche temporali non sono abilitate nella suite di rapporti, gli hit vengono scartati fino a quando lo stato di privacy non cambia in optedin. Il valore predefinito è impostato nel file `ADBMobileConfig.json`.
   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static MobilePrivacyStatus getPrivacyStatus(); 
      ```

   * Here is a code sample for this method:

      ```java
      MobilePrivacyStatus privacyStatus Config.getPrivacyStatus();
      ```


* Il metodo **setPrivacyStatus**

   * Imposta lo stato di privacy per l'utente corrente su `status`.

      Puoi impostare lo stato di privacy su uno dei seguenti valori:
      * `MOBILE_PRIVACY_STATUS_OPT_IN`, where the hits are sent immediately. Questi hit vengono inviati immediatamente.
      * `MOBILE_PRIVACY_STATUS_OPT_OUT`, where the its are discarded. Questi hit vengono scartati.
      * `MOBILE_PRIVACY_STATUS_UNKNOWN` - se la suite di rapporti ha la marca temporale abilitata, gli hit vengono salvati finché lo stato di privacy non cambia in optedin (gli hit vengono inviati) o in optedout (gli hit vengono scartati).
Se le marche temporali non sono abilitate nella suite di rapporti, gli hit vengono scartati fino a quando lo stato di privacy non cambia in optedin.
   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void setPrivacyStatus(MobilePrivacyStatus status); 
      ```

   * Esempio di codice per questo metodo:

      ```java
      Config.setPrivacyStatus(MobilePrivacyStatus.MOBILE_PRIVACY_STATUS_OPT_IN); 
      ```


* **getLifetimeValue**

   * Restituisce il valore "lifetime" del ciclo di vita dell'utente corrente. Il valore predefinito è `0`.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static BigDecimal getLifetimeValue();
      ```

   * Esempio di codice per questo metodo:

      ```java
      BigDecimal currentLifetimeValue Config.getLifetimeValue(); 
      ```

* **getUserIdentifier**

   * Se è stato impostato un identificatore personalizzato, restituisce l'identificatore utente personalizzato. In caso contrario restituisce `null`. Il valore predefinito è `null`.

      >[!TIP]
      >
      >Se l’app viene aggiornata dall’SDK Experience Cloud 3.x alla versione 4.x, l’ID visitatore precedente (personalizzato o generato in automatico) viene recuperato e memorizzato come identificatore utente personalizzato. In tal modo i dati del visitatore vengono mantenuti da un aggiornamento all'altro dell'SDK. Per le nuove installazioni sull'SDK 4.x, finché non impostato, l'identificatore utente è `null`.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static String&amp getUserIdentifier();
      ```

   * Esempio di codice per questo metodo:

      ```java
      String userId = Config.getUserIdentifier();
      ```

* **setUserIdentifier**

   * Imposta l'identificatore utente su `identifier`.
   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void setUserIdentifer(String identifier);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      Config.setUserIdentifier("billybob"); 
      ```

* **getDebugLogging**

   * Restituisce l'attuale preferenza di accesso di debug. Il valore predefinito è `false`.
   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static Boolean getDebugLogging(); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      Boolean debugging = Config.getDebugLogging(); 
      ```

* **setDebugLogging**
   * Imposta la preferenza per l'accesso di su `debugLogging`debug.
   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void setDebugLogging(Boolea debugLogging);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      Config.setDebugLogging(true);
      ```

* **collectLifecycleData**
   * Indica all'SDK che i dati del ciclo di vita devono essere raccolti per l'utilizzo in tutte le soluzioni dell'SDK. Per ulteriori informazioni, vedi [Metriche del ciclo di vita](/help/android/configuration/methods.md).

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void collectLifecycleData(final Activity activity,final Map<String, Object>contextData); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      @Override
      protectedvoid  onResume()  {
        super.onResume();
        Config.collectLifecycleData(this);
        } 
      ```

      Con dati contestuali ulteriori:

      ```java
      @Override
      public  void  onResume()  {
        HashMap<String, Object> contextData = new HashMap<String, Object>();
        contextData.put("myapp.category", "Game");        Config.collectLifecycleData(this, contextData);} 
      ```

* **collectLifecycleData (Activity activity)**

   * (**Versione 4.2 o versioni successive**) Indica all'SDK che i dati del ciclo di vita devono essere raccolti per l'utilizzo in tutte le soluzioni nell'SDK. Per ulteriori informazioni, vedi [Metriche del ciclo di vita](/help/android/metrics.md).
   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void collectLifecycleData(final Activity activity);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      @Overrideprotected void onResume() {
        super.onResume()
        // assume being called in an Activity class Config.collectLifecycleData(this);
        } 
        ```
      
* **pauseCollecting&#x200B;LifecycleData**

   * Indica all'SDK che l'applicazione è in pausa, in modo che le metriche del ciclo di vita vengano calcolate correttamente. Ad esempio, `onPause` recupera una marca temporale per determinare la durata della sessione precedente. Inoltre, imposta un flag in modo che il ciclo di vita acquisisca che l'applicazione non si è bloccata. Per ulteriori informazioni, vedi [Metriche del ciclo di vita](/help/android/metrics.md).

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void pauseCollectingLifecycleData(); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      @Override
      protected void onPause() {
        super.onPause();
        Config.pauseCollectingLifecycleData();
      } 
      ```

* **setSmallIconResourceId(int resourceId)**

   * (**Versione 4.2 o successiva**) Imposta l'icona piccola che verrà utilizzata per le notifiche create dall'SDK. Questa icona compare sulla barra di stato e sarà l'immagine secondaria visualizzata quando l'utente visualizza la notifica completa nel Centro notifiche.
   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void setSmallIconResourceId(final int resourceId); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      Config.setSmallIconResourceId(R.drawable.appIcon);
      ```

* **setLargeIconResourceId(int resourceId)**

   * (**Versione 4.2 o successiva**) Imposta l'icona grande che verrà utilizzata per le notifiche create dall'SDK. Questa icona sarà l'immagine principale visualizzata dall'utente nella notifica completa all'interno del Centro notifiche.
   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void setLargeIconResourceId(final int  resourceId);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```Java
      Config.setLargeIconResourceId(R.drawable.appIcon);
      ```

* **overrideConfigStream(InputStream configInput)**

   * (**Versione 4.2 o successiva**) Consente di caricare un diverso file di configurazione ADBMobile JSON all'avvio dell'applicazione. La diversa configurazione viene utilizzata fino alla chiusura dell'applicazione.
   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void overrideConfigStream(final InputStream configInput);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
       try {
          InputStream configInput = getAssets().open("ExampleJSONFile.json") 
          Config.overrideConfigStream(configInput)
          } catch (IOException ex) { 
          //do something with the exception if needed
      }
      ```

* **setPushIdentifier**

   * Imposta il token dispositivo per le notifiche push.
   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void setPushIdentifier(final String registrationId); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      ...// note the code to retreive the push token must run in the background
      InstanceID instanceID= InstanceID.getInstance(getApplicationContext());String token=instanceID.getToken("835015092242", GoogleCloudMessaging.INSTANCE_ID_SCOPE null);Config.setPushIdentifier(token);
      ...
      ```

* **submitAdvertisingIdentifierTask**

   * Fornisce un oggetto chiamabile all'SDK che restituisce la stringa dell'Identificatore pubblicitario restituito da Google Play Services. L'SDK esegue questo task in un thread di background e imposta una variabile interna per l'Identificatore pubblicitario che si basa sul valore restituito dall'oggetto chiamabile.

      >[!IMPORTANT]
      > 
      >If you want to use the Advertising Identifier in Acquisition or Lifecycle, call it before calling `Config.collectLifecycleData`.

      * Di seguito è riportata la sintassi per questo metodo:

         ```java
         public static void submitAdvertisingIdentifierTask(final Callable<String> task); 
         ```

      * Di seguito è riportato un esempio di codice per questo metodo:

         ```java
         @Override
         public void  onResume() {
             super.onResume();
             final  Callable<String>; task = new Callable<String>(){
                 @Override
                 public String call() throws Exception {
                    AdvertisingIdClient.Info idInfo;
                    String adid = null;
                    Context appContext = CLASSNAME.this.getApplicationContext();
                    try {
                         idInfo = AdvertisingIdClient.getAdvertisingIdInfo(appContext);
                         if (idInfo != null) { 
                             adid = idInfo.getId();
                         } 
                    } catch  (Exception ex) {
                        Log.e("Error",  ex.getLocalizedMessage());
                    }
                    return  adid;
                 }
           };
           Config.submitAdvertisingIdentifierTask(task); 
           Config.collectLifecycleData(this);
         }
         ```


## AdobeDataCallback Interface {#section_600A63B3136F47DCB928071485C5117C}

```java
public interface AdobeDataCallback {  
    void call(MobileDataEvent event, Map<String, Object> contextData);  
} 
```

## MobileDataEvent Enum {#section_92732814141646E294782BC9020367EB}

```java
public enum MobileDataEvent {  
    MobileDataEvent.MOBILE_EVENT_LIFECYCLE, // triggers on a lifecycle hit  
    MobileDataEvent.MOBILE_EVENT_ACQUISITION_INSTALL, // triggers on a app install that has acquisition data  
    MobileDataEvent.MOBILE_EVENT_ACQUISITION_LAUNCH // triggers on launch when the device previously installed via acquisition  
}
```
