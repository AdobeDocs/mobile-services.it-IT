---
description: Per "stati" si intendono le diverse schermate o visualizzazioni disponibili nell'app.
seo-description: Per "stati" si intendono le diverse schermate o visualizzazioni disponibili nell'app.
seo-title: Tracciare gli stati dell'app
solution: Marketing Cloud,Analytics
title: Tracciare gli stati dell'app
topic: Sviluppatore e implementazione
uuid: 69c99d05-5816-4c86-97c5-d218dc26c129
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Track app states {#track-app-states}

Per "stati" si intendono le diverse schermate o visualizzazioni disponibili nell'app.

Ogni volta che nell'applicazione viene visualizzato un nuovo stato, ad esempio quando l'utente si sposta dalla homepage al feed di notizie, viene inviata una chiamata `trackState`. In Android, `trackState` viene generalmente chiamato ogni volta che si carica una nuova attività.

## Tracking states {#section_380DF56C4EE4432A823940E4AE4C9E91}

1. Aggiungi la libreria al tuo progetto e implementa le funzioni di ciclo di vita (lifecycle).

   For more information, see Add the SDK and Config File to your IntelliJ IDEA or Eclipse Project in Core implementation and lifecycle.**[](/help/android/getting-started/dev-qs.md)

1. Importa la libreria:

   ```java
   import com.adobe.mobile.*;
   ```

1. Nella funzione `onCreate`, chiama `trackState` per inviare un hit per questa visualizzazione di stato:

   ```java
   @Override 
   public void onCreate(Bundle savedInstanceState) { 
       super.onCreate(savedInstanceState); 
       setContentView(R.layout.main); 
   
       // Adobe - track when this state loads 
       Analytics.trackState("State Name", null); 
   }
   ```

The `"State Name"` is reported in the `View State` variable in Adobe Mobile services, and a view is recorded for each `trackState` call. In other Analytics interfaces,  is reported as , and  is reported as .`View State``Page Name``state views``page views`

## Send additional data {#section_CFDB4F944496401786A145C209AB387C}

In addition to the `"State Name"`, you can send additional context data with each track action call:

```java
@Override 
public void onCreate(Bundle savedInstanceState) { 
    super.onCreate(savedInstanceState); 
    setContentView(R.layout.main); 
  
    // Adobe - track when this state loads 
    HashMap<String, Object> exampleContextData = new HashMap<String, Object>(); 
    exampleContextData.put("myapp.login.LoginStatus", "logged in"); 
    Analytics.trackState("Home Screen", exampleContextData); 
}
```

I valori dei dati contestuali devono essere mappati su variabili personalizzate in Adobe Mobile Services:

![](assets/map-variable-context-state.png)

## App state reporting {#section_0F6A54AB7A3F42C9BB042D86A0FC4630}

Gli stati vengono generalmente visualizzati utilizzando un rapporto del percorso, che consente di vedere in che modo gli utenti si spostano nell'app e quali stati vengono visualizzati più di frequente.

|  |  |
|--- |--- |
| Adobe Mobile Services | Il rapporto **[!UICONTROL Stati di visualizzazione.]** Questo rapporto si basa sui percorsi seguiti dagli utenti all'interno dell'applicazione. A sample path is  **[!UICONTROL Home]**  &gt;  **[!UICONTROL Settings]**  &gt; **[!UICONTROL Feed]**. |
| Adobe Analytics | Gli stati possono essere visualizzati ovunque possano essere visualizzate le Pagine, ad esempio nei rapporti **Pagine**, **[!UICONTROL Visualizzazioni pagina]** e **Percorso[!UICONTROL .]** |
| Analisi ad hoc | Gli stati possono essere visualizzati ovunque possano essere visualizzate le Pagine utilizzando la dimensione **Pagina**, la metrica **[!UICONTROL Visualizzazioni pagina]** e i rapporti **Percorso[!UICONTROL .]** |


