---
description: Elenco dei metodi di Adobe Analytics forniti dalla libreria Android.
keywords: android,libreria,mobile,sdk
seo-description: Elenco dei metodi di Adobe Analytics forniti dalla libreria Android.
seo-title: Metodi di Analytics
solution: Experience Cloud,Analytics
title: Metodi di Analytics
topic: Sviluppatore e implementazione
uuid: ac7c640e-9dcc-4724-b561-019cc025d5a7
translation-type: ht
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Metodi di Analytics {#analytics-methods}

Elenco dei metodi di Adobe Analytics forniti dalla libreria Android.

L'SDK supporta attualmente più soluzioni Adobe Experience Cloud, tra cui Analytics, Target, Audience Manager e il servizio Adobe Experience Platform Identity. I metodi hanno un prefisso in base alla soluzione; ad esempio, i metodi del servizio Experience Cloud ID hanno il prefisso `analytics`.

Ciascuno dei seguenti metodi è utilizzato per inviare dati alla suite di rapporti di Adobe Analytics:

* **trackState**

   Tiene traccia dello stato di un'app con dati contestuali facoltativi. Gli stati sono le visualizzazioni disponibili nell'app, ad esempio `home dashboard`, `app settings`, `cart` e così via. Questi stati sono simili alle pagine di un sito Web e le chiamate `trackState` incrementano le visualizzazioni di pagina.

   Se `state` è vuoto, nei rapporti viene visualizzato `app name app version (build)`. Se visualizzi questo valore nei rapporti, accertati di impostare `state` in ciascuna chiamata `trackState`.

   >[!TIP]
   >
   >Questa è l'unica chiamata di tracciamento che incrementa le visualizzazioni pagina.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public staticvoidtrackState(Stringstate, Map<String,Object> contextData);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      Analytics.trackState("loginScreen",null);
      ```

* **trackAction**
Tiene traccia di un'azione nell'applicazione.

   Azioni che si verificano nell'app e che desideri misurare, ad esempio `logons`, `banner taps`, `feed subscriptions` e altre metriche.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      publicstaticvoidtrackAction(Stringstate,Map<String,Object> contextData);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      Analytics.trackAction("heroBannerTouched",null);
      ```

* **getTrackingIdentifier**
Restituisce l'identificatore del visitatore generato automaticamente per Analytics.

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

   Invia la latitudine, la longitudine e la posizione attuali in un punto di interesse definito. Per ulteriori informazioni, vedi [Geolocalizzazione e punti di interesse](/help/android/location/geo-poi.md).

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

   Termina un'azione temporizzata. Se fornisci `block`, puoi accedere ai valori finali di tempo e manipolare i `data` prima di inviare l'hit finale.

   >[!TIP]
   >
   >Se fornisci `block`, devi restituire `true` per inviare un hit. Passando `null` per `block` si invia l'hit finale.

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