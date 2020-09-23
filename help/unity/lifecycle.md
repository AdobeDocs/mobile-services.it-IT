---
description: 'null'
keywords: Unity
seo-description: 'null'
seo-title: Implementare le metriche sul ciclo di vita
solution: Experience Cloud
title: Implementare le metriche sul ciclo di vita
uuid: 7ff2c194-569c-42a6-922d-dccd2aa9eb8d
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '85'
ht-degree: 11%

---


# Implementare le metriche sul ciclo di vita{#implement-lifecycle}

Per ulteriori informazioni sulle metriche e dimensioni misurabili automaticamente dalla libreria mobile dopo l’implementazione del ciclo di vita, vedi Metriche del [ciclo di vita in Android](/help/android/metrics.md) o [Ciclo di vita in iOS](/help/ios/metrics.md).

## iOS

Le metriche del ciclo di vita vengono raccolte automaticamente in iOS.

## Android

Nello script Unity, imposti il contesto dell’applicazione per l’SDK Android. Aggiungete il codice seguente alla `Awake()` funzione della scena FIRST:

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

