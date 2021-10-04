---
description: Puoi creare e gestire i punti di interesse, che permettono di definire posizioni geografiche da utilizzare per correlazioni nei rapporti, come destinazioni di messaggi in-app e per altri scopi. Quando un hit viene inviato in un punto di interesse, quest’ultimo è associato all’hit.
keywords: dispositivi mobili
solution: Experience Cloud,Analytics
title: Gestire i punti di interesse
topic-fix: Metrics
uuid: 7b362534-54fb-43a3-b6b2-dfc8f45ff7c6
exl-id: 9598b06b-fb6a-436c-811c-f74015cc2ab0
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '529'
ht-degree: 100%

---

# Gestire i punti di interesse {#manage-points-of-interest}

Puoi creare e gestire i punti di interesse, che permettono di definire posizioni geografiche da utilizzare per correlazioni nei rapporti, come destinazioni di messaggi in-app e per altri scopi. Quando un hit viene inviato in un punto di interesse, questo è collegato all’hit.

Prima di poter utilizzare la posizione, verifica i seguenti requisiti:

* Devi avere Analytics – Mobile Apps o Analytics Premium.
* Devi abilitare i **[!UICONTROL Rapporti sulla posizione]** per l’app.
* Se utilizzi una versione dell’SDK iOS o Android precedente alla versione 4.2, dopo aver aggiunto nuovi **[!UICONTROL punti di interesse]**, devi scaricare un nuovo file di configurazione e passarlo ai tuoi sviluppatori di app.

   Se utilizzi iOS SDK o Android SDK versione 4.2 o successiva, non è necessario inviare un aggiornamento dell’app allo store per aggiornare i **[!UICONTROL punti di interesse]**. Nella pagina Gestisci punti di interesse, quando fai clic su **[!UICONTROL Salva]**, le modifiche vengono inserite nell’elenco **[!UICONTROL Punti di interesse]** e il file di configurazione per l’app attiva viene aggiornato. Il salvataggio comporta anche l’aggiornamento dell’elenco dei punti all’interno dell’app sui dispositivi dell’utente, fino a quando l’app utilizza l’SDK aggiornato e la configurazione con un URL dei punti di interesse remoto.

Sul dispositivo dell’utente, affinché un hit possa essere assegnato a un **[!UICONTROL punto di interesse]**, la posizione deve essere abilitata nell’app.

Per utilizzare Posizione, completa le seguenti attività:

1. Fai clic sul nome dell’app per visualizzare la pagina Gestione impostazioni app.
1. Fai clic su **[!UICONTROL Posizione]** > **[!UICONTROL Gestisci punti di interesse]**.

   ![Risultato del passaggio](assets/poi.png)

1. Digita le informazioni in ciascuno dei campi seguenti:

   * **[!UICONTROL Nome punto]**

      Digita il nome del **[!UICONTROL punto di interesse]**.

      Può essere il nome di una città, una provincia o una regione. Puoi anche creare **[!UICONTROL punti di interesse]** per posizioni specifiche, ad esempio uno stadio sportivo o un’azienda.

   * **[!UICONTROL Latitudine]**

      Digita la latitudine del **[!UICONTROL punto di interesse]**. Puoi ricavare questa informazione da altre fonti, ad esempio Internet.

   * **[!UICONTROL Longitudine]**

      Digita la longitudine del **[!UICONTROL punto di interesse]**. Puoi ricavare questa informazione da altre fonti, ad esempio Internet.

   * **[!UICONTROL Raggio (metri)]**

      Digita il raggio (in metri) intorno al **[!UICONTROL punto di interesse]** che vuoi includere. Ad esempio, se crei un punto di interesse per la città di Denver in Colorado, potresti specificare un raggio sufficientemente ampio che includa sia la città che la zona circostante, escludendo però Colorado Springs.

   * **[!UICONTROL Icona mappa]**

      Seleziona un’icona che verrà visualizzata nei rapporti [Panoramica](/help/using/location/c-location-overview.md) e [Mappa](/help/using/location/c-map-points.md).

1. Se necessario, aggiungi altri punti di interesse.

   È consigliabile non aggiungerne più di 5000. Se aggiungi più di 5.000 punti di interesse, potrai salvarli ma riceverai un avviso che ti consiglia di non superare i 5.000 punti di interesse.

1. Fai clic su **[!UICONTROL Salva]**.

Per eliminare uno o più punti di interesse, seleziona le caselle di controllo applicabili e fai clic su **[!UICONTROL Rimuovi selezionati]**.

Fai clic su **[!UICONTROL Importa]** o **[!UICONTROL Esporta]** per lavorare con i dati utilizzando un file `.csv` anziché l’interfaccia utente di Adobe Mobile.
