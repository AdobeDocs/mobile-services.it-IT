---
description: Puoi configurare le opzioni SDK Analytics nella pagina Gestione impostazioni quando crei una nuova app o ne modifichi una esistente.
keywords: dispositivi mobili
solution: Experience Cloud Services,Analytics
title: Configurare le opzioni SDK Analytics
topic-fix: Metrics
uuid: fd3a21d2-6560-4e96-92fe-b99caac5e834
exl-id: f2c35b65-1052-4bfc-af9d-8778e4ff0522
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 100%

---

# Configurare le opzioni SDK Analytics {#configure-sdk-analytics-options}

Puoi configurare le opzioni SDK Analytics nella pagina Gestione impostazioni app quando crei una nuova app o ne modifichi una esistente.

Compila i seguenti campi nella sezione **[!UICONTROL Opzioni SDK Analytics]**:

* **[!UICONTROL Usa HTTPS]**

   Abilita il protocollo HTTPS per una maggiore sicurezza.

* **[!UICONTROL Retrodata hit sessioni]**

   Abilita o disabilita la possibilità di Adobe SDK di retrodatare gli hit di informazioni delle sessioni. Gli hit di informazioni delle sessioni al momento consistono di arresti anomali e durata della sessione. Se questa opzione è abilitata, Adobe SDK retrodaterà l’hit di informazioni della sessione a 1 secondo dopo l’ultimo hit della sessione precedente. Ciò significa che i dati di arresto anomalo e di sessione saranno correlati alla data corretta in cui si sono verificati. Sarà retrodatato un hit per ogni nuovo avvio dell’applicazione. Se l’opzione è disabilitata, Adobe SDK assocerà le informazioni di sessione al ciclo di vita corrente.

* **[!UICONTROL Privacy]**

   Seleziona un’opzione di privacy:

   * **[!UICONTROL Invia dati fino a rinuncia]**
   * **[!UICONTROL Mantieni dati fino a consenso]**

* **[!UICONTROL Timeout sessione (secondi)]**

   Specifica il valore di timeout della sessione.

   Il valore predefinito è 300 secondi. Specifica il tempo, in secondi, che deve trascorrere tra il momento in cui l’app viene avviata e quello in cui l’avvio viene considerato come una nuova sessione. Questo timeout si applica anche quando l’applicazione viene messa in background e riattivata. Il tempo trascorso in background dall’app non viene incluso nella durata della sessione.

* **[!UICONTROL Limite batch]**

   Specifica quanti hit mettere in coda prima di inviare i dati.

   Imposta questo valore su 0 per inviare gli hit immediatamente. Il limite batch rappresenta la soglia per il numero di hit da inviare in chiamate consecutive. Ad esempio, se questa opzione è impostata su 10, ogni hit prima del decimo viene memorizzato nella coda. All’arrivo del decimo hit, tutti i 10 hit in coda vengono inviati consecutivamente.

* **[!UICONTROL Maggiori dettagli]**

   Fai clic sul collegamento **[!UICONTROL Maggiori dettagli]** per visualizzare l’ID della suite di rapporti e il server di tracciamento, abilitare o disabilitare il tracciamento offline e visualizzare il modello di codifica dei caratteri in uso (ad esempio UTF-8).

   Quando il tracciamento offline è abilitato, i dati generati dal dispositivo offline vengono contrassegnati con una marca temporale e inviati in un secondo momento. Se questa opzione è disabilitata, i dati offline vengono scartati.
