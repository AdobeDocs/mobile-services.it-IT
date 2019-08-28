---
description: nulle
keywords: Unity
seo-description: nulle
seo-title: Implementazione del ciclo di vita
solution: Marketing Cloud, Sviluppatore
title: Implementazione del ciclo di vita
uuid: 7 ff 2 c 194-569 c -42 a 6-922 d-dccd 2 aa 9 eb 8 d
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Implementazione del ciclo di vita{#implement-lifecycle}

Per ulteriori informazioni sulle metriche e sulle dimensioni misurabili automaticamente dalla libreria mobile dopo l'implementazione del ciclo di vita, vedi [Metriche del ciclo di vita in Android](/help/android/metrics.md) o [Lifecycle in iOS](/help/ios/metrics.md).

## iOS

Le metriche del ciclo di vita vengono raccolte automaticamente in iOS.

## Android

Nello script Unity è necessario impostare il contesto dell'applicazione per l'SDK di Android. Add the following code to the `Awake()` function of your FIRST scene:

```java
void Awake()
 {
  ...
  ADBMobile.SetContext();
  ...
 }
```

Per raccogliere le metriche del ciclo di vita, aggiungi il codice seguente a tutti gli script di scena:

```java
void OnEnable()
 {
  ...
  ADBMobile.CollectLifecycleData (); 
  ...
 }
 
 void OnDisable()
 {
  ...
  ADBMobile.PauseCollectingLifecycleData (); 
  ...
 }
  
 void OnApplicationPause(bool isPaused) 
 {
  ...
  if (isPaused) {
   ADBMobile.PauseCollectingLifecycleData (); 
  }  
  else {
   ADBMobile.CollectLifecycleData(); 
  }
  ...
 }
```

