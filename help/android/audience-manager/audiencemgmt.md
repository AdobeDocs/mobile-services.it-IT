---
description: Puoi inviare segnali e recuperare segmenti di visitatori da Gestione dell'audience.
keywords: android;libreria;mobile;sdk
seo-description: Puoi inviare segnali e recuperare segmenti di visitatori da Gestione dell'audience.
seo-title: Configurazione di Audience Manager
solution: Marketing Cloud,Analytics
title: Configurazione di Audience Manager
topic: Sviluppatore e implementazione
uuid: f68d5b2e-fa2c-4db6-98ad-d1855a2c45ac
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Audience Manager configuration{#audience-manager-configuration}

Puoi inviare segnali e recuperare segmenti di visitatori da Audience Manager.

## Set the application context {#section_37CAE496FF894FCA821F7760605574CA}

**(Required)** The `setContext()` method must be called once in the `onCreate()` method of your main activity.

Di seguito è riportato un esempio di codice per questo metodo:

```java
@Override 
public void onCreate(Bundle savedInstanceState) { 
  super.onCreate(savedInstanceState); 
  setContentView(R.layout.main); 
  Config.setContext(this.getApplicationContext()); 
}
```

Se hai aggiunto questa chiamata del metodo quando hai implementato Analytics o Target, non devi aggiungerla di nuovo.
