---
description: 'Per configurare una suite di rapporti per la raccolta di dati di app iOS, completa questi passaggi:'
solution: Experience Cloud Services,Analytics
title: Prima di iniziare
topic-fix: Developer and implementation
uuid: 04133f68-3618-41fd-8a13-aec5b6f04df6
exl-id: 83da7cf5-3211-484d-bfe8-7b3b4999eea2
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '584'
ht-degree: 94%

---

# Prima di iniziare {#before-you-start}

Per configurare una suite di rapporti per la raccolta di dati di app iOS, completa questi passaggi:

## Attività per specifici ruoli {#section_8B9EA1FA189F4C6DB7D829F0B5844FBC}

Gli amministratori di Analytics e gli sviluppatori di app devono completare le seguenti attività:

### Amministratori di Analytics

Per configurare una suite di rapporti e raccogliere i dati dalle app per dispositivi mobili:

1. Completa una delle sezioni in [Eseguire l’accesso all’interfaccia utente di Adobe Mobile Services](/help/ios/getting-started/getting-started.md).
1. Crea un account Analytics per ogni sviluppatore di app.

Gli sviluppatori di app ora hanno accesso alla visualizzazione delle suite di rapporti che hai creato.

>[!IMPORTANT]
>
>Per creare una nuova suite di rapporti e scaricare gli SDK, devi essere un amministratore di Analytics.

### Sviluppatori di app

1. Assicurati che il tuo amministratore di Analytics abbia completato i passaggi descritti nella sezione *Amministratori di Analytics* nella sezione precedente.

1. Verifica che il tuo amministratore di Analytics abbia eseguito una delle procedure descritte in *Eseguire l&#39;accesso all&#39;interfaccia utente di Adobe Mobile Services* di seguito.
1. Dopo che la suite di rapporti è stata configurata, completa i passaggi descritti nella sezione *Scaricare l&#39;SDK*.

Per ulteriori informazioni su ruoli e autorizzazioni, vedi [Ruoli e autorizzazioni](/help/using/gs/c-mob-roles-and-permissions.md).

## Eseguire l&#39;accesso all&#39;interfaccia utente di Adobe Mobile Services  {#section_690A2EC4572E47869F183974E932A6A8}

Adobe Mobile Services è l’interfaccia di reportistica principale per l’analisi e il targeting delle app per dispositivi mobili. Dopo aver completato questi passaggi, puoi scaricare un file di configurazione preconfigurato con il server di raccolta dati, la suite di rapporti e molte altre impostazioni.

Puoi accedere ad Adobe Mobile Services in uno dei seguenti modi:

* **Experience Cloud**

   Accedi a [Experience Cloud](https://experience.adobe.com) con il tuo Adobe ID.

   Questo metodo presuppone che sia stato eseguito il provisioning della tua società e che tu abbia collegato il tuo account di Analytics. Per ulteriori informazioni sul provisioning, consulta [Gestione di utenti e prodotti Experience Cloud](https://experienceleague.adobe.com/docs/core-services/interface/administration/admin-getting-started.html?lang=it) nella guida Experience Cloud Central Interface Components . Per ulteriori informazioni sul collegamento dell&#39;account, consulta [Organizzazioni nell&#39;Experience Cloud](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=it).

   >[!TIP]
   >
   >Se non sei sicuro se per la tua società sia già stato eseguito il provisioning in Experience Cloud, usa il tuo account Adobe Analytics esistente.

* **Adobe Analytics**

   Fai clic su **[!UICONTROL Accedi con l&#39;account Analytics]** e immetti il nome della tua società Analytics, il tuo nome utente e la tua password.

## Creare una suite di rapporti {#section_7BC602ED1ABA42C6AB722F506B5219F3}

Per impostare una nuova suite di rapporti per la raccolta dei dati dall&#39;app e definire un&#39;app:

1. Fai clic su **[!UICONTROL Crea nuova app]**.

   Se non trovi questo pulsante, fai clic su **[!UICONTROL Gestione app]** > **[!UICONTROL Aggiungi]**.

1. Nel menu a discesa **[!UICONTROL Suite di rapporti]**, seleziona **[!UICONTROL Nuova suite di rapporti]**.

1. Immetti il nome dell&#39;app e seleziona un ID suite di rapporti univoco.

   Ad esempio, l&#39;ID suite di rapporti potrebbe essere `mycomobileappdev`. Devi impostare suite di rapporti e app distinte per le versioni di sviluppo e produzione. Quando sei pronto per configurare la versione di produzione, ripeti questi passaggi.
1. Lascia selezionata l’opzione **[!UICONTROL Modello per app mobile]**.

   Questo modello abilita le marche temporali per la raccolta dei dati offline e attiva le variabili della soluzione mobile per l&#39;acquisizione delle metriche sul ciclo di vita.

1. Seleziona il **[!UICONTROL Fuso orario]** e la **[!UICONTROL Valuta]**, quindi fai clic su **[!UICONTROL Salva]**.

## Scaricare l&#39;SDK {#section_044C17DF82BC4FD8A3E409C456CE9A46}

Per scaricare l&#39;SDK di Mobile:

1. Accedi a Mobile Services e apri la tua app tramite uno dei seguenti modi:

   * Seleziona l’app nell’elenco a discesa **[!UICONTROL Tutte le app]**.
   * Individua l’app nel riquadro a destra e aprila.

1. Fai clic su **[!UICONTROL Gestione impostazioni app]**.
1. Nella sezione **[!UICONTROL Download di SDK per app]**, scorri fino alla sezione **[!UICONTROL Download di SDK per app]**.

1. Scarica l&#39;SDK e l&#39;app di esempio per la tua piattaforma.

>[!TIP]
>
>Nel download dell&#39;SDK viene automaticamente incluso un file di configurazione per la tua app; non è quindi necessario scaricare manualmente tale file. Tuttavia, se hai scaricato l&#39;SDK in precedenza e ora desideri ottenere le impostazioni aggiornate, dovrai scaricare nuovamente il file di configurazione.
