---
description: Impossibile impostare la variabile "products" utilizzando le regole di elaborazione. Nell’SDK di Mobile devi usare una sintassi particolare nel parametro dei dati contestuali per impostare i prodotti direttamente nella chiamata al server.
solution: Experience Cloud Services,Analytics
title: 'Variabile "products" '
topic-fix: Developer and implementation
uuid: 2057a564-06ae-4171-bbe7-0baffa71608b
exl-id: b731e794-7134-4c6d-a41b-09ac9b84763d
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '139'
ht-degree: 15%

---

# Variabile &quot;products&quot; {#products-variable}

Impossibile impostare la variabile &quot;products&quot; utilizzando le regole di elaborazione. Nell’SDK di Mobile devi usare una sintassi particolare nel parametro dei dati contestuali per impostare i prodotti direttamente nella chiamata al server.

Per impostare *`products`* imposta una chiave di dati contestuali su `"&&products"`e imposta il valore utilizzando la sintassi definita per la *`products`*:

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

*`products`* è impostato direttamente nella richiesta dell’immagine, e le altre variabili sono impostate come dati contestuali. Tutte le variabili di dati di contesto devono essere mappate utilizzando le regole di elaborazione:

![](assets/products-procrules.png)

Non è necessario mappare il *`products`* mediante le regole di elaborazione, in quanto viene impostata direttamente nella richiesta dell’immagine dall’SDK.
