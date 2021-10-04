---
description: Il valore "lifetime" permette di misurare e impostare come destinazione un valore del ciclo di vita per ogni utente.
solution: Experience Cloud,Analytics
title: Valore "lifetime" del ciclo di vita del visitatore
topic-fix: Developer and implementation
uuid: d830d18b-4313-43bb-8d75-3789869d0f1d
exl-id: f1b684b1-9919-400d-a88a-6d4a0809d9e1
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 100%

---

# Valore &quot;lifetime&quot; del ciclo di vita del visitatore {#visitor-lifetime-value}

Il valore &quot;lifetime&quot; permette di misurare e impostare come destinazione un valore del ciclo di vita per ogni utente.

Ogni volta che viene inviato un valore con `trackLifetimeValueIncrease`, tale valore viene aggiunto a quello esistente. Il valore &quot;lifetime&quot; del ciclo di vita è memorizzato nel dispositivo e può essere recuperato in qualsiasi momento con una chiamata `lifetimeValue`. È utile per memorizzare gli acquisti, le visualizzazioni di annunci, la visione completa di un video, le condivisioni social, i caricamenti di foto, ecc. nel corso del ciclo di vita.

## Tracciare il valore del ciclo di vita del visitatore {#section_390943A49AF841F2941E65D6DF2B3F5A}

1. Aggiungi la libreria al tuo progetto e implementa le funzioni di ciclo di vita (lifecycle).

   Per ulteriori informazioni, consulta *Aggiungere l’SDK e il file di configurazione al progetto* in [Implementazione e ciclo di vita di base](/help/ios/getting-started/dev-qs.md).
1. Importa la libreria:

   ```objective-c
   import com.adobe.mobile.*;
   ```

1. Invoca `trackLifetimeValueIncrease` con l&#39;incremento da aggiungere al valore:

   ```objective-c
   [ADBMobile trackLifetimeValueIncrease:increaseAmount data:nil];
   ```

## Inviare dati aggiuntivi {#section_3EBE813E54A24F6FB669B2478B5661F9}

Oltre al valore &quot;lifetime&quot; del ciclo di vita, con ogni chiamata di tracciamento delle azioni puoi inviare anche dati di contesto aggiuntivi:

```objective-c
NSMutableDictionary *contextData = [NSMutableDictionary dictionary]; 
[contextData setObject:imageName forKey:@"myapp.ImageLiked"]; 
[ADBMobile trackLifetimeValueIncrease:increaseAmount data:contextData];
```

I valori dei dati contestuali devono essere mappati su variabili personalizzate:

![](assets/map-variable-context-ltv.png)
