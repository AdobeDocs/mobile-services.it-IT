---
description: Questi sono i metodi del servizio Experience Cloud ID forniti dalla libreria Android.
keywords: android; libreria; mobile; sdk
seo-description: Questi sono i metodi del servizio Experience Cloud ID forniti dalla libreria Android.
seo-title: Metodi del servizio Identità Adobe Experience Platform
solution: Marketing Cloud, Analytics
title: Metodi del servizio Identità Adobe Experience Platform
topic: Sviluppatore e implementazione
uuid: c 5107 a 7 e -273 b -4 f 71-8738-4 c 603479 b 24 c
translation-type: tm+mt
source-git-commit: a54a969bb6abedfeb0fc20276d260664b68c1d66

---


# Metodi del servizio Identità Adobe Experience Platform{#experience-cloud-id-service-methods}

Questi sono i metodi del servizio Experience Cloud ID forniti dalla libreria Android.

L'SDK supporta attualmente più soluzioni Adobe Experience Cloud, tra cui Analytics, Target, Audience Manager e Adobe Experience Platform Identity Service.

Methods are prefixed according to the solution. For example, Experience Cloud ID methods are prefixed with `visitor`. For more information, see [Experience Cloud ID Configuration](/help/android/c-marketing-cloud/mcvid.md).

* **public static String appendToURL(final String URL)**

   Aggiunge i dati visitatore Adobe a una stringa URL da usare con la libreria Adobe JavaScript. Per utilizzare questo metodo, occorre avere Mobile SDK 4.12+. Per ulteriori informazioni, consulta [Funzione aggiuntiva ID visitatore](https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid-appendvisitorid.html).

   >[! Importante]
   >
   >Questo metodo può provocare una chiamata di rete di blocco. Non invocare questa chiamata su thread sensibili a fattori temporali.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      URL java.lang.String  
      ```

      Una stringa URL obbligatoria alla quale vengono collegate le informazioni dei visitatori.

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      String urlSample = "https://example.com";`
              String urlWithAdobeVisitorInfo = Visitor.appendToURL(urlSample);
      
              Intent(Intent.ACTION_VIEW);
              i.setData(Uri.parse(urlWithAdobeVisitorInfo));
              startActivity(i);
      ```

* **getMarketingCloudId**

   Recupera l'Experience Cloud ID dal servizio ID.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static String getMarketingCloudId(); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      String = Visitor.getMarketingCloudId();
      ```

      >[!IMPORTANT]
      >
      >This method can cause a blocking network call and should **not** be called from a UI thread.

* **syncIdentifiers**

   Insieme all'Experience Cloud ID, puoi impostare altri ID cliente da associare a ogni visitatore. L'API Visitor accetta più ID cliente per lo stesso visitatore, con un identificatore del tipo di cliente che consente di distinguere l'ambito dei diversi ID cliente. Questo metodo corrisponde a `setCustomerIDs` nella libreria JavaScript.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void syncIdentifiers(Map<String, String> identifiers); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      Map<String,String> identifiers = new HashMap<String, String>();
      identifiers.put("idType", "idValue");
      Visitor.syncIdentifiers(identifiers);
      ```

* **Syncidentifier**

   Sincronizza con il servizio ID visitatori il tipo e il valore dell’identificatore fornito.

   Passa lo stato `authenticationState` come uno dei seguenti valori:

   * `VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_UNKNOWN`
   * `VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_AUTHENTICATED`
   * `VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_LOGGED_OUT`

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void syncIdentifier(final String identifierType, final String identifier, final VisitorID.VisitorIDAuthenticationState authenticationState);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      Visitor.syncIdentifier("myIdType", "valueForUser", VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_LOGGED_OUT);
      ```

* **syncIdentifiers**

   Sincronizza gli identificatori forniti con il servizio ID.

   Passa lo stato `authenticationState` come uno dei seguenti valori:
   * `VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_UNKNOWN`
   * `VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_AUTHENTICATED`
   * `VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_LOGGED_OUT`

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void syncIdentifiers(final Map<String String> identifiers, final VisitorID.VisitorIDAuthenticationState authenticationState);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      Map<String, String> identifiers = new HashMap<String, String>();
          identifiers.put("myIdType", "valueForUser"); Visitor.syncIdentifiers(identifiers,
      VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_AUTHENTICATED); 
      ```

* **getIdentifiers**

   Recupera un elenco di oggetti `ADBVisitorID` di sola lettura.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static List<VisitorID> getIdentifiers(); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      List<VisitorID> myVisitorIDs = Visitor.getIdentifiers(); 
      ```

* **Geturlvariablesasync**

   Introdotto nella versione 4.16.0, questo metodo restituisce una stringa formata correttamente contenente variabili URL del servizio ID visitatore. Per ulteriori informazioni sull'utilizzo di questo metodo, vedi [Metodi di servizio identità Adobe Experience Platform](/help/android/reference/hybrid-app.md).

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void getUrlVariablesAsync(final VisitorCallback callback);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      final String urlString = https://www.mydomain.com/index.php; 
      Visitor.getUrlVariablesAsync(new Visitor.VisitorCallback(){ 
        @Override 
        public void call(String urlVariables) { 
            final String urlStringWithVisitorData = String.format("%s?%s", urlString, urlVariables); 
            ...
        } 
      });
      ```

## Public methods {#section_8AC744B431A3438C9B45629CA3EA0F51}

```java
public class VisitorID { 
    public final String idOrigin; 
    public final String idType; 
    public final String id; 
    public VisitorIDAuthenticationState authenticationState; 
 
    public enum VisitorIDAuthenticationState { 
         VISITOR_ID_AUTHENTICATION_STATE_UNKNOWN(0), 
         VISITOR_ID_AUTHENTICATION_STATE_AUTHENTICATED(1), 
         VISITOR_ID_AUTHENTICATION_STATE_LOGGED_OUT(2); 
    } 
}
```
