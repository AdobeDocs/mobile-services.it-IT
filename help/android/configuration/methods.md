---
description: Elenco dei metodi di forniti dalla libreria Android.
keywords: android;library;mobile;sdk
seo-description: Elenco dei metodi di forniti dalla libreria Android.
seo-title: Metodi di Configurazione
solution: Marketing Cloud,Analytics
title: Metodi di Configurazione
topic: Developer and implementation
uuid: 663aeb6c-1b97-4a3a-8c0e-dd4c2ec28c01
translation-type: tm+mt
source-git-commit: dae60a21286edc28c84b7638da214b824abf0cd3

---


# Metodi di configurazione{#configuration-methods}

Elenco dei metodi di forniti dalla libreria Android.

## Configurazione iniziale {#section_9169243ECC4744A899A8271F92090ECD}

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
   ```

## Impostazioni SDK (classe di configurazione) {#section_C1EB977043C04D2B93E5A63DB72828B6}

* **registerAdobeDataCallback**

   * Registra un oggetto che implementa l&#39;interfaccia `AdobeDataCallback`. Il metodo &quot;call&quot; sovrascritto sarà invocato con un valore `Config.MobileDataEvent` e i dati associati in una `Map<String, Object>` per l&#39;evento che scatena l&#39;attivazione. Per ulteriori dettagli sugli eventi che attiveranno questo callback, vedi *MobileDataEventEnum* in fondo a questo argomento.

      >[!TIP]
      >
      >Questo metodo richiede la versione 4.9.0 o successiva.

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

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      String libraryVersion = Config.getVersion(); 
      ```

* **getPrivacyStatus**

   * Restituisce la rappresentazione enum dello stato di privacy per l’utente corrente.

      I valori di stato della privacy sono i seguenti:

      * `MOBILE_PRIVACY_STATUS_OPT_IN` - gli hit vengono inviati immediatamente.
      * `MOBILE_PRIVACY_STATUS_OPT_OUT` - gli hit vengono scartati.
      * `MOBILE_PRIVACY_STATUS_UNKNOWN` - se la suite di rapporti ha la marca temporale abilitata, gli hit vengono salvati finché lo stato di privacy non cambia in optedin (gli hit vengono inviati) o in optedout (gli hit vengono scartati).

         Se le marche temporali non sono abilitate nella suite di rapporti, gli hit vengono scartati fino a quando lo stato di privacy non cambia in optedin. Il valore predefinito è impostato nel file `ADBMobileConfig.json`.
   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static MobilePrivacyStatus getPrivacyStatus(); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      MobilePrivacyStatus privacyStatus Config.getPrivacyStatus();
      ```


* Il metodo **setPrivacyStatus**

   * Imposta lo stato di privacy per l&#39;utente corrente su `status`.

      Puoi impostare lo stato di privacy su uno dei seguenti valori:
      * `MOBILE_PRIVACY_STATUS_OPT_IN` - gli hit vengono inviati immediatamente. Questi hit vengono inviati immediatamente.
      * `MOBILE_PRIVACY_STATUS_OPT_OUT` - gli hit vengono scartati. Questi hit vengono scartati.
      * `MOBILE_PRIVACY_STATUS_UNKNOWN` - se la suite di rapporti ha la marca temporale abilitata, gli hit vengono salvati finché lo stato di privacy non cambia in optedin (gli hit vengono inviati) o in optedout (gli hit vengono scartati). Se le marche temporali non sono abilitate nella suite di rapporti, gli hit vengono scartati fino a quando lo stato di privacy non cambia in optedin.
   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void setPrivacyStatus(MobilePrivacyStatus status); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      Config.setPrivacyStatus(MobilePrivacyStatus.MOBILE_PRIVACY_STATUS_OPT_IN); 
      ```


