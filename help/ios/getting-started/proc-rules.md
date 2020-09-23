---
description: Le regole di elaborazione vengono utilizzate per copiare i dati inviati in variabili di dati di contesto a elementi eVar, prop e ad altre variabili a scopo di reportistica.
seo-description: Le regole di elaborazione vengono utilizzate per copiare i dati inviati in variabili di dati di contesto a elementi eVar, prop e ad altre variabili a scopo di reportistica.
seo-title: Regole di elaborazione e dati contestuali
solution: Experience Cloud,Analytics
title: Regole di elaborazione e dati contestuali
topic: Developer and implementation
uuid: 51338ccd-fa52-4d9c-97c4-947a4100465d
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 51%

---


# Regole di elaborazione e dati contestuali{#processing-rules-and-context-data}

Le regole di elaborazione vengono utilizzate per copiare i dati inviati in variabili di dati di contesto a elementi eVar, prop e ad altre variabili a scopo di reportistica.

Per ulteriori informazioni, consulta:

* [Formazione](https://tv.adobe.com/embed/1181/16506/?captions=ita) sulle regole di elaborazione @ Summit 2013
* Ottenere l&#39;autorizzazione all&#39;utilizzo delle regole di elaborazione

   Per ulteriori informazioni sulle regole di elaborazione, consulta [Panoramica sulle regole di elaborazione](https://docs.adobe.com/content/help/it-IT/analytics/admin/admin-tools/processing-rules/processing-rules.html).

Se lavori con le regole di elaborazione, ricorda quanto segue:

* Raggruppare le variabili di dati di contesto utilizzando gli spazi dei nomi, in quanto consente di mantenere un ordine logico.

   Ad esempio, se desideri raccogliere informazioni su un prodotto, puoi definire le seguenti variabili:

   ```js
   "product.type":"hat" 
   "product.team":"mariners" 
   "product.color":"blue"
   ```

* Le variabili di dati di contesto sono ordinate in ordine alfabetico nell&#39;interfaccia delle regole di elaborazione, consentendo di vedere rapidamente quali variabili si trovano nello stesso namespace.

   Evitate di denominare le chiavi dei dati contestuali utilizzando il numero evar o prop:

   ```js
   "eVar1":"jimbo"
   ```

   Questo potrebbe rendere *leggermente* più semplice eseguire la mappatura una tantum nelle regole di elaborazione, ma si perde la leggibilità durante il debug e gli aggiornamenti futuri del codice, il che può essere più difficile. Utilizzate, invece, nomi descrittivi per chiavi e valori:

   ```js
   "username":"jimbo"
   ```

* Le variabili di contesto che definiscono eventi contatore devono essere impostate su 1:

   ```js
   "logon":"1"
   ```

* Le variabili di contesto che definiscono eventi di incremento possono avere l’evento come chiave e l’entità dell’incremento come valore:

   ```js
   "levels completed":"6"
   ```

>[!TIP]
>
>Adobe riserva lo spazio dei nomi &quot; `a.`&quot;. A parte questa restrizione, per evitare conflitti l&#39;unico requisito consiste nell&#39;usare variabili di dati di contesto univoche per la società di accesso.

