---
description: Le regole di elaborazione vengono utilizzate per copiare i dati inviati in variabili di dati di contesto a elementi eVar, prop e ad altre variabili a scopo di reportistica.
seo-description: Le regole di elaborazione vengono utilizzate per copiare i dati inviati in variabili di dati di contesto a elementi eVar, prop e ad altre variabili a scopo di reportistica.
seo-title: Regole di elaborazione e dati contestuali
solution: Marketing Cloud, Analytics
title: Regole di elaborazione e dati contestuali
topic: Sviluppatore e implementazione
uuid: ea 892228-86 f 5-4980-acb 8-45 ae 43 c 6996 d
translation-type: tm+mt
source-git-commit: bf076aa8e59d5c3e634fc4ae21f0de0d4541a83f

---


# Processing rules and context data {#processing-rules-and-context-data}

Le regole di elaborazione vengono utilizzate per copiare i dati inviati in variabili di dati di contesto a elementi eVar, prop e ad altre variabili a scopo di reportistica. Per ulteriori informazioni, vedi [Regole di elaborazione](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules.html).

Se lavori con le regole di elaborazione, ricorda quanto segue:

* Consigliamo di raggruppare le variabili di dati di contesto utilizzando namespace, per mantenere un ordine logico. Ad esempio, se desideri raccogliere informazioni su un prodotto, puoi definire le seguenti variabili:

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

   Anche se tali numeri possono facilitare *leggermente* i un lavoro di mappatura una tantum nelle regole di elaborazione, rendono il codice meno leggibile e complicano le attività di debug e gli aggiornamenti futuri. Piuttosto, consigliamo vivamente di assegnare a chiavi e valori dei nomi descrittivi:

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
>Adobe riserva lo spazio nomi `"a."`. A parte questa piccola restrizione, per evitare conflitti l'unico requisito consiste nell'usare variabili di dati di contesto univoche per la società di accesso.