* **getLifetimeValue**

   * Restituisce il valore &quot;lifetime&quot; del ciclo di vita dell&#39;utente corrente. Il valore predefinito è `0`.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static BigDecimal getLifetimeValue();
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      BigDecimal currentLifetimeValue Config.getLifetimeValue(); 
      ```

* **getUserIdentifier**

   * Se è stato impostato un identificatore personalizzato, restituisce l&#39;identificatore utente personalizzato. In caso contrario restituisce `null`. Il valore predefinito è `null`.

      >[!TIP]
      >
      >Se l&#39;app viene aggiornata dall&#39;SDK di Experience Cloud 3.x alla versione 4.x, l&#39;ID precedente (personalizzato o generato in automatico) viene recuperato e memorizzato come identificatore utente personalizzato. In tal modo i dati del visitatore vengono mantenuti da un aggiornamento all&#39;altro dell&#39;SDK. Per le nuove installazioni sull&#39;SDK 4.x, finché non impostato, l&#39;identificatore utente è `null`.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static String&amp getUserIdentifier();
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      String userId = Config.getUserIdentifier();
      ```

* **setUserIdentifier**

   * Imposta l&#39;identificatore utente su `identifier`.
   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void setUserIdentifer(String identifier);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      Config.setUserIdentifier("billybob"); 
      ```

* **getDebugLogging**

   * Restituisce l&#39;attuale preferenza di accesso di debug. Il valore predefinito è `false`.
   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static Boolean getDebugLogging(); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      Boolean debugging = Config.getDebugLogging(); 
      ```

* **setDebugLogging**
   * Imposta la preferenza per l&#39;accesso di su `debugLogging`debug.
   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void setDebugLogging(Boolea debugLogging);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      Config.setDebugLogging(true);
      ```

* **collectLifecycleData**
   * Indica all&#39;SDK che i dati del ciclo di vita devono essere raccolti per l&#39;utilizzo in tutte le soluzioni dell&#39;SDK. Per ulteriori informazioni, vedi [Metriche del ciclo di vita](/help/android/configuration/methods.md).

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

   * (**Versione 4.2 o versioni successive**) Indica all&#39;SDK che i dati del ciclo di vita devono essere raccolti per l&#39;utilizzo in tutte le soluzioni nell&#39;SDK. Per ulteriori informazioni, vedi [Metriche del ciclo di vita](/help/android/metrics.md).
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

   * Indica all&#39;SDK che l&#39;applicazione è in pausa, in modo che le metriche del ciclo di vita vengano calcolate correttamente. Ad esempio, `onPause` recupera una marca temporale per determinare la durata della sessione precedente. Inoltre, imposta un flag in modo che il ciclo di vita acquisisca che l&#39;applicazione non si è bloccata. Per ulteriori informazioni, vedi [Metriche del ciclo di vita](/help/android/metrics.md).

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

   * (**Versione 4.2 o successiva**) Imposta l’icona piccola che verrà utilizzata per le notifiche create dall’SDK. Questa icona apparirà sulla barra di stato e sarà l&#39;immagine secondaria visualizzata quando l&#39;utente visualizza la notifica completa nel Centro notifiche.
   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void setSmallIconResourceId(final int resourceId); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      Config.setSmallIconResourceId(R.drawable.appIcon);
      ```

* **setLargeIconResourceId(int resourceId)**

   * (**Versione 4.2 o successiva**) Imposta l’icona grande che verrà utilizzata per le notifiche create dall’SDK. Questa icona sarà l&#39;immagine principale visualizzata quando l&#39;utente visualizza la notifica completa nel Centro notifiche.
   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void setLargeIconResourceId(final int  resourceId);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```Java
      Config.setLargeIconResourceId(R.drawable.appIcon);
      ```

* **overrideConfigStream(InputStream configInput)**

   * (**Versione 4.2 o successiva**) Consente di caricare un diverso file di configurazione ADBMobile JSON all’avvio dell’applicazione. La diversa configurazione viene utilizzata fino alla chiusura dell’applicazione.
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

   * Fornisce un oggetto chiamabile all&#39;SDK che restituisce la stringa dell&#39;Identificatore pubblicitario restituito da Google Play Services. L&#39;SDK esegue questo task in un thread di background e imposta una variabile interna per l&#39;Identificatore pubblicitario che si basa sul valore restituito dall&#39;oggetto chiamabile.

      >[!IMPORTANT]
      > 
      >Se desideri utilizzare l&#39;Identificatore pubblicitario in Acquisizione o Lifecycle, chiamalo prima di `Config.collectLifecycleData`.

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
