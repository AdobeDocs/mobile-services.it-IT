---
description: Esempio di variabile "products" con eVar per merchandising ed eventi per singoli prodotti.
keywords: android; libreria; mobile; sdk
seo-description: Esempio di variabile "products" con eVar per merchandising ed eventi per singoli prodotti.
seo-title: Variabile "products" con eVar per merchandising ed eventi per singoli prodotti
solution: Marketing Cloud, Analytics
title: Variabile "products" con eVar per merchandising ed eventi per singoli prodotti
topic: Sviluppatore e implementazione
uuid: 64 f 822 a 0-6 ccf -48 e 7-8886-31 b 93 d 8198 a 3
translation-type: tm+mt
source-git-commit: bf076aa8e59d5c3e634fc4ae21f0de0d4541a83f

---


# Products variable with merchandising eVars and product-specific events {#products-variable-with-merchandising-evars-and-product-specific-events}

Esempio di variabile "products" con eVar per merchandising ed eventi per singoli prodotti.

```java
//create a context data dictionary 
HashMap cdata = new HashMap<String, Object>(); 
  
// add products, a purchase id, a purchase context data key, and any other data you want to collect. 
// Note the special syntax for products 
cdata.put("&&events", "event1"); 
cdata.put("&&products", ";Running Shoes;1;69.95;event1=5.5;eVar1=Merchandising,;Running Socks;10;29.99"); 
cdata.put("myapp.purchase", "1"); 
cdata.put("myapp.purchaseid", "1234567890"); 
  
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
Analytics.trackAction("purchase", cdata); 
// trackState example: 
Analytics.trackState("Order Confirmation", cdata);
```

>[!TIP]
>
>Se attivate un evento specifico per un prodotto utilizzando la *`&&products`* variabile, dovete anche impostare tale evento nella *`&&events`* variabile. In caso contrario, l'evento verrà escluso durante l'elaborazione.
