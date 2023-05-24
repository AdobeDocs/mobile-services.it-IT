---
description: In Adobe Analytics puoi gestire i ruoli nella home page di Strumenti di amministrazione.
title: Ruoli e autorizzazioni
uuid: ad350f8d-ef51-4519-98aa-3025bc0f5588
exl-id: 70f0b427-60d5-4a79-a8d3-e03274edd917
source-git-commit: 7cfaa5f6d1318151e87698a45eb6006f7850aad4
workflow-type: tm+mt
source-wordcount: '555'
ht-degree: 61%

---

# Ruoli e autorizzazioni{#roles-and-permissions}

{#eol}

In Adobe Analytics puoi gestire i ruoli nella home page di Strumenti di amministrazione.

## Panoramica {#section_91B8192891E14E5285718C8118912500}

I seguenti ruoli possono gestire le autorizzazioni nell’interfaccia utente di Mobile Services:

### Amministratore di Analytics

Un amministratore di Analytics gestisce i gruppi di utenti e assegna le autorizzazioni, tra cui quella denominata Amministratori app mobili. L’amministratore di Experience Cloud collega il tuo Adobe ID al tuo account Adobe Analytics, che ti consente di accedere all’interfaccia utente di Mobile Services utilizzando il tuo Adobe ID. Per ulteriori informazioni sull&#39;amministratore Experience Cloud, vedere [Gestione di utenti e prodotti Experienci Cloud](https://experienceleague.adobe.com/docs/core-services/interface/administration/admin-getting-started.html?lang=it) nella guida Experience Cloud Central Interface Components.

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

Tutte le app Mobile Services sono collegate alle suite di rapporti. Se gli utenti non hanno accesso a una suite di rapporti, non possono accedere all’app associata a tale suite di rapporti.

### Mobile Services e funzioni di Analytics

Se la tua azienda non ha un contratto Analytics per l’accesso a una determinata funzionalità dell’interfaccia utente (ad esempio i messaggi push), nessun utente dell’azienda potrà accedere a tale funzionalità, indipendentemente dal proprio livello di autorizzazione.

## Ruoli e autorizzazioni {#section_20AA029D5B8C413C8659777E79B11620}

Di seguito sono elencati i ruoli dell’interfaccia utente di Mobile Services, con le relative autorizzazioni disponibili:

### Amministratore di Analytics autorizzazioni

* Tutte le autorizzazioni utente e autorizzazioni dell’amministratore di app mobili
* Creare un’app con una nuova suite di rapporti
* Elimina app da Mobile Services

   >[!IMPORTANT]
   >
   >Anche se l’app è stata eliminata nell’interfaccia utente di Mobile Services, la suite di rapporti esiste ancora in Analytics.

* Gestire le impostazioni dell’app

   * Abilita rapporti sul ciclo di vita
   * Abilita reporting posizione
   * Creare/aggiornare/eliminare variabili e metriche

### Amministratori app mobili autorizzazioni

* Tutte le autorizzazioni utente
* Crea app con suite di rapporti esistente
* Gestire le impostazioni dell’app

   * Configurare le opzioni SDK di Mobile dell’app
   * Configurare le impostazioni di interfaccia dell’app
   * Configurare le app dell’app store collegate
   * Configurare le opzioni Collegamento universale dell’app
   * Configurare i certificati e le chiavi API dei servizi push
   * Creare/Aggiornare/Attivare/Disattivare/Duplicare/Archiviare/Eliminare Postback
   * Creare/Aggiornare/Archiviare/Eliminare le destinazioni dei collegamenti

* Creare/Aggiornare/Archiviare collegamenti di marketing
* Creare/importare/aggiornare/eliminare collegamenti di acquisizione legacy
* Configurazione di Crea/Importa/Aggiorna/Elimina luoghi (punti di interesse)
* Creare/Aggiornare/Inviare/Pianificare/Annullare/Duplicare/Archiviare/Eliminare Messaggi Push
* Creare/Aggiornare/Attivare/Disattivare/Duplicare/Archiviare/Eliminare Messaggi In-App

Per ulteriori informazioni su gruppi e utenti, consulta i seguenti contenuti nella documentazione di Adobe Analytics:

* [Impostazioni gruppo utenti (legacy)](https://experienceleague.adobe.com/docs/analytics/admin/admin-console/home.html?lang=it)
* [Aggiungi un utente a un gruppo](https://experienceleague.adobe.com/docs/analytics/admin/admin-console/home.html?lang=it)

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
   * Configurazione di visualizzazione variabili e metriche
   * Visualizza postback
   * Visualizzare le destinazioni dei collegamenti

* Visualizzare ed eseguire i rapporti
* Visualizzare i collegamenti di marketing
* Visualizzare ed esportare collegamenti di acquisizione legacy
* Configurazione di Visualizza ed Esporta luoghi (punti di interesse)
* Visualizzare i messaggi push
* Visualizzare i messaggi in-app
