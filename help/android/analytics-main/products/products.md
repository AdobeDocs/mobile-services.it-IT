---
description: Non è possibile impostare la variabile "products" utilizzando le regole di elaborazione. Nell’SDK di Mobile devi usare una sintassi particolare nel parametro dei dati contestuali per impostare i prodotti nella chiamata al server.
keywords: android,libreria,mobile,sdk
seo-description: Non è possibile impostare la variabile "products" utilizzando le regole di elaborazione. Nell’SDK di Mobile devi usare una sintassi particolare nel parametro dei dati contestuali per impostare i prodotti nella chiamata al server.
seo-title: Variabile "products"
solution: Experience Cloud,Analytics
title: Variabile "products"
topic-fix: Developer and implementation
uuid: f4484022-cb8b-4dea-9209-5a110ba607df
exl-id: 1d850ce1-6fd4-463e-8949-8b8cf40d8467
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 100%

---

# Variabile &quot;products&quot; {#products-variable}

Non è possibile impostare la variabile &quot;products&quot; utilizzando le regole di elaborazione. Nell’SDK di Mobile devi usare una sintassi particolare nel parametro dei dati contestuali per impostare i prodotti nella chiamata al server.

Per impostare la variabile *products*, imposta una chiave di dati contestuali su `"&&products"`, quindi imposta il valore utilizzando la sintassi definita per la variabile *products*:

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

La variabile *products* è impostata sulla richiesta dell’immagine e le altre variabili sono impostate come dati contestuali. Tutte le variabili dei dati di contesto devono essere mappate utilizzando le regole di elaborazione:

![](assets/map-products.png)

Non è necessario mappare la variabile   *products* mediante le regole di elaborazione, perché viene impostata direttamente nella richiesta dell’immagine dall’SDK.
