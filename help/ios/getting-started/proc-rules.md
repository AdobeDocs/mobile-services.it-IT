---
description: Le regole di elaborazione vengono utilizzate per copiare i dati inviati in variabili di dati di contesto a elementi eVar, prop e ad altre variabili a scopo di reportistica.
seo-description: Le regole di elaborazione vengono utilizzate per copiare i dati inviati in variabili di dati di contesto a elementi eVar, prop e ad altre variabili a scopo di reportistica.
seo-title: Regole di elaborazione e dati contestuali
solution: Experience Cloud,Analytics
title: Regole di elaborazione e dati contestuali
topic-fix: Developer and implementation
uuid: 51338ccd-fa52-4d9c-97c4-947a4100465d
exl-id: a3968160-42c4-4671-b541-c14639b8a451
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 100%

---

# Regole di elaborazione e dati contestuali {#processing-rules-and-context-data}

Le regole di elaborazione vengono utilizzate per copiare i dati inviati in variabili di dati di contesto a elementi eVar, prop e ad altre variabili a scopo di reportistica.

Per ulteriori informazioni, consulta:

* [Formazione sulle regole di elaborazione](https://tv.adobe.com/embed/1181/16506/) @ Summit 2013
* Ottenere l&#39;autorizzazione all&#39;utilizzo delle regole di elaborazione

   Per ulteriori informazioni sulle regole di elaborazione, consulta [Panoramica sulle regole di elaborazione](https://docs.adobe.com/content/help/it-IT/analytics/admin/admin-tools/processing-rules/processing-rules.html).

Se lavori con le regole di elaborazione, ricorda quanto segue:

* Raggruppa le variabili di dati di contesto utilizzando spazi dei nomi (namespace), utili per mantenere un ordine logico.

   Ad esempio, se desideri raccogliere informazioni su un prodotto, puoi definire le seguenti variabili:

   ```js
   "product.type":"hat" 
   "product.team":"mariners" 
   "product.color":"blue"
   ```

* Nell’interfaccia delle regole di elaborazione, le variabili di dati contestuali sono presentate in ordine alfabetico in modo che si possa rapidamente individuare le variabili che si trovano nello stesso spazio dei nomi.

   Evita di denominare le chiavi dei dati contestuali utilizzando il numero evar o prop:

   ```js
   "eVar1":"jimbo"
   ```

   Questo potrebbe semplificare *leggermente* la mappatura una tantum nelle regole di elaborazione, a scapito però della leggibilità durante il debug e gli aggiornamenti futuri del codice. Utilizza piuttosto nomi descrittivi per chiavi e valori:

   ```js
   "username":"jimbo"
   ```

* Le variabili di contesto che definiscono eventi contatore devono essere impostate su 1:

   ```js
   "logon":"1"
   ```

* Per le variabili di contesto che definiscono eventi di incremento, è possibile usare l’evento come chiave e l’entità di incremento come valore:

   ```js
   "levels completed":"6"
   ```

>[!TIP]
>
>Adobe riserva lo spazio dei nomi &quot; `a.`&quot;. A parte questa restrizione, per evitare conflitti l&#39;unico requisito consiste nell&#39;usare variabili di dati di contesto univoche per la società di accesso.
