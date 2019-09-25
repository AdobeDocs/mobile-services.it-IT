---
description: Di seguito sono elencati i metodi Adobe Experience Platform Identity Service forniti dalla libreria iOS.
seo-description: Di seguito sono elencati i metodi Adobe Experience Platform Identity Service forniti dalla libreria iOS.
seo-title: Metodi di Adobe Experience Platform Identity
solution: Marketing Cloud,Analytics
title: Metodi di Adobe Experience Platform Identity
topic: Sviluppatore e implementazione
uuid: cdd307bc-8b7d-47a8-b77e-00902b9e2968
translation-type: tm+mt
source-git-commit: cbbb85b4d117fcaa502a1e01423f1f5d3b2ecc2b

---


# Adobe Experience Platform Identity Service methods {#experience-cloud-id-service-methods}

Di seguito sono elencati i metodi Adobe Experience Platform Identity Service forniti dalla libreria iOS.

L'SDK supporta attualmente più soluzioni Adobe Experience Cloud, tra cui Analytics, Target, Audience Manager e il servizio ID di Experience Cloud.

Methods are prefixed according to the solution, and Experience Cloud ID methods are prefixed with `visitor`. Per maggiori informazioni, consulta [Attivare il servizio Experience Cloud ID](/help/ios/marketing-cloud/mcvid.md).

* **`+`(nullable NSURL )visitorAppendToURL:(nullable NSURL )url;`*``*`**

   Aggiunge i dati visitatore Adobe a una stringa URL da usare con la libreria Adobe JavaScript. To use this method, you must have Mobile SDK version 4.12 or higher. Per ulteriori informazioni, consulta [Funzione aggiuntiva ID visitatore](https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid-appendvisitorid.html).

   >[!IMPORTANT]
   >
   >Questo metodo può provocare una chiamata di rete di blocco. Non invocare questa chiamata su thread sensibili a fattori temporali.

   * Input: `URL<NSURL>`
A required URL string that the visitor information will be appended to.
   * `URL<NSURL>`
Stringa completa a cui sono state aggiunte le informazioni sul visitatore.

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
       NSURL *url = [NSURL URLWithString:@"https://www.example.com"];  
       NSURL *decoratedURL = [ADBMobile visitorAppendToURL: url];  
       [[UIApplication sharedApplication] openURL: decoratedURL];  
      ```

* **visitorMarketingCloudID**

   Recupera l'Experience Cloud ID dal servizio ID.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      + (NSString  *)  visitorMarketingCloudID;
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      NSString *mcid = [ADBMobile visitorMarketingCloudID]; 
      ```

      >[!IMPORTANT]
      >
      >This method can cause a blocking network call and should **not** be called from a UI thread.

* **visitorSyncIdentifiers:**

   Insieme all'Experience Cloud ID, puoi impostare altri ID cliente da associare a ogni visitatore. L'API Visitor accetta più ID cliente per lo stesso visitatore, con un identificatore del tipo di cliente che consente di distinguere l'ambito dei diversi ID cliente. Questo metodo corrisponde a `setCustomerIDs` nella libreria JavaScript.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      +  (void)  visitorSyncIdentifiers:(NSDictionary  *)identifiers;
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      [ADBMobile visitorSyncIdentifiers:@{@"idType":@"idValue"}];
      ```

* **visitorSyncIdentifiers:authenticationState:**

   Sincronizza gli identificatori forniti con il servizio ID. Passa lo stato `authState` come uno dei seguenti valori:

   * `ADBMobileVisitorAuthenticationStateUnknown`
   * `ADBMobileVisitorAuthenticationStateAuthenticated`
   * `ADBMobileVisitorAuthenticationStateLoggedOut`

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      +  (void) visitorSyncIdentifiers:(nullable NSDictionary  *)identifiers  authenticationState:(ADBMobileVisitorAuthenticationState)authState; 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      [ADBMobile visitorSyncIdentifiers:@{@"myIdType":@"valueForUser"}  authenticationState:ADBMobileVisitorAuthenticationStateAuthenticated]; 
      ```

* **visitorSyncIdentifierWithType:identifier:authenticationState:**

   Sincronizza con il servizio ID il tipo e il valore dell'identificatore fornito. Pass in the `authState` one of the following values:

   * `ADBMobileVisitorAuthenticationStateUnknown`
   * `ADBMobileVisitorAuthenticationStateAuthenticated`
   * `ADBMobileVisitorAuthenticationStateLoggedOut`

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      + (void) visitorSyncIdentifierWithType:(nullable NSString *)identifierType  
      identifier:(nullable NSString *)identifier authenticationState:
      (ADBMobileVisitorAuthenticationState)authState; 
      ```

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      [ADBMobile visitorSyncIdentifierWithType:@"myIdType" identifier:@"valueForUser"  
      authenticationState:ADBMobileVisitorAuthenticationStateLoggedOut]; 
      ```

* **visitorGetIDs**

   Recupera un array di oggetti `ADBVisitorID` di sola lettura.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      +  (nullable NSArray *) visitorGetIDs;
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      NSArray *myVisitorIDs = [ADBMobile visitorGetIDs];
      ```

* **visitorgetUrlVariablesAsync**

   Introduced in version 4.16.0, this method returns an appropriately formed string that contains Visitor ID Service URL variables. For more information about how this method is used, see Adobe Experience Platform Identity Service methods.[](/help/ios/reference/hybrid-app.md)

   * Di seguito è riportata la sintassi per questo metodo:

      ```objectivec
      + (void) visitorGetUrlVariablesAsync:(nullable void (^)(NSString* __nullable urlVariables))callback;
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objectivec
      NSString *urlString = @"https://www.mydomain.com/index.php"; 
      [ADBMobile visitorGetUrlVariablesAsync:^(NSString * _Nullable urlVariables) { 
        NSString *urlStringWithVisitorData = [NSString stringWithFormat:@"%@?%@", urlString, urlVariables]; 
        // use urlStringWithVisitorData 
      }];
      ```

## Interfaccia ADBVisitorID {#section_2FF74454D25C4ADABAC5E43CBFAAEC26}

**Metodi pubblici:**

```objective-c
- (nullable NSString *) idType; 
- (nullable NSString *) identifier; 
- (ADBMobileVisitorAuthenticationState) authenticationState; 
```

## ADBMobileVisitorAuthenticationState enum {#section_A55A3F336DDF4F838900632087F51430}

```objective-c
ADBMobileVisitorAuthenticationStateUnknown, 
ADBMobileVisitorAuthenticationStateAuthenticated, 
ADBMobileVisitorAuthenticationStateLoggedOut
```

