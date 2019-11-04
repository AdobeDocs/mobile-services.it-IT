---
description: I postback consentono di inviare i dati raccolti da Adobe Mobile a un altro server di terze parti. Sfruttando le caratteristiche e gli attivatori utilizzati per visualizzare un messaggio in-app, puoi configurare Mobile Services per l’invio di dati personalizzati a una destinazione terza.
seo-description: I postback consentono di inviare i dati raccolti da Adobe Mobile a un altro server di terze parti. Sfruttando le caratteristiche e gli attivatori utilizzati per visualizzare un messaggio in-app, puoi configurare Mobile Services per l’invio di dati personalizzati a una destinazione terza.
seo-title: Configurare i postback
title: Configurare i postback
uuid: a026575c-057b-4868-b6c8-9514cbc32b4d
translation-type: ht
source-git-commit: d028fe0f9477bc011aa8fda21a0a389808df0fce

---


# Configurare i postback {#configure-postbacks}

I postback consentono di inviare i dati raccolti da Adobe Mobile a un altro server di terze parti. Sfruttando le caratteristiche e gli attivatori utilizzati per visualizzare un messaggio in-app, puoi configurare Mobile Services per l’invio di dati personalizzati a una destinazione terza.

>[!IMPORTANT]
>
>Per utilizzare i postback devi installare SDK 4.6 o successivo. Per maggiori informazioni, vedi [Android - Postback](/help/android/analytics-main/postbacks/postbacks.md) o [iOS - Postback](/help/ios/analytics-main/postback/postback.md).

1. Fai clic sul nome dell’app desiderata per passare alla relativa pagina Gestione impostazioni app, quindi fai clic sul collegamento **[!UICONTROL Gestione postback]** in alto a destra.
1. Fai clic su **[!UICONTROL Crea postback]**.
1. Compila i seguenti campi:

   * **[!UICONTROL Tipo di postback]**

      Scegli **[!UICONTROL Personalizzato]**. I modelli saranno disponibili in futuro.

   * **[!UICONTROL Nome]**

      Inserisci un nome descrittivo il postback.

   * **[!UICONTROL URL]**

      Specifica un URL di endpoint valido (con i parametri di query necessari per le richieste GET). Puoi ottenere questo URL dalla parte a cui stai inviando i dati (server di annunci pubblicitari o il tuo proprio endpoint). Ad esempio `https://my.server.com/?user=bob&amp;zip=90210&amp;c16=4.6.0-iOS&amp;c27=cln,132`.

   * **[!UICONTROL Variabile di contesto]**

      Evidenzia parti dell’URL e seleziona la variabile di contesto desiderata dall’elenco a discesa. Puoi anche inserire le variabili di contesto nell’URL e l’URL sostituirà tutte le variabili di modello con i valori dell’hit.

   * **[!UICONTROL Aggiungi corpo del post]**

      Specifica l’eventuale contenuto aggiuntivo per il corpo del post, ad esempio per una richiesta POST. Se specifichi il testo del corpo del post, indica anche il relativo tipo di contenuto. Ad esempio, `application/json`.

   * **[!UICONTROL Timeout (in secondi)]**

      Specifica il tempo (in secondi) per l’attesa del postback.

   * **[!UICONTROL Attivatore/i]**

      Specifica i tag di dati e le condizioni che attivano il postback. Ad esempio, puoi scegliere **[!UICONTROL Arresto anomalo]** come attivatore ed **[!UICONTROL Esiste]** come condizione che attiva il postback quando l’app subisce un arresto anomalo. Puoi anche specificare quali metriche attivano il postback. Ad esempio, puoi scegliere **[!UICONTROL Nome del dispositivo]** come attivatore ed **[!UICONTROL È uguale a]** e **[!UICONTROL iPhone 6 Plus]** come condizioni che attivano il postback quando l’app subisce un arresto anomalo su dispositivi iPhone 6 Plus.

   * **[!UICONTROL Caratteristiche]**
   Specifica chi può visualizzare il messaggio quando viene attivato. Le opzioni disponibili sono **[!UICONTROL Durata sessione**, **[!UICONTROL Data primo avvio]** e **[!UICONTROL ID app]**.

1. Fai clic su **[!UICONTROL Salva]** per creare il postback e aggiungerlo all’elenco **[!UICONTROL Gestione postback]**.

   Per attivare il postback in futuro, effettua una delle operazioni seguenti:

   * Seleziona la casella di controllo accanto al postback nell’elenco **[!UICONTROL Gestione postback]**, quindi fai clic su **[!UICONTROL Attiva selezionati]**.
   * Fai clic su **[!UICONTROL Salva e attiva]** per salvare le modifiche e attivare immediatamente il postback.
