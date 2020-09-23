---
description: Le azioni temporizzate consentono di misurare il tempo trascorso in-app e il tempo totale tra l'inizio e la fine di un'azione. L’SDK calcola il tempo necessario per completare l’azione in ogni sessione e complessivamente in più sessioni. Puoi usare le azioni temporizzate per definire i segmenti e confrontare il tempo necessario per effettuare un acquisto, per passare al livello successivo, per le fasi del checkout e così via.
seo-description: Le azioni temporizzate consentono di misurare il tempo trascorso in-app e il tempo totale tra l'inizio e la fine di un'azione. L’SDK calcola il tempo necessario per completare l’azione in ogni sessione e complessivamente in più sessioni. Puoi usare le azioni temporizzate per definire i segmenti e confrontare il tempo necessario per effettuare un acquisto, per passare al livello successivo, per le fasi del checkout e così via.
seo-title: Azioni temporizzate
solution: Experience Cloud,Analytics
title: Azioni temporizzate
topic: Developer and implementation
uuid: 5a48a580-b942-4e49-9f1b-078fea7fccdb
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 49%

---


# Azioni temporizzate {#timed-actions}

Le azioni temporizzate consentono di misurare il tempo trascorso in-app e il tempo totale tra l&#39;inizio e la fine di un&#39;azione. L’SDK calcola il tempo necessario per completare l’azione in ogni sessione e complessivamente in più sessioni. Puoi usare le azioni temporizzate per definire i segmenti e confrontare il tempo necessario per effettuare un acquisto, per passare al livello successivo, per le fasi del checkout e così via.

Per le azioni temporizzate vengono riportate le metriche seguenti:

* Numero totale di secondi trascorsi nell&#39;app tra avvio e fine (sessioni diverse)
* Numero totale di secondi tra inizio e fine (tempo di clock)

Una callback facoltativa consente di eseguire azioni aggiuntive al completamento dell’azione temporizzata:

* Eseguire il codice e aggiungere qualsiasi logica - logica personalizzata facoltativa basata sui risultati della durata.
* Aggiungere dati contestuali prima di passare le durate.
* Annulla hit e durate non ancora inviate.

## Tracciare le azioni temporizzate {#section_FF5B1EDC1A5340A5B13BC0F1BF2E13E1}

1. Aggiungi la libreria al tuo progetto e implementa le funzioni di ciclo di vita (lifecycle).

   Per ulteriori informazioni, consulta *Aggiungere l’SDK e il file di configurazione al progetto IntelliJ IDEA o Eclipse* in [Implementazione e ciclo di vita di base](/help/android/getting-started/dev-qs.md).
1. Importa la libreria:

   ```java
   import com.adobe.mobile.*;
   ```

1. Invoca `trackTimedActionStart` e fornisci il nome di un&#39;azione temporizzata ed eventuali dati contestuali.

   ```java
   HashMap cdata = new HashMap<String, Object>(); 
   cdata.put("ExperienceName", experience); 
   Analytics.trackTimedActionStart("TimeUntilPurchase", cdata);
   ```

1. (Facoltativo) In qualsiasi momento, puoi invocare `trackTimedActionUpdate` con il nome dell&#39;azione temporizzata per aggiungere dati di contesto aggiuntivi.

   ```java
   HashMap cdata = new HashMap<String, Object>(); 
   cdata.put("myapp.ImageLiked", imageName); 
   Analytics.trackTimed​ActionUpdate("TimeUntilPurchase", cdata);
   ```

1. Al completamento dell&#39;evento, invoca `trackTimedActionEnd` e passa il nome dell&#39;azione temporizzata e `TimedActionBlock` (callback) che controlleranno tutti i dati e le durate calcolate.

   ```java
   Analytics.trackTimedActionEnd("TimeUntilPurchase", cdata);
   ```

   Le metriche degli eventi temporizzati vengono salvate come le variabili della soluzione mobile a scopo di reportistica automatica.

## Invio di dati aggiuntivi {#section_3EBE813E54A24F6FB669B2478B5661F9}

Oltre al nome dell&#39;azione temporizzata, con le chiamate di inizio azione e aggiornamento azione puoi inviare anche dati di contesto aggiuntivi:

```java
HashMap cdata = new HashMap<String, Object>(); 
cdata.put("myapp.ImageLiked", imageName); 
Analytics.trackTimed​ActionUpdate("TimeUntilPurchase", cdata);
```

I valori dei dati contestuali devono essere mappati su variabili personalizzate in Adobe Mobile Services:

![](assets/map-variable-context-ltv.png)

## Esempi {#section_7BA344B8BD4F48DCBAE27AC9320CBCEA}

```java
// Timed Action Start Example 
HashMap cdata = new HashMap<String, Object>(); 
cdata.put("ExperienceName", experience); 
Analytics.trackTimedActionStart("TimeUntilPurchase", cdata); 
 
// Timed Action Update Example 
cdata = new HashMap<String, Object>(); 
cdata.put("ImageLiked", imageName); 
Analytics.trackTimed​ActionUpdate("TimeUntilPurchase", cdata); 
 
// Timed Action End Example 
Analytics.trackTimedActionEnd("TimeUntilPurchase", null); 
 
// Timed Action End Example with Callback 
Analytics.trackTimedActionEnd("TimeUntilPurchase", new Analytics.TimedActionBlock<Boolean>() { 
 @Override 
 public Boolean call(long inAppDuration, long totalDuration, Map<String, Object> contextData) { 
  contextData.put("PurchaseItem", "Item453"); 
  return true; // return true to send the hit, false to cancel 
 } 
});
```

