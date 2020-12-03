---
description: Elenco di metodi di Audience Manager  forniti dalla libreria della piattaforma UWP (Universal Windows Platform).
seo-description: Elenco di metodi di Audience Manager  forniti dalla libreria della piattaforma UWP (Universal Windows Platform).
seo-title: Metodi di Audience Manager
solution: Experience Cloud,Analytics
title: Metodi di Audience Manager
topic: Developer and implementation
uuid: efbe8f33-7f53-40a6-b7aa-a36ac718c047
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 38%

---


# Metodi di Audience Manager {#audience-manager-methods}

Elenco di metodi di Audience Manager  forniti dalla libreria della piattaforma UWP (Universal Windows Platform).

L’SDK supporta attualmente più soluzioni Adobe Experience Cloud, tra cui Analytics, Target e  Audience Manager. Methods are prefixed according to the solution. Audience Manager methods are prefixed with `AudienceManager`.

>[!TIP]
>
>Quando utilizzi `winmd` metodi da winJS (JavaScript), tutti i metodi hanno automaticamente la prima lettera minuscola.

Se Audience Manager è configurato nel tuo file JSON, con l&#39;hit del ciclo di vita viene inviato un segnale che contiene le metriche del ciclo di vita.

* **GetVisitorProfile (winJS: getVisitorProfile)**

   Restituisce il profilo del visitatore ottenuto più di recente. Returns `null` if no signal has been submitted yet. Visitor profile is saved in `SharedPreferences` for easy access across multiple launches of your app.

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

   Imposta gli identificatori DPID e DPUUID. Se impostati, DPID e DPUUID saranno inviati con ogni segnale.

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

   Invia a Gestione dell&#39;audience un segnale con caratteristiche e fa sì che i segmenti corrispondenti vengano restituiti in una callback di blocco.

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
