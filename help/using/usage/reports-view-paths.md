---
description: Il rapporto Percorsi di visualizzazione, basato sull'analisi dei percorsi, visualizza un grafico che rappresenta i percorsi seguiti tra gli stati dell'app.
keywords: dispositivi mobili
seo-description: Il rapporto Percorsi di visualizzazione, basato sull'analisi dei percorsi, visualizza un grafico che rappresenta i percorsi seguiti tra gli stati dell'app.
seo-title: Report Percorsi di visualizzazione
solution: Marketing Cloud, Analytics
title: Report Percorsi di visualizzazione
topic: Rapporti, Metriche
uuid: bc 73 edce -0 cc 0-4349-9 a 48-e 0 a 40 cbe 1 b 67
translation-type: tm+mt
source-git-commit: e9691f9cbeadd171948aa752b27a014c3ab254d6

---


# Report Percorsi di visualizzazione {#view-paths}

Il rapporto **[!UICONTROL Percorsi di visualizzazione], basato sull'analisi dei percorsi, visualizza un grafico che rappresenta i percorsi seguiti tra gli stati dell'app.**

>[!TIP]
>
>The **[!UICONTROL View Paths]** and **[!UICONTROL View Action]** reports are similar because both are pathing reports. Il rapporto **[!UICONTROL Percorsi di visualizzazione]ti permette di vedere come gli utenti si spostano nell'app passando da una schermata all'altra.** Il rapporto **[!UICONTROL Percorsi azione]mostra la sequenza di azioni (clic, selezioni, ridimensionamento ecc.) eseguite dagli utenti nell'app.** Puoi usare un rapporto funnel per combinare la navigazione e le azioni in un unico rapporto. For more information, see [Funnel](/help/using/usage/reports-funnel.md).

![percorsi di visualizzazione](assets/view_paths.png)

Ogni nodo, a forma di casella, rappresenta uno stato nei percorsi seguiti dall'utente attraverso un'app. Ad esempio, nell'illustrazione qui sopra, il nodo più in alto rappresenta quanti utenti hanno avviato l'app e poi hanno visualizzato la vista principale.

Quando fai clic su un nodo per visualizzare altre opzioni per la modifica del grafico, vengono visualizzate altre opzioni quali **[!UICONTROL Attiva]** e **Espandi[!UICONTROL .]** Ad esempio, se fai clic sullo stato **[!UICONTROL MainView]** nel nodo principale, diventano visibili le icone **[!UICONTROL Attiva]ed** Espandi **.**

To expand the view, click the **[!UICONTROL +]** icon to display the additional paths that come in to or go from the node. Nell'illustrazione seguente, lo stato 1 è l'avvio dell'app, lo stato 2 è la visualizzazione della pagina principale dell'app e lo stato 3 include i percorsi seguenti che sono stati seguiti dagli utenti:

* Accesso al rullino fotografico
* Accesso al selettore di elementi
* Accesso alla fotocamera
* Accesso alla pagina di informazioni sull'elemento

![](assets/view_paths_expand.png)

Click ![focus icon](assets/icon_focus.png) to isolate the node and to show the paths that are coming into and going out of the selected node. Nell'illustrazione seguente, i seguenti percorsi hanno preceduto la visualizzazione della vista principale dell'app da parte degli utenti:

* Informazioni elemento
* Selettore elemento
* Rullino fotografico
* Fotocamera

![visualizzazione percorso di visualizzazione](assets/view_paths_focus.png)

Puoi rendere attivi o espandere più nodi per ottenere una vista dettagliata dei percorsi seguiti dagli utenti nell'app. Ad esempio:

![view path multipli](assets/view_paths_mult.png)

Per questo rapporto puoi configurare le seguenti opzioni:

* **[!UICONTROL Periodo
di tempo]** Fai clic sull'icona **[!UICONTROL Calendario]** per selezionare un periodo personalizzato o per selezionare un periodo di tempo predefinito dall'elenco a discesa.
* **[!UICONTROL Personalizza Personalizza]**
i rapporti modificando le opzioni **[!UICONTROL Mostra per]** , aggiungendo metriche e filtri, nonché serie (metriche) supplementari e altri elementi. Per ulteriori informazioni, consultate [Personalizzare i rapporti](/help/using/usage/reports-customize/reports-customize.md).
* **[!UICONTROL Filtro]**
Fate clic **[!UICONTROL su Filtro]** per creare un filtro per più rapporti in modo da visualizzare il comportamento di un segmento in tutti i rapporti mobili. Un filtro fisso consente di definire un filtro applicato a tutti i rapporti non di percorso. Per ulteriori informazioni, consultate [Aggiungere filtri fissi](/help/using/usage/reports-customize/t-sticky-filter.md).
* **[!UICONTROL Scarica]**
clic **[!UICONTROL su PDF]** o **[!UICONTROL CSV]** per scaricare o aprire i documenti e condividerli con utenti che non hanno accesso a Mobile Services o per utilizzare il file in presentazioni.