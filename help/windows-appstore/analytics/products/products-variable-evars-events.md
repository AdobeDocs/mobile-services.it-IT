---
description: Esempio di variabile "products" con eVar per merchandising ed eventi per singoli prodotti.
seo-description: Esempio di variabile "products" con eVar per merchandising ed eventi per singoli prodotti.
seo-title: Variabile "products" con eVar per merchandising ed eventi per singoli prodotti
solution: Marketing Cloud,Analytics
title: Variabile "products" con eVar per merchandising ed eventi per singoli prodotti
topic: Sviluppatore e implementazione
uuid: 94e882e4-b19d-4c48-9dfb-331465490347
translation-type: tm+mt
source-git-commit: b630c5cf09be7fbe31018cbf50564001eb6e2a5a

---


# Products variable with merchandising eVars and product-specific events{#products-variable-with-merchandising-evars-and-product-specific-events}

Esempio di variabile "products" con eVar per merchandising ed eventi per singoli prodotti.

```
//create a context data dictionary 
var cdata = new Windows.Foundation.Collections.PropertySet(); 
  
// add products, a purchase id, a purchase context data key, and any other data you want to collect. 
// Note the special syntax for products 
cdata["&&events"] = "event1 "; 
cdata["&&products"] = ";Running Shoes;1;69.95;event1=5.5;eVar1=Merchandising,;Running Socks;10;29.99"; 
cdata["m.purchaseid"] = "1234567890"; 
cdata["m.purchase"] = "1"; 
  
var ADB = ADBMobile; 
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
ADB.Analytics.trackAction("purchase", cdata); 
// trackState example: 
ADB.Analytics.trackState("Order Confirmation", cdata);
```

>[!TIP]
>
>Se si attiva un evento specifico per il prodotto utilizzando la *`&&products`* variabile, è necessario impostare tale evento anche nella *`&&events`* variabile, altrimenti l'evento viene escluso durante l'elaborazione.

