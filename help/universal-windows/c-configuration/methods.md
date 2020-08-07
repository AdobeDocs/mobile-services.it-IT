---
description: Classi e metodi forniti dalla libreria della piattaforma UWP (Universal Windows Platform).
seo-description: Classi e metodi forniti dalla libreria della piattaforma UWP (Universal Windows Platform).
seo-title: Metodi SDK
solution: Marketing Cloud,Analytics
title: Metodi SDK
topic: Developer and implementation
uuid: e3aa41d6-7bc0-4208-a662-12907c209a77
translation-type: tm+mt
source-git-commit: c198ae57b05f8965a8e27191443ee2cd552d6c50
workflow-type: tm+mt
source-wordcount: '588'
ht-degree: 66%

---


# SDK methods {#sdk-methods}

Classi e metodi forniti dalla libreria della piattaforma UWP (Universal Windows Platform).

>[!TIP]
>
>Quando utilizzi `winmd` metodi da winJS (JavaScript), tutti i metodi hanno automaticamente la prima lettera minuscola.

* **GetVersion (winJS: getVersion)**

   Restituisce la versione corrente della libreria Adobe Mobile.

   * Di seguito è riportata la sintassi per questo metodo:

      ```csharp
      static Platform::String ^GetVersion();
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```js
      var ADB = ADBMobile;var libVersion = ADB.Config.getVersion();
      ```

* **GetPrivacyStatusAsync (winJS: getPrivacyStatusAsync)**

   Restituisce la rappresentazione enum dello stato di privacy per l’utente corrente.

   * `ADBMobilePrivacyStatusOptIn` - gli hit vengono inviati immediatamente.
   * `ADBMobilePrivacyStatusOptOut` - gli hit vengono scartati.
   * `ADBMobilePrivacyStatusUnknown` - Se le marche temporali sono abilitate nella suite di rapporti, gli hit vengono salvati fino a quando lo stato di privacy non cambia in optedin (gli hit vengono inviati) o optedout (gli hit vengono scartati). Se le marche temporali non sono abilitate nella suite di rapporti, gli hit vengono eliminati fino alla modifica dello stato di privacy, quando l&#39;utente acconsente (optedin).

      The default value is set in the `ADBMobileConfig.json` config file. Per ulteriori informazioni, vedi [ADBMobileConfig.json file](/help/universal-windows/c-configuration/c.json.md)di configurazione.

   * Di seguito è riportata la sintassi per questo metodo:

      ```csharp
      static Windows::Foundation::IAsyncOperation<ADBMobilePrivacyStatus>
      ^getPrivacyStatusAsync();
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      **C Nitido**

      ```csharp
      public enum class ADBMobilePrivacyStatus : int { ADBMobilePrivacyStatusOptIn = 1, 
      ADBMobilePrivacyStatusOptOut = 2, 
      ADBMobilePrivacyStatusUnknown = 3};
      ```

      **JavaScript**

      ```javascript
      var ADB = ADBMobile;
      var status;
      ADB.Config.getPrivacyStatusAsync.then(function(privacyStatus) {
        status = privacyStatus;}
      );
      ```

