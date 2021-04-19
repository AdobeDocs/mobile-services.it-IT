---
description: Le azioni temporizzate consentono di misurare il tempo trascorso in-app e il tempo totale dall’inizio alla fine di un’azione. L’SDK calcola il tempo di una sessione e il tempo totale (per più sessioni) necessario per completare l’azione. Puoi usare le azioni temporizzate per definire i segmenti e confrontare il tempo necessario per effettuare un acquisto, per passare al livello successivo, per le fasi del checkout e così via.
seo-description: Le azioni temporizzate consentono di misurare il tempo trascorso in-app e il tempo totale dall’inizio alla fine di un’azione. L’SDK calcola il tempo di una sessione e il tempo totale (per più sessioni) necessario per completare l’azione. Puoi usare le azioni temporizzate per definire i segmenti e confrontare il tempo necessario per effettuare un acquisto, per passare al livello successivo, per le fasi del checkout e così via.
seo-title: Azioni temporizzate
solution: Experience Cloud,Analytics
title: Azioni temporizzate
topic-fix: Developer and implementation
uuid: dbcbac5a-6345-49f6-b050-0db05292f005
exl-id: 3499766b-55f6-4861-8291-2269d56ba983
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 100%

---

# Azioni temporizzate {#timed-actions}

Le azioni temporizzate consentono di misurare il tempo trascorso in-app e il tempo totale dall’inizio alla fine di un’azione. L’SDK calcola il tempo di una sessione e il tempo totale (per più sessioni) necessario per completare l’azione. Puoi usare le azioni temporizzate per definire i segmenti e confrontare il tempo necessario per effettuare un acquisto, per passare al livello successivo, per le fasi del checkout e così via.

Per le azioni temporizzate vengono riportate le metriche seguenti:

* Numero totale di secondi trascorsi nell’app dall’inizio alla fine, per più sessioni
* Numero totale di secondi dall’inizio alla fine (in base all’ora effettiva)

Una callback facoltativa consente di eseguire azioni aggiuntive al completamento dell’azione temporizzata:

* Eseguire il codice e aggiungere qualsiasi logica; logica personalizzata facoltativa in base ai risultati della durata.
* Aggiungere dati contestuali prima di passare le durate.
* Annullare l’hit e le durate non ancora inviate.

## Tracciamento delle azioni temporizzate {#section_FF5B1EDC1A5340A5B13BC0F1BF2E13E1}

1. Aggiungi la libreria al tuo progetto e implementa le funzioni di ciclo di vita (lifecycle).

   Per ulteriori informazioni, consulta *Aggiungere l’SDK e il file di configurazione al progetto* in [Implementazione e ciclo di vita di base](/help/ios/getting-started/dev-qs.md).
1. Importa la libreria:

   ```objective-c
   #import "ADBMobile.h"
   ```

1. Invoca `trackTimedActionStart` e fornisci il nome di un&#39;azione temporizzata ed eventuali dati contestuali.

   ```objective-c
   [ADBMobile trackTimedActionStart:@"TimeUntilPurchase"  
                               data:@{@"ExperienceName" : experience}];
   ```

1. (Facoltativo) Per aggiungere dati di contesto aggiuntivi in qualsiasi momento, puoi invocare `trackTimedActionUpdate` con il nome dell&#39;azione temporizzata.

   ```objective-c
   [ADBMobile trackTimedActionUpdate:@"TimeUntilPurchase"  
                                data:@{@"myapp.ImageLiked" : imageName}];
   ```

1. Al completamento dell&#39;evento, invoca `trackTimedActionEnd` e passa il nome dell&#39;azione temporizzata e `TimedActionBlock` (callback) che controlleranno tutti i dati e le durate calcolate.

   Le metriche degli eventi temporizzati vengono salvate come le variabili della soluzione mobile a scopo di reportistica automatica.

   ```objective-c
   [ADBMobile trackTimedActionEnd:@"TimeUntilPurchase"  
                            logic:nil];
   ```

## Invio di dati aggiuntivi {#section_3EBE813E54A24F6FB669B2478B5661F9}

Oltre al nome dell&#39;azione temporizzata, con le chiamate di inizio azione e aggiornamento azione puoi inviare anche dati di contesto aggiuntivi:

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
