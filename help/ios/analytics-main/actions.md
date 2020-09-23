---
description: Per "azioni" si intendono gli eventi che si verificano nell’app e che desideri misurare. Ogni azione ha una o più metriche corrispondenti che vengono incrementate ogni volta che si verifica l'evento. Ad esempio, potete tenere traccia di una nuova iscrizione, ogni volta che viene visualizzato un articolo o ogni volta che viene completato un livello. Le metriche corrispondenti per questi eventi sono configurate come abbonamenti, articoli letti e livelli completati.
seo-description: Le azioni sono gli eventi che si verificano nell’app e che desideri misurare. Ogni azione ha una o più metriche corrispondenti che vengono incrementate ogni volta che si verifica l'evento. Ad esempio, potete tenere traccia di una nuova iscrizione, ogni volta che viene visualizzato un articolo o ogni volta che viene completato un livello. Le metriche corrispondenti per questi eventi sono configurate come abbonamenti, articoli letti e livelli completati.
seo-title: Tracciare le azioni eseguite nell'app
solution: Experience Cloud,Analytics
title: Tracciare le azioni eseguite nell'app
topic: Developer and implementation
uuid: 62017be1-5395-4d16-bde3-4c40a2c012d4
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '537'
ht-degree: 63%

---


# Tracciare le azioni eseguite nell&#39;app {#track-app-actions}

Le azioni sono gli eventi che si verificano nell’app e che desideri misurare. Ogni azione ha una o più metriche corrispondenti che vengono incrementate ogni volta che si verifica l&#39;evento. Ad esempio, potete tenere traccia di una nuova iscrizione, ogni volta che viene visualizzato un articolo o ogni volta che viene completato un livello. Le metriche corrispondenti per questi eventi sono configurate come abbonamenti, articoli letti e livelli completati.

Le azioni non vengono tracciate automaticamente, pertanto per tracciare un evento devi invocare `trackAction`.

## Tracciamento delle azioni {#section_380DF56C4EE4432A823940E4AE4C9E91}

1. Aggiungi la libreria al tuo progetto e implementa le funzioni di ciclo di vita (lifecycle).

   Per ulteriori informazioni, consulta *Aggiungere l’SDK e il file di configurazione al progetto* in [Implementazione e ciclo di vita di base](/help/ios/getting-started/dev-qs.md).
1. Importa la libreria.

   ```objective-c
   #import "ADBMobile.h"
   ```

1. Quando l&#39;azione da tracciare si verifica nell&#39;app, invoca `trackAction` per inviare un hit per questa azione.

   ```objective-c
   [ADBMobile trackAction:@"myapp.ActionName"  
                     data:nil];
   ```

   >[!TIP]
   >
   >In presenza di codice che potrebbe essere eseguito mentre l&#39;app è in background, usa `trackActionFromBackground` invece di `trackAction`.

1. Nell&#39;interfaccia utente di Adobe Mobile Services, seleziona l&#39;app e fai clic su **[!UICONTROL Gestioni impostazioni app]**.

1. Fai clic su **[!UICONTROL Gestione variabili e metriche]** e quindi sulla scheda **[!UICONTROL Metriche personalizzate]**.

1. Mappa su un evento personalizzato il nome dei dati contestuali definito nel codice, ad esempio `a.action=myapp.ActionName`.

   ![](assets/map-event-context-data.png)

Puoi anche impostare un prop che contenga tutti i valori delle azioni mediante la mappatura di un prop personalizzato con un nome come **[!UICONTROL Azioni personalizzate]** e l&#39;impostazione del valore su `a.action`.

![](assets/map-custom-prop.png)

## Invio di dati aggiuntivi {#section_3EBE813E54A24F6FB669B2478B5661F9}

Oltre al nome dell&#39;azione, con ogni chiamata di tracciamento delle azioni puoi inviare anche dati di contesto aggiuntivi:

```objective-c
NSMutableDictionary *contextData = [NSMutableDictionary dictionary]; 
[contextData setObject:@"Twitter" forKey:@"myapp.social.SocialSource"]; 
[ADBMobile trackAction:@"myapp.SocialShare" data:contextData];
```

I valori dei dati contestuali devono essere mappati su variabili personalizzate:

![](assets/map-variable-context-action.png)

## Tracciamento delle azioni in background {#section_AC13013F207D4FBAAF27E4412034251E}

Se tieni traccia di un&#39;azione nel codice che potrebbe venire eseguita quando l&#39;app funziona in background, invoca `trackActionFromBackground` invece di `trackAction`. `trackActionFromBackground` ha gli stessi parametri, ma contiene elementi di logica aggiuntiva per impedire che le chiamate &quot;lifecycle&quot; possano essere eseguite al momento sbagliato.

## Rapporti sulle azioni {#section_0F6A54AB7A3F42C9BB042D86A0FC4630}

| Interfaccia | Rapporto |
|--- |--- |
| Adobe Mobile Services | **[!UICONTROL Rapporto Percorsi azione]**. Visualizza l&#39;ordine in cui si verificano le azioni nell&#39;app. Puoi anche fare clic su **[!UICONTROL Personalizza]** su qualsiasi rapporto per visualizzare le azioni in base a classifica, tendenze o dettagli, oppure puoi applicare un filtro per vedere le azioni relative a un dato segmento. |
| Reporting e analisi di marketing | **[!UICONTROL Rapporto Evento personalizzato]**. Dopo aver mappato un&#39;azione su un evento personalizzato, puoi visualizzare gli eventi da app mobile in modo analogo a tutti gli altri eventi di Analytics. |
| Analisi ad hoc | **[!UICONTROL Rapporto Evento personalizzato]**. Dopo aver mappato un&#39;azione su un evento personalizzato, puoi visualizzare gli eventi da app mobile in modo analogo a tutti gli altri eventi di Analytics. |