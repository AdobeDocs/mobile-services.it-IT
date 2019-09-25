---
description: La variabile "products" non può essere impostata mediante le regole di elaborazione. Nell'SDK di Mobile devi usare una sintassi particolare nel parametro dei dati contestuali per impostare i prodotti nella chiamata al server.
keywords: android;library;mobile;sdk
seo-description: La variabile "products" non può essere impostata mediante le regole di elaborazione. Nell'SDK di Mobile devi usare una sintassi particolare nel parametro dei dati contestuali per impostare i prodotti nella chiamata al server.
seo-title: Variabile "products"
solution: Marketing Cloud,Analytics
title: Variabile "products"
topic: Sviluppatore e implementazione
uuid: f4484022-cb8b-4dea-9209-5a110ba607df
translation-type: tm+mt
source-git-commit: 7aff336586058302046a728a0b1b0ce12660c1ba

---


# Products variable {#products-variable}

La variabile "products" non può essere impostata mediante le regole di elaborazione. Nell'SDK di Mobile devi usare una sintassi particolare nel parametro dei dati contestuali per impostare i prodotti nella chiamata al server.

To set the *products* variable, set a context data key to `"&&products"`, and set the value by using the syntax that is defined for the *products* variable:

```java
cdata.put("&&products", "Category;Product;Quantity;Price[,Category;Product;Quantity;Price]");
```

Ad esempio:

```java
//create a context data dictionary 
HashMap cdata = new HashMap<String, Object>(); 
 
// add products, a purchase id, a purchase context data key, and any other data you want to collect. 
// Note the special syntax for products 
cdata.put("&&products", ";Running Shoes;1;69.95,;Running Socks;10;29.99"); 
cdata.put("myapp.purchase", "1"); 
cdata.put("myapp.purchaseid", "1234567890"); 
 
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
Analytics.trackAction("purchase", cdata); 
// trackState example: 
Analytics.trackState("Order Confirmation", cdata);
```

The *products* variable is set on the image request, and the other variables are set as context data. Tutte le variabili dei dati di contesto devono essere mappate utilizzando le regole di elaborazione:

![](assets/map-products.png)

Non è necessario mappare la variabile *products* variable by using processing rules because this variable is set directly on the image request by the SDK.
