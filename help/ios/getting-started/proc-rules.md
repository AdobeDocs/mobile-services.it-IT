---
description: Le regole di elaborazione vengono utilizzate per copiare i dati inviati in variabili di dati di contesto a elementi eVar, prop e ad altre variabili a scopo di reportistica.
seo-description: Le regole di elaborazione vengono utilizzate per copiare i dati inviati in variabili di dati di contesto a elementi eVar, prop e ad altre variabili a scopo di reportistica.
seo-title: Regole di elaborazione e dati contestuali
solution: Marketing Cloud, Analytics
title: Regole di elaborazione e dati contestuali
topic: Sviluppatore e implementazione
uuid: 51338 ccd-fa 52-4 d 9 c -97 c 4-947 a 4100465 d
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Processing rules and context data{#processing-rules-and-context-data}

Le regole di elaborazione vengono utilizzate per copiare i dati inviati in variabili di dati di contesto a elementi eVar, prop e ad altre variabili a scopo di reportistica.

Per ulteriori informazioni, consulta:

* [Formazione sulle regole di elaborazione](https://tv.adobe.com/embed/1181/16506/) @ Summit 2013
* Diventare autorizzati a utilizzare le regole di elaborazione

   Per ulteriori informazioni sulle regole di elaborazione, consulta [Panoramica sulle regole di elaborazione](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules.html).

Se lavori con le regole di elaborazione, ricorda quanto segue:

* Consigliamo di raggruppare le variabili di dati di contesto utilizzando namespace, per mantenere un ordine logico.

   Ad esempio, se desideri raccogliere informazioni su un prodotto, puoi definire le seguenti variabili:

   ```js
   "product.type":"hat" 
   "product.team":"mariners" 
   "product.color":"blue"
   ```

* Le variabili di dati di contesto sono riportate in ordine alfabetico nell'interfaccia delle regole di elaborazione, così puoi vedere rapidamente le variabili di uno stesso namespace.

   Evita di denominare le chiavi dei dati di contesto utilizzando il numero evar o prop:

   ```js
   "eVar1":"jimbo"
   ```

   Anche se tali numeri possono facilitare *leggermente* un lavoro di mappatura una tantum nelle regole di elaborazione, rendono il codice meno leggibile e complicano le attività di debug e gli aggiornamenti futuri. Usa invece nomi descrittivi per tasti e valori:

   ```js
   "username":"jimbo"
   ```

* Le variabili di contesto che definiscono eventi di contatore devono essere impostate su 1:

   ```js
   "logon":"1"
   ```

* Per le variabili di contesto che definiscono eventi di incremento, puoi usare l'evento come chiave e l'entità dell'incremento come valore:

   ```js
   "levels completed":"6"
   ```

>[!TIP]
>
>Adobe riserva lo spazio nomi " `a.`". A parte questa restrizione, per evitare conflitti l'unico requisito consiste nell'usare variabili di dati di contesto univoche per la società di accesso.

