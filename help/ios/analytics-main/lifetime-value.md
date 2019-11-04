---
description: Il valore "lifetime" permette di misurare e impostare come destinazione un valore del ciclo di vita per ogni utente.
seo-description: Il valore "lifetime" permette di misurare e impostare come destinazione un valore del ciclo di vita per ogni utente.
seo-title: Valore "lifetime" del ciclo di vita del visitatore
solution: Experience Cloud,Analytics
title: Valore "lifetime" del ciclo di vita del visitatore
topic: Sviluppatore e implementazione
uuid: d830d18b-4313-43bb-8d75-3789869d0f1d
translation-type: ht
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Valore "lifetime" del ciclo di vita del visitatore {#visitor-lifetime-value}

Il valore "lifetime" permette di misurare e impostare come destinazione un valore del ciclo di vita per ogni utente.

Ogni volta che viene inviato un valore con `trackLifetimeValueIncrease`, tale valore viene aggiunto a quello esistente. Il valore "lifetime" del ciclo di vita è memorizzato nel dispositivo e può essere recuperato in qualsiasi momento con una chiamata `lifetimeValue`. È utile per memorizzare gli acquisti, le visualizzazioni di annunci, la visione completa di un video, le condivisioni social, i caricamenti di foto, ecc. nel corso del ciclo di vita.

## Tracciare il valore del ciclo di vita del visitatore {#section_390943A49AF841F2941E65D6DF2B3F5A}

1. Aggiungi la libreria al tuo progetto e implementa le funzioni di ciclo di vita (lifecycle).

   Per ulteriori informazioni, consulta *Aggiungere l’SDK e il file di configurazione al progetto* in [Implementazione e ciclo di vita di base](/help/ios/getting-started/dev-qs.md).
1. Importa la libreria:

   ```objective-c
   import com.adobe.mobile.*;
   ```

1. Invoca `trackLifetimeValueIncrease` con l'incremento da aggiungere al valore:

   ```objective-c
   [ADBMobile trackLifetimeValueIncrease:increaseAmount data:nil];
   ```

## Inviare dati aggiuntivi {#section_3EBE813E54A24F6FB669B2478B5661F9}

Oltre al valore "lifetime" del ciclo di vita, con ogni chiamata di tracciamento delle azioni puoi inviare anche dati di contesto aggiuntivi:

```objective-c
NSMutableDictionary *contextData = [NSMutableDictionary dictionary]; 
[contextData setObject:imageName forKey:@"myapp.ImageLiked"]; 
[ADBMobile trackLifetimeValueIncrease:increaseAmount data:contextData];
```

I valori dei dati contestuali devono essere mappati su variabili personalizzate:

![](assets/map-variable-context-ltv.png)

