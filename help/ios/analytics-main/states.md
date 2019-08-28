---
description: Per "stati" si intendono le diverse schermate o visualizzazioni disponibili nell'app. Ogni volta che nell'app viene visualizzato un nuovo stato, ad esempio, quando un utente passa dalla home page al feed delle notizie, è utile inviare una chiamata di tracciamento dello stato. In iOS, il tracciamento di uno stato avviene solitamente con il metodo viewDidLoad di ciascuna visualizzazione.
seo-description: Per "stati" si intendono le diverse schermate o visualizzazioni disponibili nell'app. Ogni volta che nell'app viene visualizzato un nuovo stato, ad esempio, quando un utente passa dalla home page al feed delle notizie, è utile inviare una chiamata di tracciamento dello stato. In iOS, il tracciamento di uno stato avviene solitamente con il metodo viewDidLoad di ciascuna visualizzazione.
seo-title: Tracciare gli stati dell'app
solution: Marketing Cloud, Analytics
title: Tracciare gli stati dell'app
topic: Sviluppatore e implementazione
uuid: 12 cca 4 eb -1 f 15-4 cec-a 58 f -76 b 69 eaff 99 d
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Track app states {#track-app-states}

Per "stati" si intendono le diverse schermate o visualizzazioni disponibili nell'app. Ogni volta che nell'app viene visualizzato un nuovo stato, ad esempio, quando un utente passa dalla home page al feed delle notizie, è utile inviare una chiamata di tracciamento dello stato. In iOS, il tracciamento di uno stato avviene solitamente con il metodo viewDidLoad di ciascuna visualizzazione.

>[!TIP]
>
>To track states, make a call to `trackState`. Gli stati non vengono tracciati automaticamente.

## Tracking states {#section_380DF56C4EE4432A823940E4AE4C9E91}

1. Aggiungi la libreria al tuo progetto e implementa le funzioni di ciclo di vita (lifecycle).

   Per ulteriori informazioni, vedi *Aggiungere l'SDK e il file di configurazione al progetto* in [Implementazione e ciclo di vita di base](/help/ios/getting-started/dev-qs.md).
1. Importa la libreria.

   ```objective-c
   #import "ADBMobile.h"
   ```

1. Invoca `trackState` per inviare un hit per la visualizzazione di questo stato.

   ```objective-c
   [ADBMobile trackState:@"Login Screen"  
                    data:nil];
   ```

In Adobe Mobile services, the **[!UICONTROL State Name]** is reported in the *`View State`* variable, and a view is recorded for each `trackState` call. Nelle altre interfacce di Analytics, **[!UICONTROL Stato di visualizzazione]** è indicato come **[!UICONTROL Nome pagina]** e stati di visualizzazione è indicato come visualizzazioni pagina.

## Sending additional data {#section_CFDB4F944496401786A145C209AB387C}

In addition to the **[!UICONTROL State Name]**, you can send additional context data with each track action call:

```objective-c
NSMutableDictionary *contextData = [NSMutableDictionary dictionary]; 
[contextData setObject:@"logged in" forKey:@"myapp.login.LoginStatus"]; 
[ADBMobile trackState:@"Home Screen" data:contextData];
```

I valori dei dati contestuali devono essere mappati su variabili personalizzate:

![](assets/map-variable-context-state.png)

## App state reporting {#section_0F6A54AB7A3F42C9BB042D86A0FC4630}

Per visualizzare gli stati si usa solitamente un rapporto sui percorsi che consente di vedere in che modo gli utenti navigano nell'app e quali stati vengono visualizzati con maggiore frequenza.

|  |  |
|--- |--- |
| Adobe Mobile Services | Il rapporto **[!UICONTROL Stati di visualizzazione.]** Questo rapporto si basa sui percorsi seguiti dagli utenti all'interno dell'applicazione. A sample path is  **[!UICONTROL Home]**  &gt;  **[!UICONTROL Settings]**  &gt; **[!UICONTROL Feed]**. |
| Adobe Analytics | Gli stati possono essere visualizzati ovunque possano essere visualizzate le Pagine, ad esempio nei rapporti **Pagine**, **[!UICONTROL Visualizzazioni pagina]** e **Percorso[!UICONTROL .]** |
| Analisi ad hoc | Gli stati possono essere visualizzati ovunque possano essere visualizzate le Pagine utilizzando la dimensione **Pagina**, la metrica **[!UICONTROL Visualizzazioni pagina]** e i rapporti **Percorso[!UICONTROL .]** |
