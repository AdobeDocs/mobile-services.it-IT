---
description: Elenco dei metodi di Adobe Target forniti dalla libreria Android.
keywords: android;libreria;mobile;sdk
seo-description: Elenco dei metodi di Adobe Target forniti dalla libreria Android.
seo-title: Metodi di destinazione per Android
solution: Marketing Cloud,Analytics
title: Metodi di destinazione per Android
topic: Sviluppatore e implementazione
uuid: 8e9808b2-ba80-4646-ba05-8e62d4fde065
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Metodi di destinazione per Android{#target-methods}

Elenco dei metodi di Adobe Target forniti dalla libreria Android.

L’SDK supporta attualmente più soluzioni Adobe Experience Cloud, tra cui Analytics, Target, Audience Manager e il servizio identità della piattaforma Adobe Experience. Methods are prefixed according to the solution. For example, Experience Cloud ID methods are prefixed with `target`.

>[!TIP]
>
>[Le metriche del ciclo di vita](/help/android/metrics.md) sono inviate come parametri a ciascun caricamento Mbox.

## Class reference : TargetLocationRequest {#section_A8CC898922164E819EC730DC92A6742B}

**Proprietà:**

```java
public String name; 
public String defaultContent; 
public HashMap<String, Object> parameters;
```

**Costanti stringa**

>[!TIP]
>
>Le seguenti costanti sono utili per semplificare l'utilizzo quando si impostano le chiavi per i parametri personalizzati.

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
>* If you are using SDKs **before** version 4.14.0, see [https://developers.adobetarget.com/api/#input-parameters](https://developers.adobetarget.com/api/#input-parameters) for parameters limitations.
   >
   >
* If you are using SDKs version 4.14.0 **or later**, see [https://developers.adobetarget.com/api/#batch-input-parameters](https://developers.adobetarget.com/api/#batch-input-parameters) for parameters limitations.


* **loadRequest**

   Invia la richiesta al server di Target configurato e restituisce il valore della stringa dell'offerta generato in un blocco callback.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void loadRequest(TargetLocationRequest request, TargetCallback<String> callback);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      Target.loadRequest(heroBannerRequest, new Target.TargetCallback<String>() {  @Override  public void call(String item) {   // do something with item  } });
      ```

* **loadRequest**

   Invia la richiesta al server di Target configurato e restituisce il valore della stringa dell'offerta generato in un blocco callback.

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

   Invia una richiesta al server di Target configurato e restituisce il valore della stringa dell'offerta generato in un blocco TargetCallback.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void loadRequest(final String name, final String defaultContent, final Map<String, Object> profileParameters, final Map<String, Object> orderParameters, final Map<String, Object> mboxParameters, final Map<String, Object> requestLocationParameters, final TargetCallback<String> callback);
      ```

   * **Restituisce:** N/D

   * **Parametri:**

      I parametri di questo metodo sono i seguenti:

      * **name**

         Nome dell'Mbox/posizione Target che desideri recuperare.

         * **** Tipo: Stringa
      * **defaultContent**

         Valore restituito nella callback se il server di Target non è raggiungibile, oppure se l'utente non è qualificato per la campagna.

         * **Type:** String
      * **profileParameters**

         I valori in questo dizionario entrano nell'oggetto "profileParameters" nella richiesta a Target.

         * **** Tipo: Mappa `<String, Object>`
      * **orderParameters**

         I valori in questo dizionario entrano nell'oggetto "order" nella richiesta a Target.

         * **** Tipo: Mappa `<String, Object>`
      * **mboxParameters**

         I valori in questo dizionario entrano nella richiesta a Target.

         * **** Tipo: Mappa `<String, Object>`
      * **requestLocationParameters**

         I valori in questo dizionario entrano nell'oggetto "requestLocation" nella richiesta a Target.

         * **** Tipo: Mappa `<String, Object>`
      * **callback**

         Questo metodo sarà chiamato con il contenuto dell'offerta dal server di Target. Se il server di Target non è raggiungibile o se l'utente non si qualifica per la campagna, verrà restituito defaultContent.

         * **** Tipo: TargetCallback `<String>`
   * Esempio di codice per questo metodo:

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

      Per ulteriori informazioni sulle API Target sottostanti, vedi [Consegna](https://docs.adobe.com/dev/products/target/reference/delivery.html) nella guida per gli sviluppatori di Target.








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

   Elimina tutti i cookie di Target dall'applicazione.

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

   Restituisce l'ID della sessione.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static String getSessionID();
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      Target.getSessionID();
      ```

* **setThirdPartyID**

   Imposta l'ID di terze parti.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static String setThirdPartyID(final String thirdPartyId);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      Target.setThirdPartyID(“third-party-id”);
      ```

* **getThirdPartyID**

   Restituisce l'ID di terze parti.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static String getThirdPartyID();
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      String thirdPartyId = Target.getThirdPartyID();
      ```
