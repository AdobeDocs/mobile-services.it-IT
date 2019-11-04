---
description: Le azioni temporizzate consentono di misurare il tempo trascorso all'interno dell'app e il tempo totale dall'inizio alla fine di un'azione. L'SDK calcola il tempo necessario a completare l'azione, per ogni sessione e complessivamente per più sessioni. Puoi usare le azioni temporizzate per definire i segmenti e confrontare il tempo necessario per effettuare un acquisto, per passare al livello successivo, per le fasi del checkout e così via.
seo-description: Le azioni temporizzate consentono di misurare il tempo trascorso all'interno dell'app e il tempo totale dall'inizio alla fine di un'azione. L'SDK calcola il tempo necessario a completare l'azione, per ogni sessione e complessivamente per più sessioni. Puoi usare le azioni temporizzate per definire i segmenti e confrontare il tempo necessario per effettuare un acquisto, per passare al livello successivo, per le fasi del checkout e così via.
seo-title: Azioni temporizzate
solution: Experience Cloud,Analytics
title: Azioni temporizzate
topic: Sviluppatore e implementazione
uuid: 5a48a580-b942-4e49-9f1b-078fea7fccdb
translation-type: ht
source-git-commit: 97c0dc17bcc624b38e9eb8023eb1d69d02568d11

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

## Tracciare le azioni temporizzate {#section_FF5B1EDC1A5340A5B13BC0F1BF2E13E1}

1. Aggiungi la libreria al tuo progetto e implementa le funzioni di ciclo di vita (lifecycle).

   Per ulteriori informazioni, consulta *Aggiungere l’SDK e il file di configurazione al progetto IntelliJ IDEA o Eclipse* in [Implementazione e ciclo di vita di base](/help/android/getting-started/dev-qs.md).
1. Importa la libreria:

   ```java
   import com.adobe.mobile.*;
   ```

1. Invoca `trackTimedActionStart` e fornisci il nome di un'azione temporizzata ed eventuali dati contestuali.

   ```java
   HashMap cdata = new HashMap<String, Object>(); 
   cdata.put("ExperienceName", experience); 
   Analytics.trackTimedActionStart("TimeUntilPurchase", cdata);
   ```

1. (Facoltativo) In qualsiasi momento, puoi invocare `trackTimedActionUpdate` con il nome dell'azione temporizzata per aggiungere dati di contesto aggiuntivi.

   ```java
   HashMap cdata = new HashMap<String, Object>(); 
   cdata.put("myapp.ImageLiked", imageName); 
   Analytics.trackTimed​ActionUpdate("TimeUntilPurchase", cdata);
   ```

1. Al completamento dell'evento, invoca `trackTimedActionEnd` e passa il nome dell'azione temporizzata e `TimedActionBlock` (callback) che controlleranno tutti i dati e le durate calcolate.

   ```java
   Analytics.trackTimedActionEnd("TimeUntilPurchase", cdata);
   ```

   Le metriche degli eventi temporizzati vengono salvate come le variabili della soluzione mobile a scopo di reportistica automatica.

## Invio di dati aggiuntivi {#section_3EBE813E54A24F6FB669B2478B5661F9}

Oltre al nome dell'azione temporizzata, con le chiamate di inizio azione e aggiornamento azione puoi inviare anche dati di contesto aggiuntivi:

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

