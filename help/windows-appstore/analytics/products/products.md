---
description: La variabile "products" non può essere impostata mediante le regole di elaborazione. Nell’SDK di Mobile devi usare una sintassi particolare nel parametro dei dati contestuali per impostare i prodotti direttamente nella chiamata al server.
seo-description: La variabile "products" non può essere impostata mediante le regole di elaborazione. Nell’SDK di Mobile devi usare una sintassi particolare nel parametro dei dati contestuali per impostare i prodotti direttamente nella chiamata al server.
seo-title: Variabile Products
solution: Marketing Cloud, Analytics
title: Variabile Products
topic: Sviluppatore e implementazione
uuid: 2057 a 564-06 ae -4171-bbe 7-0 baffa 71608 b
translation-type: tm+mt
source-git-commit: 7aff336586058302046a728a0b1b0ce12660c1ba

---


# Products variable{#products-variable}

La variabile "products" non può essere impostata mediante le regole di elaborazione. Nell’SDK di Mobile devi usare una sintassi particolare nel parametro dei dati contestuali per impostare i prodotti direttamente nella chiamata al server.

To set the *`products`* variable, set a context data key to `"&&products"`, and set the value using the syntax defined for the *`products`*:

```js
cdata["&&products"] = "Category;Product;Quantity;Price[,Category;Product;Quantity;Price]";
```

Ad esempio:

```js
//create a context data dictionary 
var cdata = new Windows.Foundation.Collections.PropertySet(); 
 
// add products, a purchase id, a purchase context data key, and any other data you want to collect. 
// Note the special syntax for products 
cdata["&&products"] = ";Running Shoes;1;69.95,;Running Socks;10;29.99"; 
cdata["m.purchaseid"] = "1234567890"; 
cdata["m.purchase"] = "1"; 
 
var ADB = ADBMobile; 
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
ADB.Analytics.trackAction("purchase", cdata); 
// trackState example: 
ADB.Analytics.trackState("Order Confirmation", cdata);
```

*`products`* è impostato direttamente nella richiesta dell'immagine, e le altre variabili sono impostate come dati contestuali. Tutte le variabili dei dati di contesto devono essere mappate utilizzando le regole di elaborazione:

![](assets/products-procrules.png)

Non è necessario mappare la *`products`* variabile utilizzando le regole di elaborazione, poiché viene impostata direttamente nella richiesta dell'immagine dall'SDK.
