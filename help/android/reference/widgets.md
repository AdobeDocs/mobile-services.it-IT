---
description: I widget Android possono essere tracciati utilizzando gli stessi metodi dell'app. I widget condividono il contesto dell’applicazione con l’app, pertanto l’ordine degli hit e l’identificazione dei visitatori vengono mantenuti.
keywords: android;library;mobile;sdk
seo-description: I widget Android possono essere tracciati utilizzando gli stessi metodi dell'app. I widget condividono il contesto dell’applicazione con l’app, pertanto l’ordine degli hit e l’identificazione dei visitatori vengono mantenuti.
seo-title: Widget Android
solution: Experience Cloud,Analytics
title: Widget Android
topic: Developer and implementation
uuid: 1a3718ff-967b-4c8e-ae0b-ba15bddbda0a
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 46%

---


# Widget Android {#android-widgets}

I widget Android possono essere tracciati utilizzando gli stessi metodi dell&#39;app. I widget condividono il contesto dell’applicazione con l’app, pertanto l’ordine degli hit e l’identificazione dei visitatori vengono mantenuti.

Le seguenti linee guida sono utili per tenere traccia dei widget Android:

* Non implementare chiamate delle metriche del ciclo di vita ( `startActivity`/ `stopActivity`) nel widget.

* Per tracciare il momento in cui un widget viene aggiunto alla schermata principale, aggiungi una chiamata `trackState` o `trackEvent` al metodo `onEnabled` del widget.

* Per tracciare il momento in cui l&#39;app è avviata da un widget, aggiungi una chiamata `trackState` o `trackEvent` prima di creare l&#39;intento di avviare l&#39;applicazione.

* Per tracciare il contesto di un&#39;azione, puoi definire una variabile `ContextData` che offre l&#39;opzione di segmentare separatamente ciascuna azione (ad esempio, `AppExperienceType="widget"` vs. `app`).

