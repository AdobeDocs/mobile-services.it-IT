---
description: Elenco dei metodi di Adobe Target forniti dalla libreria Android.
keywords: android;library;mobile;sdk
seo-description: Elenco dei metodi di Adobe Target forniti dalla libreria Android.
seo-title: Metodi di Target per Android
solution: Experience Cloud,Analytics
title: Metodi di Target per Android
topic: Developer and implementation
uuid: 8e9808b2-ba80-4646-ba05-8e62d4fde065
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '603'
ht-degree: 100%

---


# Metodi di Target per Android {#target-methods}

Elenco dei metodi di Adobe Target forniti dalla libreria Android.

L&#39;SDK supporta attualmente più soluzioni Adobe Experience Cloud, tra cui Analytics, Target, Audience Manager e il servizio Adobe Experience Platform Identity. I metodi hanno un prefisso in base alla soluzione. Ad esempio, i metodi del servizio Experience Cloud ID hanno il prefisso `target`.

>[!TIP]
>
>[Le metriche del ciclo di vita](/help/android/metrics.md) sono inviate come parametri a ciascun caricamento Mbox.

## Riferimento classe: TargetLocationRequest {#section_A8CC898922164E819EC730DC92A6742B}

**Proprietà:**

```java
public String name; 
public String defaultContent; 
public HashMap<String, Object> parameters;
```

**Costanti di stringa**

>[!TIP]
>
>Le seguenti costanti di stringa offrono facilità di utilizzo quando imposti le chiavi per i parametri personalizzati.

```java
public static final String TARGET_PARAMETER_ORDER_ID   = "orderId"; 
public static final String TARGET_PARAMETER_ORDER_TOTAL         = "orderTotal"; 
public static final String TARGET_PARAMETER_PRODUCT_PURCHASE_ID = "productPurchasedId"; 
public static final String TARGET_PARAMETER_CATEGORY_ID         = "categoryId"; 
public static final String TARGET_PARAMETER_MBOX_3RDPARTY_ID    = "mbox3rdPartyId"; 
public static final String TARGET_PARAMETER_MBOX_PAGE_VALUE     = "mboxPageValue"; 
public static final String TARGET_PARAMETER_MBOX_PC             = "mboxPC"; // pcId in cookie 
public static final String TARGET_PARAMETER_MBOX_SESSION_ID     = "mboxSession"; // sessionId in cookie 
public static final String TARGET_PARAMETER_MBOX_HOST           = "mboxHost";
```

