---
description: Puoi creare o modificare i collegamenti di marketing per effettuare collegamenti profondi nell'app mobile o nel tuo sito web.
keywords: dispositivi mobili
seo-description: Puoi creare o modificare i collegamenti di marketing per effettuare collegamenti profondi nell'app mobile o nel tuo sito web.
seo-title: Creare o modificare collegamenti di marketing
solution: Marketing Cloud, Analytics
title: Creare o modificare collegamenti di marketing
topic: Metrics (Metriche)
uuid: 305 a 8265-38 de -4 d 19-8 c 79-b 3912 f 5 aae 7 c
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Create or edit marketing links{#create-or-edit-marketing-links}

Puoi creare o modificare i collegamenti di marketing per fornire collegamenti profondi alla tua app mobile o al tuo sito web. Per ulteriori informazioni, vedi [Collegamenti universali Apple e collegamenti app Android](/help/using/c-manage-app-settings/c-mob-confg-app/c-universal-app-links.md).

1. In your app, in the left navigation pane, expand **[!UICONTROL Acquisition]** and click **[!UICONTROL Marketing Link Builder]**.
1. Completa una delle seguenti attività:

   * To create a Marketing Link, click **[!UICONTROL Create New]**.
   * Per modificare un collegamento, fai clic sul nome del collegamento nella colonna **[!UICONTROL Titolo].**

1. Digita le informazioni nei campi seguenti:

   * **[!UICONTROL Nome collegamento marketing]**:

      **(Obbligatorio**) Specifica un nome descrittivo per il collegamento marketing. Il nome viene visualizzato solo sulla pagina Collegamenti marketing dell'interfaccia utente di Adobe Mobile Services. Un nome descrittivo può essere utile per trovare rapidamente un collegamento specifico e può fornire indicazioni sulla sua funzione.

   * **[!UICONTROL Codice di tracciamento univoco]**:

      **(Obbligatorio**) Specifica il codice di tracciamento desiderato o fai clic su (![icona Genera](assets/icon_generate.png) per creare un nuovo codice di tracciamento. Puoi visualizzare i rapporti che forniscono informazioni dettagliate sull'utilizzo del codice di tracciamento.

   * **[!UICONTROL Aggiungi dati contestuali tracciamento]**:

      **(Facoltativo**) Fai clic sull'icona **[!UICONTROL +]** e immetti le informazioni necessarie per tracciare la campagna utilizzando i dati contestuali. Nell'elenco a discesa **[!UICONTROL Dati contestuali personalizzati], seleziona un tag predefinito o uno dei tuoi tag personalizzati.** I dati contestuali vengono utilizzati per generare rapporti quando viene distribuito il collegamento marketing.

      Sono disponibili i seguenti tag preimpostati:

      * **Dati
contestuali personalizzati** Specificate la chiave e il valore. Se aggiungi dei dati contestuali personalizzati, devi creare una regola di elaborazione. Per ulteriori informazioni, consultate [Panoramica delle regole di elaborazione](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules.html).

      * **Sorgente**
Consente di specificare il referente originale, ad esempio "newsletter" o "homepage."

      * **Supporto**
Consente di specificare il canale di marketing, ad esempio "banner" o "email".

      * **Contenuto**
Specifica il nome o l'ID dell'annuncio con il collegamento.

      * **Term**
Specificare termini a pagamento o altri termini di ricerca per l'annuncio.
1. Fai clic su **[!UICONTROL Salva]**.
1. Digita le informazioni nei campi seguenti:

   * **(Obbligatorio)** Nell'URL **** di fallback, specificate l'URL a cui vengono indirizzati gli utenti quando una destinazione non trova corrispondenza (ad esempio, se l'utente si trova su un desktop o altra piattaforma che non corrisponde a una regola di destinazione).
   * In **[!UICONTROL Marketing Link Options]**, select **[!UICONTROL Interstitials]** or **[!UICONTROL Universal and App Links]**.

      Per ulteriori informazioni, vedi [Interstiziali](/help/using/acquisition-main/c-marketing-links-builder/t-create-edit-adobe-links/t-interstitials.md) o [Collegamenti universali Apple e collegamenti app Android](/help/using/c-manage-app-settings/c-mob-confg-app/c-universal-app-links.md).

   * **(Condizionale)** Se **[!UICONTROL è selezionata l'opzione Collegamenti]** universali o Collegamenti app, in **[!UICONTROL Percorso]** personalizzato gli utenti possono definire l'URL dopo il dominio con qualsiasi parametro di query. Per ulteriori informazioni, vedi [Collegamenti universali Apple e collegamenti app Android](/help/using/c-manage-app-settings/c-mob-confg-app/c-universal-app-links.md).

1. Click **[!UICONTROL Edit Deep Link Interstitial]** and configure the link.

   **(Facoltativo**) In presenza di più destinazioni, gli utenti possono essere indirizzati a seconda che abbiano installato un'app mobile. Se l'app è installata, viene visualizzata una pagina di destinazione interstiziale.

   Per ulteriori informazioni, vedi [Interstiziali](/help/using/acquisition-main/c-marketing-links-builder/t-create-edit-adobe-links/t-interstitials.md).

1. Click **[!UICONTROL Save]** and click **[!UICONTROL Next]**.
1. Nella pagina Destinazione, configura il collegamento.

   1. Click the **[!UICONTROL Decision]** icon (![decision icon](assets/icon_decision.png)) and select one of the following decision locations:

      * **[!UICONTROL Aggiungi decisione]**
      * **[!UICONTROL Aggiungi percorso]**
   1. If you selected **[!UICONTROL Add Decision]**, select one of the following decision types:

      * **[!UICONTROL Sistema operativo]**

         I sistemi operativi supportati sono: iOS, Android, AMX e altri.

      * **[!UICONTROL Tipo di dispositivo]**

         I tipi di dispositivi possono essere desktop, eReader, console giochi, telefoni cellulari, decoder e altri.
   1. Click the **[!UICONTROL Destination]** icon ( ![square icon](assets/icon_square.png) ) and select one of the following destination types:

      * **[!UICONTROL App store]**
      * **[!UICONTROL Collegamento web]**
      * **[!UICONTROL Collegamento profondo app]**
      * **[!UICONTROL Collegamento ibrido]**
      >[!TIP]
      >
      >When you use the **[!UICONTROL Web Link]** destination type with a link to the app store, acquisition is not tracked. A tale scopo, usa piuttosto il tipo di destinazione **[!UICONTROL App store].**

      Per ulteriori informazioni, consultate [Creare una nuova destinazione di collegamento](/help/using/acquisition-main/c-manage-link-destinations/t-create-new-app-deep-link-destination.md).




1. Per salvare il collegamento marketing, fai clic ![su Elipses](assets/icon_elipses.png) , quindi **[!UICONTROL Salva]**.
