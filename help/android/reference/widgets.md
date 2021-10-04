---
description: È possibile tenere traccia dei widget Android utilizzando gli stessi metodi applicabili per l’app. Poiché i widget condividono con l’app il contesto applicativo, vengono mantenuti sia l’ordine degli hit sia l’identificazione dei visitatori.
keywords: android,libreria,mobile,sdk
solution: Experience Cloud,Analytics
title: Widget Android
topic-fix: Developer and implementation
uuid: 1a3718ff-967b-4c8e-ae0b-ba15bddbda0a
exl-id: 229ea987-256a-45f4-a5ca-afe17dd596b8
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 100%

---

# Widget Android {#android-widgets}

È possibile tenere traccia dei widget Android utilizzando gli stessi metodi applicabili per l’app. Poiché i widget condividono con l’app il contesto applicativo, vengono mantenuti sia l’ordine degli hit sia l’identificazione dei visitatori.

Le seguenti linee guida sono utili per tenere traccia dei widget Android:

* Non implementare chiamate delle metriche del ciclo di vita ( `startActivity`/ `stopActivity`) nel widget.

* Per tracciare il momento in cui un widget viene aggiunto alla schermata principale, aggiungi una chiamata `trackState` o `trackEvent` al metodo `onEnabled` del widget.

* Per tracciare il momento in cui l&#39;app è avviata da un widget, aggiungi una chiamata `trackState` o `trackEvent` prima di creare l&#39;intento di avviare l&#39;applicazione.

* Per tracciare il contesto di un&#39;azione, puoi definire una variabile `ContextData` che offre l&#39;opzione di segmentare separatamente ciascuna azione (ad esempio, `AppExperienceType="widget"` vs. `app`).
