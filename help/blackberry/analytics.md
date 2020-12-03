---
description: Dopo aver aggiunto la libreria al progetto, puoi effettuare una qualsiasi chiamata ai metodi di Analytics in qualsiasi punto dell’app (assicurati di importare ADBMobile.h nella classe).
seo-description: Dopo aver aggiunto la libreria al progetto, puoi effettuare una qualsiasi chiamata ai metodi di Analytics in qualsiasi punto dell’app (assicurati di importare ADBMobile.h nella classe).
seo-title: Analytics
title: Analytics
uuid: de018eda-b37d-4afe-83a0-8011381d7aff
translation-type: tm+mt
source-git-commit: 7ae626be4d71641c6efb127cf5b1d3e18fccb907
workflow-type: tm+mt
source-wordcount: '684'
ht-degree: 14%

---


# Analytics {#analytics}

Dopo aver aggiunto la libreria al progetto, puoi effettuare una qualsiasi chiamata ai metodi di Analytics in qualsiasi punto dell’app (assicurati di importare ADBMobile.h nella classe).

## Abilitare i rapporti sulle applicazioni mobili in Analytics {#task_3DA1354942CF4BF4B11B9CC97588A9ED}

Prima di aggiungere il codice, chiedi all’amministratore di Analytics di completare quanto segue per abilitare il tracciamento del ciclo di vita delle app mobili. In questo modo, la suite di rapporti è pronta per acquisire le metriche all&#39;inizio dello sviluppo.


1. Apri Strumenti **[!UICONTROL di]** amministrazione > Suite di **[!UICONTROL rapporti]** e seleziona le suite di rapporti per dispositivi mobili.
1. Fate clic su **[!UICONTROL Modifica impostazioni]** > **[!UICONTROL Mobile Management]** > **[!UICONTROL Mobile Application Reporting]**.

   ![](assets/mobile-settings.png)

1. Fate clic su **[!UICONTROL Abilita rapporti]** app più recenti.

   Facoltativamente, puoi anche fare clic su **[!UICONTROL Abilita tracciamento]** posizione mobile e **[!UICONTROL Abilita rapporti legacy e attribuzione per hit]** in background.

   ![](assets/enable-lifecycle.png)

Le metriche del ciclo di vita sono ora pronte per essere acquisite e i rapporti sulle applicazioni mobili vengono visualizzati nel menu **[!UICONTROL Rapporti]** nell&#39;interfaccia dei rapporti di marketing.

## Raccolta delle metriche del ciclo di vita {#task_25D469C62DF84573AEB5E8E950B96205}

1. Per raccogliere le metriche del ciclo di vita nell&#39;app, invoca `collectLifecycleData()` il `ApplicationUI` costruttore.

   Esempio:

   ```java
   ApplicationUI::ApplicationUI(bb::cascades::Application *app): QObject(app) { 
   //... 
   ADBMobile::collectLifecycleData(); 
   } 
   ```

   Se `collectLifecycleData()` viene chiamato due volte nella stessa sessione, l&#39;applicazione segnalerà un arresto anomalo a ogni chiamata successiva alla prima. L’SDK imposta un flag quando l’applicazione viene chiusa per indicare un’uscita corretta. Se questo flag non è impostato, `collectLifecyleData()` segnala un arresto anomalo.

## Eventi, prop ed eVar {#concept_B885D5A71A5D45129CE7C1C3426A7D28}


Se hai esaminato la Guida di riferimento [per le classi e i metodi di](/help/blackberry/methods.md)ADBMobile, probabilmente ti stai chiedendo dove impostare eventi, eVar, prop, eredi ed elenchi. Nella versione 4, non è più possibile assegnare questi tipi di variabili direttamente nell&#39;app. L’SDK utilizza invece i dati contestuali e le regole di elaborazione per mappare i dati dell’app sulle variabili di Analytics a scopo di reportistica.

Le regole di elaborazione offrono diversi vantaggi:

* Puoi modificare la mappatura dei dati senza inviare un aggiornamento all’App Store.
* Puoi assegnare ai dati dei nomi significativi invece di impostare variabili specifiche per una suite di rapporti.
* L’invio di dati aggiuntivi ha un impatto minimo. Questi valori verranno visualizzati nei rapporti solo dopo che saranno stati mappati utilizzando delle regole di elaborazione.

Any values that you were assigning directly to variables should be added to the `data` HashMap instead.

## Regole di elaborazione {#concept_3EA4CD602AF4488A896B0EDD3BA2D969}

Le regole di elaborazione vengono utilizzate per copiare i dati inviati in variabili di dati di contesto a variabili evar, prop e ad altre variabili per il reporting.

[Formazione sulle regole di elaborazione](https://tv.adobe.com/embed/1181/16506/) @ Summit 2013

[Regole di elaborazione](https://docs.adobe.com/content/help/it-IT/analytics/admin/admin-tools/processing-rules/processing-rules.html)

[Ottenere l&#39;autorizzazione all&#39;utilizzo delle regole di elaborazione](https://helpx.adobe.com/analytics/kb/processing-rules-authorization.html)

È consigliabile raggruppare le variabili di dati di contesto utilizzando &quot;spazi dei nomi&quot;, in quanto consente di mantenere l&#39;ordine logico. Ad esempio, se desideri raccogliere informazioni su un prodotto, puoi definire le seguenti variabili:

```js
"product.type":"hat" 
"product.team":"mariners" 
"product.color":"blue"
```

Le variabili di dati di contesto sono ordinate in ordine alfabetico nell&#39;interfaccia delle regole di elaborazione, per cui gli spazi dei nomi consentono di visualizzare rapidamente le variabili che si trovano nello stesso namespace.

Inoltre, alcuni di voi stanno denominando le chiavi dei dati di contesto utilizzando il numero evar o prop:

```js
"eVar1":"jimbo"
```

This might make it *slightly* easier when you perform the one time mapping in processing rules, but you lose readability during debugging and future code updates can be more difficult. È invece consigliabile utilizzare nomi descrittivi per chiavi e valori:

```js
"username":"jimbo"
```

Le variabili di contesto che definiscono eventi contatore possono avere la stessa chiave e lo stesso valore:

```js
"logon":"logon"
```

Le variabili di contesto che definiscono eventi di incremento possono avere l&#39;evento come chiave e la quantità da incrementare come valore:

```js
"levels completed":"6"
```

>[!TIP]
>
>Adobe riserva lo spazio dei nomi `a.`. A parte questa piccola restrizione, le variabili dei dati di contesto devono essere univoche nella società di accesso per evitare conflitti.

## Abilita tracciamento offline {#concept_402F4ECE240B4CA1B779322A7BFCB8DE}

Per memorizzare gli hit quando il dispositivo è offline, puoi facoltativamente abilitare il tracciamento offline nel `ADBMobileConfig.json` file.

Prima di attivare il tracciamento offline, prestate molta attenzione ai requisiti relativi alle marche temporali descritti nel riferimento al file di configurazione.

## Metodi di Analytics

Per un elenco dei metodi di Analytics disponibili per BlackBerry, consultate Metodi *di* Analytics in [Guida di riferimento](/help/blackberry/methods.md)delle classi e dei metodi per dispositivi mobili di Adobe.