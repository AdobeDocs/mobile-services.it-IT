---
description: Le azioni temporizzate consentono di misurare il tempo trascorso all'interno dell'app e il tempo totale dall'inizio alla fine di un'azione. L'SDK calcola il tempo necessario a completare l'azione, per ogni sessione e complessivamente per più sessioni. Puoi usare le azioni temporizzate per definire i segmenti e confrontare il tempo necessario per effettuare un acquisto, per passare al livello successivo, per le fasi del checkout e così via.
seo-description: Le azioni temporizzate consentono di misurare il tempo trascorso all'interno dell'app e il tempo totale dall'inizio alla fine di un'azione. L'SDK calcola il tempo necessario a completare l'azione, per ogni sessione e complessivamente per più sessioni. Puoi usare le azioni temporizzate per definire i segmenti e confrontare il tempo necessario per effettuare un acquisto, per passare al livello successivo, per le fasi del checkout e così via.
seo-title: Azioni temporizzate
solution: Experience Cloud,Analytics
title: Azioni temporizzate
topic: Sviluppatore e implementazione
uuid: dbcbac5a-6345-49f6-b050-0db05292f005
translation-type: ht
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Azioni temporizzate {#timed-actions}

Le azioni temporizzate consentono di misurare il tempo trascorso all'interno dell'app e il tempo totale dall'inizio alla fine di un'azione. L'SDK calcola il tempo necessario a completare l'azione, per ogni sessione e complessivamente per più sessioni. Puoi usare le azioni temporizzate per definire i segmenti e confrontare il tempo necessario per effettuare un acquisto, per passare al livello successivo, per le fasi del checkout e così via.

Per le azioni temporizzate vengono riportate le metriche seguenti:

* Numero totale di secondi trascorsi nell'app tra avvio e fine, attraverso sessioni diverse
* Numero totale di secondi tra avvio e fine (tempo effettivo)

Un callback facoltativo consente di intraprendere azioni aggiuntive al completamento di un'azione temporizzata:

* Eseguire il codice e aggiungere eventuale logica - logica personalizzata opzionale basata sui risultati della durata.
* Aggiungere dati contestuali prima di passare le durate.
* Annullare l'hit e le durate non ancora inviate.

## Tracciamento delle azioni temporizzate {#section_FF5B1EDC1A5340A5B13BC0F1BF2E13E1}

1. Aggiungi la libreria al tuo progetto e implementa le funzioni di ciclo di vita (lifecycle).

   Per ulteriori informazioni, consulta *Aggiungere l’SDK e il file di configurazione al progetto* in [Implementazione e ciclo di vita di base](/help/ios/getting-started/dev-qs.md).
1. Importa la libreria:

   ```objective-c
   #import "ADBMobile.h"
   ```

1. Invoca `trackTimedActionStart` e fornisci il nome di un'azione temporizzata ed eventuali dati contestuali.

   ```objective-c
   [ADBMobile trackTimedActionStart:@"TimeUntilPurchase"  
                               data:@{@"ExperienceName" : experience}];
   ```

1. (Facoltativo) Per aggiungere dati di contesto aggiuntivi in qualsiasi momento, puoi invocare `trackTimedActionUpdate` con il nome dell'azione temporizzata.

   ```objective-c
   [ADBMobile trackTimedActionUpdate:@"TimeUntilPurchase"  
                                data:@{@"myapp.ImageLiked" : imageName}];
   ```

1. Al completamento dell'evento, invoca `trackTimedActionEnd` e passa il nome dell'azione temporizzata e `TimedActionBlock` (callback) che controlleranno tutti i dati e le durate calcolate.

   Le metriche degli eventi temporizzati vengono salvate come le variabili della soluzione mobile a scopo di reportistica automatica.

   ```objective-c
   [ADBMobile trackTimedActionEnd:@"TimeUntilPurchase"  
                            logic:nil];
   ```

## Invio di dati aggiuntivi {#section_3EBE813E54A24F6FB669B2478B5661F9}

Oltre al nome dell'azione temporizzata, con le chiamate di inizio azione e aggiornamento azione puoi inviare anche dati di contesto aggiuntivi:

```objective-c
[ADBMobile trackTimedActionUpdate:@"TimeUntilPurchase"  
                             data:@{@"myapp.ImageLiked" : imageName}];
```

I valori dei dati contestuali devono essere mappati su variabili personalizzate:

![](assets/map-variable-context-ltv.png)

## Esempio {#section_7BA344B8BD4F48DCBAE27AC9320CBCEA}

```objective-c
// Timed Action Start Example 
[ADBMobile trackTimedActionStart:@"TimeUntilPurchase"  
                            data:@{@"ExperienceName" : experience}];

// Timed Action Update Example 
[ADBMobile trackTimedActionUpdate:@"TimeUntilPurchase"  
                             data:@{@"ImageLiked" : imageName}];

// Timed Action End Example 
[ADBMobile trackTimedActionEnd:@"TimeUntilPurchase"  
                         logic:nil]; 
 
// Timed Action End Example with Callback 
[ADBMobile trackTimedActionEnd:@"TimeUntilPurchase"  
                         logic:^BOOL(NSTimeInterval inAppDuration,  
                                     NSTimeInterval totalDuration,  
                                     NSMutableDictionary *data) { 
                                        [data setObject:@"PurchaseItem" forKey:@"Item453"]; 
                                        return YES; //return YES to send the hit, NO to cancel 
                                     }];
```

