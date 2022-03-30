---
description: Elenco di metodi di Audience Manager forniti dalla libreria della piattaforma UWP (Universal Windows Platform).
solution: Experience Cloud Services,Analytics
title: Metodi di Audience Manager
topic-fix: Developer and implementation
uuid: efbe8f33-7f53-40a6-b7aa-a36ac718c047
exl-id: a7b4001d-d90f-4a8a-a801-d66e56ea43b5
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 39%

---

# Metodi di Audience Manager{#audience-manager-methods}

Elenco di metodi di Audience Manager forniti dalla libreria della piattaforma UWP (Universal Windows Platform).

L&#39;SDK supporta attualmente più soluzioni Adobe Experience Cloud, tra cui Analytics, Target e Audience Manager. I metodi sono contraddistinti dal prefisso della relativa soluzione. I metodi di Audience Manager hanno il prefisso `AudienceManager`.

>[!TIP]
>
>Quando utilizzi `winmd` metodi di winJS (JavaScript), tutti i metodi presentano automaticamente la prima lettera minuscola.

Se audience manager è configurato nel tuo file JSON, viene inviato un segnale contenente le metriche sul ciclo di vita con l&#39;hit del ciclo di vita.

* **GetVisitorProfile (winJS: getVisitorProfile)**

   Restituisce il profilo del visitatore ottenuto più di recente. Restituisce `null` se non è stato ancora inviato alcun segnale. Il profilo del visitatore viene salvato in `SharedPreferences` per un accesso facilitato tra più avvii dell’app.

   * Di seguito è riportata la sintassi per questo metodo:

      ```csharp
      static Windows::Foundation::Collections::IMap<Platform::String^,Platform::Object^> ^GetVisitorProfile();
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

   Invia a Gestione dell&#39;audience un segnale con caratteristiche e fa sì che i segmenti corrispondenti vengano restituiti in un callback di blocco.

   * Di seguito è riportata la sintassi per questo metodo:

      ```csharp
      static 
      Windows::Foundation::IAsyncOperation<Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^> ^SignalWithData(Windows::Foundation::Collections::IMap<Platform::String^,Platform::Object> ^data);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```js
      var ADB = ADBMobile;
      var traits = new Windows.Foundation.Collections.PropertySet(); 
      traits["trait"] = "b";
      ADB.AudienceManager.signalWithData(traits).then(function (visitorProfile) { 
        // segments come back here in "visitorProfile", normally found in the "segs" object of your json 
      });
      ```
