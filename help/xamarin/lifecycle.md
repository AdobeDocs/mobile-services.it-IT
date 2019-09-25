---
description: Informazioni che consentono di implementare le metriche del ciclo di vita per Android. Le metriche del ciclo di vita vengono raccolte automaticamente per iOS.
keywords: Xamarin
seo-description: Informazioni che consentono di implementare le metriche del ciclo di vita per Android. Le metriche del ciclo di vita vengono raccolte automaticamente per iOS.
seo-title: Implement lifecycle
solution: Marketing Cloud,Sviluppatore
title: Implementa ciclo di vita
uuid: 6dccc12e-8b57-4231-9c74-d47bc0ac93ba
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Implement lifecycle {#implement-lifecycle}

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