>[!IMPORTANT]
>
>* Se utilizzi gli SDK **precedenti** alla versione 4.14.0, consulta [https://developers.adobetarget.com/api/#input-parameters](https://developers.adobetarget.com/api/#input-parameters) per informazioni sulle limitazioni dei parametri.
>
>* Se utilizzi gli SDK versione 4.14.0 o **successiva**, consulta [https://developers.adobetarget.com/api/#batch-input-parameters](https://developers.adobetarget.com/api/#batch-input-parameters) per informazioni sulle limitazioni dei parametri.


* **loadRequest**

   Invia la richiesta al server di Target configurato e restituisce il valore della stringa dell&#39;offerta generato in un blocco callback.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void loadRequest(TargetLocationRequest request, TargetCallback<String> callback);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      Target.loadRequest(heroBannerRequest, new Target.TargetCallback<String>() {  @Override  public void call(String item) {   // do something with item  } });
      ```

* **loadRequest**

   Invia la richiesta al server di Target configurato e restituisce il valore della stringa dell&#39;offerta generato in un blocco callback.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void loadRequest(final String name final String defaultContent, final Map `<String, Object>` profileParameters, 
                                     final Map `<String, Object>` orderParameters,final Map `<String Object>` mboxParameters, final TargetCallback<String> callback)
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      Map `<String, Object>` profileParameters = new HashMap `<String, Object>`(); profileParameters.put(“profile-parameter-key”, “profile-parameter-value”); 
      Map `<String, Object>` orderParameters = new HashMap `<String, Object>`(); orderParameters.put(“order-parameter-key”, “order-parameter-value”);
      Map `<String, Object>` mboxParameters = new HashMap `<String, Object>`(); 
      mboxParameters.put(“mbox-parameter-key”, “mbox-parameter-value”); 
      Target.loadRequest(“mboxName”, “defaultContent”, profileParameters, orderParameters, mboxParameters
      new TargetCallback<String>() {
          @Override
          public void call (String item) {
             Log.d(“Target Content”, item); 
          }
      });
      ```

* **loadRequest**

   Invia una richiesta al server di Target configurato e restituisce il valore della stringa dell&#39;offerta generato in un blocco TargetCallback.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void loadRequest(final String name, final String defaultContent, final Map<String, Object> profileParameters, final Map<String, Object> orderParameters, final Map<String, Object> mboxParameters, final Map<String, Object> requestLocationParameters, final TargetCallback<String> callback);
      ```

   * **Restituisce:** N/D

   * **Parametri:**

      I parametri di questo metodo sono i seguenti:

      * **nome**

         Nome dell&#39;Mbox/posizione Target che desideri recuperare.

         * **Tipo:** String
      * **defaultContent**

         Valore restituito nella callback se il server di Target non è raggiungibile, oppure se l&#39;utente non è qualificato per la campagna.

         * **Tipo:** String
      * **profileParameters**

         I valori in questo dizionario entrano nell&#39;oggetto &quot;profileParameters&quot; nella richiesta a Target.

         * **Tipo:** mappa `<String, Object>`
      * **orderParameters**

         I valori in questo dizionario entrano nell&#39;oggetto &quot;order&quot; nella richiesta a Target.

         * **Tipo:** mappa `<String, Object>`
      * **mboxParameters**

         I valori in questo dizionario entrano nella richiesta a Target.

         * **Tipo:** mappa `<String, Object>`
      * **requestLocationParameters**

         I valori in questo dizionario entrano nell&#39;oggetto &quot;requestLocation&quot; nella richiesta a Target.

         * **Tipo:** mappa `<String, Object>`
      * **callback**

         Questo metodo sarà chiamato con il contenuto dell&#39;offerta dal server di Target. Se il server di Target non è raggiungibile o se l&#39;utente non si qualifica per la campagna, verrà restituito defaultContent.

         * **Tipo:** TargetCallback `<String>`
   * Di seguito è riportato un codice di esempio per questo metodo:

      ```java
      Map `<String, Object>` profileParameters = new HashMap `<String, Object>`(); profileParameters.put(“profile-parameter-key”, “profile-parameter-value”); 
      Map `<String, Object>` orderParameters = new HashMap `<String, Object>`(); orderParameters.put(“order-parameter-key”, “order-parameter-value”); 
      Map `<String, Object>` mboxParameters = new HashMap `<String, Object>`(); mboxParameters.put(“mbox-parameter-key”, “mbox-parameter-value”); 
      Map `<String, Object>` requestLocationParameters = new HashMap `<String, Object>`(); requestLocationParameters.put(“request-location-parameter-key”, “request-location-parameter-value”); 
      
      Target.loadRequest(“mboxName”, “defaultContent”, profileParameters, orderParameters, mboxParameters, requestLocationParameters,new TargetCallback<String>() {
         @Override
         public void call (String item) { 
            Log.d(“Target Content”, item);
         } 
      });
      ```

      Per ulteriori informazioni sulle API Target sottostanti, consulta [Consegna](https://docs.adobe.com/dev/products/target/reference/delivery.html) nella guida per gli sviluppatori di Target.








* **createOrder&#x200B;ConfirmRequest**

   Crea un oggetto TargetLocationRequest con i parametri forniti.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static TargetLocationRequest createOrderConfirmRequest(String name, String orderId, String orderTotal, String productPurchasedId, Map<String, Object> parameters);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      TargetLocationRequest orderConfirm = Target.createOrderConfirmRequest("orderConfirm", "order", "47.88", "3722", null);
      ```

* **createRequest**

   Crea un oggetto TargetLocationRequest con i parametri forniti.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static TargetLocationRequest createRequest(String name, String defaultContent, Map<String, Object> parameters);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      TargetLocationRequest heroBannerRequest = Target.createRequest("heroBanner", "default.png", null);
      ```

* **clearCookies**

   Elimina tutti i cookie di Target dall&#39;applicazione.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void clearCookies();
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      Target.clearCookies();
      ```

* **getPcID**

   Restituisce il pcID.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static String getPcID();
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      Target.getPcID();
      ```

* **getSessionID**

   Restituisce l&#39;ID della sessione.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static String getSessionID();
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      Target.getSessionID();
      ```

* **setThirdPartyID**

   Imposta l&#39;ID di terze parti.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static String setThirdPartyID(final String thirdPartyId);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      Target.setThirdPartyID(“third-party-id”);
      ```

* **getThirdPartyID**

   Restituisce l&#39;ID di terze parti.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static String getThirdPartyID();
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      String thirdPartyId = Target.getThirdPartyID();
      ```
