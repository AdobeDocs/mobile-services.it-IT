---
description: Per “azioni” si intendono gli eventi che si verificano nell'app Android oggetto delle misurazioni.
seo-description: Per “azioni” si intendono gli eventi che si verificano nell'app Android oggetto delle misurazioni.
seo-title: Tracciamento delle azioni dell'app
solution: Marketing Cloud, Analytics
title: Tracciamento delle azioni dell'app
topic: Sviluppatore e implementazione
uuid: fe 01 c 1 df-f 6 bb -4 b 32-b 3 ef -959 d 2 c 724 af 6
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Track app actions {#track-app-actions}

Per “azioni” si intendono gli eventi che si verificano nell'app Android oggetto delle misurazioni.

A ogni azione corrispondono una o più metriche che vengono incrementate ogni volta che si verifica l'evento. Ad esempio, puoi inviare una chiamata `trackAction` per ciascun nuovo abbonamento, ogni volta che viene visualizzato un articolo oppure ogni volta che viene completato un livello. Le azioni non vengono tracciate automaticamente, pertanto devi chiamare `trackAction` quando si verifica un evento che desideri tracciare e mappare l'azione a un evento personalizzato.

## Tracking actions {#section_380DF56C4EE4432A823940E4AE4C9E91}

1. Aggiungi la libreria al tuo progetto e implementa le funzioni di ciclo di vita (lifecycle).

   Per ulteriori informazioni, vedi *Aggiungere l'SDK e il file di configurazione al progetto intellij IDEA o Eclipse* nell'implementazione [e nel ciclo di vita principali](/help/android/getting-started/dev-qs.md).

1. Importa la libreria:

   ```java
   import com.adobe.mobile.*;
   ```

1. Quando l'azione da tracciare si verifica nell'app, invoca `trackAction` per inviare un hit per questa azione:

   ```java
   Analytics.trackAction("myapp.ActionName", null);
   ```

1. Nell'interfaccia utente di Adobe Mobile Services, seleziona l'app e fai clic su **[!UICONTROL Gestione impostazioni app]**.
1. Fai clic su **[!UICONTROL Gestione variabili e metriche]** e quindi sulla scheda **Metriche personalizzate[!UICONTROL .]**

1. Mappa su un evento personalizzato il nome dei dati contestuali definito nel codice, ad esempio `myapp.ActionName`.

   ![](assets/map-event-context-data.png)

Puoi anche impostare un prop che contenga tutti i valori delle azioni mediante la mappatura di un prop personalizzato con un nome come **[!UICONTROL Azioni personalizzate]** e l'impostazione del valore su `a.action`.

![](assets/map-custom-prop.png)

## Sending additional data {#section_3EBE813E54A24F6FB669B2478B5661F9}

Oltre al nome dell'azione, con ogni chiamata di tracciamento delle azioni puoi inviare anche dati di contesto aggiuntivi:

```java
HashMap<String, Object> exampleContextData = new HashMap<String, Object>(); 
exampleContextData.put("myapp.social.SocialSource", "Twitter"); 
Analytics.trackAction("myapp.SocialShare", exampleContextData);
```

I valori dei dati contestuali devono essere mappati su variabili personalizzate in Adobe Mobile Services:

![](assets/map-variable-context-action.png)

## Action reporting {#section_0F6A54AB7A3F42C9BB042D86A0FC4630}

| Interfaccia | Rapporto |
|--- |--- |
| Adobe Mobile Services | **[!UICONTROL Rapporto Percorsi azione.]**  Visualizza l'ordine in cui si verificano le azioni nell'app. Puoi anche fare clic su **[!UICONTROL Personalizza]su qualsiasi rapporto per visualizzare le azioni in base a classifica, tendenze o dettagli, oppure puoi applicare un filtro per vedere le azioni relative a un dato segmento.** |
| Reporting e analisi di marketing | **[!UICONTROL Rapporto Evento personalizzato.]**  Dopo aver mappato un'azione su un evento personalizzato, puoi visualizzare gli eventi da app mobile in modo analogo a tutti gli altri eventi di Analytics. |
| Analisi ad hoc | **[!UICONTROL Rapporto Evento personalizzato.]**  Dopo aver mappato un'azione su un evento personalizzato, puoi visualizzare gli eventi da app mobile in modo analogo a tutti gli altri eventi di Analytics. |

