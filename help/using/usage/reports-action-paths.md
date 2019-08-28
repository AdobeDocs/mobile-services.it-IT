---
description: Il rapporto Percorsi azione è basato sull'analisi dei percorsi e visualizza un grafico che rappresenta i percorsi seguiti da uno stato dell'app a un altro stato.
keywords: dispositivi mobili
seo-description: Il rapporto Percorsi azione è basato sull'analisi dei percorsi e visualizza un grafico che rappresenta i percorsi seguiti da uno stato dell'app a un altro stato.
seo-title: Rapporto Action Paths (Percorsi azione)
solution: Marketing Cloud, Analytics
title: Rapporto Action Paths (Percorsi azione)
topic: Rapporti, Metriche
uuid: a 21 e 5 d 9 e-fd 57-4178-9 d 64-87181 b 7 f 988 b
translation-type: tm+mt
source-git-commit: e9691f9cbeadd171948aa752b27a014c3ab254d6

---


# Rapporto Action Paths (Percorsi azione){#action-paths}

Il rapporto Percorsi azione è basato sull'analisi dei percorsi e visualizza un grafico che rappresenta i percorsi seguiti da uno stato dell'app a un altro stato.

I rapporti **[!UICONTROL Percorsi di visualizzazione]** e **Percorsi azione]sono entrambi rapporti relativi ai percorsi.[!UICONTROL ** Il rapporto **[!UICONTROL Percorsi di visualizzazione]ti permette di vedere come gli utenti si spostano nell'app passando da una schermata all'altra.** Il rapporto **[!UICONTROL Percorsi azione]mostra la sequenza di eventi e di azioni (clic, selezioni, ridimensionamento ecc.) eseguite dagli utenti nell'app.**

>[!TIP]
>
>Puoi usare un rapporto funnel per combinare la navigazione e le azioni in un unico rapporto. For more information, see [Funnel](/help/using/usage/reports-funnel.md).

![](assets/action_paths.png)

Ogni nodo, a forma di casella, rappresenta uno stato nei percorsi seguiti dall'utente attraverso un'app. Ad esempio, nell'immagine qui sopra, il nodo più in alto rappresenta il numero di utenti che hanno avviato l'app e poi scelto una foto dalla galleria.

Per visualizzare le opzioni di modifica del grafico, fai clic su un nodo e poi su **[!UICONTROL Attiva]** o **[!UICONTROL Espandi]**. Ad esempio, se fai clic sullo stato **[!UICONTROL PhotoPicked]** nel nodo principale, vengono visualizzate le icone **[!UICONTROL Attiva]ed** Espandi **.**

![](assets/action_paths_icons.png)

To expand, click the **[!UICONTROL +]** icon. Con questa opzione vengono visualizzati i percorsi aggiuntivi (in entrata o in uscita) del nodo. Nell'illustrazione seguente, lo stato 1 è l'avvio dell'app, lo stato 2 è la scelta di una foto (l'elemento che abbiamo espanso), lo stato 3 include quattro percorsi differenti che sono stati seguiti dagli utenti:

* Selezione di un elemento
* Aggiunta di un elemento
* Trascinamento di un elemento
* Ridimensionamento di un elemento

L'espansione di uno stato è simile alla creazione di un funnel.

![path path expand](assets/action_paths_expand.png)

To isolate the node and show paths that come into, and go out of the selected node, click the  ![focus icon](assets/icon_focus.png) icon. Nell'immagine seguente, i percorsi seguenti sono stati completati **prima** che gli utenti abbiano selezionato una foto:

* Rotazione di un elemento
* Ridimensionamento di un elemento
* Trascinamento di un elemento
* Rimozione di un elemento

Per gli utenti che hanno selezionato una foto, i percorsi seguenti sono stati completati **dopo** la selezione della foto:

* Selezione di un elemento
* Aggiunta di un elemento
* Trascinamento di un elemento
* Ridimensionamento di un elemento

![evidenziazione percorso azione](assets/action_paths_focus.png)

Puoi rendere attivi o espandere più nodi per ottenere una vista dettagliata dei percorsi seguiti dagli utenti nell'app. Ad esempio:

![percorso azione multipla](assets/action_paths_mult.png)

Per questo rapporto puoi configurare le seguenti opzioni:

* **[!UICONTROL Periodo di tempo]**

   Fai clic sull'icona **[!UICONTROL Calendario]per selezionare un periodo di tempo personalizzato o per sceglierne uno preimpostato dall'elenco a discesa.**

* **[!UICONTROL Personalizza]**

   Customize your reports by changing the **[!UICONTROL Show By]** options, adding metrics and filters, and adding additional series (metrics), and more. Per ulteriori informazioni, consultate [Personalizzare i rapporti](/help/using/usage/reports-customize/reports-customize.md).

* **[!UICONTROL Filtro]**

   Fai clic su **[!UICONTROL Filtro]per creare un filtro per più rapporti in modo da visualizzare il comportamento di un segmento in tutti i rapporti mobili.** Un filtro fisso consente di definire un filtro applicato a tutti i rapporti non di percorso. Per ulteriori informazioni, consultate [Aggiungere un filtro fisso](/help/using/usage/reports-customize/t-sticky-filter.md).

* **[!UICONTROL Scarica]**

   Click **[!UICONTROL PDF]** or **[!UICONTROL CSV]** to download or open documents and share with users who do not have access to Mobile Services or to use the file in presentations.