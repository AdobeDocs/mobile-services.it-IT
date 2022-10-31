---
description: Quando si personalizzano i rapporti, l’ampia flessibilità può far sorgere alcune domande rispetto al tipo di rapporto più adatto per ottenere i dati necessari.
keywords: dispositivi mobili
solution: Experience Cloud Services,Analytics
title: Tipi di rapporti
topic-fix: Reports,Metrics
uuid: 8747b11e-31b1-47bc-ad55-db5ab4ef7078
exl-id: ba7af2f5-8c84-4c49-a793-5fbaa8947566
source-git-commit: 7cfaa5f6d1318151e87698a45eb6006f7850aad4
workflow-type: tm+mt
source-wordcount: '743'
ht-degree: 100%

---

# Tipi di rapporti {#report-types}

{#eol}

Quando si personalizzano i rapporti, l’ampia flessibilità può far sorgere alcune domande rispetto al tipo di rapporto più adatto per ottenere i dati necessari.

Prima di personalizzare un rapporto, è importante comprendere la differenza tra una metrica e una dimensione.

* Metrica

   La metrica viene utilizzata per misurare i dati. Le metriche sono valori che possono essere contati e sommati; sono utilizzate per sapere con quale frequenza si verificano azioni specifiche nell’app. Alcune metriche comuni sono installazioni, avvii, ricavi, valore del ciclo di vita e accessi. Ad esempio, ogni volta che l’app viene avviata,   gli   _launches_value viene incrementato di un’unità.

* Dimensione

   La dimensione viene utilizzata per descrivere i dati. Le dimensioni sono rappresentate da una stringa o un numero che funge da stringa (ad esempio, un codice postale) e vengono utilizzate per organizzare e segmentare i dati. Esempi comuni di dimensioni sono la versione del sistema operativo, il nome della campagna, il nome del prodotto e l’operatore di telefonia mobile. A ciascuna dimensione sono associati dei valori specifici. Ad esempio, la dimensione di versione del sistema operativo può avere valori quali _iOS 7_ e _Android 4.1.2_.

Di seguito sono elencati i tipi d rapporti che è possibile generare nell’interfaccia utente di Mobile:

## Rapporto nel tempo {#section_2741DA54C90C49AFB17C7B9BC7AD627D}

I rapporti nel tempo, o temporali, mostrano le prestazioni delle metriche in un intervallo di tempo e permettono di individuare rapidamente picchi e tendenze. Spesso l’analisi inizia con un rapporto temporale, quindi si passa a rapporti con tendenze e classifica per approfondire la ricerca e individuare i fattori che contribuiscono a un particolare picco o a una tendenza della metrica.

Ad esempio, se osservi un picco negli avvii, puoi eseguire un rapporto con tendenze che mostra gli avvii per i primi cinque sistemi operativi, per individuare i sistemi operativi che contribuiscono maggiormente al picco negli avvii:

![](assets/overtime.png)

Per visualizzare i valori delle dimensioni con altre metriche in un rapporto temporale, puoi utilizzare la metrica delle istanze e definire un filtro dimensione.

## Rapporto con tendenze   {#section_C9BE9A2EDBFF4D938B9AF14C8AA67883}

I rapporti con tendenze consentono di vedere le prestazioni delle dimensioni più comuni rispetto a una specifica metrica. Puoi utilizzare questo rapporto per determinare quali valori contribuiscono maggiormente a un cambiamento osservato in una metrica.

![](assets/trended.png)

Per visualizzare un rapporto con tendenze per una dimensione, aggiungi un filtro fisso (ad esempio, Sistema operativo = iOS 6.0.1) a un rapporto temporale per visualizzarne i dati. Inoltre, puoi aggiungere al rapporto temporale filtrato cinque ulteriori metriche.

## Rapporto nel tempo filtrato {#section_F8FAF2A4496F449CA99EF1E052C71A2D}

Se desideri visualizzare un valore di dimensione specifico, puoi aggiungere un filtro fisso a un rapporto nel tempo, o temporale. Il rapporto seguente mostra 30 giorni di avvii, aggiornamenti e arresti per una versione specifica di un sistema operativo.

![](assets/overtime-filter.png)

## Rapporto con classifica {#section_C073D744A95843AF99EE74FB5B013735}

I rapporti con classifica mostrano la frequenza con cui le prime 50 dimensioni contribuiscono a determinare una metrica. Tale rapporto è utile per visualizzare il contributo totale di un intervallo di date su un grande numero di valori.

![](assets/ranked.png)

## Rapporti sunburst   {#section_17A9842039174DE094A6B1E9837E35BB}

I rapporti sunburst forniscono, ad esempio, il rapporto di base con raggruppamenti. La visualizzazione utilizza l’altezza per mostrare la metrica e le differenze di prestazioni tra le metriche. Ogni cerchio concentrico rappresenta un segmento di pubblico nella categoria del dato cerchio. Puoi intraprendere azioni su un pubblico, quali l’applicazione di un filtro fisso e la visualizzazione di metriche.

Puoi visualizzare il rapporto in un’esercitazione interna al prodotto che descrive come interagire con un grafico sunburst.

Per avviare l’esercitazione:

1. In Gestione impostazioni app, fai clic su **[!UICONTROL Utilizzo]**.

1. Fai clic su **[!UICONTROL Tecnologia]** > **[!UICONTROL Suddivisione tecnologia]**.
1. Nella barra del titolo del rapporto, fai clic su **[!UICONTROL Personalizza]**, quindi fai clic sull’icona delle informazioni.

![](assets/report_technology.png)

### Rapporto di percorsi {#section_AD400106BC684B50B27CCCD3F4497114}

Un rapporto di percorsi, basato sull’analisi dei percorsi, consiste in un grafico che rappresenta i percorsi seguiti per passare da uno stato dell’app a un altro stato.

![](assets/action_paths.png)

Ogni nodo ha la forma di una casella e rappresenta uno stato nei percorsi seguiti dall’utente attraverso un’app. Ad esempio, nell’immagine qui sopra, il nodo più in alto rappresenta il numero di utenti che hanno avviato l’app e poi scelto una foto dalla galleria.

### Rapporto Funnel   {#section_AF3B0C899D844FC3AD1F91A2C452C92F}

Un rapporto funnel consente di determinare dove i clienti abbandonano una campagna di marketing o deviano da un percorso di conversione definito durante l’interazione con la tua app mobile. Puoi usare il rapporto funnel anche per confrontare le azioni di segmenti diversi.

La visualizzazione funnel permette di vedere in quale fase del processo si verifica l’abbandono da parte del cliente. Grazie alla visibilità delle decisioni dei clienti in ogni fase, puoi comprendere più facilmente in quale momento vengono scoraggiati, che percorso tendono a seguire e quando i clienti abbandonano l’app.

![](assets/funnel.png)
