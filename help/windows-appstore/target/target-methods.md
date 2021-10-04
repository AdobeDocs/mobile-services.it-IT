---
description: Elenco dei metodi di Target forniti dalla libreria Windows 8.1 Universal App Store.
solution: Experience Cloud,Analytics
title: Metodi di Target
topic-fix: Developer and implementation
uuid: 8c35b31c-c70b-4dba-8759-173342a301e9
exl-id: 2db9f594-01e7-4ca8-a90e-9d12278350d0
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 43%

---

# Metodi di Target {#target-methods}

Elenco dei metodi di Target forniti dalla libreria Windows 8.1 Universal App Store.

L&#39;SDK supporta attualmente più soluzioni Adobe Experience Cloud, tra cui Analytics, Target e Audience Manager. Ai metodi è applicato il prefisso della relativa soluzione. I metodi di Analytics hanno il prefisso &quot;Target&quot;.

[Le metriche del ciclo di vita](/help/windows-appstore/metrics.md) sono inviate come parametri a ciascun caricamento Mbox.

>[!TIP]
>
>Quando utilizzi metodi `winmd` da winJS (JavaScript), tutti i metodi presentano automaticamente la prima lettera minuscola.

## Riferimento classe: TargetLocationRequest

### Proprietà

```
property Platform::String ^name; 
property Platform::String ^defaultContent; 
property Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^parameters;
```

## Costanti di stringa

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

* **LoadRequest (winJS: loadRequest)**

   Invia `request` al server di Target configurato e restituisce il valore stringa dell&#39;offerta generata in un blocco `callback`.

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

* **CreateRequest (winJS: createRequest)**

   Crea un oggetto `TargetLocationRequest` con i parametri specificati.

   * Di seguito è riportata la sintassi per questo metodo:

      ```csharp
      static TargetLocationRequest ^CreateRequest(Platform::String ^name, Platform::String ^defaultContent, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^parameters); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```js
      var ADB = ADBMobile; 
      var heroBannerRequest = ADB.Target.createRequest("heroBanner", "default.png", null); 
      ```

* **CreateOrder &#x200B; ConfirmRequest (winJS: createOrder &#x200B; ConfirmRequest)**

   Crea un oggetto `TargetLocationRequest` con i parametri specificati.

   * Di seguito è riportata la sintassi per questo metodo:

      ```csharp
      static TargetLocationRequest ^CreateOrderConfirmRequest(Platform::String ^name, Platform::String ^orderId, Platform::String ^orderTotal, Platform::String ^productPurchasedId, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> ^parameters); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```js
      var ADB = ADBMobile; 
      var orderConfirm = ADB.Target.createOrderConfirmRequest("orderConfirm", "order", "47.88", "3722", null); 
      ```

* **ClearCookies (winJS: clearCookies)**

   Cancella i cookie di Target per l’applicazione sul dispositivo corrente.

   * Di seguito è riportata la sintassi per questo metodo:

      ```csharp
      static void ClearCookies(); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```js
      ADBMobile.Target.clearCookies();
      ```

* **GetPcId (winJS: getPcId)**

   Restituisce il cookie ID PC del dispositivo corrente.

   * Di seguito è riportata la sintassi per questo metodo:

      ```csharp
      static Platform::String ^GetPcId();
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```js
      auto pcId = ADBMobile.Target.getPcId(); 
      ```

* **GetSessionId (winJS: getSessionId)**

   Restituisce il cookie ID sessione per il dispositivo corrente.

   * Di seguito è riportata la sintassi per questo metodo:

      ```csharp
      static Platform::String ^GetSessionId(); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```js
      auto sessionId = ADBMobile.Target.getSessionId(); 
      ```
