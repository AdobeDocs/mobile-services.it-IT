---
description: Informazioni utili per implementare le metriche del ciclo di vita per Android. Le metriche del ciclo di vita vengono raccolte automaticamente per iOS.
keywords: Xamarin
seo-description: Informazioni utili per implementare le metriche del ciclo di vita per Android. Le metriche del ciclo di vita vengono raccolte automaticamente per iOS.
seo-title: Implementare le metriche sul ciclo di vita
solution: Experience Cloud
title: Implementare le metriche sul ciclo di vita
uuid: 6dccc12e-8b57-4231-9c74-d47bc0ac93ba
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '102'
ht-degree: 7%

---


# Implementare le metriche sul ciclo di vita {#implement-lifecycle}

Queste informazioni sono utili per implementare le metriche del ciclo di vita per Android.

>[!TIP]
>
>Le metriche del ciclo di vita vengono raccolte automaticamente per iOS.

For the metrics and dimensions that can be measured automatically by the mobile library after lifecycle is implemented, see [Lifecycle Metrics](/help/ios/metrics.md).

## iOS

In iOS, le metriche del ciclo di vita vengono raccolte automaticamente.

## Android

Nell’attività principale, imposta il contesto dell’applicazione per l’SDK Android.

```java
protected override void OnCreate (Bundle bundle) 
{
    ... 
    Config.SetContext (Application.Context); 
    ... 
}
```

In ogni attività, implementa le chiamate del ciclo di vita.

```java
protected override void OnResume()
{
    ...
    Config.CollectLifecycleData (this);
    ...
}
protected override void OnPause() 
{
    ...
    Config.PauseCollectingLifecycleData ();
    ...
}
```
