---
description: Elenco dei metodi di Audience Manager forniti dalla libreria Android.
keywords: android,libreria,mobile,sdk
seo-description: Elenco dei metodi di Audience Manager forniti dalla libreria Android.
seo-title: Metodi di Audience Manager
solution: Experience Cloud,Analytics
title: Metodi di Audience Manager
topic: Sviluppatore e implementazione
uuid: 2f6e4664-1306-41d4-9fa7-e3a99f1df4ab
translation-type: ht
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Metodi di Audience Manager{#audience-manager-methods}

Elenco dei metodi di Audience Manager forniti dalla libreria Android.

L'SDK supporta attualmente più soluzioni Adobe Experience Cloud, tra cui Analytics, Target, Audience Manager e il servizio Adobe Experience Platform Identity. I metodi hanno un prefisso in base alla soluzione. Ad esempio, i metodi del servizio Experience Cloud ID hanno il prefisso `audience manager`.

Se Audience Manager è configurato nel tuo file JSON, un segnale contenente le metriche del ciclo di vita è inviato con l'hit del ciclo di vita.

* **getVisitorProfile**

   Restituisce il profilo del visitatore ottenuto più di recente e, se non è stato inviato un segnale, restituisce `null`. Il profilo del visitatore viene salvato in `SharedPreferences` in modo da essere facilmente accessibile per diversi avvii dell'applicazione.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static HashMap<String, Object> getVisitorProfile(); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      HashMap<String, Object> visitorProfile = AudienceManager.getVisitorProfile(); 
      ```

* **getDpid**

   Restituisce il DPID corrente.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void getDpid(); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      String dpid = AudienceManager.getDpid(); 
      ```

* **getDpuuid**

   Restituisce il DPUUID corrente.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void getDpuuid(); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      String dpuuid = AudienceManager.getDpuuid(); 
      ```

* **setDpidAndDpuuid**

   Imposta il DPID e il DPUUID; questi valori vengono inviati con ciascun segnale.

   Se il valore DPUUID passato a questo metodo contiene caratteri che non sono sicuri per gli URL, i clienti devono codificare il parametro prima di passarlo all'SDK.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void setDpidAndDpuuid(String dpid, String dpuuid); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      AudienceManager.setDpidAndDpuuid("myDpid", "myDpuuid"); 
      ```

* **signalWithData**

   Invia a Gestione dell'audience un segnale con traits e fa sì che i segmenti corrispondenti vengano restituiti in un callback di blocco.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void signalWithData(Map<String, Object> data, AudienceManagerCallback<Map<String, Object>> callback);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      HashMap Traits = new HashMap<String, Object>();
      aamTraits.put("trait", "b");
      AudienceManager.signalWithData(aamTraits, new AudienceManager.AudienceManagerCallback<Map<String, Object>> () {
        @Override
         public void call(Map<String, Object> item) { 
              // segments come back here normally found in the segs object of your json 
         }
      });
      ```
