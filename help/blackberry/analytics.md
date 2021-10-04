---
description: Dopo aver aggiunto la libreria al progetto, puoi eseguire qualsiasi chiamata dei metodi di Analytics in qualsiasi punto dell’app (assicurati di importare ADBMobile.h nella classe).
title: Analytics
uuid: de018eda-b37d-4afe-83a0-8011381d7aff
exl-id: 4cd27e1a-e806-4dbb-84f5-63902ca2003f
source-git-commit: 1fa6111d6bf1c2d36f15d2f037718646a035435a
workflow-type: tm+mt
source-wordcount: '639'
ht-degree: 12%

---

# Analytics {#analytics}

Dopo aver aggiunto la libreria al progetto, puoi eseguire qualsiasi chiamata dei metodi di Analytics in qualsiasi punto dell’app (assicurati di importare ADBMobile.h nella classe).

## Abilitare i rapporti sulle applicazioni mobili in Analytics {#task_3DA1354942CF4BF4B11B9CC97588A9ED}

Prima di aggiungere il codice, chiedi all’amministratore di Analytics di completare quanto segue per abilitare il tracciamento del ciclo di vita delle app mobili. Queste azioni assicurano che la suite di rapporti sia pronta per acquisire le metriche quando inizi lo sviluppo.

1. Apri **[!UICONTROL Strumenti di amministrazione]** > **[!UICONTROL Suite di rapporti]** e seleziona le suite di rapporti mobili.
1. Fai clic su **[!UICONTROL Modifica impostazioni]** > **[!UICONTROL Gestione mobile]** > **[!UICONTROL Generazione rapporti applicazioni mobili]**.

   ![Impostazioni di Mobile](assets/mobile-settings.png)

1. Fai clic su **[!UICONTROL Abilita rapporti app più recenti]**.

   Facoltativamente, puoi anche fare clic su **[!UICONTROL Abilita tracciamento posizione mobile]** e **[!UICONTROL Abilita rapporti legacy e attribuzione per hit di background]**.

   ![Attiva ciclo di vita](assets/enable-lifecycle.png)

Le metriche del ciclo di vita sono ora pronte per essere acquisite e i rapporti sulle applicazioni mobili vengono visualizzati nel menu **[!UICONTROL Report]** nell’interfaccia dei rapporti di marketing.

## Raccogliere metriche del ciclo di vita {#task_25D469C62DF84573AEB5E8E950B96205}

1. Per raccogliere le metriche del ciclo di vita nell&#39;app, chiama `collectLifecycleData()` nel costruttore `ApplicationUI` .

   Esempio:

   ```java
   ApplicationUI::ApplicationUI(bb::cascades::Application *app): QObject(app) { 
   //... 
   ADBMobile::collectLifecycleData(); 
   } 
   ```

   Se `collectLifecycleData()` viene chiamato due volte nella stessa sessione, l&#39;applicazione segnalerà un arresto anomalo per ogni chiamata successiva alla prima. L&#39;SDK imposta un flag quando l&#39;applicazione viene chiusa che indica una corretta uscita. Se questo flag non è impostato, `collectLifecyleData()` segnala un arresto anomalo.

## Eventi, prop ed eVar {#concept_B885D5A71A5D45129CE7C1C3426A7D28}

Se hai esaminato la [Guida di riferimento delle classi e dei metodi ADBMobile](/help/blackberry/methods.md), probabilmente ti chiederai dove impostare eventi, eVar, prop, eredi ed elenchi. Nella versione 4, non puoi più assegnare direttamente nell’app questi tipi di variabili. L’SDK utilizza invece i dati contestuali e le regole di elaborazione per mappare i dati dell’app sulle variabili di Analytics a scopo di reportistica.

Le regole di elaborazione offrono diversi vantaggi:

* Puoi modificare la mappatura dei dati senza inviare un aggiornamento all’App Store.
* Puoi assegnare ai dati dei nomi significativi invece di impostare variabili specifiche per una suite di rapporti.
* L’invio di dati aggiuntivi ha un impatto minimo. Questi valori verranno visualizzati nei rapporti solo dopo che saranno stati mappati utilizzando delle regole di elaborazione.

Eventuali valori che venivano assegnati direttamente alle variabili ora dovranno essere aggiunti all&#39; `data` HashMap .

## Regole di elaborazione {#concept_3EA4CD602AF4488A896B0EDD3BA2D969}

Le regole di elaborazione vengono utilizzate per copiare i dati inviati in variabili di dati di contesto a eVar, prop e ad altre variabili a scopo di reportistica.

[Regole di elaborazione](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/processing-rules/processing-rules.html)

Adobe consiglia di raggruppare le variabili di dati di contesto utilizzando &quot;namespace&quot;, in quanto consente di mantenere l’ordine logico. Ad esempio, se desideri raccogliere informazioni su un prodotto, puoi definire le seguenti variabili:

```js
"product.type":"hat";
"product.team":"mariners";
"product.color":"blue";
```

Le variabili di dati di contesto sono ordinate alfabeticamente nell’interfaccia delle regole di elaborazione, pertanto gli spazi dei nomi consentono di vedere rapidamente le variabili che si trovano nello stesso spazio dei nomi.

Inoltre, abbiamo sentito che alcuni di voi stanno denominando le chiavi dei dati di contesto utilizzando il numero di eVar o di proprietà:

```js
"eVar1":"jimbo";
```

Questo potrebbe semplificare leggermente *la mappatura una tantum nelle regole di elaborazione, a scapito però della leggibilità durante il debug e complicando gli aggiornamenti futuri del codice.* Consigliamo piuttosto di utilizzare nomi descrittivi per chiavi e valori:

```js
"username":"jimbo";
```

Le variabili di contesto che definiscono eventi contatore possono avere la stessa chiave e lo stesso valore:

```js
"logon":"logon";
```

Le variabili di contesto che definiscono eventi di incremento possono avere l’evento come chiave e la quantità da incrementare come valore:

```js
"levels completed":"6";
```

>[!TIP]
>
>Adobe riserva lo spazio dei nomi `a.`. A parte questa piccola restrizione, le variabili di dati di contesto devono essere univoche nella società di accesso per evitare conflitti.

## Abilita tracciamento offline {#concept_402F4ECE240B4CA1B779322A7BFCB8DE}

Per memorizzare gli hit quando il dispositivo è offline, puoi facoltativamente abilitare il tracciamento offline nel file `ADBMobileConfig.json` .

Prima di attivare il tracciamento offline, fai molta attenzione ai requisiti relativi alle marche temporali descritti nel riferimento al file di configurazione.

## Metodi di Analytics

Per un elenco dei metodi di Analytics disponibili per BlackBerry, vedi *Metodi di Analytics* in [Riferimento classe e metodo mobile di Adobe](/help/blackberry/methods.md).
