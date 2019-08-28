---
description: In Adobe Analytics puoi gestire i ruoli nella home page di Strumenti di amministrazione.
seo-description: In Adobe Analytics puoi gestire i ruoli nella home page di Strumenti di amministrazione.
seo-title: Ruoli e autorizzazioni
title: Ruoli e autorizzazioni
uuid: ad 350 f 8 d-ef 51-4519-98 aa -3025 bc 0 f 5588
translation-type: tm+mt
source-git-commit: c7cac006340e01d0fd1f6afe3419e6fd17294a98

---


# Roles and permissions{#roles-and-permissions}

In Adobe Analytics puoi gestire i ruoli nella home page di Strumenti di amministrazione.

## Panoramica {#section_91B8192891E14E5285718C8118912500}

I seguenti ruoli possono gestire le autorizzazioni nell'interfaccia utente di Mobile Services:

### Amministratore di Analytics

Un amministratore di Analytics gestisce i gruppi di utenti e assegna le autorizzazioni, tra cui quella denominata Amministratori app mobili. L’amministratore di Experience Cloud provvede a collegare il tuo Adobe ID al tuo account Adobe Analytics. Potrai così accedere all’interfaccia utente di Mobile Services utilizzando il tuo Adobe ID. Per ulteriori informazioni sull’amministratore di Experience Cloud, consulta [Amministrazione - Gestione utenti e domande frequenti](https://docs.adobe.com/content/help/en/core-services/interface/manage-users-and-products/admin-getting-started.html).

>[!TIP]
>
>Un amministratore di Analytics può assegnare il ruolo di amministratore di Analytics a qualsiasi utente.

Per ulteriori informazioni su questo ruolo, consulta gli argomenti seguenti:

* [Panoramica sulla gestione degli utenti](https://docs.adobe.com/content/help/en/analytics/admin/user-product-management/user-management/users.html)

* [Modifiche alle autorizzazioni Utente e Gruppo](https://docs.adobe.com/content/help/en/analytics/admin/user-product-management/user-management/permissions-changes.html)

### Amministratori app mobili

Questo è il ruolo di amministratore dell'interfaccia utente di Mobile Services.

>[!IMPORTANT]
>
>For some features, such as push messaging, the Analytics Admin must select the **[!UICONTROL Segment Creation]** check box in User Management.

## Managing access {#section_E6939C2695AA4A0DBF432D50B2670920}

Seguono alcune informazioni aggiuntive sulle opzioni di accesso dell'interfaccia utente di Mobile Services:

### App e suite di rapporti

Tutte le app di Mobile Services sono associate a delle suite di rapporti. Se gli utenti non hanno accesso a una suite di rapporti, non possono accedere all'app associata a tale suite di rapporti.

### Funzioni di Mobile Services e Analytics

Se la tua azienda non ha un contratto Analytics per l'accesso a una determinata funzionalità dell'interfaccia utente (ad esempio i messaggi push), nessun utente dell'azienda potrà accedere a tale funzionalità, indipendentemente dal proprio livello di autorizzazione.

## Roles and permissions {#section_20AA029D5B8C413C8659777E79B11620}

Di seguito sono elencati i ruoli dell'interfaccia utente di Mobile Services, con le relative autorizzazioni disponibili:

### Amministratore di Analytics

* Tutte le autorizzazioni Amministratore app mobili e Amministratori app mobili
* Creazione di app con una nuova suite di rapporti
* Eliminare app da Mobile Services

   >[!IMPORTANT]
   >
   >Anche se l'app è stata eliminata nell'interfaccia utente di Mobile Services, la suite di rapporti esiste ancora in Analytics.

* Gestire le impostazioni dell'app

   * Attivare i rapporti sul ciclo di vita
   * Attivare i rapporti sulla posizione
   * Creare/aggiornare/eliminare variabili e metriche

### Amministratori app mobili

* Tutte le autorizzazioni utente
* Creare app con una suite di rapporti esistente
* Gestire le impostazioni dell'app

   * Configurare le opzioni SDK di Mobile dell'app
   * Configurare le impostazioni di interfaccia dell'app
   * Configurare le app dell'app store collegate
   * Configurare le opzioni Collegamento universale dell'app
   * Configurare i certificati Servizi push e le chiavi API
   * Creare/aggiornare/attivare/disattivare/duplicare/archiviare/eliminare postback
   * Creare/aggiornare/archiviare/eliminare destinazioni collegamenti

* Creare/aggiornare/archiviare collegamenti di marketing
* Creare/importare/aggiornare/eliminare collegamenti di acquisizione legacy
* Creare/importare/aggiornare/eliminare una configurazione Luoghi (Punti di interesse)
* Creare/aggiornare/inviare/pianificare/annullare/duplicare/archiviare/eliminare messaggi push
* Creare/aggiornare/attivare/disattivare/duplicare/archiviare/eliminare messaggi in-app

Per maggiori informazioni su gruppi e utenti, vedi:

* [Impostazioni gruppo utenti](https://docs.adobe.com/content/help/en/analytics/admin/user-product-management/user-groups/groups.html)
* [Aggiungere un utente a un gruppo](https://docs.adobe.com/content/help/en/analytics/admin/user-product-management/user-management/t-add-user-to-group.html)

### Utente Mobile Services

Questo ruolo dispone di autorizzazioni di sola lettura e può fornire un feedback nell'interfaccia di Mobile Services.

* Fornire un feedback nell'interfaccia di Mobile Services
* Visualizzare le app

   >[!IMPORTANT]
   >
   >Gli utenti possono vedere solo le suite di rapporti per le quali hanno accesso in Adobe Analytics.

* Visualizzare le impostazioni delle app

   * Scaricare la configurazione dell'SDK per app
   * Visualizzare tutte le impostazioni dell'interfaccia e dell'SDK
   * Visualizzare la configurazione variabili e metriche
   * Visualizzare i postback
   * Visualizzare le destinazioni collegamenti

* Visualizzare ed eseguire rapporti
* Visualizzare i collegamenti di marketing
* Visualizzare ed esportare i collegamenti di acquisizione legacy
* Visualizzare ed esportare una configurazione Luoghi (Punti di interesse)
* Visualizzare i messaggi push
* Visualizzare i messaggi in-app
