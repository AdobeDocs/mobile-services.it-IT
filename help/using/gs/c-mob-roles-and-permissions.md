---
description: In Adobe Analytics puoi gestire i ruoli nella home page di Strumenti di amministrazione.
title: Ruoli e autorizzazioni
uuid: ad350f8d-ef51-4519-98aa-3025bc0f5588
exl-id: 70f0b427-60d5-4a79-a8d3-e03274edd917
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '596'
ht-degree: 56%

---

# Ruoli e autorizzazioni{#roles-and-permissions}

In Adobe Analytics puoi gestire i ruoli nella home page di Strumenti di amministrazione.

## Panoramica {#section_91B8192891E14E5285718C8118912500}

I seguenti ruoli possono gestire le autorizzazioni nell’interfaccia utente di Mobile Services:

### Amministratore di Analytics

Un amministratore di Analytics gestisce i gruppi di utenti e assegna le autorizzazioni, tra cui quella denominata Amministratori app mobili. L’amministratore di Experience Cloud collega il tuo Adobe ID al tuo account Adobe Analytics, che ti consente di accedere all’interfaccia utente di Mobile Services utilizzando il tuo Adobe ID. Per ulteriori informazioni sull&#39;amministratore di Experience Cloud, consulta [Gestire utenti e prodotti Experience Cloud](https://experienceleague.adobe.com/docs/core-services/interface/administration/admin-getting-started.html) nella guida dei componenti dell&#39;interfaccia centrale di Experience Cloud.

>[!TIP]
>
>Un amministratore Analytics può assegnare il ruolo di amministratore Analytics a qualsiasi utente.

Per ulteriori informazioni su questo ruolo, consulta i seguenti contenuti nella documentazione di Adobe Analytics:

* [Panoramica della gestione utente](https://experienceleague.adobe.com/docs/analytics/admin/user-product-management/user-management/users.html)
* [Modifiche delle autorizzazioni utente e gruppo](https://experienceleague.adobe.com/docs/analytics/admin/user-product-management/user-management/permissions-changes.html)

### Amministratori app mobili

Questo è il ruolo di amministratore dell’interfaccia utente di Mobile Services.

>[!IMPORTANT]
>
>Per alcune funzionalità, ad esempio i messaggi push, l’amministratore di Analytics deve selezionare la casella di controllo **[!UICONTROL Creazione di segmenti]** in Gestione utente.

## Gestione dell’accesso {#section_E6939C2695AA4A0DBF432D50B2670920}

Seguono alcune informazioni aggiuntive sulle opzioni di accesso dell’interfaccia utente di Mobile Services:

### App e suite di rapporti

Tutte le app Mobile Services sono associate a suite di rapporti. Se gli utenti non hanno accesso a una suite di rapporti, non possono accedere all’app associata a tale suite di rapporti.

### Mobile Services e funzioni di Analytics

Se la tua azienda non ha un contratto Analytics per l’accesso a una determinata funzionalità dell’interfaccia utente (ad esempio i messaggi push), nessun utente dell’azienda potrà accedere a tale funzionalità, indipendentemente dal proprio livello di autorizzazione.

## Ruoli e autorizzazioni {#section_20AA029D5B8C413C8659777E79B11620}

Di seguito sono elencati i ruoli dell’interfaccia utente di Mobile Services, con le relative autorizzazioni disponibili:

### Amministratore di Analytics permissions

* Tutte le autorizzazioni utente e autorizzazioni dell’amministratore di app mobili
* Creare app con una nuova suite di rapporti
* Eliminare app da Mobile Services

   >[!IMPORTANT]
   >
   >Anche se l’app è stata eliminata nell’interfaccia utente di Mobile Services, la suite di rapporti esiste ancora in Analytics.

* Gestire le impostazioni dell’app

   * Abilitare i rapporti sul ciclo di vita
   * Abilitare i rapporti sulla posizione
   * Creare/aggiornare/eliminare variabili e metriche

### Amministratori app mobili permissions

* Tutte le autorizzazioni utente
* Creare app con suite di rapporti esistente
* Gestire le impostazioni dell’app

   * Configurare le opzioni SDK di Mobile dell’app
   * Configurare le impostazioni di interfaccia dell’app
   * Configurare le app dell’app store collegate
   * Configurare le opzioni Collegamento universale dell’app
   * Configurare i certificati Servizi push e le chiavi API
   * Creare/aggiornare/attivare/disattivare/duplicare/archiviare/eliminare postback
   * Creare/aggiornare/archiviare/eliminare destinazioni collegamenti

* Creare/aggiornare/archiviare collegamenti di marketing
* Creare/importare/aggiornare/eliminare collegamenti di acquisizione legacy
* Creare/importare/aggiornare/eliminare la configurazione Luoghi (Punti di interesse)
* Creare/aggiornare/inviare/programmare/annullare/duplicare/archiviare/eliminare messaggi push
* Creare/aggiornare/attivare/disattivare/duplicare/archiviare/eliminare messaggi in-app

Per ulteriori informazioni su gruppi e utenti, consulta i seguenti contenuti nella documentazione di Adobe Analytics:

* [Impostazioni gruppo di utenti (legacy)](https://experienceleague.adobe.com/docs/analytics/admin/user-product-management/user-groups/groups.html)
* [Aggiungi un utente a un gruppo](https://experienceleague.adobe.com/docs/analytics/admin/user-product-management/user-management/t-add-user-to-group.html)

### Utente di Mobile Services

Questo ruolo dispone di autorizzazioni di sola lettura e può fornire un feedback nell’interfaccia di Mobile Services.

* Fornire un feedback nell’interfaccia di Mobile Services
* Visualizza app

   >[!IMPORTANT]
   >
   >Gli utenti possono visualizzare solo le suite di rapporti alle quali hanno accesso in Adobe Analytics.

* Visualizza impostazioni app

   * Scaricare la configurazione dell’SDK per app
   * Visualizzare tutte le impostazioni dell’interfaccia e dell’SDK
   * Visualizzare la configurazione di variabili e metriche
   * Visualizza postback
   * Visualizzare le destinazioni dei collegamenti

* Visualizzare ed eseguire i rapporti
* Visualizzare i collegamenti di marketing
* Visualizzare ed esportare collegamenti di acquisizione legacy
* Visualizzare ed esportare la configurazione Luoghi (Punti di interesse)
* Visualizzare i messaggi push
* Visualizzare messaggi in-app
