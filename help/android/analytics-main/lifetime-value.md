---
description: Il valore del ciclo di vita consente di misurare e focalizzare un valore dei ciclo di vita per ciascun utente Android. Il valore può essere utilizzato per archiviare gli acquisti del ciclo di vita, le visualizzazioni di annunci, i completamenti di video, le condivisioni su social network, i caricamenti di foto e così via.
seo-description: Il valore del ciclo di vita consente di misurare e focalizzare un valore dei ciclo di vita per ciascun utente Android. Il valore può essere utilizzato per archiviare gli acquisti del ciclo di vita, le visualizzazioni di annunci, i completamenti di video, le condivisioni su social network, i caricamenti di foto e così via.
seo-title: Valore "lifetime" del ciclo di vita del visitatore
solution: Experience Cloud,Analytics
title: Valore "lifetime" del ciclo di vita del visitatore
topic: Sviluppatore e implementazione
uuid: ba0308de-282e-46f9-a14c-19fb6d5c363e
translation-type: ht
source-git-commit: bf076aa8e59d5c3e634fc4ae21f0de0d4541a83f

---


# Valore "lifetime" del ciclo di vita del visitatore {#visitor-lifetime-value}

Il valore del ciclo di vita consente di misurare e focalizzare un valore dei ciclo di vita per ciascun utente Android. Il valore può essere utilizzato per archiviare gli acquisti del ciclo di vita, le visualizzazioni di annunci, i completamenti di video, le condivisioni su social network, i caricamenti di foto e così via.

Ogni volta che viene inviato un valore con `trackLifetimeValueIncrease`, tale valore viene aggiunto a quello esistente. Il valore "lifetime" del ciclo di vita è memorizzato nel dispositivo e può essere recuperato in qualsiasi momento con una chiamata `lifetimeValue`.

## Tracciare il valore del ciclo di vita del visitatore {#section_390943A49AF841F2941E65D6DF2B3F5A}

1. Aggiungi la libreria al tuo progetto e implementa le funzioni di ciclo di vita (lifecycle).

   Per ulteriori informazioni, consulta *Aggiungere l’SDK e il file di configurazione al progetto IntelliJ IDEA o Eclipse* in [Implementazione e ciclo di vita di base](/help/android/getting-started/dev-qs.md).
1. Importa la libreria:

   ```java
   import com.adobe.mobile.*;
   ```

1. Invoca `trackLifetimeValueIncrease` con l'incremento da aggiungere al valore:

   ```java
   Analytics.trackLifetimeValueIncrease(BigDecimal.valueOf(5.0), null);
   ```

## Inviare dati aggiuntivi {#section_3EBE813E54A24F6FB669B2478B5661F9}

Oltre al valore "lifetime" del ciclo di vita, con ogni chiamata di tracciamento delle azioni puoi inviare anche dati di contesto aggiuntivi:

```java
HashMap cdata = new HashMap<String, Object>(); 
cdata.put("myapp.ImageLiked", imageName); 
Analytics.trackLifetimeValueIncrease(BigDecimal.valueOf(5.0), cdata);
```

I valori dei dati contestuali devono essere mappati su variabili personalizzate in Adobe Mobile Services:

![](assets/map-variable-context-ltv.png)

