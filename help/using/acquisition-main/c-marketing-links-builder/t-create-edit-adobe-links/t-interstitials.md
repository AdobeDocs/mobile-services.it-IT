---
description: Puoi indirizzare gli utenti a una particolare destinazione a seconda che abbiano installato l'app (un collegamento profondo nell'app) o meno (un sito web o un app store).
keywords: dispositivi mobili
seo-description: Puoi indirizzare gli utenti a una particolare destinazione a seconda che abbiano installato l'app (un collegamento profondo nell'app) o meno (un sito web o un app store).
seo-title: Interstiziali
solution: Marketing Cloud,Analytics
title: Interstiziali
topic: Metrics (Metriche)
uuid: 7dce8ab2-2a5d-4384-ac1e-e31dfaa33654
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Interstiziali{#interstitials}

Puoi indirizzare gli utenti a una particolare destinazione a seconda che abbiano installato l'app (un collegamento profondo nell'app) o meno (un sito web o un app store). È meglio lasciare agli utenti la scelta della destinazione. Gli addetti al marketing possono configurare una pagina interstiziale che proponga agli utenti una serie di possibili pagine di destinazione tra cui scegliere.

Per configurare una pagina interstiziale durante la creazione di un collegamento marketing:

1. Click **[!UICONTROL Edit Deep Link Interstitial]**.

   ![Interstiziale collegamento profondo](assets/interstitial2.png)

1. Digita le informazioni nei campi seguenti:

   * **[!UICONTROL HTML personalizzato]**

      Seleziona la tua pagina HTML interstiziale.

      Utilizzando interstiziali personalizzati, gli addetti al marketing possono personalizzare le pagine di destinazione interstiziali con codice HTML/CSS/JS personalizzato, per aggiungere elementi di branding alle pagine.

      I requisiti per la pagina HTML sono i seguenti:

      * Deve essere un file HTML.
      * Must contain the `%%DEST%%` and `%%FALLBACK%%` placeholders.
      * Il codice HTML caricato deve essere servito in un `<iframe>`.

         Le tue destinazioni di collegamento devono puntare a una finestra principale. You can include `<base target="_parent" />` in `<head>` or specify a target property for each `<a/>` individually.

         >[!TIP]
         >
         >If you upload custom HTML, the other four options in this table will not be used unless you remove the uploaded file.
   * **[!UICONTROL URL immagine]**

      Specifica l'URL di una risorsa di immagine.

   * **[!UICONTROL Corpo del testo]**

      Specifica il corpo del testo per l'interstiziale.

   * **[!UICONTROL Testo di conferma]**

      Specifica il testo per il pulsante di conferma.

   * **[!UICONTROL Testo di riserva]**

      Specifica il testo di riserva da visualizzare.

      Questo campo aggiorna il pulsante di testo se un collegamento profondo non giunge a destinazione. Gli utenti vengono invitati a provare il collegamento profondo prima di ricorrere a un'altra opzione. Ad esempio, la destinazione alternativa potrebbe essere un app store da cui scaricare e installare l'app oppure il sito web dell'azienda. Il testo di riserva segnala agli utenti che è disponibile un'altra azione se il collegamento profondo non funziona.


1. (**Optional**) Click the icons above the image to see how the interstitial looks rotated and on different devices.

   Puoi cambiare o modificare l'immagine fuori da Mobile Services per assicurarti che sia visualizzata correttamente in situazioni diverse.
1. Fai clic su **[!UICONTROL Salva]**.
