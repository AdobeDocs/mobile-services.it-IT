---
description: Classi e metodi forniti dalla libreria Windows 8.1 Universal App Store.
solution: Experience Cloud,Analytics
title: Metodi dell’SDK
topic-fix: Developer and implementation
uuid: 0f558ff4-73d3-4439-9d51-62fbd74d2cea
exl-id: c328fd79-6e10-43b7-9d08-8da395098b60
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '642'
ht-degree: 51%

---

# Metodi dell’SDK {#sdk-methods}

Classi e metodi forniti dalla libreria Windows 8.1 Universal App Store.

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
      varADB = ADBMobile;var libVersion = ADB.Config.getVersion(); 
      ```

* **GetPrivacyStatusAsync (winJS: getPrivacyStatusAsync)**

   Restituisce la rappresentazione enum dello stato di privacy per l’utente corrente.

   * `ADBMobilePrivacyStatusOptIn` - gli hit vengono inviati immediatamente.
   * `ADBMobilePrivacyStatusOptOut` - gli hit vengono eliminati.
   * `ADBMobilePrivacyStatusUnknown` - Se le marche temporali sono abilitate nella suite di rapporti, gli hit vengono salvati fino a quando lo stato di privacy non cambia in optedin (gli hit vengono inviati) o optedout (gli hit vengono scartati). Se le marche temporali non sono abilitate nella suite di rapporti, gli hit vengono eliminati fino alla modifica dello stato di privacy, quando l&#39;utente acconsente (optedin).

      Il valore predefinito è impostato nel file di configurazione [ADBMobileConfig.json config](/help/windows-appstore/c-configuration/c.json.md) .

   * Di seguito è riportata la sintassi per questo metodo:

      ```csharp
      static Windows::Foundation::IAsyncOperation<ADBMobilePrivacyStatus> ^getPrivacyStatusAsync(); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

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

* **SetPrivacyStatus (winJS: setPrivacyStatus)**

   Imposta lo stato di privacy per l&#39;utente corrente su `status`. Imposta uno dei valori seguenti:

   * `ADBMobilePrivacyStatusOptIn` - gli hit vengono inviati immediatamente.
   * `ADBMobilePrivacyStatusOptOut` - gli hit vengono eliminati.
   * `ADBMobilePrivacyStatusUnknown` - Se le marche temporali sono abilitate nella suite di rapporti, gli hit vengono salvati fino a quando lo stato di privacy non cambia in optedin (gli hit vengono inviati) o optedout (gli hit vengono scartati). Se le marche temporali non sono abilitate nella suite di rapporti, gli hit vengono eliminati fino alla modifica dello stato di privacy, quando l&#39;utente acconsente (optedin).

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

* **GetLifetimeValue (winJS: getLifetimeValue)**

   Restituisce il valore &quot;lifetime&quot; del ciclo di vita dell&#39;utente corrente. Il valore predefinito è 0.

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

   Restituisce l&#39;identificatore utente personalizzato se è stato impostato un identificatore personalizzato. Restituisce null se non è impostato un identificatore personalizzato. Il valore predefinito è `null`.

   >[!TIP]
   >
   >Se l’app viene aggiornata dall’SDK di Experience Cloud 3.x alla versione 4.x, l’ID precedente (personalizzato o generato in automatico) viene recuperato e memorizzato come identificatore utente personalizzato. In tal modo i dati del visitatore vengono mantenuti da un aggiornamento all’altro dell’SDK. Per le nuove installazioni con l&#39;SDK 4.x, l&#39;identificatore dell&#39;utente è `null` finché non viene impostato.

   * Di seguito è riportata la sintassi per questo metodo:

      ```csharp
      static Platform::String^GetUserIdentifier();
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```js
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

      ```js
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

      ```js
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

   Indica all&#39;SDK che i dati del ciclo di vita devono essere raccolti per l&#39;utilizzo in tutte le soluzioni dell&#39;SDK. Per ulteriori informazioni, vedi [Metriche del ciclo di vita](/help/windows-appstore/metrics.md).

   >[!TIP]
   >
   >Richiama questo metodo nel metodo `onResume()` in ogni attività all&#39;interno dell&#39;applicazione, come illustrato nell&#39;esempio seguente. È inoltre consigliabile passare l’attività o il servizio come oggetto contestuale invece che come contesto dell’applicazione globale.

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

   Indica all&#39;SDK che l&#39;applicazione è in pausa, in modo che le metriche del ciclo di vita vengano calcolate correttamente. Ad esempio, al momento della pausa recupera una marca temporale per determinare la lunghezza della sessione precedente. Inoltre, imposta un flag in modo che il ciclo di vita acquisisca correttamente che l&#39;app non si è bloccata. Per ulteriori informazioni, vedi [Metriche del ciclo di vita](/help/windows-appstore/metrics.md).

   >[!TIP]
   >
   >Richiama questo metodo nei metodi `onPause()` di ogni attività all&#39;interno dell&#39;applicazione, come illustrato nell&#39;esempio. È inoltre consigliabile passare l’attività o il servizio come oggetto contestuale invece che come contesto dell’applicazione globale.

   * Di seguito è riportata la sintassi per questo metodo:

      ```csharp
      static void PauseCollectingLifecycleData();
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```js
      var ADB = ADBMobile;
      ADB.Config.pauseCollectingLifecycleData();
      ```
