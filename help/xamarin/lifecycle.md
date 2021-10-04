---
description: Informazioni utili per implementare le metriche del ciclo di vita per Android. Le metriche del ciclo di vita vengono raccolte automaticamente per iOS.
keywords: Xamarina
solution: Experience Cloud
title: Implementare le metriche sul ciclo di vita
uuid: 6dccc12e-8b57-4231-9c74-d47bc0ac93ba
exl-id: c76e63d1-48a5-4831-85d5-f3d3e9798a43
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '85'
ht-degree: 7%

---

# Implementare le metriche sul ciclo di vita {#implement-lifecycle}

Queste informazioni sono utili per implementare le metriche del ciclo di vita per Android.

>[!TIP]
>
>Le metriche del ciclo di vita vengono raccolte automaticamente per iOS.

Per le metriche e le dimensioni misurabili automaticamente dalla libreria mobile dopo l&#39;implementazione del ciclo di vita, consulta [Metriche del ciclo di vita](/help/ios/metrics.md).

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

In ogni attività, implementa le chiamate al ciclo di vita.

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
