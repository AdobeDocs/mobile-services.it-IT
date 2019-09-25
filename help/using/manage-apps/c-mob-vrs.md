---
description: Una suite di rapporti virtuale (VRS) è suite di rapporti che è stata creata applicando una o più definizioni di segmento a una suite di rapporti. In questo modo gli utenti possono mantenere i propri dati in una singola suite di rapporti ma gestirli come se fossero contenuti in suite di rapporti separate.
seo-description: Una suite di rapporti virtuale (VRS) è suite di rapporti che è stata creata applicando una o più definizioni di segmento a una suite di rapporti. In questo modo gli utenti possono mantenere i propri dati in una singola suite di rapporti ma gestirli come se fossero contenuti in suite di rapporti separate.
seo-title: Suite di rapporti virtuali
title: Suite di rapporti virtuali
uuid: 3f467cad-43e7-4cd0-889b-89f8c61febbd
translation-type: tm+mt
source-git-commit: 814c99695f538160ae28484ca8e2a92f5b24bb1a

---


# Virtual report suites {#virtual-report-suites}

Una suite di rapporti virtuale (VRS) è suite di rapporti che è stata creata applicando una o più definizioni di segmento a una suite di rapporti. Questo consente agli utenti di mantenere i propri dati in una singola suite di rapporti, ma di gestirli come se fossero in suite di rapporti separate.

Le app che utilizzano le VRS eseguono le stesse operazioni delle app che utilizzano una normale suite di rapporti, fatta eccezione per la gestione delle seguenti funzionalità:

* Regole di elaborazione
* eVar/prop/listVar/eventi
* Opzione con funzione Timestamp
* Flag di dimensioni (ciclo di vita, posizione ecc.)
* Classificazioni

Questi valori vengono gestiti nella suite di rapporti principale e sono condivisi con le VRS che appartengono alla stessa suite di rapporti principale.

Le aree seguenti sono accessibili nell’interfaccia utente di Adobe Mobile Services indipendentemente dalla suite di rapporti principale:

* Il file di configurazione
* Gestire i punti di interesse
* Gestire le destinazioni dei collegamenti
* Gestione postback
* Collegamenti ai messaggi
* Acquisizione

Una VRS può aiutarti a completare le seguenti attività:

* Limitare l'accesso ai dati

   Prendiamo il caso di un'app di un'azienda multinazionale che consente di inviare dati a una suite di rapporti per tutte le geolocalità. Tuttavia, l'azienda vuole fare in modo che l'utente aziendale di una determinata regione non possa visualizzare i dati di una regione diversa. L'amministratore della società può creare una VRS per segmentare gli utenti per regione e concedere l'autorizzazione alla VRS solo all'utente aziendale che gestisce la regione.

   Questa limitazione impedisce agli utenti aziendali di visualizzare i dati che non riguardano la propria regione. Ad esempio, un utente aziendale della regione EMEA non ha necessità di vedere i dati della regione APAC.

* Consentite il controllo dei messaggi in-app/push, dei punti di interesse di posizione, dell'acquisizione e dei postback, con l'invio di tutti i dati a una singola suite di rapporti.

   Prendiamo il caso di un'azienda multinazionale che vuole inviare tutti i dati alla stessa suite di rapporti per tutte le geolocalità. Tuttavia, l'azienda vuole fare in modo che il team di marketing di ogni regione provveda alla gestione dei messaggi in-app e push solo della propria regione. L'amministratore dell'azienda può quindi creare delle VRS regionali e dare così la possibilità a ciascun team di gestire la propria app in base alla rispettiva VRS.

   Più specificamente, il team regionale crea la propria app utilizzando il file di configurazione della VRS. I dati vengono inviati alla suite di rapporti principale, ma i messaggi in-app/push, i POI di posizione, l'acquisizione e i postback sono controllati nell'app creata dalla VRS.

## Create a virtual report suite in Adobe Analytics {#section_D56B90B2653847D68ECA1F9B39204330}

