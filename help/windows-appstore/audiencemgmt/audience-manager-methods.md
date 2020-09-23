---
description: Elenco di metodi di Audience Manager  forniti dalla libreria Windows 8.1 Universal App Store.
seo-description: Elenco di metodi di Audience Manager  forniti dalla libreria Windows 8.1 Universal App Store.
seo-title: Metodi di Audience Manager
solution: Experience Cloud,Analytics
title: Metodi di Audience Manager
topic: Developer and implementation
uuid: e39c9c3e-fd53-4b46-8fff-88101a064a9c
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 40%

---


# Metodi di Audience Manager {#audience-manager-methods}

Elenco di metodi di Audience Manager  forniti dalla libreria Windows 8.1 Universal App Store.

L’SDK supporta attualmente più soluzioni Adobe Experience Cloud, tra cui Analytics, Target e  Audience Manager. Ai metodi è applicato il prefisso della relativa soluzione.  metodi di Audience Manager hanno il prefisso &quot;AudienceManager&quot;.

>[!NOTE]
>
>Quando utilizzi metodi winmd da winJS (JavaScript), tutti i metodi hanno automaticamente la prima lettera minuscola.

Se Audience Manager è configurato nel tuo file JSON, con l&#39;hit del ciclo di vita viene inviato un segnale contenente le metriche del ciclo di vita.

* **GetVisitorProfile (winJS: getVisitorProfile)**

   Restituisce il profilo del visitatore ottenuto più di recente. Returns `null` if no signal has been submitted yet. Visitor profile is saved in `SharedPreferences` for easy access across multiple launches of your app.

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

   Invia  Audience Manager un segnale con caratteristiche e fa sì che i segmenti corrispondenti vengano restituiti in un callback di blocco.

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

