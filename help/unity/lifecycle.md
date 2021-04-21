---
description: Misura metriche e dimensioni misurabili automaticamente dalla libreria mobile
keywords: Unity
solution: Experience Cloud
title: Implementare le metriche sul ciclo di vita
uuid: 7ff2c194-569c-42a6-922d-dccd2aa9eb8d
exl-id: eca0cebb-6c69-4b0f-b003-c7fc422d0383
translation-type: tm+mt
source-git-commit: b9ee49ba26d4726b1f97ef36f5c2e9923361b1ee
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 7%

---

# Implementare le metriche sul ciclo di vita{#implement-lifecycle}

Per ulteriori informazioni sulle metriche e dimensioni misurabili automaticamente dalla libreria mobile dopo l&#39;implementazione del ciclo di vita, consulta [Metriche del ciclo di vita in Android](/help/android/metrics.md) o [Ciclo di vita in iOS](/help/ios/metrics.md).

## iOS

Le metriche del ciclo di vita vengono raccolte automaticamente in iOS.

## Android

Nello script Unity, imposta il contesto dell&#39;applicazione per l&#39;SDK Android. Aggiungi il codice seguente alla funzione `Awake()` della scena FIRST:

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
