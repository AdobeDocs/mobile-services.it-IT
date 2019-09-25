---
description: 'Prima di configurare una suite di rapporti e raccogliere dati dell''app Android, completa le seguenti attività di prerequisito '
seo-description: 'Prima di configurare una suite di rapporti e raccogliere dati dell''app Android, completa le seguenti attività di prerequisito '
seo-title: Prima di iniziare
solution: Marketing Cloud,Analytics
title: Prima di iniziare
topic: Sviluppatore e implementazione
uuid: 0ca9e937-8d40-4570-9dbf-9aecc6ecedf6
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Before you start {#before-you-start}

Prima di configurare una suite di rapporti e raccogliere dati dell'app Android, completa le seguenti attività di prerequisito:

## Role-specific tasks {#section_8B9EA1FA189F4C6DB7D829F0B5844FBC}

Gli amministratori di Analytics e gli sviluppatori di app devono completare le seguenti attività:

### Amministratori di Analytics

Per configurare una suite di rapporti e raccogliere i dati dalle app per dispositivi mobili:

1. Esegui una delle procedure riportate in [Eseguire l'accesso all'interfaccia utente di Adobe Mobile Services](../getting-started/requirements.md#section_690A2EC4572E47869F183974E932A6A8).
1. Crea un account Analytics per ogni sviluppatore di app.

Gli sviluppatori di app possono ora visualizzare le suite di rapporti che hai creato.

>[!IMPORTANT]
>
>Per creare una nuova suite di rapporti e scaricare gli SDK, devi essere un amministratore di Analytics.

### Sviluppatori di app

1. Assicurati che il tuo amministratore di Analytics abbia completato i passaggi descritti nella sezione *Amministratori di Analytics* in [Attività per specifici ruoli](../getting-started/requirements.md#section_8B9EA1FA189F4C6DB7D829F0B5844FBC).

1. Verifica che il tuo amministratore di Analytics abbia eseguito una delle procedure descritte in [Eseguire l'accesso all'interfaccia utente di Adobe Mobile Services](../getting-started/requirements.md#section_690A2EC4572E47869F183974E932A6A8).
1. Dopo che la suite di rapporti è stata configurata, esegui i passaggi descritti nella sezione [Scaricare l'SDK](../getting-started/requirements.md#section_044C17DF82BC4FD8A3E409C456CE9A46).

Per ulteriori informazioni su ruoli e autorizzazioni, vedi [Ruoli e autorizzazioni](/help/using/gs/c-mob-roles-and-permissions.md).

## Eseguire l'accesso all'interfaccia utente di Adobe Mobile Services {#section_690A2EC4572E47869F183974E932A6A8}

Adobe Mobile Services è l'interfaccia principale per la gestione dei rapporti per l'analisi delle app per dispositivi mobili e la definizione delle destinazioni (targeting). Una volta completati questi passaggi, puoi scaricare un file di configurazione in cui sono già stati configurati il server per la raccolta dei dati, la suite di rapporti e numerose altre impostazioni.

Puoi accedere all'interfaccia utente di Adobe Mobile Services in uno dei seguenti modi:

### Experience Cloud

Accedi a [Experience Cloud](https://marketing.adobe.com) con il tuo Adobe ID. Questo metodo presuppone che sia stato eseguito il provisioning della tua società in Experience Cloud e che sia stato effettuato il collegamento all'account di Analytics. Per ulteriori informazioni, consulta [Gestione di utenti e prodotti](https://docs.adobe.com/content/help/en/core-services/interface/manage-users-and-products/admin-getting-started.html)Experience Cloud.

>[!TIP]
>
>Se non sei sicuro se per la tua società sia stato eseguito il provisioning in Experience Cloud, usa il tuo account Adobe Analytics esistente.

### Adobe Analytics

Fai clic su **[!UICONTROL Accedi con l'account Analytics]** e immetti il nome della tua società Analytics, il tuo nome utente e la tua password.

## Create a report suite {#section_7BC602ED1ABA42C6AB722F506B5219F3}

Per impostare una nuova suite di rapporti per la raccolta dei dati dall'app e definire un'app:

1. Fai clic su **[!UICONTROL Crea nuova app]**.

   If you do not see this button, click **[!UICONTROL Manage Apps]** &gt; **[!UICONTROL Add]**.

1. Nel menu a discesa **[!UICONTROL Suite di rapporti]**, seleziona **[!UICONTROL Nuova suite di rapporti]**.

1. Immetti il nome dell'app e seleziona un tipo di suite di rapporti.

   Ad esempio, l'ID suite di rapporti potrebbe essere `mycomobileappdev`. Devi impostare suite di rapporti e app distinte per le versioni di sviluppo e di produzione. Ripeti quindi questi passaggi quando sarà il momento di impostare la versione di produzione.
1. In **[!UICONTROL Report Suite ID]**, verify that your report suite name is displayed.
1. In **[!UICONTROL Copia impostazioni da]**, verifica che sia selezionato **Modello per app mobile[!UICONTROL .]**

   Questo modello abilita le marche temporali per la raccolta dei dati offline e attiva le variabili della soluzione mobile per l'acquisizione delle metriche sul ciclo di vita.

1. Seleziona il tuo fuso orario e la tua valuta, quindi fai clic su **[!UICONTROL Salva]**.

## Scaricare l'SDK {#section_044C17DF82BC4FD8A3E409C456CE9A46}

Per scaricare l'SDK di Mobile:

1. Accedi all'interfaccia utente di Mobile Services e apri la tua app tramite uno dei seguenti modi:

   * Seleziona l'app nell'elenco a discesa **[!UICONTROL Tutte le app].**
   * Individua l'app nel riquadro a destra e aprila.

1. Fai clic su **[!UICONTROL Gestione impostazioni app]**.
1. Scorri fino alla sezione **[!UICONTROL Download di SDK per app].**
1. Scarica l'SDK e l'app di esempio per la tua piattaforma.

>[!TIP]
>
>A config file for your app is automatically included in the SDK download, so you do not need to download that file separately. Tuttavia, se hai scaricato l'SDK in precedenza e ora desideri ottenere le impostazioni aggiornate, dovrai scaricare nuovamente il file di configurazione.

Se usi Android Studio, puoi anche aggiungere la riga seguente al file `build.gradle` dell'app:

```java
compile 'com.adobe.mobile:adobeMobileLibrary:4.13.7'
```

Considerazioni da ricordare:

* Sostituisci il numero di versione riportato nell'esempio con quello appropriato degli SDK per Android.
* Scarica il file di configurazione e includilo nel progetto.