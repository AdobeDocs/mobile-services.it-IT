---
description: Le geolocalità permette di misurare i dati relativi alla posizione utilizzando latitudine e longitudine e punti di interesse predefiniti nelle app iOS.
seo-description: Le geolocalità permette di misurare i dati relativi alla posizione utilizzando latitudine e longitudine e punti di interesse predefiniti nelle app iOS.
seo-title: Geolocalità e punti di interesse
solution: Marketing Cloud, Analytics
title: Geolocalità e punti di interesse
topic: Sviluppatore e implementazione
uuid: c 800 ec 85-a 33 f -425 d-b 28 f-bfe 8 bf 229 ae 8
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Geo-location and points of interest {#geo-location-and-points-of-interest}

Le geolocalità permette di misurare i dati relativi alla posizione utilizzando latitudine e longitudine e punti di interesse predefiniti nelle app iOS.

Ogni chiamata `trackLocation` invia i seguenti dati:

* Latitudine, longitudine e posizione in un punto di interesse (POI) definito in Adobe Mobile Services.

   Questi dati vengono passati alle variabili della soluzione mobile a scopo di reportistica automatica.

* Distanza dal centro e precisione passate come dati contestuali.

   Queste variabili non vengono acquisite automaticamente. You must map these context data variables by using the instructions in *Sending Additional Data* section below.

## Aggiornamenti POI dinamici {#section_3747B310DD5147E2AAE915E762997712}

A partire dalla versione 4.2, i punti di interesse (POI) sono definiti nell'interfaccia di Adobe Mobile e sincronizzati dinamicamente con il file di configurazione dell'app. This synchronization requires an `analytics.poi` setting in the `ADBMobile.json` file:

```js
“analytics.poi”: “https://assets.adobedtm.com/…/yourfile.json”,
```

Per ulteriori informazioni, vedi [Configurazione adbmobile JSON](/help/ios/configuration/json-config/json-config.md).

Se non è configurata, devi scaricare e aggiungere all'app una versione aggiornata del file `ADBMobile.json`. Per ulteriori informazioni e istruzioni, *vedi Scaricare l'SDK e gli strumenti di test* in [prima di iniziare](/help/ios/getting-started/requirements.md).

## Tracciare geolocalità e POI {#section_B1616E400A7548F9A672F97FEC75AE27}

1. Aggiungi la libreria al tuo progetto e implementa le funzioni di ciclo di vita (lifecycle).

   Per ulteriori informazioni, vedi *Aggiungere l'SDK e il file di configurazione al progetto* in [Implementazione e ciclo di vita di base](/help/ios/getting-started/dev-qs.md).
1. Importa la libreria:

   ```objective-c
   #import "ADBMobile.h"
   ```

1. Invoca `trackLocation` per tenere traccia della posizione corrente:

   ```objective-c
   CLLocation *currentLocation = location; 
   [ADBMobile trackLocation: currentLocation data: nil]; 
   ```

   >[!TIP]
   >
   >You can call `trackLocation` at any time.

   Per determinare la posizione che viene passata alla `trackLocation` chiamata, utilizza [la posizione utente](https://developer.apple.com/Library/ios/documentation/UserExperience/Conceptual/LocationAwarenessPG/CoreLocation/CoreLocation.html).

Inoltre, se la posizione è determinata entro il raggio definito per un POI, con l'hit `a.loc.poi` viene inviata una variabile di dati di contesto `trackLocation` che viene inserita come POI nei rapporti sulla posizione. Viene inoltre inviata una variabile di dati contestuali `a.loc.dist`, con la distanza (in metri) dalle coordinate definite.

## Send additional data {#section_3EBE813E54A24F6FB669B2478B5661F9}

Oltre ai dati sulla posizione, con ogni chiamata di tracciamento della posizione puoi inviare anche dati di contesto aggiuntivi:

```objective-c
NSMutableDictionary *contextData = [NSMutableDictionary dictionary]; 
[contextData setObject:@"GPS" forKey:@"myapp.location.LocationSource"]; 
[ADBMobile trackLocation: currentLocation data:contextData];
```

I valori dei dati contestuali devono essere mappati su variabili personalizzate:

![](assets/map-location-context-data.png)

## Location context data {#section_FFB71E6653F9410A89CC6ACC0C9164A9}

I dati di latitudine e longitudine vengono inviati utilizzando in totale sei parametri di dati di contesto: tre diversi parametri di dati contestuali per ciascuno, ognuno dei quali rappresenta un diverso livello di precisione.

Ad esempio, le coordinate "lat = 40.93231, lon = -111.93152" rappresentano una posizione con precisione di 1 m. Questa viene divisa in base al livello di precisione nelle seguenti variabili:

* `a.loc.lat.a`= 040.9
* `a.loc.lat.b` = 32
* `a.loc.lat.c` = 31
* `a.loc.lon.a` = -111.9
* `a.loc.lon.b` = 31
* `a.loc.lon.c` = 52

Alcuni livelli di precisione potrebbe essere riportati come "00", a seconda dell'accuratezza della posizione corrente. Ad esempio, se la posizione ha un livello di precisione di 100 m, `a.loc.lat.c` e `a.loc.lon.c` saranno pari a "00".

## Informazioni aggiuntive {#section_931AC1E0D88147E29FE1B6E3CC1E9550}

Considerazioni da ricordare:

* A `trackLocation` request sends in the equivalent of a `trackAction` call.

* I POI non vengono passati in normali chiamate `trackAction` e `trackState`; per tenere traccia dei POI devi quindi usare una chiamata `trackLocation`.

* La chiamata `trackLocation` deve essere invocata ogni volta che sia necessario per tenere traccia di posizione e POI.

   Consigliamo di invocare `trackLocation` all'avvio dell'app e quindi in base alle esigenze, secondo i requisiti dell'applicazione.

* I POI vengono compilati solo dopo essere stati definiti nel file di configurazione dell'app.

   Non vengono applicati a chiamate `trackLocation` storiche precedentemente inviate.
* Le chiamate `trackLocation` supportano l'invio di dati di contesto aggiuntivi, in modo analogo alle chiamate `trackAction`.

* Quando i diametri di due POI si sovrappongono, viene usato il primo POI che contiene la posizione corrente.

   Se devi usare dei POI che si sovrappongono, elencali in ordine dal più dettagliato al meno dettagliato, per fare sì che venga trasmesso quello più dettagliato.

