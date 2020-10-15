---
description: Questi sono i metodi del servizio Experience Cloud ID forniti dalla libreria Android.
keywords: android;library;mobile;sdk
seo-description: Questi sono i metodi del servizio Experience Cloud ID forniti dalla libreria Android.
seo-title: Metodi di Adobe Experience Platform Identity
solution: Experience Cloud,Analytics
title: Metodi di Adobe Experience Platform Identity
topic: Developer and implementation
uuid: c5107a7e-273b-4f71-8738-4c603479b24c
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '449'
ht-degree: 100%

---


# Metodi di Adobe Experience Platform Identity {#experience-cloud-id-service-methods}

Questi sono i metodi del servizio Experience Cloud ID forniti dalla libreria Android.

L’SDK supporta attualmente più soluzioni Adobe Experience Cloud, tra cui Analytics, Target, Audience Manager e il servizio Adobe Experience Platform Identity.

I metodi hanno un prefisso in base alla soluzione. Ad esempio, i metodi del servizio Experience Cloud ID hanno il prefisso `visitor`. Per ulteriori informazioni, consulta [Configurazione Experience Cloud ID](/help/android/c-marketing-cloud/mcvid.md).

* **public static String appendToURL(final String URL)**

   Aggiunge i dati visitatore Adobe a una stringa URL da usare con la libreria Adobe JavaScript. Per utilizzare questo metodo, devi disporre dell’SDK di Mobile versione 4.12 o successiva. Per ulteriori informazioni, consulta [Funzione aggiuntiva ID visitatore](https://docs.adobe.com/content/help/it-IT/id-service/using/id-service-api/methods/appendvisitorid.html).

   >[!IMPORTANT]
   >
   >Questo metodo può provocare una chiamata di rete di blocco. Non invocare questa chiamata su thread sensibili a fattori temporali.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static String appendToURL(final String URL) 
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

   Recupera l&#39;Experience Cloud ID dal servizio ID.

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
      >Questo metodo può provocare una chiamata di rete di blocco e **non** deve essere invocato da un thread di interfaccia utente.

* **syncIdentifiers**

   Con Experience Cloud ID, puoi impostare ID cliente aggiuntivi da associare a ogni visitatore. L’API visitatore accetta più ID cliente per lo stesso visitatore, con un identificatore del tipo di cliente per separare l’ambito dei diversi ID cliente. Questo metodo corrisponde a `setCustomerIDs` nella libreria JavaScript.

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

* **syncIdentifier**

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

* **getUrlVariablesAsync**

   Introdotto nella versione 4.16.0, questo metodo restituisce una stringa con formato appropriato che contiene le variabili URL del servizio ID visitatore. Per ulteriori informazioni sull’utilizzo di questo metodo, consulta [Metodi di Adobe Experience Platform Identity](/help/android/reference/hybrid-app.md).

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

## Metodi pubblici {#section_8AC744B431A3438C9B45629CA3EA0F51}

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
