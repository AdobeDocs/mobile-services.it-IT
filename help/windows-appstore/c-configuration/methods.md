---
description: Classi e metodi forniti dalla libreria Windows 8.1 Universal App Store.
seo-description: Classi e metodi forniti dalla libreria Windows 8.1 Universal App Store.
seo-title: Metodi SDK
solution: Marketing Cloud, Analytics
title: Metodi SDK
topic: Sviluppatore e implementazione
uuid: 0 f 558 ff 4-73 d 3-4439-9 d 51-62 fbd 74 d 2 cea
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# SDK methods {#sdk-methods}

Classi e metodi forniti dalla libreria Windows 8.1 Universal App Store.

>[!TIP]
>
>When you consume `winmd` methods from winJS (JavaScript), all methods automatically have their first letter lowercased.

* **Getversion (winjs: Getversion)**

   Restituisce la versione corrente della libreria Adobe Mobile.

   * Di seguito è riportata la sintassi per questo metodo:

      ```csharp
      static Platform::String ^GetVersion();
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```js
      varADB = ADBMobile;var libVersion = ADB.Config.getVersion(); 
      ```

* **Getprivacystatusasync (winjs: Getprivacystatusasync)**

   Restituisce la rappresentazione enum dello stato di privacy per l’utente corrente.

   * `ADBMobilePrivacyStatusOptIn` - gli hit vengono inviati immediatamente.
   * `ADBMobilePrivacyStatusOptOut` - gli hit vengono eliminati.
   * Per `ADBMobilePrivacyStatusUnknown`, se le marche temporali sono abilitate nella suite di rapporti, gli hit vengono salvati fino alla modifica dello stato di privacy, quando l’utente acconsente (optedin, gli hit vengono inviati) o rinuncia (optedout, gli hit vengono eliminati). Se le marche temporali non sono abilitate nella suite di rapporti, gli hit vengono eliminati fino alla modifica dello stato di privacy, quando l’utente acconsente (optedin).

      The default value is set in the [ADBMobileConfig.json config](/help/windows-appstore/c-configuration/c.json.md) file.

   * Di seguito è riportata la sintassi per questo metodo:

      ```csharp
      static Windows::Foundation::IAsyncOperation<ADBMobilePrivacyStatus> ^getPrivacyStatusAsync(); 
      ```

   * Di seguito sono riportati gli esempi di codice per questo metodo:

      ```csharp
      public enum class ADBMobilePrivacyStatus : int  {
        ADBMobilePrivacyStatusOptIn = 1, 
        ADBMobilePrivacyStatusOptOut =  2,
        ADBMobilePrivacyStatusUnknown = 3
      };
      ```

      ```js
      var ADB = ADBMobile;
      var status;
      ADB.Config.getPrivacyStatusAsync.then(function(privacyStatus) {
      status = privacyStatus;
      }); 
      ```

* **Setprivacystatus (winjs: Setprivacystatus)**

   Imposta lo stato di privacy per l'utente corrente su `status`. Imposta uno dei valori seguenti:

   * `ADBMobilePrivacyStatusOptIn` - gli hit vengono inviati immediatamente.
   * `ADBMobilePrivacyStatusOptOut` - gli hit vengono eliminati.
   * Per `ADBMobilePrivacyStatusUnknown`, se le marche temporali sono abilitate nella suite di rapporti, gli hit vengono salvati fino alla modifica dello stato di privacy, quando l’utente acconsente (optedin, gli hit vengono inviati) o rinuncia (optedout, gli hit vengono eliminati). Se le marche temporali non sono abilitate nella suite di rapporti, gli hit vengono eliminati fino alla modifica dello stato di privacy, quando l’utente acconsente (optedin).

   * Di seguito è riportata la sintassi per questo metodo:

      ```csharp
      static void SetPrivacyStatus(ADBMobilePrivacyStatus status);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```csharp
      public enum class ADBMobilePrivacyStatus : int {
        ADBMobilePrivacyStatusOptIn = 1,
        ADBMobilePrivacyStatusOptOut = 2,
        ADBMobilePrivacyStatusUnknown = 3
        }; 
      ```

      ```js
      var ADB = ADBMobile;
      ADB.Config.setPrivacyStatus(ADB.ADBMobilePrivacyStatus.adbmobilePrivacyStatusOptIn); 
      ```

