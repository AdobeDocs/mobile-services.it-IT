---
description: Puoi indirizzare gli utenti a una particolare destinazione a seconda che abbiano installato l’app (un collegamento profondo nell’app) o meno (un sito web o un app store).
keywords: mobile
seo-description: Puoi indirizzare gli utenti a una particolare destinazione a seconda che abbiano installato l’app (un collegamento profondo nell’app) o meno (un sito web o un app store).
seo-title: Interstiziali
solution: Experience Cloud,Analytics
title: Interstiziali
topic: Metrics
uuid: 7dce8ab2-2a5d-4384-ac1e-e31dfaa33654
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 85%

---


# Interstiziali{#interstitials}

Puoi indirizzare gli utenti a una particolare destinazione a seconda che abbiano installato l’app (un collegamento profondo nell’app) o meno (un sito web o un app store). È meglio lasciare agli utenti la scelta del percorso. Gli addetti al marketing possono configurare una pagina interstiziale che mostri agli utenti le destinazioni di destinazione disponibili.

Per configurare una pagina interstiziale durante la  creazione di un collegamento di marketing:

1. Fai clic su **[!UICONTROL Modifica interstiziale collegamento diretto]**.

   ![Interstiziale collegamento diretto](assets/interstitial2.png)

1. Digita le informazioni nei campi seguenti:

   * **[!UICONTROL HTML personalizzato]**

      Seleziona la tua pagina HTML interstiziale.

      Utilizzando interstiziali personalizzati, gli addetti al marketing possono personalizzare le pagine di destinazione interstiziali con codice HTML/CSS/JS personalizzato, per aggiungere elementi di branding alle pagine.

      I requisiti per la pagina HTML sono i seguenti:

      * Deve essere un file HTML.
      * Deve contenere sia `%%DEST%%` sia `%%FALLBACK%%` come segnaposto.
      * Il codice HTML caricato deve essere servito in un `<iframe>`.

         Le tue destinazioni di collegamento devono puntare a una finestra principale. Puoi includere `<base target="_parent" />` in `<head>` oppure specificare una proprietà target specifica per ogni `<a/>`.

         >[!TIP]
         >
         >Se carichi un file HTML personalizzato, le altre quattro opzioni di questa tabella non vengono utilizzate a meno che tu non rimuova il file caricato.
   * **[!UICONTROL URL immagine]**

      Specifica l’URL di una risorsa di immagine.

   * **[!UICONTROL Corpo del testo]**

      Specifica il corpo del testo per l’interstiziale.

   * **[!UICONTROL Testo di conferma]**

      Specifica il testo per il pulsante di conferma.

   * **[!UICONTROL Testo di riserva]**

      Specificate il testo di riserva da visualizzare.

      Questo campo aggiorna il pulsante di testo se un collegamento profondo non riesce. Gli utenti vengono invitati a provare il collegamento profondo prima di ricorrere a un’altra opzione. Ad esempio, la destinazione alternativa potrebbe essere un app store da cui scaricare e installare l’app oppure il sito web dell’azienda. Il testo di riserva segnala agli utenti che è disponibile un’altra azione se il collegamento profondo non funziona.


1. (**Facoltativo**) Fai clic sulle icone sopra l’immagine per controllare l’aspetto dell’interstiziale quando è ruotato e su diversi dispositivi.

   Puoi cambiare o modificare l’immagine fuori da Mobile Services per assicurarti che sia visualizzata correttamente in situazioni diverse.
1. Fai clic su **[!UICONTROL Salva]**.
