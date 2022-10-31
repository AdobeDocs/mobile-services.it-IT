---
description: Una suite di rapporti virtuale (VRS) è suite di rapporti che è stata creata applicando una o più definizioni di segmento a una suite di rapporti. In questo modo gli utenti possono mantenere i propri dati in una singola suite di rapporti ma gestirli come se fossero contenuti in suite di rapporti separate.
title: Suite di rapporti virtuali
uuid: 3f467cad-43e7-4cd0-889b-89f8c61febbd
exl-id: c9ce7f7c-2023-4a9d-9e4d-bacc21f9ad40
source-git-commit: 7cfaa5f6d1318151e87698a45eb6006f7850aad4
workflow-type: tm+mt
source-wordcount: '1006'
ht-degree: 81%

---

# Suite di rapporti virtuali {#virtual-report-suites}

{#eol}

Una suite di rapporti virtuale (VRS) è suite di rapporti che è stata creata applicando una o più definizioni di segmento a una suite di rapporti. In questo modo gli utenti possono mantenere i propri dati in una singola suite di rapporti ma gestirli come se fossero contenuti in suite di rapporti separate.

Le app che utilizzano le VRS si comportano come quelle che usano le normali suite di rapporti, tranne che per la gestione delle seguenti funzionalità:

* Regole di elaborazione
* eVar/prop/listvars/events
* Opzione con abilitazione Timestamp
* Flag di Dimension (ciclo di vita, posizione e così via)
* Classificazioni

Questi valori vengono gestiti nella suite di rapporti principale e sono condivisi con le VRS che appartengono alla stessa suite di rapporti principale.

Le aree seguenti dell’interfaccia utente di Adobe Mobile Services sono sempre accessibili, indipendentemente dalla suite di rapporti principale:

* Il file di configurazione
* Gestire i punti di interesse
* Gestire le destinazioni dei collegamenti
* Gestione postback
* Collegamenti ai messaggi
* Acquisizione

Una VRS può essere utile per completare le seguenti attività:

* Limitare l’accesso ai dati

   Prendiamo il caso di un’app di un’azienda multinazionale che consente di inviare dati a una suite di rapporti per tutte le geolocalità. Tuttavia, l’azienda vuole fare in modo che l’utente aziendale di una determinata regione non possa visualizzare i dati di una regione diversa. A questo scopo, l’amministratore dell’azienda può creare una suite di rapporti virtuale per segmentare gli utenti per regione e concedere l’autorizzazione per tale VRS solo all’utente aziendale che gestisce la regione.

   Questa limitazione impedisce agli utenti aziendali di visualizzare i dati che non riguardano la propria regione. Ad esempio, un utente aziendale della regione EMEA non ha necessità di vedere i dati della regione APAC.

* Consenti il controllo di messaggi in-app/push, punti di interesse di posizione, acquisizione e postback, con l’invio di tutti i dati a una singola suite di rapporti.

   Prendiamo il caso di un’azienda multinazionale che vuole inviare tutti i dati alla stessa suite di rapporti per tutte le geolocalità. Tuttavia, l’azienda vuole fare in modo che il team di marketing di ogni regione provveda alla gestione dei messaggi in-app e push solo della propria regione. L’amministratore dell’azienda può quindi creare delle VRS regionali e dare così la possibilità a ciascun team di gestire la propria app in base alla rispettiva VRS.

   Più specificamente, il team regionale crea la propria app utilizzando il file di configurazione della VRS. I dati vengono inviati alla suite di rapporti principale, ma i messaggi in-app e push, i punti di interesse di posizione, l’acquisizione e i postback sono controllati dall’app creata in base alla VRS.

## Creare una suite di rapporti virtuale in Adobe Analytics {#section_D56B90B2653847D68ECA1F9B39204330}

>[!IMPORTANT]
>
>Solo gli amministratori di Adobe Analytics possono creare e modificare le suite di rapporti virtuali in Adobe Analytics. Per creare una suite di rapporti virtuale, vedi [Creare suite di rapporti virtuali](https://experienceleague.adobe.com/docs/analytics/components/virtual-report-suites/vrs-workflow/vrs-create.html?lang=it) nella documentazione di Adobe Analytics.

Ogni VRS ha un ID univoco. Per visualizzare l’ID suite di rapporti principali nell’interfaccia utente di Adobe Mobile Services, nella pagina Gestisci impostazioni app, nella sezione **[!UICONTROL Informazioni app]**, fai clic su **[!UICONTROL Maggiori dettagli]**.

Nell’interfaccia di Adobe Mobile Services, puoi utilizzare una VRS per creare un’app e segmentare i dati per un gruppo specifico dell’organizzazione. In questo modo, ad esempio, un utente aziendale in Spagna non può visualizzare i dati relativi a un utente aziendale in Giappone.

>[!TIP]
>
>Non è possibile modificare i valori che vengono ereditati dalla suite di rapporti principale.

Una VRS è una definizione di segmento lato server associata a una suite di rapporti principale. Di conseguenza, non è possibile eseguire attività di raccolta dati su una VRS, poiché l’SDK invia gli hit solo alla suite di rapporti principale, che a sua volta li registra.

## Suite di rapporti virtuale in Adobe Mobile Services e raccolta dati {#section_8ED8FBA5B44044D9ABC2151A39C577D4}

In Adobe Mobile Services, è possibile creare un’app basata su una suite di rapporti principale o su una suite di rapporti virtuale. Quando crei un’app basata su una suite di rapporti virtuale, ti consigliamo di allineare il segmento VRS con la definizione dell’app.

>[!TIP]
>
>Le certificazioni push vengono collegate a livello di app nell’interfaccia utente di Mobile Services.

Per garantire che i messaggi push vengano inviati correttamente, il segmento di pubblico deve essere definito correttamente. Per ulteriori informazioni, consulta [Pubblico: Definire e configurare i segmenti di pubblico per i messaggi push](/help/using/in-app-messaging/t-create-push-message/c-audience-push-message.md).

## Comprensione dei fusi orari {#section_498E1EED22D741C3BDED44F01FACA72A}

La proprietà Fuso orario, nella pagina Gestione impostazioni è diversa dalla proprietà relativa al fuso orario che si utilizza per creare una VRS in Adobe Analytics. La proprietà della pagina Gestione impostazioni viene ereditata dalla suite di rapporti principale, che viene utilizzata per inviare i dati a Adobe Analytics. La proprietà che specifichi quando crei una VRS in Adobe Analytics, invece, viene utilizzata per visualizzare i rapporti nell’interfaccia utente di Mobile Services e può essere diversa da quella della suite di rapporti principale.

## Selezionare una suite di rapporti virtuale nell’interfaccia utente di Mobile Services {#section_3212D0FC01FD43DCAF30FBAA354CD6E4}

Per utilizzare una VRS quando crei un’app, selezionala dall’elenco a discesa **[!UICONTROL Suite di rapporti]** nella pagina Informazioni app. Questo elenco contiene suite di rapporti principali e virtuali.

>[!IMPORTANT]
>
>Per selezionare una VRS dall’elenco, cerca le voci con un pallino blu e la convenzione di denominazione `vrs_` *`<company_name>`*`_`*`<unique name>`*  .

## Proprietà delle suite di rapporti virtuali {#section_20ECE6243F664C4FB4347ADB4FF0458A}

Nella tabella seguente sono riportate le proprietà delle VRS:

>[!TIP]
>
>Le proprietà di sola lettura sono ereditate dalla suite di rapporti principale.

| Proprietà | Ereditato dalla suite di rapporti principale | Modificabile? | Note |
|--- |--- |--- |--- |
| `target.clientCode` | No | Sì |  |
| `target.timeout` | No | Sì |  |
| `audienceManager.server` | No | Sì |  |
| `audienceManager.analyticsForwardingEnabled` | Sì | Sì |  |
| `audienceManager.timeout` | No | Sì |  |
| `acquisition.server` | No | No |  |
| `acquisition.appid` | No | No |  |
| `analytics.rsids` | Sì | No |  |
| `analytics.server` | No | No |  |
| `analytics.ssl` | No | Sì |  |
| `analytics.offlineEnabled` | Sì |  |  |
| `analytics.charset` | Sì | No |  |
| `analytics.lifecycleTimeout` | No | Sì | Deve essere la suite di rapporti principale, se gli utenti non desiderano che i loro dati siano incoerenti. |
| `analytics.privacyDefault` | No | Sì |  |
| `analytics.batchLimit` | No | Sì |  |
| `analytics.timezone` | Sì | Sì, quando crei l’app. | Questa proprietà relativa al fuso orario viene utilizzata per inviare dati ad Adobe Analytics ed è diversa dalla proprietà relativa al fuso orario impostata al momento della creazione di una VRS. |
| `analytics.timezoneOffset` | Sì | No |  |
| `analytics.referrerTimeout` | No | Sì |  |
| `analytics.backdateSessionInfo` | Sì | Sì |  |

## Informazioni aggiuntive {#section_4C4446F1FBE64F659BC0A2362C9F3E59}

Seguono alcune informazioni aggiuntive sulle suite di rapporti virtuali:

* Per ulteriori informazioni sulle VRS, consulta [Panoramica delle suite di rapporti virtuali](https://experienceleague.adobe.com/docs/analytics/components/virtual-report-suites/vrs-about.html?lang=it).
* Per ulteriori informazioni sulla pianificazione dell’implementazione di una VRS, consulta [Virtual Report Suite Workflow](https://experienceleague.adobe.com/docs/analytics/components/virtual-report-suites/vrs-workflow/vrs-workflow.html) (Flusso di lavoro delle suite di rapporti virtuali).
