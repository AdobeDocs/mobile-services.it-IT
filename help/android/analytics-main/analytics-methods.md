---
description: Elenco dei metodi di Adobe Analytics forniti dalla libreria Android.
keywords: android;library;mobile;sdk
seo-description: Elenco dei metodi di Adobe Analytics forniti dalla libreria Android.
seo-title: Metodi di Analytics
solution: Marketing Cloud,Analytics
title: Metodi di Analytics
topic: Developer and implementation
uuid: ac7c640e-9dcc-4724-b561-019cc025d5a7
translation-type: tm+mt
source-git-commit: c198ae57b05f8965a8e27191443ee2cd552d6c50
workflow-type: tm+mt
source-wordcount: '740'
ht-degree: 94%

---


# Metodi di Analytics {#analytics-methods}

Elenco dei metodi di Adobe Analytics forniti dalla libreria Android.

L&#39;SDK supporta attualmente più soluzioni Adobe Experience Cloud, tra cui Analytics, Target, Audience Manager e il servizio Adobe Experience Platform Identity. I metodi hanno un prefisso in base alla soluzione; ad esempio, i metodi del servizio Experience Cloud ID hanno il prefisso `analytics`.

Ciascuno dei seguenti metodi è utilizzato per inviare dati alla suite di rapporti di Adobe Analytics:

* **trackState**

   Tiene traccia dello stato di un&#39;app con dati contestuali facoltativi. Gli stati sono le visualizzazioni disponibili nell&#39;app, ad esempio `home dashboard`, `app settings`, `cart` e così via. Questi stati sono simili alle pagine di un sito Web e le chiamate `trackState` incrementano le visualizzazioni di pagina.

   Se `state` è vuoto, nei rapporti viene visualizzato `app name app version (build)`. Se visualizzi questo valore nei rapporti, accertati di impostare `state` in ciascuna chiamata `trackState`.

   >[!TIP]
   >
   >Questa è l&#39;unica chiamata di tracciamento che incrementa le visualizzazioni pagina.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void trackState(String state, Map<String, Object> contextData);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      Analytics.trackState("loginScreen", null);
      ```

* **trackAction**
Tiene traccia di un&#39;azione nell&#39;applicazione.

   Azioni che si verificano nell&#39;app e che desideri misurare, ad esempio `logons`, `banner taps`, `feed subscriptions` e altre metriche.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void trackAction(String state, Map<String, Object> contextData);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      Analytics.trackAction("heroBannerTouched", null);
      ```

* **getTrackingIdentifier**
Restituisce l&#39;identificatore del visitatore generato automaticamente per Analytics.

   Si tratta di un ID visitatore univoco specifico per l’app, che viene generato all’avvio iniziale e quindi memorizzato e utilizzato da quel momento in poi. L&#39;ID viene mantenuto nei successivi aggiornamenti dell&#39;app e rimosso quando l&#39;app viene disinstallata.

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
      public static void trackLocation(Location location, Map<String, Object> contextData);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      Analytics.trackLocation(userLocation, null);
      ```

* **trackLifetime&#x200B;ValueIncrease**

   Aggiunge al valore &quot;lifetime&quot; del ciclo di vita dell&#39;utente un incremento pari a `amount`.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void trackLifetimeValueIncrease(BigDecimal amount, Map<String, Object> contextData);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      Analytics.trackLifetimeValueIncrease(new BigDecimal(30), null);
      ```

* **trackTimed&#x200B;ActionStart**

   Avvia un&#39;azione temporizzata con il nome `action`.

   Se invochi questo metodo per un&#39;azione già avviata, l&#39;azione temporizzata precedente viene sovrascritta.

   >[!TIP]
   >
   >Questa chiamata non invia un hit.

   * Di seguito è riportata la sintassi per questo metodo:

   ```java
   public static void trackTimedActionStart(String action, Map<String, Object> contextData);
   ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      Analytics.trackTimedActionStart("cartToCheckout", null)
      ```


* **trackTimed&#x200B;ActionUpdate**

   Passa in `contextData` per aggiornare i dati contestuali associati all&#39;azione `action`. I dati `data` passati vengono aggiunti alla fine dei dati esistenti per l&#39;azione, e li sovrascrivono se per l&#39;azione `action`, è già definita la stessa chiave.

   >[!TIP]
   >
   >Questa chiamata non invia un hit.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void trackTimedActionUpdate(String action, Map<String, Object> contextData);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      HashMap cdata = new HashMap<String Object> ();
      cdata.put("quantity",3);
      Analytics.trackTimedActionUpdate("cartToCheckout", cdata);
      ```

* **trackTimed&#x200B;ActionEnd**

   Termina un&#39;azione temporizzata. Se fornisci `block`, puoi accedere ai valori finali di tempo e manipolare i `data` prima di inviare l&#39;hit finale.

   >[!TIP]
   >
   >Se fornisci `block`, devi restituire `true` per inviare un hit. Passando `null` per `block` si invia l&#39;hit finale.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void trackTimedActionEnd(String action, TimedActionBlock<Boolean> logic);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      Analytics.trackTimedActionEnd("cartToCheckout",new
      Analytics.TimedActionBlock<Boolean>(){
          @Override
          public Boolean call(long inAppDuration, long totalDuration, Map<String, Object> contextData) {
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
      public static void sendQueuedHits();
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      Analytics.sendQueuedHits();
      ```

* **getQueueSize**

   Restituisce il numero di chiamate di tracking memorizzate nella coda offline.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static long getQueueSize();
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      long queueSize = Analytics.getQueueSize();
      ```

* **clearQueue**

   Elimina tutti gli hit dalla coda offline.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void clearQueue();
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      Analytics.clearQueue();
      ```

      >[!WARNING]
      >
      > Fai molta attenzione quando cancelli manualmente la coda. Questo processo non può essere annullato.

* **processReferrer**

   Elabora i dati della campagna referente da Google Play Store per un utilizzo successivo.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void processReferrer(final Context context, final Intent intent);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      Analytics.processReferrer(getApplicationContext(), intent);
      ```

* **processGooglePlayInstallReferrerUrl**

   >[!IMPORTANT]
   >
   > Questa API è disponibile a partire dalla versione SDK 4.18.0

   Recupera i dati di acquisizione dall’URL di riferimento Google Play Install fornito.

   I dati raccolti da questa API verranno inviati sugli hit di installazione inviati ad Analytics e saranno disponibili in Adobe Data Callback.

   Se i dati del referente sono già stati raccolti dall’SDK, la chiamata di questo metodo determinerà un no-op.

   Per informazioni su come recuperare l’URL del referente, consulta la documentazione di Google: https://developer.android.com/google/play/installreferrer/library.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void processGooglePlayInstallReferrerUrl(final String referrerUrl);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      Analytics.processGooglePlayInstallReferrerUrl(referrerUrl);
      ```
