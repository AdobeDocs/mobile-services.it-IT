---
description: Elenco dei metodi di Target forniti dalla libreria Windows 8.1 Universal App Store.
seo-description: Elenco dei metodi di Target forniti dalla libreria Windows 8.1 Universal App Store.
seo-title: Metodi di Target
solution: Marketing Cloud, Analytics
title: Metodi di Target
topic: Sviluppatore e implementazione
uuid: 8 c 35 b 31 c-c 70 b -4 dba -8759-173342 a 301 e 9
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Target methods {#target-methods}

Elenco dei metodi di Target forniti dalla libreria Windows 8.1 Universal App Store.

Al momento l’SDK dispone di supporto per più Soluzioni Adobe Experience Cloud, tra cui Analytics, Target e Audience Manager. Ai metodi è applicato il prefisso della relativa soluzione. I metodi di Analytics hanno il prefisso "Target".

[Le metriche del ciclo di vita](/help/windows-appstore/metrics.md) sono inviate come parametri a ciascun caricamento Mbox.

>[!TIP]
>
>When you consume `winmd` methods from winJS (JavaScript), all methods automatically have their first letter lowercased.

## Riferimento classe: Targetlocationrequest

### Proprietà

```
property Platform::String ^name; 
property Platform::String ^defaultContent; 
property Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^parameters;
```

## Costanti stringa

Queste informazioni sono utili per impostare le chiavi per i parametri personalizzati.

```
static property Platform::String ^TARGET_PARAMETER_ORDER_ID { 
  Platform::String ^get() { return L"orderId"; } 
} 
static property Platform::String ^TARGET_PARAMETER_ORDER_TOTAL { 
  Platform::String ^get() { return L"orderTotal"; } 
} 
static property Platform::String ^TARGET_PARAMETER_PRODUCT_PURCHASE_ID { 
  Platform::String ^get() { return L"productPurchasedId"; } 
} 
static property Platform::String ^TARGET_PARAMETER_CATEGORY_ID { 
  Platform::String ^get() { return L"categoryId"; } 
} 
static property Platform::String ^TARGET_PARAMETER_MBOX_3RDPARTY_ID { 
  Platform::String ^get() { return L"mbox3rdPartyId"; } 
} 
static property Platform::String ^TARGET_PARAMETER_MBOX_PAGE_VALUE { 
  Platform::String ^get() { return L"mboxPageValue"; } 
} 
static property Platform::String ^TARGET_PARAMETER_MBOX_PC { 
  Platform::String ^get() { return L"mboxPC"; } 
} 
static property Platform::String ^TARGET_PARAMETER_MBOX_SESSION_ID { 
  Platform::String ^get() { return L"mboxSession"; } 
} 
static property Platform::String ^TARGET_PARAMETER_MBOX_HOST { 
  Platform::String ^get() { return L"mboxHost"; } 
}
```

* **Loadrequest (winjs: Loadrequest**

   Sends `request` to your configured Target server and returns the string value of the offer generated in a block `callback`.

   * Di seguito è riportata la sintassi per questo metodo:

      ```csharp
      static Windows::Foundation::IAsyncOperation<Platform::String ^> ^LoadRequest(TargetLocationRequest ^request);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```js
      var ADB = ADBMobile; 
      ADB.Target.loadRequest(heroBannerRequest).then(function(content) { 
      // do something with content returned from target server 
      });
      ```

* **Createrequest (winjs: Createrequest)**

   Crea un oggetto `TargetLocationRequest` con i parametri forniti.

   * Di seguito è riportata la sintassi per questo metodo:

      ```csharp
      static TargetLocationRequest ^CreateRequest(Platform::String ^name, Platform::String ^defaultContent, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^parameters); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```js
      var ADB = ADBMobile; 
      var heroBannerRequest = ADB.Target.createRequest("heroBanner", "default.png", null); 
      ```

* **Createorderconfirmrequest (winjs: Createorderconfirmrequest)**

   Crea un oggetto `TargetLocationRequest` con i parametri forniti.

   * Di seguito è riportata la sintassi per questo metodo:

      ```csharp
      static TargetLocationRequest ^CreateOrderConfirmRequest(Platform::String ^name, Platform::String ^orderId, Platform::String ^orderTotal, Platform::String ^productPurchasedId, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> ^parameters); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```js
      var ADB = ADBMobile; 
      var orderConfirm = ADB.Target.createOrderConfirmRequest("orderConfirm", "order", "47.88", "3722", null); 
      ```

* **Clearcookies (winjs: Clearcookies**

   Elimina i cookie di Target per l’applicazione sul dispositivo corrente.

   * Di seguito è riportata la sintassi per questo metodo:

      ```csharp
      static void ClearCookies(); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```js
      ADBMobile.Target.clearCookies();
      ```

* **Getpcid (winjs: Getpcid)**

   Restituisce il cookie dell’ID del PC del dispositivo corrente.

   * Di seguito è riportata la sintassi per questo metodo:

      ```csharp
      static Platform::String ^GetPcId();
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```js
      auto pcId = ADBMobile.Target.getPcId(); 
      ```

* **Getsessionid (winjs: Getsessionid)**

   Restituisce il cookie dell’ID sessione del dispositivo corrente.

   * Di seguito è riportata la sintassi per questo metodo:

      ```csharp
      static Platform::String ^GetSessionId(); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```js
      auto sessionId = ADBMobile.Target.getSessionId(); 
      ```