>[!IMPORTANT]
>
>Solo gli amministratori di Adobe Analytics possono creare e modificare suite di rapporti virtuali in Adobe Analytics. To create a virtual report suite, see [Create virtual report suites](https://docs.adobe.com/content/help/en/analytics/components/virtual-report-suites/vrs-workflow/vrs-create.html).

Ogni VRS ha un ID univoco. Per visualizzare l'ID suite di rapporti principale nell'interfaccia utente di Adobe Mobile Services, nella pagina Gestione impostazioni app, nella sezione Informazioni **** app, fai clic su **[!UICONTROL Maggiori dettagli]**.

Nell'interfaccia di Adobe Mobile Services, puoi utilizzare una VRS per creare un'app e segmentare i dati per un gruppo specifico dell'organizzazione. In questo modo, ad esempio, un utente aziendale in Spagna non può visualizzare i dati relativi a un utente aziendale in Giappone.

>[!TIP]
>
>Non è possibile modificare i valori ereditati dalla suite di rapporti principale.

Una VRS è una definizione di segmento lato server che è associata a una suite di rapporti principale. Di conseguenza, non è possibile eseguire attività di raccolta dati su una VRS, poiché l'SDK invia gli hit solo alla suite di rapporti principale, che a sua volta li registra.

## Virtual report suite in Adobe Mobile Services and data collection {#section_8ED8FBA5B44044D9ABC2151A39C577D4}

In Adobe Mobile Services, puoi creare un'app basata su una suite di rapporti principale o virtuale. Quando crei un'app basata su una suite di rapporti virtuale, ti consigliamo di allineare il segmento VRS con la definizione dell'app.

>[!TIP]
>
>Le certificazioni push sono associate a livello di app nell'interfaccia utente di Mobile Services.

Per assicurare che i messaggi push vengano inviati correttamente, è necessario definire correttamente il segmento di pubblico. Per ulteriori informazioni, vedi [Pubblico: definire e configurare i segmenti di pubblico per i messaggi push](/help/using/in-app-messaging/t-create-push-message/c-audience-push-message.md).

## Understanding time zones {#section_498E1EED22D741C3BDED44F01FACA72A}

La proprietà Fuso orario nella pagina Gestione impostazioni app è diversa dalla proprietà Fuso orario utilizzata per creare la VRS in Adobe Analytics. La proprietà della pagina Gestione impostazioni viene ereditata dalla suite di rapporti principale, che viene utilizzata per inviare i dati a Adobe Analytics. La proprietà specificata al momento della creazione della VRS in Adobe Analytics viene utilizzata per visualizzare i rapporti nell'interfaccia utente di Mobile Services e potrebbe essere diversa dalla suite di rapporti principale.

## Select a virtual report suite in the Mobile Services UI {#section_3212D0FC01FD43DCAF30FBAA354CD6E4}

Per utilizzare una VRS quando crei un'app, selezionala dall'elenco a discesa **[!UICONTROL Suite di rapporti]** nella pagina Informazioni app. Questo elenco contiene suite di rapporti principali e virtuali.

>[!IMPORTANT]
>
>To select a VRS from the list, locate an option with the blue dot and the `vrs_` *`<company_name>`* `_` *`<unique name>`* naming convention.

## Virtual Report Suite properties {#section_20ECE6243F664C4FB4347ADB4FF0458A}

Nella tabella seguente sono riportate le proprietà delle VRS:

>[!TIP]
>
>Le proprietà di sola lettura vengono ereditate dalla suite di rapporti principale.

| Proprietà | Ereditata dalla suite di rapporti principale | Modificabile? | Note |
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
| `analytics.lifecycleTimeout` | No | Sì | Deve essere la suite di rapporti principale, se gli utenti vogliono evitare incoerenze nei loro dati. |
| `analytics.privacyDefault` | No | Sì |  |
| `analytics.batchLimit` | No | Sì |  |
| `analytics.timezone` | Sì | Sì, quando crei l'app. | Questa proprietà relativa al fuso orario viene utilizzata per inviare dati a Adobe Analytics ed è diversa dalla proprietà del fuso orario che viene impostata quando crei una VRS. |
| `analytics.timezoneOffset` | Sì | No |  |
| `analytics.referrerTimeout` | No | Sì |  |
| `analytics.backdateSessionInfo` | Sì | Sì |  |

## Informazioni aggiuntive {#section_4C4446F1FBE64F659BC0A2362C9F3E59}

Seguono alcune informazioni aggiuntive sulle suite di rapporti virtuali:

* Per ulteriori informazioni sulle VRS, vedi [Virtual Report Suites](https://docs.adobe.com/content/help/en/analytics/components/virtual-report-suites/vrs-about.html) (Suite di rapporti virtuali).
* For more information about planning a VRS implementation, see [Virtual report suite workflow](https://docs.adobe.com/content/help/en/analytics/components/virtual-report-suites/vrs-workflow/vrs-workflow.html).