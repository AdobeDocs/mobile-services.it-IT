---
description: Puoi configurare le opzioni relative al pubblico per i messaggi in-app, incluso vista, attivatore e caratteristiche.
keywords: dispositivi mobili
seo-description: Puoi configurare le opzioni relative al pubblico per i messaggi in-app, incluso vista, attivatore e caratteristiche.
seo-title: Messaggio in-app pubblico
solution: Marketing Cloud, Analytics
title: Messaggio in-app pubblico
topic: Metrics (Metriche)
uuid: 6 c 815 d 4 c -7626-4 cf 4-9158-3 f 059 c 79317 a
translation-type: tm+mt
source-git-commit: d028fe0f9477bc011aa8fda21a0a389808df0fce

---


# Audience: in-app message {#audience-in-app-message}

Puoi configurare le opzioni relative al pubblico per i messaggi in-app, incluso vista, attivatore e caratteristiche.

1. In your app, click **[!UICONTROL Messaging]** &gt; **[!UICONTROL Manage Messages]** &gt; **[!UICONTROL Create Message]** &gt; **[!UICONTROL Create In-App]**.
1. Nella pagina Pubblico, digita le informazioni nei campi seguenti:

   * **[!UICONTROL Visualizzazione]**

      Specifica l'opzione che attiva la visualizzazione di un messaggio:

      * **[!UICONTROL Sempre]**

         Il messaggio viene visualizzato ogni volta che si verifica l'evento di attivazione.

      * **[!UICONTROL Una volta]**

         Il messaggio viene visualizzato solo la prima volta che si verifica l'evento di attivazione.

      * **[!UICONTROL Fino al click-through]**

         Il messaggio viene visualizzato ogni volta che si verifica l'evento di attivazione fino al click-through dell'utente. Questo attivatore vale solo per i messaggi a schermo intero e di avviso. La maggior parte dei messaggi richiede un reindirizzamento o utilizza una risorsa da Internet e non viene visualizzata in modalità offline. Per visualizzare sempre il messaggio indipendentemente dalla connettività di rete, seleziona la casella di controllo **[!UICONTROL Mostra offline].**
   * **[!UICONTROL Attivatore]**

      Seleziona un'opzione dall'elenco a discesa, quindi scegli una condizione. Ad esempio, seleziona **[!UICONTROL Avviato]** dal primo elenco a discesa ed **Esiste]dal secondo.[!UICONTROL ** Per visualizzare il messaggio, puoi inoltre specificare dati di contesto personalizzato che devono essere inclusi nell'hit di attivazione.

      >[!IMPORTANT]
      >
      >Se selezioni più attivatori, per visualizzare il messaggio tutti gli attivatori devono verificarsi sullo stesso hit.

   * **[!UICONTROL Caratteristiche]**
Puoi determinare chi deve visualizzare il messaggio in-app quando viene attivato e filtrare (segmentare) il pubblico in base a hit con dati specifici. Ad esempio, puoi definire una regola in cui i punti di interesse contengono Denver. Questo filtro consente di mostrare il messaggio a clienti che rientrano in uno dei tuoi punti di interesse il cui nome contiene Denver, al momento dell'attivazione.



## Additional information about traits and triggers {#section_48C39EFB8CAA4F62B994FCC91DF588E6}

>[!IMPORTANT]
>
>Attivatori e caratteristiche utilizzano i dati passati ad Analytics dall'app. Tali valori sono passati come dati di contesto, variabili mappate e metriche. Una variabile è un valore di testo; una metrica è invece un valore numerico.

To see the mapping of these key value pairs in the Mobile Services UI and validate the value for your trigger, click **[!UICONTROL Manage App Settings]** &gt;  **[!UICONTROL Manage Variables &amp; Metrics]** &gt;, which displays the following tabs:

* **[!UICONTROL Variabili standard e metriche]**
* **[!UICONTROL Variabili personalizzate]**
* **[!UICONTROL Metriche personalizzate]**

Convalida la mappatura, quindi seleziona la corrispondenza o l’operatore logico appropriato per configurare il pubblico per il messaggio.

### Selecting metrics and variables {#example_AB126F03BD1C4094B791E230B3DB1189}

![opzioni trigger](assets/custom_trigger_matcher_options.png)

Gli scenari seguenti ti aiutano a determinare se selezionare una metrica o una variabile come attivatore:

### Metrics (Metriche)

Una metrica è un valore numerico, ad esempio il numero di acquisti effettuati.

1. Click **[!UICONTROL Manage Messages]** &gt; **[!UICONTROL Create Message]**.
1. Completa i seguenti passaggi nella sezione **[!UICONTROL Attivatore]** della scheda **Pubblico[!UICONTROL :]**

   1. Seleziona un evento standard, ad esempio **[!UICONTROL Avviato]** e seleziona **[!UICONTROL esiste]**.
   1. Seleziona un secondo attivatore che sia un punto dati personalizzato, mappato su una metrica.
   1. Under **[!UICONTROL Number]**, select a matcher option.

### Variabili

Una variabile è una stringa di testo che sia un identificatore univoco, ad esempio paese, aeroporto e così via.

1. Click **[!UICONTROL Manage Messages]** &gt; **[!UICONTROL Create Message]**.
1. Completa i seguenti passaggi nella sezione **[!UICONTROL Attivatore]** della scheda **Pubblico[!UICONTROL :]**

   1. Seleziona un evento standard, ad esempio **[!UICONTROL Avviato]** e seleziona **[!UICONTROL esiste]**.
   1. Seleziona un secondo attivatore che sia un punto dati personalizzato, mappato su una variabile.
   1. Under **[!UICONTROL Text]**, select a matcher option.

For more information about context data, variables, and metrics, see [Managing your app](/help/using/manage-apps/manage-apps.md).
