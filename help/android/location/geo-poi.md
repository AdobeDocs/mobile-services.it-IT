---
description: La geolocalità consente di misurare i dati sulla posizione mediante latitudine e longitudine e punti di interesse predefiniti nelle app Android.
seo-description: La geolocalità consente di misurare i dati sulla posizione mediante latitudine e longitudine e punti di interesse predefiniti nelle app Android.
seo-title: Geo-Location and points of interest
solution: Marketing Cloud,Analytics
title: Geolocalità e punti di interesse
topic: Sviluppatore e implementazione
uuid: b8209370-cbc4-40f9-97d8-017e2d74a377
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Geo-location and points of interest {#geo-location-and-points-of-interest}

La geolocalità consente di misurare i dati sulla posizione mediante latitudine e longitudine e punti di interesse predefiniti nelle app Android.

Ciascuna chiamata `trackLocation` invia le informazioni seguenti:

* Latitudine, longitudine e posizione in un punto di interesse (POI) che è definito nell'interfaccia utente di Adobe Mobile Services.

   Questi dati vengono passati alle variabili della soluzione mobile a scopo di reportistica automatica.

* Distanza dal centro e precisione passate come dati contestuali.

   Queste variabili non vengono acquisite automaticamente. You must map these context data variables by using the instructions in the *Sending Additional Data* section below.

## Aggiornamenti POI dinamici {#section_3747B310DD5147E2AAE915E762997712}

A partire della versione 4.2, i POI sono definiti nell'interfaccia di Adobe Mobile e sincronizzati in modo dinamico con il file di configurazione dell'app. This synchronization requires an `analytics.poi` setting in the [ADBMobile JSON Config](/help/android/configuration/json-config/json-config.md):

```js
“analytics.poi”: “https://assets.adobedtm.com/…/yourfile.json”,
```

Se questa configurazione non è presente, devi scaricare una versione aggiornata del file `ADBMobile.json` e aggiungerla all'app. For more information, see Download the SDK and Testing Tools.[](/help/android/getting-started/requirements.md)

## Tracking geo-location and POIs {#section_B1616E400A7548F9A672F97FEC75AE27}

1. Aggiungi la libreria al tuo progetto e implementa le funzioni di ciclo di vita (lifecycle).

   For more information, see Add the SDK and Config File to your IntelliJ IDEA or Eclipse Project in Core implementation and lifecycle.**[](/help/android/getting-started/dev-qs.md)

1. Importa la libreria:

   ```java
   import com.adobe.mobile.*;
   ```

1. Invoca `trackLocation` per tenere traccia della posizione corrente:

   ```java
   Location currentLocation = new Location("my location here"); 
   Analytics.trackLocation(currentLocation, null);
   ```

   >[!TIP]
   >
   >You can call `trackLocation` at any time.

   You can use location strategies to determine the location that is passed to the `trackLocation` call. For more information, see [Android Location Strategies](https://developer.android.com/guide/topics/location/strategies.html).

Inoltre, se la posizione è determinata essere nel raggio di un POI definito, una variabile di dati di contesto `a.loc.poi` viene inviata con l'hit `trackLocation` e indicata come POI nei rapporti di **dettaglio della posizione**. Viene inoltre inviata una variabile di dati contestuali `a.loc.dist`, con la distanza (in metri) dalle coordinate definite.

## Sending additional data {#section_3EBE813E54A24F6FB669B2478B5661F9}

Oltre ai dati sulla posizione, con ogni chiamata di tracciamento della posizione puoi inviare anche dati di contesto aggiuntivi:

```java
HashMap<String, Object> locationContextData = new HashMap<String, Object>(); 
locationContextData.put("myapp.location.LocationSource", "GPS"); 
 
Location currentLocation = new Location("my location here"); 
Analytics.trackLocation(currentLocation, locationContextData);
```

I valori dei dati contestuali devono essere mappati su variabili personalizzate nell'interfaccia utente di Adobe Mobile Services:

![](assets/map-location-context-data.png)

## Location context data {#section_FFB71E6653F9410A89CC6ACC0C9164A9}

Latitudine e longitudine vengono inviati usando tre diversi parametri di dati contestuali, dove ciascun parametro rappresenta un diverso livello di precisione, per un totale di sei parametri di dati contestuali.

Ad esempio, le coordinate lat = 40.93231, long = -111.93152 rappresentano una posizione con precisione di 1 m. Questa viene divisa in base al livello di precisione nelle seguenti variabili:

`a.loc.lat.a`= 040.9

`a.loc.lat.b` = 32

`a.loc.lat.c` = 31

`a.loc.lon.a` = -111.9

`a.loc.lon.b` = 31

`a.loc.lon.c` = 52

Alcuni livelli di precisione possono apparire come `00` in base alla precisione della posizione attuale. Ad esempio, se la posizione ha un livello di precisione di 100 m, `a.loc.lat.c` e `a.loc.lon.c` saranno pari a `00`.

Considerazioni da ricordare:

* A `trackLocation` request sends in the equivalent of a `trackAction` call.

* I POI non sono passati nell'ambito di chiamate `trackAction` e `trackState` tipiche, pertanto devi usare una chiamata `trackLocation` per tracciare i POI.

* La chiamata `trackLocation` deve essere invocata ogni volta che sia necessario per tenere traccia di posizione e POI.

   Consigliamo di chiamare `trackLocation` all'avvio dell'app e quindi quando necessario, in base ai requisiti dell'app.

* I POI sono popolati solo dopo essere stati definiti nel file di configurazione dell'app.

   I POI non vengono applicati a chiamate `trackLocation` storiche inviate in precedenza.
* Le chiamate `trackLocation` supportano l'invio di dati di contesto aggiuntivi, in modo analogo alle chiamate `trackAction`.

* Quando i diametri di due POI si sovrappongono, viene usato il primo POI che contiene la posizione corrente.

   Se devi usare dei POI che si sovrappongono, elencali in ordine dal più dettagliato al meno dettagliato, per fare sì che venga trasmesso quello più dettagliato.

