---
description: Esempio di variabile "products" con eVar per merchandising ed eventi per singoli prodotti.
keywords: android,libreria,mobile,sdk
solution: Experience Cloud Services,Analytics
title: Variabile "products" con eVar per merchandising ed eventi per singoli prodotti
topic-fix: Developer and implementation
uuid: 64f822a0-6ccf-48e7-8886-31b93d8198a3
exl-id: 2ede6341-3068-4423-a509-c0ec3a2db5e8
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '80'
ht-degree: 100%

---

# Variabile &quot;products&quot; con eVar per merchandising ed eventi per singoli prodotti {#products-variable-with-merchandising-evars-and-product-specific-events}

Esempio di variabile &quot;products&quot; con eVar per merchandising ed eventi per singoli prodotti.

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
>Se si attiva un evento specifico per il prodotto utilizzando la variabile *`&&products`*, è necessario impostare tale evento anche nella variabile *`&&events`*. In caso contrario, l’evento verrà escluso durante l’elaborazione.
