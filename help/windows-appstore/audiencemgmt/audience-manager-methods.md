---
description: Elenco di metodi di Audience Manager forniti dalla libreria Windows 8.1 Universal App Store.
seo-description: Elenco di metodi di Audience Manager forniti dalla libreria Windows 8.1 Universal App Store.
seo-title: Metodi di Audience Manager
solution: Experience Cloud,Analytics
title: Metodi di Audience Manager
topic-fix: Developer and implementation
uuid: e39c9c3e-fd53-4b46-8fff-88101a064a9c
exl-id: b10d7274-0fc6-4822-a40b-1192b71592b9
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 40%

---

# Metodi di Audience Manager {#audience-manager-methods}

Elenco di metodi di Audience Manager forniti dalla libreria Windows 8.1 Universal App Store.

L&#39;SDK supporta attualmente più soluzioni Adobe Experience Cloud, tra cui Analytics, Target e Audience Manager. Ai metodi è applicato il prefisso della relativa soluzione. I metodi di Audience Manager hanno il prefisso &quot;AudienceManager&quot;.

>[!NOTE]
>
>Quando utilizzi metodi winmd da winJS (JavaScript), tutti i metodi presentano automaticamente la prima lettera minuscola.

Se audience manager è configurato nel tuo file JSON, viene inviato un segnale contenente le metriche sul ciclo di vita con l&#39;hit del ciclo di vita.

* **GetVisitorProfile (winJS: getVisitorProfile)**

   Restituisce il profilo del visitatore ottenuto più di recente. Restituisce `null` se non è stato ancora inviato alcun segnale. Il profilo del visitatore viene salvato in `SharedPreferences` per un accesso facilitato tra più avvii dell’app.

   * Di seguito è riportata la sintassi per questo metodo:

      ```csharp
      static fWindows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^GetVisitorProfile();
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```js
      var ADB = ADBMobile; 
      var profile = ADB.AudienceManager.getVisitorProfile();
      ```

* **GetDpid (winJS: getDpid)**

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

* **GetDpuuid (winJS: getDpuuid)**

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

* **SetDpidAndDpuuid (winJS: setDpidAndDpuuid)**

   Imposta gli identificatori DPID e DPUUID. Se sono impostati DPID e DPUUID, saranno inviati con ogni segnale.

   * Di seguito è riportata la sintassi per questo metodo:

      ```csharp
      static void SetDpidAndDpuuid(Platform::String ^dpid, Platform::String ^dpuuid); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```js
      var ADB = ADBMobile; 
      ADB.AudienceManager.setDpidAndDpuuid("newDpid", "newDpuuid");
      ```

* **SignalWithData (winJS: signalWithData)**

   Invia un Audience Manager di segnale con caratteristiche e fa sì che i segmenti corrispondenti vengano restituiti in un callback di un blocco.

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
