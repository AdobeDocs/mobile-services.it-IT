---
description: Elenco di metodi Audience Manager forniti dalla libreria Windows 8.1 Universal App Store.
seo-description: Elenco di metodi Audience Manager forniti dalla libreria Windows 8.1 Universal App Store.
seo-title: Metodi Audience Manager
solution: Marketing Cloud, Analytics
title: Metodi Audience Manager
topic: Sviluppatore e implementazione
uuid: e 39 c 9 c 3 e-fd 53-4 b 46-8 fff -88101 a 064 a 9 c
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Audience Manager methods {#audience-manager-methods}

Elenco di metodi Audience Manager forniti dalla libreria Windows 8.1 Universal App Store.

Al momento l’SDK dispone di supporto per più Soluzioni Adobe Experience Cloud, tra cui Analytics, Target e Audience Manager. Ai metodi è applicato il prefisso della relativa soluzione. I metodi di Audience Manager hanno il prefisso "Audience Manager".

>[!NOTE]
>
>Quando utilizzi metodi winmd da winjs (javascript), tutti i metodi hanno automaticamente la prima lettera minuscola.

Se Audience Manager è configurato nel file JSON, viene inviato un segnale contenente le metriche del ciclo di vita con l’hit del ciclo di vita.

* **Getvisitorprofile (winjs: Getvisitorprofile)**

   Restituisce il profilo del visitatore ottenuto più di recente. Restituisce `null` se non è stato ancora inviato alcun segnale. Il profilo del visitatore viene salvato in `SharedPreferences` per un accesso facilitato in più avvii dell’applicazione.

   * Di seguito è riportata la sintassi per questo metodo:

      ```csharp
      static fWindows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^GetVisitorProfile();
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```js
      var ADB = ADBMobile; 
      var profile = ADB.AudienceManager.getVisitorProfile();
      ```

* **Getdpid (winjs: Getdpid)**

   Restituisce il DPID corrente.

   * Di seguito è riportata la sintassi per questo metodo:

      ```csharp
      static Platform::String ^GetDpid();
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```js
      var ADB = ADBMobile; 
      var dpid = ADB.AudienceManager.getDpid();
      ```

* **Getdpuuid (winjs: Getdpuuid)**

   Restituisce il DPUUID corrente.

   * Di seguito è riportata la sintassi per questo metodo:

      ```csharp
      static Platform::String ^GetDpuuid();
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```js
      var ADB = ADBMobile; 
      var dpuuid = ADB.AudienceManager.getDpuuid();
      ```

* **Setdpidanddpuuid (winjs: Setdpidanddpuuid)**

   Imposta gli identificatori DPID e DPUUID. Se impostati, DPID e DPUUID saranno inviati congiuntamente con ogni segnale.

   * Di seguito è riportata la sintassi per questo metodo:

      ```csharp
      static void SetDpidAndDpuuid(Platform::String ^dpid, Platform::String ^dpuuid); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```js
      var ADB = ADBMobile; 
      ADB.AudienceManager.setDpidAndDpuuid("newDpid", "newDpuuid");
      ```

* **Signalwithdata (winjs: Signalwithdata)**

   Invia a Audience Manager un segnale con caratteristiche e fa sì che i segmenti corrispondenti vengano restituiti in una callback.

   * Di seguito è riportata la sintassi per questo metodo:

      ```csharp
      static Windows::Foundation::IAsyncOperation<Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> > ^SignalWithData(Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^data);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```js
      var ADB = ADBMobile; 
      var traits = new Windows.Foundation.Collections.PropertySet(); 
      traits["trait"] = "b"; 
      ADB.AudienceManager.signalWithData(traits).then(function(visitorProfile) { 
        // segments come back here in "visitorProfile", normally found in the "segs" object of your json 
      }); 
      ```

