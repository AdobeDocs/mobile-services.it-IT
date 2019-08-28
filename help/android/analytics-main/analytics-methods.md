---
description: Elenco dei metodi di Adobe Analytics forniti dalla libreria Android.
keywords: android; libreria; mobile; sdk
seo-description: Elenco dei metodi di Adobe Analytics forniti dalla libreria Android.
seo-title: Metodi di Analytics
solution: Marketing Cloud, Analytics
title: Metodi di Analytics
topic: Sviluppatore e implementazione
uuid: ac 7 c 640 e -9 dcc -4724-b 561-019 cc 025 d 5 a 7
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Analytics methods {#analytics-methods}

Elenco dei metodi di Adobe Analytics forniti dalla libreria Android.

L'SDK supporta attualmente più soluzioni Adobe Experience Cloud], tra cui Analytics], Target], Audience Manager] e Adobe Experience Platform Identity Service]. I metodi hanno un prefisso in base alla soluzione; ad esempio, i metodi del servizio Experience Cloud ID hanno il prefisso `analytics`.

Ciascuno dei seguenti metodi è utilizzato per inviare dati alla suite di rapporti di Adobe Analytics:

* **trackState**

   Tiene traccia dello stato di un'app con dati contestuali facoltativi. States are the views that are available in your app, such as `home dashboard`, `app settings`, `cart`, and so on. Questi stati sono simili alle pagine di un sito Web e le chiamate `trackState` incrementano le visualizzazioni di pagina.

   If `state` is empty, `app name app version (build)` is displayed in reports. Se visualizzi questo valore nei rapporti, accertati di impostare `state` in ciascuna chiamata `trackState`.

   >[!TIP]
   >
   >Questa è l'unica chiamata di tracciamento che incrementa le visualizzazioni di pagina.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public staticvoidtrackState(Stringstate, Map<String,Object> contextData);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      Analytics.trackState("loginScreen",null);
      ```

* **Trackaction**
Tieni traccia di un'azione nell'app.

   Actions that you want to measure, such as `logons`, `banner taps`, `feed subscriptions`, and other metrics, that occur in your app.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      publicstaticvoidtrackAction(Stringstate,Map<String,Object> contextData);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      Analytics.trackAction("heroBannerTouched",null);
      ```

* **Gettrackingidentifier**
Restituisce l'identificatore visitatore generato automaticamente per Analytics.

   Si tratta di un ID visitatore univoco specifico per l'app, che viene generato all'avvio iniziale e quindi memorizzato e utilizzato da quel momento in poi. L'ID viene conservato durante gli aggiornamenti dell'app e rimosso quando l'app viene disinstallata.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static String getTrackingIdentifier(); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      String trackingId = Analytics.getTrackingIdentifier(); 
      ```

* **trackLocation**

   Invia la latitudine, la longitudine e la posizione correnti in un punto di interesse definito. Per ulteriori informazioni, consulta [Geolocalità e punti di interesse](/help/android/location/geo-poi.md).

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void trackLocation(Location location, Map<String,Object> contextData); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      Analytics.trackLocation(userLocation, null);
      ```

* **trackLifetime&#x200B;ValueIncrease**

   Aggiunge al valore "lifetime" del ciclo di vita dell'utente un incremento pari a `amount`.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      publicstaticvoidtrackLifetimeValueIncrease(BigDecimalamount,Map<String,Object>contextData);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      Analytics.trackLifetimeValueIncrease(new BigDecimal(30), null);
      ```

* **trackTimed&#x200B;ActionStart**

   Avvia un'azione temporizzata con il nome `action`.

   Se invochi questo metodo per un'azione già avviata, l'azione temporizzata precedente viene sovrascritta.

   >[!TIP]
   >
   >Questa chiamata non invia un hit.

   * Di seguito è riportata la sintassi per questo metodo:
   ```java
   publicstaticvoidtrackTimedActionStart(Stringaction,Map<String,Object>contextData);
   ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      Analytics.trackTimedActionStart("cartToCheckout",null)
      ```


* **trackTimed&#x200B;ActionUpdate**

   Passa in `contextData` per aggiornare i dati contestuali associati all'azione `action`. I dati `data` passati vengono aggiunti alla fine dei dati esistenti per l'azione, e li sovrascrivono se per l'azione `action`, è già definita la stessa chiave.

   >[!TIP]
   >
   >Questa chiamata non invia un hit.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void trackTimedActionUpdate(Stringaction,Map <String,Object> contextData); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      HashMap cdata = new HashMap<String Object> (); 
      cdata.put("quantity",3); 
      Analytics.trackTimedActionUpdate("cartToCheckout", cdata);
      ```

* **trackTimed&#x200B;ActionEnd**

   Termina un'azione temporizzata. If you provide `block`, you can access the final time values and can manipulate `data` before sending the final hit.

   >[!TIP]
   >
   >If you provide `block`, you must return `true` to send a hit. Passing `null` for `block` sends the final hit.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void trackTimedActionEnd(Stringaction,TimedActionBlock<Boolean> logic); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      Analytics.trackTimedActionEnd("cartToCheckout",new
      Analytics.TimedActionBlock<Boolean>(){
        @Override
        public Booleancall(long inAppDuration,long totalDuration, Map<String,
      Object> contextData) {
              contextData.put("price", 49.95);
              return true;
         }
      });
      ```

* **sendQueuedHits**

   **Richiede SDK 4.1.**

   Indipendentemente dal numero di hit nella coda, questo metodo forza la libreria a inviare tutti gli hit nella coda offline.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      voidsendQueuedHits()
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      Analytics.sendQueuedHits();
      ```

* **getQueueSize**

   Restituisce il numero di chiamate di tracking memorizzate nella coda offline.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      long getQueueSize()
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      long queueSize = Analytics.getQueueSize(); 
      ```

* **clearQueue**

   Elimina tutti gli hit dalla coda offline.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      voidclearQueue()
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      Analytics.clearQueue();
      ```

      >[!WARNING]
      >
      > Fai molta attenzione quando cancelli manualmente la coda. Questo processo non può essere annullato.