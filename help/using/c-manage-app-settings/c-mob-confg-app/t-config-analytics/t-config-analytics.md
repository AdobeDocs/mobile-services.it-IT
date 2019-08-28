---
description: Puoi configurare le Opzioni SDK Analytics nella pagina Gestione impostazioni quando crei una nuova app o ne modifichi una esistente.
keywords: dispositivi mobili
seo-description: Puoi configurare le opzioni SDK Analytics nella pagina Gestione impostazioni quando crei una nuova app o ne modifichi una esistente.
seo-title: Configurare le opzioni SDK Analytics
solution: Marketing Cloud, Analytics
title: Configurare le opzioni SDK Analytics
topic: Metrics (Metriche)
uuid: fd 3 a 21 d 2-6560-4 e 96-92 fe-b 99 caac 5 e 834
translation-type: tm+mt
source-git-commit: d028fe0f9477bc011aa8fda21a0a389808df0fce

---


# Configure SDK Analytics options {#configure-sdk-analytics-options}

Puoi configurare le opzioni SDK Analytics nella pagina Gestione impostazioni quando crei una nuova app o ne modifichi una esistente.

Type information in the following fields under **[!UICONTROL SDK Analytics Options]**:

* **[!UICONTROL Usa HTTPS]**

   Abilita il protocollo HTTPS per una maggiore sicurezza.

* **[!UICONTROL Retrodata hit sessioni]**

   Abilita o disabilita la capacità di Adobe SDK di retrodatare gli hit delle informazioni delle sessioni. Gli hit di informazioni delle sessioni al momento consistono di arresti anomali e durata della sessione. Se questa opzione è abilitata, Adobe SDK retrodaterà l'hit di informazioni della sessione a 1 secondo dopo l'ultimo hit della sessione precedente. Ciò significa che gli arresti anomali e i dati delle sessioni saranno correlati alla data corretta in cui si sono verificati. Sarà retrodatato un hit per ogni nuovo avvio dell'applicazione. Se l'opzione è disabilitata, Adobe SDK assocerà le informazioni di sessione al ciclo di vita corrente.

* **[!UICONTROL Privacy]**

   Seleziona un'opzione di privacy:

   * **[!UICONTROL Invia dati fino a rinuncia]**
   * **[!UICONTROL Mantieni dati fino a consenso]**

* **[!UICONTROL Timeout sessione (secondi)]**

   Specifica il valore di timeout della sessione.

   Il valore predefinito è 300 secondi. Specifica l’intervallo di tempo, in secondi, che deve trascorrere tra un avvio dell’app e quello successivo affinché questo sia considerato come una nuova sessione. Il timeout viene applicato anche quando l’applicazione viene lasciata in background e poi riattivata. Il tempo durante il quale l’app rimane in background non viene incluso nella durata della sessione.

* **[!UICONTROL Limite batch]**

   Specifica quanti hit mettere in coda prima di inviare i dati.

   Imposta questo valore su 0 per inviare gli hit immediatamente. Il limite batch rappresenta la soglia per il numero di hit da inviare in chiamate consecutive. Ad esempio, se questa opzione è impostata su 10, ogni hit prima del decimo viene memorizzato nella coda. Quando arriva il 10° hit, tutti i 10 hit vengono inviati consecutivamente.

* **[!UICONTROL Maggiori dettagli]**

   Fai clic sul collegamento **[!UICONTROL Maggiori dettagli]per visualizzare l'ID suite di rapporti e il server di tracciamento, abilitare o disabilitare il tracciamento offline e visualizzare il modello di codifica dei caratteri in uso (ad esempio UTF-8).**

   Quando il tracciamento offline è abilitato, i dati generati dal dispositivo offline vengono contrassegnati con marca temporale e inviati in un secondo momento. Se questa opzione è disabilitata, i dati offline vengono scartati.
