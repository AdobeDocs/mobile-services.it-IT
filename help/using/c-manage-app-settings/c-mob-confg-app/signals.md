---
description: I postback consentono di inviare i dati raccolti da Adobe Mobile a un altro server di terze parti. Sfruttando le caratteristiche e gli attivatori utilizzati per visualizzare un messaggio in-app, puoi configurare Mobile Services per l'invio di dati personalizzati a una destinazione terza.
seo-description: I postback consentono di inviare i dati raccolti da Adobe Mobile a un altro server di terze parti. Sfruttando le caratteristiche e gli attivatori utilizzati per visualizzare un messaggio in-app, puoi configurare Mobile Services per l'invio di dati personalizzati a una destinazione terza.
seo-title: Configurare i postback
title: Configurare i postback
uuid: a 026575 c -057 b -4868-b 6 c 8-9514 cbc 32 b 4 d
translation-type: tm+mt
source-git-commit: d028fe0f9477bc011aa8fda21a0a389808df0fce

---


# Configure postbacks {#configure-postbacks}

I postback consentono di inviare i dati raccolti da Adobe Mobile a un altro server di terze parti. Sfruttando le caratteristiche e gli attivatori utilizzati per visualizzare un messaggio in-app, puoi configurare Mobile Services per l'invio di dati personalizzati a una destinazione terza.

>[!IMPORTANT]
>
>Per utilizzare i postback, devi installare l'SDK 4.6 o successivo. Per maggiori informazioni, vedi [Android - Postback](/help/android/analytics-main/postbacks/postbacks.md) o [iOS - Postback](/help/ios/analytics-main/postback/postback.md).

1. Fai clic sul nome dell'app desiderata per passare alla relativa pagina Gestione impostazioni app, quindi fai clic sul collegamento **Gestione postback** in alto a destra.
1. Fai clic su **[!UICONTROL Crea postback]**.
1. Compila i seguenti campi:

   * **[!UICONTROL Tipo di postback]**

      Scegli **[!UICONTROL Personalizzato]**. I modelli saranno disponibili in futuro.

   * **[!UICONTROL Nome]**

      Inserisci un nome descrittivo il postback.

   * **[!UICONTROL URL]**

      Specifica un URL di endpoint valido (con i parametri di query appropriati per le richieste GET). Puoi ottenere questo URL dalla parte a cui stai inviando i dati (server di annunci pubblicitari o il tuo proprio endpoint). Ad esempio `https://my.server.com/?user=bob&amp;zip=90210&amp;c16=4.6.0-iOS&amp;c27=cln,132`.

   * **[!UICONTROL Variabile di contesto]**

      Evidenzia parti dell'URL e seleziona la variabile di contesto desiderata dall'elenco a discesa. Puoi anche inserire variabili di contesto nell'URL e l'URL sostituirà tutte le variabili di modello con i valori dell'hit.

   * **[!UICONTROL Aggiungi corpo del post]**

      Specifica l'eventuale contenuto aggiuntivo per il corpo del post, ad esempio per una richiesta POST. Se specificate il testo del corpo del post, specificate il tipo di contenuto per il corpo del post. Ad esempio, `application/json`.

   * **[!UICONTROL Timeout (in secondi)]**

      Specifica il tempo (in secondi) per l'attesa del postback.

   * **[!UICONTROL Attivatore/i]**

      Specifica i tag di dati e le condizioni che attivano il postback. For example, you might choose **[!UICONTROL Crashed]** as the trigger and **[!UICONTROL Exists]** as the condition to trigger the postback when the app crashes. Puoi anche specificare quali metriche attivano il postback. For example, you can select **[!UICONTROL Device Name]** as the trigger, **[!UICONTROL Equals]**, and **[!UICONTROL iPhone 6 Plus]** as conditions to activate the postback when the app crashes on iPhone 6 Plus devices.

   * **[!UICONTROL Caratteristiche]**
   Specifica chi può visualizzare il messaggio quando viene attivato. Options include **[!UICONTROL Session Length**, **[!UICONTROL First Launch Date]**, and **[!UICONTROL App ID]**.

1. Fai clic su **[!UICONTROL Salva]** per creare il postback e aggiungerlo all'elenco **Gestione postback[!UICONTROL .]**

   Per attivare il postback in futuro, effettua una delle operazioni seguenti:

   * Seleziona la casella di controllo accanto al postback nell'elenco **[!UICONTROL Gestione postback]**, quindi fai clic su **[!UICONTROL Attiva selezionati]**.
   * Fai clic su **[!UICONTROL Salva e attiva]per salvare le modifiche e attivare immediatamente il postback.**
