---
description: Puoi fornire contenuto mirato nelle applicazioni Android.
keywords: android,libreria,mobile,sdk
seo-description: Puoi fornire contenuto mirato nelle applicazioni Android.
seo-title: Configurazione di Target
solution: Experience Cloud,Analytics
title: Configurazione di Target
topic: Sviluppatore e implementazione
uuid: 09fe2c9c-7b60-49c3-bb9d-36a30ce7c350
translation-type: ht
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Configurazione di Target {#target-configuration}

Puoi fornire contenuto mirato nelle applicazioni Android.

## Impostare il contesto dell'applicazione {#section_37CAE496FF894FCA821F7760605574CA}

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

Se hai già aggiunto questa chiamata del metodo quando hai implementato Analytics o Gestione dell'audience, non devi aggiungerla nuovamente.
