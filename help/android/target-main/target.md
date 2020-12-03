---
description: Puoi fornire contenuto mirato nelle applicazioni Android.
keywords: android;library;mobile;sdk
seo-description: Puoi fornire contenuto mirato nelle applicazioni Android.
seo-title: Configurazione di Target
solution: Experience Cloud,Analytics
title: Configurazione di Target
topic: Developer and implementation
uuid: 09fe2c9c-7b60-49c3-bb9d-36a30ce7c350
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '72'
ht-degree: 100%

---


# Configurazione di Target {#target-configuration}

Puoi fornire contenuto mirato nelle applicazioni Android.

## Impostare il contesto dell&#39;applicazione {#section_37CAE496FF894FCA821F7760605574CA}

**(Obbligatorio)** Il metodo `setContext()` deve essere chiamato una volta nel metodo `onCreate()` della tua attività principale.

Ad esempio:

```java
@Override 
public void onCreate(Bundle savedInstanceState) { 
  super.onCreate(savedInstanceState); 
  setContentView(R.layout.main); 
  Config.setContext(this.getApplicationContext()); 
}
```

Se hai già aggiunto questa chiamata del metodo quando hai implementato Analytics o Gestione dell&#39;audience, non devi aggiungerla nuovamente.
