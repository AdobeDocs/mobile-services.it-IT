---
description: 'Puoi usare queste informazioni per: creare una nuova app e configurarne le metriche chiave; configurare le opzioni SDK per Adobe Analytics e Adobe Audience Manager; configurare le opzioni di acquisizione e del servizio ID; scaricare il file di configurazione, gli SDK e gli strumenti per sviluppatori e tester.'
keywords: dispositivi mobili
solution: Experience Cloud,Analytics
title: Aggiungere una nuova app
topic-fix: Metrics
uuid: 706b5e4d-1318-4a9e-8c69-ffabf51fa02c
exl-id: 30dca517-61ac-495b-aa91-3febd1cb8639
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '663'
ht-degree: 100%

---

# Aggiungere una nuova app {#add-a-new-app}

Puoi usare queste informazioni per: creare una nuova app e configurarne le metriche chiave; configurare le opzioni SDK per Adobe Analytics e Adobe Audience Manager; configurare le opzioni di acquisizione e del servizio ID; scaricare il file di configurazione, gli SDK e gli strumenti per sviluppatori e tester.

Queste istruzioni sono utili per aggiungere una nuova app e configurare le integrazioni per Adobe Analytics e Adobe Audience Manager.

Per poter configurare un’app, devi prima aggiungerla nell’interfaccia utente di Adobe Mobile Services. Dopo che hai creato l’app, la configurazione corretta dell’app viene generata automaticamente e puoi distribuirla agli sviluppatori che si occupano dell’implementazione dell’SDK Mobile per l’app.

1. Esegui l’accesso a Adobe Mobile Services ed effettua una delle operazioni seguenti:

   * Click **[!UICONTROL Crea nuovo]** per creare un’app.
   * Per aggiungere altre app, fai clic su Gestione app nel menu di navigazione a sinistra, quindi fai clic su **[!UICONTROL Aggiungi]**.

      Per ulteriori informazioni sull’accesso, consulta [Accedere](/help/using/gs/gs-signin.md).

      >[!TIP]
      >
      >Per gestire le app già esistenti, fai clic su Gestisci app nel menu di navigazione a sinistra, quindi fai clic sull’app da modificare. Puoi apportare le modifiche desiderate nella pagina Informazioni app.

1. Digita le informazioni nei campi seguenti:

   **[!UICONTROL Suite di rapporti]**

   Specifica la suite di rapporti in cui i dati per i rapporti vengono raccolti e memorizzati in Adobe Analytics. Ciascuna app è collegata a una singola suite di rapporti di Analytics. Se invii dati di app a più suite di rapporti, aggiungi una nuova app per ciascuna suite di rapporti. Ciascuna app è collegata a una singola suite di rapporti di Analytics. Se invii dati di app a più suite di rapporti, aggiungi una nuova app per ciascuna suite di rapporti.

   Se ti sono stati assegnati privilegi di amministratore Analytics in Adobe Mobile, puoi creare una nuova suite di rapporti in Adobe Mobile. Per creare una nuova suite di rapporti, seleziona **[!UICONTROL Nuova suite di rapporti]** e digita le informazioni nei campi seguenti:

   * **[!UICONTROL ID suite di rapporti]**

      Questo ID identifica in modo univoco la suite di rapporti in Adobe Analytics. Il prefisso della tua società viene aggiunto automaticamente all’inizio dell’ID.

   * **[!UICONTROL Copia impostazioni da]**

      Variabili, eventi e regole di elaborazione e altre impostazioni vengono configurati nella nuova suite di rapporti esattamente come in questa suite. Una suite di rapporti creata in Mobile Services è abilitata offline (o contrassegnata dall’indicazione di data e ora) solo se la suite di rapporti **[!UICONTROL Copia impostazioni da]** utilizzata era Modello per app mobile oppure se crei una suite di rapporti abilitata per l’uso offline.

   * **[!UICONTROL Fuso orario]**

      Tutte le date dei report presentano questo fuso orario. Questa impostazione cerca di utilizzare un fuso orario prossimo a quello utilizzato dal browser.

   * **[!UICONTROL Valuta]**

      Le entrate vengono tracciate e comunicate con questo tipo di valuta.
   >[!TIP]
   >
   >Per utilizzare una suite di rapporti virtuale (VRS), vedi [Suite di rapporti virtuali](/help/using/manage-apps/c-mob-vrs.md).

   * **[!UICONTROL Icona]**

      (**Facoltativo**) Per cercare e selezionare un’icona per la tua app, fai clic sull’**[!UICONTROL icona]**.

   * **[!UICONTROL Nome]**

      (**Facoltativo**) Immetti un nome descrittivo per l’app. Questo nome consente di individuare rapidamente un’app e un nome significativo può consentirti di comprendere rapidamente lo scopo e le impostazioni dell’app.

   * **[!UICONTROL Tipo]**

      Seleziona un tipo dall’elenco a discesa. I rapporti disponibili visualizzati nel menu di navigazione a sinistra variano a seconda del tipo di app selezionata.

      I tipi disponibili sono:

      * **[!UICONTROL Standard]**

         Per la maggior parte delle app puoi lasciare selezionata l’opzione **[!UICONTROL Standard]**.

      * **[!UICONTROL Pubblicazione]**

         Puoi selezionare questa opzione se l’app è stata creata con Adobe Digital Publishing Suite.

      * **[!UICONTROL Gioco]**

         Questa opzione è simile a **[!UICONTROL Standard]**, con la differenza che la terminologia utilizzata nei rapporti viene aggiornata con i termini tipici dei **[!UICONTROL giochi]**. Ad esempio, gli utenti vengono modificati in lettori. I rapporti specifici per i giochi vengono visualizzati automaticamente per le app di giochi.
   * **[!UICONTROL Descrizione]**

      (**Facoltativo**) Immetti una descrizione dell’app.



1. Fai clic su **[!UICONTROL Salva]** per aggiungere la nuova app.

   Una volta aggiunta l’app, puoi passare alla pagina Informazioni app e configurare ulteriori opzioni. Per ulteriori informazioni, consulta [Gestire le impostazioni app](/help/using/c-manage-app-settings/c-manage-app-settings.md).