* **Getlifetimevalue (winjs: Getlifetimevalue)**

   Restituisce il valore "lifetime" del ciclo di vita dell'utente corrente. Il valore predefinito è 0.

   * Di seguito è riportata la sintassi per questo metodo:

      ```csharp
      static float GetLifetimeValue();
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```js
       var ADB = ADBMobile;
       var ltv = ADB.Config.getLifetimeValue(); 
      ```

* **Getuseridentifier (winjs: Getuseridentifier)**

   Restituisce l'identificativo utente personalizzato se un identificatore personalizzato è stato impostato. Restituisce null se non è impostato un identificatore personalizzato. Il valore predefinito è `null`.

   >[!TIP]
   >
   >Se l'app viene aggiornata dall'SDK di Experience Cloud 3. x alla versione 4. x, l'ID precedente (personalizzato o generato in automatico) viene recuperato e memorizzato come identificatore utente personalizzato. In tal modo i dati del visitatore vengono mantenuti da un aggiornamento all’altro dell’SDK. Per le nuove installazioni con l'SDK 4.x, l'identificatore dell'utente è `null` finché non viene impostato.

   * Di seguito è riportata la sintassi per questo metodo:

      ```csharp
      static Platform::String^GetUserIdentifier();
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```js
      var ADB = ADBMobile;
      var userId = ADB.Config.getUserIdentifier(); 
      ```

* **Setuseridentifier (winjs: Setuseridentifier**

   Imposta l'identificatore utente su `identifier`.

   * Di seguito è riportata la sintassi per questo metodo:

      ```csharp
      static void SetUserIdentifier(Platform::String ^userIdentifier);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```js
      var ADB = ADBMobile;
      ADB.Config.setUserIdentifier("someUserId"); 
      ```

* **Getdebuglogging (winjs: Getdebuglogging)**

   Restituisce l'attuale preferenza di accesso di debug. Il valore predefinito è `false`.

   * Di seguito è riportata la sintassi per questo metodo:

      ```csharp
      static bool GetDebugLogging(); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```js
      var ADB = ADBMobile;
      var logging = ADB.Config.getDebugLogging(); 
      ```

* **Setdebuglogging (winjs: Setdebuglogging)**

   Imposta la preferenza per l'accesso di su `debugLogging`debug. La registrazione di debug funziona solo quando si utilizza la versione di debug della libreria, la versione finale ignora questa impostazione.

   * Di seguito è riportata la sintassi per questo metodo:

      ```csharp
      static void SetDebugLogging(bool debugLogging); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```js
      var ADB = ADBMobile;
      ADB.Config.setDebugLogging(true); 
      ```

* **Collectlifecycledata (winjs: Collectlifecycledata)**

   Indica all'SDK che i dati del ciclo di vita devono essere raccolti per l'utilizzo in tutte le soluzioni dell'SDK. Per ulteriori informazioni, vedi [Metriche del ciclo di vita](/help/windows-appstore/metrics.md).

   >[!TIP]
   >
   >Invoke this method in the `onResume()` method in each Activity inside of your application, as shown in the following example. Consigliamo inoltre di passare l’attività o il servizio come oggetto contestuale anziché come contesto Applicazione globale.

   * Di seguito è riportata la sintassi per questo metodo:

      ```csharp
      static void CollectLifecycleData();
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```js
      var ADB = ADBMobile;
      ADB.Config.collectLifecycleData(); 
      ```

* **Pausecollectinglifecycledata (winjs: Pausecollectinglifecycledata)**

   Indica all’SDK che l’applicazione è in pausa, in modo che le metriche del ciclo di vita vengano calcolate correttamente. Ad esempio, all'avvio della pausa recupera un timestamp per determinare la durata della sessione precedente. Inoltre, questo imposta un flag in modo che il ciclo di vita acquisisca correttamente che l'applicazione non si è bloccata. Per ulteriori informazioni, vedi [Metriche del ciclo di vita](/help/windows-appstore/metrics.md).

   >[!TIP]
   >
   >Invoke this method in the `onPause()` methods in each Activity inside Your application, as shown in the example. Consigliamo inoltre di passare l’attività o il servizio come oggetto contestuale anziché come contesto Applicazione globale.

   * Di seguito è riportata la sintassi per questo metodo:

      ```csharp
      static void PauseCollectingLifecycleData();
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```js
      var ADB = ADBMobile;
      ADB.Config.pauseCollectingLifecycleData();
      ```
