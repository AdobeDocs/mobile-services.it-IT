---
description: In Adobe Analytics puoi gestire i ruoli nella home page di Strumenti di amministrazione.
title: Ruoli e autorizzazioni
uuid: ad350f8d-ef51-4519-98aa-3025bc0f5588
exl-id: 70f0b427-60d5-4a79-a8d3-e03274edd917
source-git-commit: 7b26c852dd9dba67a8b5e3228c1fecadfb465dca
workflow-type: tm+mt
source-wordcount: '555'
ht-degree: 61%

---

# Ruoli e autorizzazioni{#roles-and-permissions}

In Adobe Analytics puoi gestire i ruoli nella home page di Strumenti di amministrazione.

## Panoramica {#section_91B8192891E14E5285718C8118912500}

I seguenti ruoli possono gestire le autorizzazioni nell’interfaccia utente di Mobile Services:

### Amministratore di Analytics

Un amministratore di Analytics gestisce i gruppi di utenti e assegna le autorizzazioni, tra cui quella denominata Amministratori app mobili. The Experience Cloud Admin links your Adobe ID to your Adobe Analytics account, which allows you to log in to the Mobile Services UI by using your Adobe ID. [](https://experienceleague.adobe.com/docs/core-services/interface/administration/admin-getting-started.html?lang=it)

>[!TIP]
>
>Un amministratore Analytics può assegnare il ruolo di amministratore Analytics a qualsiasi utente.

### Amministratori app mobili

Questo è il ruolo di amministratore dell’interfaccia utente di Mobile Services.

>[!IMPORTANT]
>
>Per alcune funzionalità, ad esempio i messaggi push, l’amministratore di Analytics deve selezionare la casella di controllo **[!UICONTROL Creazione di segmenti]** in Gestione utente.

## Gestione dell’accesso {#section_E6939C2695AA4A0DBF432D50B2670920}

Seguono alcune informazioni aggiuntive sulle opzioni di accesso dell’interfaccia utente di Mobile Services:

### App e suite di rapporti

All Mobile Service apps are tied to report suites. Se gli utenti non hanno accesso a una suite di rapporti, non possono accedere all’app associata a tale suite di rapporti.

### Mobile Services e funzioni di Analytics

Se la tua azienda non ha un contratto Analytics per l’accesso a una determinata funzionalità dell’interfaccia utente (ad esempio i messaggi push), nessun utente dell’azienda potrà accedere a tale funzionalità, indipendentemente dal proprio livello di autorizzazione.

## Ruoli e autorizzazioni {#section_20AA029D5B8C413C8659777E79B11620}

Di seguito sono elencati i ruoli dell’interfaccia utente di Mobile Services, con le relative autorizzazioni disponibili:

### Amministratore di Analytics permissions

* Tutte le autorizzazioni utente e autorizzazioni dell’amministratore di app mobili
* Create App with new report suite
* Delete App from Mobile Services

   >[!IMPORTANT]
   >
   >Anche se l’app è stata eliminata nell’interfaccia utente di Mobile Services, la suite di rapporti esiste ancora in Analytics.

* Gestire le impostazioni dell’app

   * Enable Lifecycle Reporting
   * Enable Location Reporting
   * Create/Update/Delete Variables and Metrics

### Amministratori app mobili permissions

* All User Permissions
* Create App with existing report suite
* Gestire le impostazioni dell’app

   * Configurare le opzioni SDK di Mobile dell’app
   * Configurare le impostazioni di interfaccia dell’app
   * Configurare le app dell’app store collegate
   * Configurare le opzioni Collegamento universale dell’app
   * Configure Push Services certs and API keys
   * Create/Update/Activate/Deactivate/Duplicate/Archive/Delete Postbacks
   * Create/Update/Archive/Delete Link Destinations

* Create/Update/Archive Marketing Links
* Create/Import/Update/Delete Legacy Acquisition Links
* Create/Import/Update/Delete Places (Points of Interest) configuration
* Create/Update/Send/Schedule/Cancel/Duplicate/Archive/Delete Push Messages
* Create/Update/Activate/Deactivate/Duplicate/Archive/Delete In-App Messages

For more information about groups and users, see the following content in the Adobe Analytics documentation:

* [](https://experienceleague.adobe.com/docs/analytics/admin/admin-console/home.html?lang=it)
* [Aggiungi un utente a un gruppo](https://experienceleague.adobe.com/docs/analytics/admin/admin-console/home.html)

### Utente di Mobile Services

Questo ruolo dispone di autorizzazioni di sola lettura e può fornire un feedback nell’interfaccia di Mobile Services.

* Fornire un feedback nell’interfaccia di Mobile Services
* View Apps

   >[!IMPORTANT]
   >
   >Gli utenti possono visualizzare solo le suite di rapporti alle quali hanno accesso in Adobe Analytics.

* View App Settings

   * Scaricare la configurazione dell’SDK per app
   * Visualizzare tutte le impostazioni dell’interfaccia e dell’SDK
   * View Variables and Metrics configuration
   * View Postbacks
   * View Link Destinations

* Visualizzare ed eseguire i rapporti
* Visualizzare i collegamenti di marketing
* View and Export Legacy Acquisition Links
* View and Export Places (Points of Interest) configuration
* View Push Messages
* View In-App Messages
