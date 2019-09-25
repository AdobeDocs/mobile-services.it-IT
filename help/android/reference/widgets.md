---
description: I widget Android possono essere tracciati utilizzando gli stessi metodi dell'app. I widget condividono il contesto dell'applicazione con l'app, pertanto l'ordine degli hit e l'identificazione dei visitatori sono mantenuti.
keywords: android;libreria;mobile;sdk
seo-description: I widget Android possono essere tracciati utilizzando gli stessi metodi dell'app. I widget condividono il contesto dell'applicazione con l'app, pertanto l'ordine degli hit e l'identificazione dei visitatori sono mantenuti.
seo-title: Widget Android
solution: Marketing Cloud,Analytics
title: Android widgets
topic: Sviluppatore e implementazione
uuid: 1a3718ff-967b-4c8e-ae0b-ba15bdbda0a
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Android widgets {#android-widgets}

I widget Android possono essere tracciati utilizzando gli stessi metodi dell'app. I widget condividono il contesto dell'applicazione con l'app, pertanto l'ordine degli hit e l'identificazione dei visitatori sono mantenuti.

Le seguenti linee guida aiutano nel tracciamento dei widget Android:

* Do not implement lifecycle metrics ( `startActivity`/ `stopActivity`) calls in the widget.

* Per tracciare il momento in cui un widget viene aggiunto alla schermata principale, aggiungi una chiamata `trackState` o `trackEvent` al metodo `onEnabled` del widget.

* Per tracciare il momento in cui l'app è avviata da un widget, aggiungi una chiamata `trackState` o `trackEvent` prima di creare l'intento di avviare l'applicazione.

* To track the context of an action, you can define a `ContextData` variable that provides the option to segment each action separately (for example, `AppExperienceType="widget"` vs. `app`).

