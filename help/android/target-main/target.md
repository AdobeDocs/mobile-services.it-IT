---
description: Puoi fornire contenuto mirato nelle applicazioni Android.
keywords: android,libreria,mobile,sdk
seo-description: Puoi fornire contenuto mirato nelle applicazioni Android.
seo-title: Configurazione di Target
solution: Experience Cloud,Analytics
title: Configurazione di Target
topic-fix: Developer and implementation
uuid: 09fe2c9c-7b60-49c3-bb9d-36a30ce7c350
exl-id: dbcc3114-e76b-4b18-a418-ac46a21a593e
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '76'
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
