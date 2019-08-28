---
description: Informazioni che consentono di implementare le metriche del ciclo di vita per Android. Le metriche del ciclo di vita vengono raccolte automaticamente per iOS.
keywords: Xamarin
seo-description: Informazioni che consentono di implementare le metriche del ciclo di vita per Android. Le metriche del ciclo di vita vengono raccolte automaticamente per iOS.
seo-title: Implementazione del ciclo di vita
solution: Marketing Cloud, Sviluppatore
title: Implementazione del ciclo di vita
uuid: 6 dccc 12 e -8 b 57-4231-9 c 74-d 47 bc 0 ac 93 ba
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

Nell'attività principale, imposta il contesto dell'applicazione per l'SDK per Android.

```java
protected override void OnCreate (Bundle bundle) 
{
    ... 
    Config.SetContext (Application.Context); 
    ... 
}
```

In ogni attività, implementa chiamate lifecycle.

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