* **SetPrivacyStatus (winJS: setPrivacyStatus)**

   Imposta lo stato di privacy per l&#39;utente corrente su `status`. Imposta uno dei valori seguenti:
   * `ADBMobilePrivacyStatusOptIn` - gli hit vengono inviati immediatamente.
   * `ADBMobilePrivacyStatusOptOut` - gli hit vengono eliminati.
   * `DBMobilePrivacyStatusUnknown` - Se le marche temporali sono abilitate nella suite di rapporti, gli hit vengono salvati fino a quando lo stato di privacy non cambia in optedin (gli hit vengono inviati) o optedout (gli hit vengono scartati. Se le marche temporali non sono abilitate nella suite di rapporti, gli hit vengono eliminati fino alla modifica dello stato di privacy, quando l&#39;utente acconsente (optedin).

      * Di seguito è riportata la sintassi per questo metodo:

         ```csharp
         static void SetPrivacyStatus(ADBMobilePrivacyStatus status);
         ```

      * Di seguito è riportato un esempio di codice per questo metodo:

         **C diesis**

         ```csharp
         public enum class ADBMobilePrivacyStatus : int { 
           ADBMobilePrivacyStatusOptIn = 1, 
           ADBMobilePrivacyStatusOptOut = 2
           ADBMobilePrivacyStatusUnknown = 3
         };
         ```

         **JavaScript**

         ```js
         var ADB = ADBMobile;
         ADB.Config.setPrivacyStatus (ADB.ADBMobilePrivacyStatus.adbmobilePrivacyStatusOptIn
         );
         ```

* **GetLifetimeValue (winJS: getLifetimeValue)**

   Restituisce il valore &quot;lifetime&quot; del ciclo di vita dell&#39;utente corrente. Il valore predefinito è `0`.

   * Di seguito è riportata la sintassi per questo metodo:

      ```csharp
      static float GetLifetimeValue(); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```js
      var ADB = ADBMobile;
      var ltv = ADB.Config.getLifetimeValue();
      ```

* **GetUserIdentifier (winJS: getUserIdentifier)**

   Restituisce l’identificatore utente personalizzato se è stato impostato un identificatore personalizzato. Returns `null` if a custom identifier is not set.
Il valore predefinito è `null`.

   >[!IMPORTANT]
   >
   >Se l’app viene aggiornata dall’SDK  Experience Cloud 3.x alla versione 4.x, il servizio ID precedente (generato in modo personalizzato o automatico) viene recuperato e memorizzato come identificatore utente personalizzato. In tal modo i dati del visitatore vengono mantenuti da un aggiornamento all’altro dell’SDK. Per le nuove installazioni con l&#39;SDK 4.x, l&#39;identificatore dell&#39;utente è `null` finché non viene impostato.

   * Di seguito è riportata la sintassi per questo metodo:

      ```csharp
      static Platform::String ^GetUserIdentifier(); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```csharp
      var ADB = ADBMobile;
      var userId = ADB.Config.getUserIdentifier(); 
      ```

* **SetUserIdentifier (winJS: setUserIdentifier)**

   Imposta l&#39;identificatore utente su `identifier`.

   * Di seguito è riportata la sintassi per questo metodo:

      ```csharp
      static void SetUserIdentifier(Platform::String ^userIdentifier); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```javascript
      var ADB = ADBMobile;
      ADB.Config.setUserIdentifier("someUserId");
      ```

* **GetDebugLogging (winJS: getDebugLogging)**

   Restituisce l&#39;attuale preferenza di accesso di debug. Il valore predefinito è `false`.

   * Di seguito è riportata la sintassi per questo metodo:

      ```csharp
      static bool GetDebugLogging();
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```javascript
      var ADB = ADBMobile;
      var logging = ADB.Config.getDebugLogging();
      ```

* **SetDebugLogging (winJS: setDebugLogging)**

   Imposta la preferenza per l&#39;accesso di su `debugLogging`debug. La registrazione del debug funziona solo quando si utilizza la versione di debug della libreria. La versione release ignora questa impostazione.

   * Di seguito è riportata la sintassi per questo metodo:

      ```csharp
      static void SetDebugLogging(bool debugLogging);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```js
      var ADB = ADBMobile;
      ADB.Config.setDebugLogging(true);
      ```

* **CollectLifecycleData (winJS: collectLifecycleData)**

   Indica all&#39;SDK che i dati del ciclo di vita devono essere raccolti per l&#39;utilizzo in tutte le soluzioni dell&#39;SDK. Per ulteriori informazioni, vedi [Metriche del ciclo di vita](/help/universal-windows/metrics.md).

   * Di seguito è riportata la sintassi per questo metodo:

      ```csharp
      static void CollectLifecycleData();
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```js
      var ADB = ADBMobile;
      ADB.Config.collectLifecycleData();
      ```

* **PauseCollecting &#x200B; LifecycleData (winJS: pauseRaccolta &#x200B; LifecycleData)**

   Indica all&#39;SDK che l&#39;applicazione è in pausa, in modo che le metriche del ciclo di vita vengano calcolate correttamente. Ad esempio, al momento della pausa recupera un timestamp per determinare la durata della sessione precedente. Inoltre, imposta un flag in modo che il ciclo di vita acquisisca correttamente che l’app non si è bloccata. Per ulteriori informazioni, vedi [Metriche del ciclo di vita](/help/universal-windows/metrics.md).

   * Di seguito è riportata la sintassi per questo metodo:

      ```csharp
      static void PauseCollectingLifecycleData();
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```js
      var ADB = ADBMobile;
      ADB.Config.pauseCollectingLifecycleData(); 
      ```
