---
description: 'Per configurare una suite di rapporti per la raccolta di dati di app iOS, completa questi passaggi:'
seo-description: 'Per configurare una suite di rapporti per la raccolta di dati di app iOS, completa questi passaggi:'
seo-title: Prima di iniziare
solution: Marketing Cloud, Analytics
title: Prima di iniziare
topic: Sviluppatore e implementazione
uuid: 04133 f 68-3618-41 fd -8 a 13-aec 5 b 6 f 04 df 6
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Before you start {#before-you-start}

Per configurare una suite di rapporti per la raccolta di dati di app iOS, completa questi passaggi:

## Role-specific tasks {#section_8B9EA1FA189F4C6DB7D829F0B5844FBC}

Gli amministratori di Analytics e gli sviluppatori di app devono completare le seguenti attività:

### Amministratori di Analytics

Per configurare una suite di rapporti e raccogliere i dati dalle app per dispositivi mobili:

1. Esegui una delle procedure riportate in [Eseguire l'accesso all'interfaccia utente di Adobe Mobile Services](/help/ios/getting-started/getting-started.md).
1. Crea un account Analytics per ogni sviluppatore di app.

Gli sviluppatori di app possono ora visualizzare le suite di rapporti che hai creato.

>[!IMPORTANT]
>
>Per creare una nuova suite di rapporti e scaricare gli SDK, devi essere un amministratore di Analytics.

### Sviluppatori di app

1. Ensure that your Analytics administrator has completed the steps in the *Analytics Administrators* section above.

1. Verify that your Analytics administrator has completed one of the sections in the *Log in to the Adobe Mobile Services UI* below.
1. After the report suite has been configured, complete steps in the *Download the SDK* section below.

Per ulteriori informazioni su ruoli e autorizzazioni, vedi [Ruoli e autorizzazioni](/help/using/gs/c-mob-roles-and-permissions.md).

## Eseguire l'accesso all'interfaccia utente di Adobe Mobile Services {#section_690A2EC4572E47869F183974E932A6A8}

Adobe Mobile Services è l'interfaccia principale per la gestione dei rapporti per l'analisi delle app per dispositivi mobili e la definizione delle destinazioni (targeting). Una volta completati questi passaggi, puoi scaricare un file di configurazione in cui sono già stati configurati il server per la raccolta dei dati, la suite di rapporti e numerose altre impostazioni.

Puoi accedere ad Adobe Mobile Services in uno dei modi seguenti:

* **Experience Cloud**

   Accedi a [Experience Cloud](https://marketing.adobe.com) con il tuo Adobe ID.

   Questo metodo presuppone che sia stato eseguito il provisioning della tua società e che sia stato collegato il tuo account Analytics. Per ulteriori informazioni sul provisioning, vedi [Gestione di utenti e prodotti Experience Cloud](https://docs.adobe.com/content/help/en/core-services/interface/manage-users-and-products/admin-getting-started.html). Per ulteriori informazioni sul collegamento del tuo account, vedi [Organizzazioni e collegamento di account](https://docs.adobe.com/content/help/en/core-services/interface/manage-users-and-products/organizations.html).

   >[!TIP]
   >
   >Se non sei sicuro se in Experience Cloud è stato eseguito il provisioning della tua società, usa il tuo account Adobe Analytics esistente.

* **Adobe Analytics**

   Fai clic su **[!UICONTROL Accedi con l'account Analytics]** e immetti il nome della tua società Analytics, il tuo nome utente e la tua password.

## Create a report suite {#section_7BC602ED1ABA42C6AB722F506B5219F3}

Per impostare una nuova suite di rapporti per la raccolta dei dati dall'app e definire un'app:

1. Fai clic su **[!UICONTROL Crea nuova app]**.

   If you do not see this button, click **[!UICONTROL Manage Apps]** &gt; **[!UICONTROL Add]**.

1. Nel menu a discesa **[!UICONTROL Suite di rapporti]**, seleziona **[!UICONTROL Nuova suite di rapporti]**.

1. Immetti il nome dell'app e seleziona un ID suite di rapporti univoco.

   Ad esempio, l'ID suite di rapporti potrebbe essere `mycomobileappdev`. Devi configurare suite di rapporti e app distinte per le versioni di sviluppo e di produzione. Quando siete pronti per impostare la versione di produzione, ripetete questi passaggi.
1. Lascia selezionata l'opzione **[!UICONTROL Modello per app mobile].**

   Questo modello abilita le marche temporali per la raccolta dei dati offline e attiva le variabili della soluzione mobile per l'acquisizione delle metriche sul ciclo di vita.

1. Select your **[!UICONTROL Timezone]**, your **[!UICONTROL Currency]**, and click **[!UICONTROL Save]**.

## Scaricare l'SDK {#section_044C17DF82BC4FD8A3E409C456CE9A46}

Per scaricare l'SDK di Mobile:

1. Accedi a Mobile Services e apri l'app in uno dei modi seguenti:

   * Seleziona l'app nell'elenco a discesa **[!UICONTROL Tutte le app].**
   * Individua l'app nel riquadro a destra e aprila.

1. Fai clic su **[!UICONTROL Gestione impostazioni app]**.
1. Nella sezione **[!UICONTROL Download di SDK per app]**, scorri fino alla sezione **Downloads di SDK per app[!UICONTROL .]**

1. Scarica l'SDK e l'app di esempio per la tua piattaforma.

>[!TIP]
>
>Un file di configurazione per l'app viene incluso automaticamente nel download dell'SDK, quindi non è necessario scaricare il file separatamente. Tuttavia, se hai scaricato l'SDK in precedenza e ora desideri ottenere le impostazioni aggiornate, dovrai scaricare nuovamente il file di configurazione.

