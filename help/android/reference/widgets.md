---
description: I widget Android possono essere tracciati utilizzando gli stessi metodi dell'app. I widget condividono il contesto dell'applicazione con l'app, pertanto l'ordine degli hit e l'identificazione dei visitatori sono mantenuti.
keywords: android,libreria,mobile,sdk
seo-description: I widget Android possono essere tracciati utilizzando gli stessi metodi dell'app. I widget condividono il contesto dell'applicazione con l'app, pertanto l'ordine degli hit e l'identificazione dei visitatori sono mantenuti.
seo-title: Widget Android
solution: Experience Cloud,Analytics
title: Widget Android
topic: Sviluppatore e implementazione
uuid: 1a3718ff-967b-4c8e-ae0b-ba15bddbda0a
translation-type: ht
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Widget Android {#android-widgets}

I widget Android possono essere tracciati utilizzando gli stessi metodi dell'app. I widget condividono il contesto dell'applicazione con l'app, pertanto l'ordine degli hit e l'identificazione dei visitatori sono mantenuti.

Le seguenti linee guida aiutano nel tracciamento dei widget Android:

* Non implementare chiamate delle metriche del ciclo di vita ( `startActivity`/ `stopActivity`) nel widget.

* Per tracciare il momento in cui un widget viene aggiunto alla schermata principale, aggiungi una chiamata `trackState` o `trackEvent` al metodo `onEnabled` del widget.

* Per tracciare il momento in cui l'app è avviata da un widget, aggiungi una chiamata `trackState` o `trackEvent` prima di creare l'intento di avviare l'applicazione.

* Per tracciare il contesto di un'azione, puoi definire una variabile `ContextData` che offre l'opzione di segmentare separatamente ciascuna azione (ad esempio, `AppExperienceType="widget"` vs. `app`).

