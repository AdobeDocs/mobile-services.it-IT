---
description: Crea, gestisci e genera rapporti sui messaggi in-app e push.
keywords: dispositivi mobili
solution: Experience Cloud,Analytics
title: Messaggistica
topic-fix: Metrics
uuid: e32d3e35-2d09-4ddf-8919-75dc895abcb3
exl-id: e6d076fc-3176-4591-8388-314b936c58cd
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 100%

---

# Messaggistica {#messaging}

Puoi creare, gestire e generare rapporti sui messaggi in-app e push.

## Nuova versione SDK per Adobe Experience Cloud

Hai bisogno di informazioni e documentazione relative all’SDK per dispositivi mobili di Adobe Experience Platform? Fai clic [qui](https://aep-sdks.gitbook.io/docs/) per la documentazione più recente.

A settembre 2018 è stata rilasciata una nuova versione principale dell&#39;SDK. Questi nuovi SDK per dispositivi mobili di Adobe Experience Platform sono configurabili tramite [Experience Platform Launch](https://www.adobe.com/it/experience-platform/launch.html).

* Per iniziare, passa a [Launch](https://launch.adobe.com/).
* Per visualizzare cosa è compreso negli archivi Experience Platform SDK, passa a [Github: SDK di Adobe Experience Platform](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

>[!IMPORTANT]
>
> Se utilizzi gli SDK per dispositivi mobili di Adobe Experience Platform con Adobe Launch, **devi** inoltre installare l’estensione Adobe Analytics Mobile Services per utilizzare le funzioni di Adobe Mobile Services, ad esempio i collegamenti di acquisizione. Per ulteriori informazioni, consulta [Adobe Analytics - Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services). Per informazioni sull’uso della messaggistica push e in-app con l’SDK di Experience Platform, consulta [Configurazione della messaggistica push](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services#set-up-push-messaging) e [Configurazione della messaggistica in-app](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services#set-up-in-app-messaging).

## Messaggi in-app {#section_8984F4568BC24D32A87429FFCB5184A6}

I messaggi in-app vengono consegnati agli utenti in tempo reale, in base alle loro azioni e caratteristiche. I messaggi vengono attivati dai dati di Analytics già tracciati dall’SDK.

Sono supportati i seguenti tipi di messaggi:

* Personalizzato e a tema
* A schermo intero
* Avvisi nativi
* Notifiche locali

Per aiutarti a capire come funziona la messaggistica in-app, ecco alcune informazioni aggiuntive:

* I messaggi in-app richiedono la versione SDK 4.2 o successiva.
* Devi specificare gli utenti con diritti di amministratore delle app per dispositivi mobili.

   Questi diritti consentono l’accesso ai collegamenti di acquisizione e ai messaggi in-app. Per ulteriori informazioni, consulta [Ruoli e autorizzazioni](/help/using/gs/c-mob-roles-and-permissions.md).
* Dopo essere stato approvato, il messaggio viene pubblicato automaticamente nell’applicazione.
* L’SDK presenta il messaggio agli utenti quando i parametri del messaggio (caratteristiche, attivatore e pianificazione) sono soddisfatti.
* I messaggi possono contenere un HTML personalizzato o un’immagine che utilizzano un URL online.

   Per i messaggi che vengono attivati offline, è inoltre possibile specificare un backup o un’immagine alternativa dal bundle dell’app.
* I messaggi attivi e completati generano rapporti su viste totali, percentuali di clic e così via.
* Per i messaggi personalizzati sono disponibili modelli che consentono di creare facilmente un messaggio in-app personale.

## Messaggi push {#section_90555A55BCE7427A90B1577E14BEF51B}

I messaggi push vengono inviati agli utenti che hanno acconsentito alla ricezione di notifiche. Puoi impostare come destinatari di questi messaggi gli utenti dei segmenti Analytics o di segmenti personalizzati. I messaggi push vengono recapitati al di fuori dell’app e sono quindi molto utili per coinvolgere di nuovo utenti passivi o per inviare informazioni specifiche in base all’ora e alla posizione.

Prima di configurare i messaggi push, consulta [Prerequisiti per abilitare i messaggi push](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/prerequisites-push-messaging.md). Una volta eseguite tali operazioni, devi configurare i messaggi push nelle impostazioni dell’app. Per ulteriori informazioni, vedi   [Configurare i messaggi push](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/configure-push-messaging.md).
