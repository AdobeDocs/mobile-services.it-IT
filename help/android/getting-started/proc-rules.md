---
description: Le regole di elaborazione vengono utilizzate per copiare i dati inviati in variabili di dati di contesto a elementi eVar, prop e ad altre variabili a scopo di reportistica.
seo-description: Le regole di elaborazione vengono utilizzate per copiare i dati inviati in variabili di dati di contesto a elementi eVar, prop e ad altre variabili a scopo di reportistica.
seo-title: Regole di elaborazione e dati contestuali
solution: Experience Cloud,Analytics
title: Regole di elaborazione e dati contestuali
topic-fix: Developer and implementation
uuid: ea892228-86f5-4980-acb8-45ae43c6996d
exl-id: 543201fd-8118-485f-8235-26ec8f9bbb11
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 100%

---

# Regole di elaborazione e dati contestuali {#processing-rules-and-context-data}

Le regole di elaborazione vengono utilizzate per copiare i dati inviati in variabili di dati di contesto a elementi eVar, prop e ad altre variabili a scopo di reportistica. Per ulteriori informazioni, consulta [Regole di elaborazione](https://docs.adobe.com/content/help/it-IT/analytics/admin/admin-tools/processing-rules/processing-rules.html).

Se lavori con le regole di elaborazione, ricorda quanto segue:

* Raggruppa le variabili di dati di contesto utilizzando spazi dei nomi (namespace), utili per mantenere un ordine logico. Ad esempio, per raccogliere informazioni su un prodotto, puoi definire le seguenti variabili:

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

   Questo potrebbe semplificare *leggermente* la mappatura una tantum nelle regole di elaborazione, a scapito però della leggibilità durante il debug e gli aggiornamenti futuri del codice. È consigliabile piuttosto utilizzare nomi descrittivi per chiavi e valori:

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
>Adobe riserva lo spazio dei nomi `"a."`. A parte questa piccola restrizione, per evitare conflitti l&#39;unico requisito consiste nell&#39;usare variabili di dati di contesto univoche per la società di accesso.
