---
description: Esempio di variabile "products" con eVar per merchandising ed eventi per singoli prodotti.
seo-description: Esempio di variabile "products" con eVar per merchandising ed eventi per singoli prodotti.
seo-title: Variabile "products" con eVar per merchandising ed eventi per singoli prodotti
solution: Experience Cloud,Analytics
title: Variabile "products" con eVar per merchandising ed eventi per singoli prodotti
topic-fix: Developer and implementation
uuid: f913211e-97ad-4237-bfe4-7ded01295caf
exl-id: f438190d-0d2d-4bcd-a1c7-156e46e61162
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '98'
ht-degree: 100%

---

# Variabile &quot;products&quot; con eVar per merchandising ed eventi per singoli prodotti {#products-variable-with-merchandising-evars-and-product-specific-events}

Esempio di variabile &quot;products&quot; con eVar per merchandising ed eventi per singoli prodotti.

```
//create a context data dictionary 
NSMutableDictionary *contextData = [NSMutableDictionary dictionary]; 
  
// add products, a purchase id, a purchase context data key, and any other data you want to collect. 
// Note the special syntax for products 
[contextData setObject:@"event1" forKey:@"&&events"]; 
[contextData setObject:@";Running Shoes;1;69.95;event1=5.5;eVar1=Merchandising,;Running Socks;10;29.99" forKey:@"&&products"]; 
[contextData setObject:@"1234567890" forKey:@"m.purchaseid"]; 
[contextData setObject:@"1" forKey:@"m.purchase"]; 
  
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
[ADBMobile trackAction:@"purchase" data:contextData]; 
// trackState example: 
[ADBMobile trackState:@"Order Confirmation" data:contextData];
```

>[!TIP]
>
>Se si attiva un evento specifico per il prodotto utilizzando la variabile *`&&products`*, è necessario impostare tale evento anche nella variabile *`&&events`*. In caso contrario, l’evento verrà escluso durante l’elaborazione.
