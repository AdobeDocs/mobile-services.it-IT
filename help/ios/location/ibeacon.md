---
description: Il tracciamento iBeacon consente di misurare e indirizzare come destinazioni micro posizioni utilizzando le tecnologie iBeacon e Low Energy Bluetooth.
seo-description: Il tracciamento iBeacon consente di misurare e indirizzare come destinazioni micro posizioni utilizzando le tecnologie iBeacon e Low Energy Bluetooth.
seo-title: Tracciamento iBeacon
solution: Experience Cloud,Analytics
title: Tracciamento iBeacon
topic: Developer and implementation
uuid: 390883db-027e-4d12-8a16-86d514579db1
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 100%

---


# Tracciamento iBeacon {#ibeacon-tracking}

Il tracciamento iBeacon consente di misurare e indirizzare come destinazioni micro posizioni utilizzando le tecnologie iBeacon e Low Energy Bluetooth.

Quando viene invocato `trackBeacon`, i seguenti dati beacon vengono inviati ad Analytics e Target:

* `a.beacon.uuid` - ProximityUUID del beacon.
* `a.beacon.major` - numero principale del beacon, ad esempio numero del negozio.
* `a.beacon.minor` - numero secondario del beacon, ad esempio un numero univoco nel negozio.
* `a.beacon.prox` - i seguenti valori rappresentano la distanza dell&#39;utente dal beacon:

   * `0`: distanza sconosciuta
   * `1`: nelle immediate vicinanze
   * `2`: nelle vicinanze
   * `3`: distante

## Tracciare iBeacon {#section_FC3F213545944A468B1E6D5D5C8E2F1F}

1. Aggiungi la libreria al tuo progetto e implementa le funzioni di ciclo di vita (lifecycle).

   Per ulteriori informazioni, consulta *Aggiungere l’SDK e il file di configurazione al progetto* in [Implementazione e ciclo di vita di base](/help/ios/getting-started/dev-qs.md).
1. Importa la libreria:

   ```objective-c
   #import "ADBMobile.h"
   ```

1. Quando un dispositivo si trova nelle vicinanze di un beacon, invoca `trackBeacon`:

   ```objective-c
   [ADBMobile trackBeacon:beacon data:nil];
   ```

1. Quando l&#39;utente lascia le vicinanze del beacon, cancella il beacon corrente:

   ```objective-c
   [ADBMobile trackingClearCurrentBeacon];
   ```

## Inviare dati aggiuntivi {#section_3EBE813E54A24F6FB669B2478B5661F9}

Oltre al nome dell&#39;azione temporizzata, con ogni chiamata di tracciamento puoi inviare anche dati di contesto aggiuntivi:

```objective-c
[ADBMobile trackBeacon:beacon data:@{@"myapp.ImageLiked" : imageName}];
```

I valori dei dati contestuali devono essere mappati su variabili personalizzate:

![](assets/map-variable-context-ltv.png)

## Esempi {#section_9749238BCBC148998CB18E97D7670D19}

```objective-c
- (void)locationManager:(CLLocationManager *)manager didRangeBeacons:(NSArray *)beacons inRegion:(CLBeaconRegion *)region { 
    if (beacons.count > 0) { 
        CLBeacon *beacon = beacons[0]; 
        // Adobe - track when in range of a beacon 
        [ADBMobile trackBeacon:beacon data:@{@"sampleContextData" : @"sampleContextDataVal"}]; 
    } 
} 
 
// When the user leaves the proximity of the beacon, clear the current beacon 
[ADBMobile trackingClearCurrentBeacon];
```

