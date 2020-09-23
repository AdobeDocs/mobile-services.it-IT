---
description: Puoi inviare segnali e recuperare segmenti di visitatori da Gestione dell'audience.
keywords: android;library;mobile;sdk
seo-description: Puoi inviare segnali e recuperare segmenti di visitatori da Gestione dell'audience.
seo-title: Configurazione di Audience Manager
solution: Experience Cloud,Analytics
title: Configurazione di Audience Manager
topic: Developer and implementation
uuid: f68d5b2e-fa2c-4db6-98ad-d1855a2c45ac
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '88'
ht-degree: 100%

---


# Configurazione di Audience Manager{#audience-manager-configuration}

Puoi inviare segnali e recuperare segmenti di visitatori da Audience Manager.

## Impostare il contesto dell&#39;applicazione {#section_37CAE496FF894FCA821F7760605574CA}

**(Obbligatorio)** Il metodo `setContext()` deve essere chiamato una volta nel metodo `onCreate()` della tua attività principale.

Di seguito è riportato un esempio di codice per questo metodo:

```java
@Override 
public void onCreate(Bundle savedInstanceState) { 
  super.onCreate(savedInstanceState); 
  setContentView(R.layout.main); 
  Config.setContext(this.getApplicationContext()); 
}
```

Se hai aggiunto questa chiamata del metodo quando hai implementato Analytics o Target, non devi aggiungerla nuovamente.
