---
description: Classi e metodi forniti dalla libreria della piattaforma UWP (Universal Windows Platform).
solution: Experience Cloud,Analytics
title: Metodi dell’SDK
topic-fix: Developer and implementation
uuid: e3aa41d6-7bc0-4208-a662-12907c209a77
exl-id: 0aac477c-074d-457c-b117-bb205119c475
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '576'
ht-degree: 68%

---

# Metodi dell’SDK {#sdk-methods}

Classi e metodi forniti dalla libreria della piattaforma UWP (Universal Windows Platform).

>[!TIP]
>
>Quando utilizzi metodi `winmd` da winJS (JavaScript), tutti i metodi presentano automaticamente la prima lettera minuscola.

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

      Il valore predefinito è impostato nel file di configurazione `ADBMobileConfig.json`. Per ulteriori informazioni, consulta [File di configurazione ADBMobileConfig.json](/help/universal-windows/c-configuration/c.json.md).

   * Di seguito è riportata la sintassi per questo metodo:

      ```csharp
      static Windows::Foundation::IAsyncOperation<ADBMobilePrivacyStatus>
      ^getPrivacyStatusAsync();
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      **C Sharp**

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

         **Luminoso**

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

   Restituisce l&#39;identificatore utente personalizzato se è stato impostato un identificatore personalizzato. Restituisce `null` se non è impostato un identificatore personalizzato.
Il valore predefinito è `null`.

   >[!IMPORTANT]
   >
   >Se l’app viene aggiornata dall’SDK di Experience Cloud 3.x alla versione 4.x, il servizio ID precedente (generato in modo personalizzato o automatico) viene recuperato e memorizzato come identificatore utente personalizzato. In tal modo i dati del visitatore vengono mantenuti da un aggiornamento all’altro dell’SDK. Per le nuove installazioni con l&#39;SDK 4.x, l&#39;identificatore dell&#39;utente è `null` finché non viene impostato.

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

   Imposta la preferenza per l&#39;accesso di su `debugLogging` debug. La registrazione di debug funziona solo quando si utilizza la versione di debug della libreria, la versione di rilascio ignora questa impostazione.

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

   Indica all&#39;SDK che l&#39;applicazione è in pausa, in modo che le metriche del ciclo di vita vengano calcolate correttamente. Ad esempio, al momento della pausa recupera una marca temporale per determinare la lunghezza della sessione precedente. Inoltre, imposta un flag in modo che il ciclo di vita acquisisca correttamente che l&#39;app non si è bloccata. Per ulteriori informazioni, vedi [Metriche del ciclo di vita](/help/universal-windows/metrics.md).

   * Di seguito è riportata la sintassi per questo metodo:

      ```csharp
      static void PauseCollectingLifecycleData();
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```js
      var ADB = ADBMobile;
      ADB.Config.pauseCollectingLifecycleData(); 
      ```
