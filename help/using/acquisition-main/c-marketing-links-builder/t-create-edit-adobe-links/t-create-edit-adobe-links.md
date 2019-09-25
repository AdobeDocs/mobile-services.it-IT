---
description: Puoi creare o modificare collegamenti di marketing per fornire collegamenti profondi nella tua app mobile o nel tuo sito web.
keywords: dispositivi mobili
seo-description: Puoi creare o modificare collegamenti di marketing per fornire collegamenti profondi nella tua app mobile o nel tuo sito web.
seo-title: Creare o modificare collegamenti di marketing
solution: Marketing Cloud,Analytics
title: Creare o modificare collegamenti di marketing
topic: Metrics (Metriche)
uuid: 305a8265-38de-4d19-8c79-b3912f5aae7c
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Create or edit marketing links{#create-or-edit-marketing-links}

Puoi creare o modificare collegamenti di marketing per fornire collegamenti profondi alla tua app mobile o al tuo sito web. Per ulteriori informazioni, consulta Collegamenti universali [Apple e Collegamenti alle](/help/using/c-manage-app-settings/c-mob-confg-app/c-universal-app-links.md)app Android.

1. In your app, in the left navigation pane, expand **[!UICONTROL Acquisition]** and click **[!UICONTROL Marketing Link Builder]**.
1. Completa una delle seguenti attività:

   * To create a Marketing Link, click **[!UICONTROL Create New]**.
   * Per modificare un collegamento, fai clic sul nome del collegamento nella colonna **[!UICONTROL Titolo].**

1. Digita le informazioni nei campi seguenti:

   * **[!UICONTROL Nome collegamento marketing]**:

      (**Required**) Specify a descriptive name for your Marketing Link. Il nome viene visualizzato solo sulla pagina Collegamenti marketing dell'interfaccia utente di Adobe Mobile Services. Un nome descrittivo può essere utile per trovare rapidamente un collegamento specifico e può fornire indicazioni sulla sua funzione.

   * **[!UICONTROL Codice di tracciamento univoco]**:

      (**Required**) Specify the desired tracking code or click (![generate icon](assets/icon_generate.png) to create a new tracking code. Puoi visualizzare i rapporti che forniscono informazioni dettagliate sull'utilizzo del codice di tracciamento.

   * **[!UICONTROL Aggiungi dati contestuali tracciamento]**:

      (**Optional**) Click the **[!UICONTROL +]** icon and type the relevant information to track your campaign using context data. Nell'elenco a discesa **[!UICONTROL Dati contestuali personalizzati], seleziona un tag predefinito o uno dei tuoi tag personalizzati.** I dati contestuali vengono utilizzati per generare rapporti quando viene distribuito il collegamento di marketing.

      Sono disponibili i seguenti tag preimpostati:

      * **Dati** contestuali personalizzati Specificate la chiave e il valore. Se aggiungi dei dati contestuali personalizzati, devi creare una regola di elaborazione. Per ulteriori informazioni, vedere Panoramica [sulle regole di](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules.html)elaborazione.

      * **Origine** Specifica il referente originale, ad esempio "newsletter" o "homepage".

      * **Media** Specificate il canale di marketing, ad esempio "banner" o "email".

      * **Contenuto** Specificate il nome o l'ID dell'annuncio con il collegamento.

      * **Termine** Specifica i termini a pagamento o altri termini di ricerca per l'annuncio.
1. Fai clic su **[!UICONTROL Salva]**.
1. Digita le informazioni nei campi seguenti:

   * **(Obbligatorio)** In URL **** di fallback, specificate l'URL a cui vengono indirizzati gli utenti quando una destinazione non corrisponde (ad esempio, se l'utente si trova su un desktop o su un'altra piattaforma che non corrisponde a una regola di destinazione).
   * In **[!UICONTROL Marketing Link Options]**, select **[!UICONTROL Interstitials]** or **[!UICONTROL Universal and App Links]**.

      Per ulteriori informazioni, vedi [Interstiziali](/help/using/acquisition-main/c-marketing-links-builder/t-create-edit-adobe-links/t-interstitials.md) o collegamenti universali [Apple e collegamenti](/help/using/c-manage-app-settings/c-mob-confg-app/c-universal-app-links.md)alle app Android.

   * **(Condizionale)** Se è selezionata l’opzione Collegamenti **** universali o alle app, in Percorso **** personalizzato gli utenti possono definire l’URL dopo il dominio con qualsiasi parametro di query. Per ulteriori informazioni, consulta Collegamenti universali [Apple e Collegamenti alle](/help/using/c-manage-app-settings/c-mob-confg-app/c-universal-app-links.md)app Android.

1. Click **[!UICONTROL Edit Deep Link Interstitial]** and configure the link.

   (**Optional**) When there are multiple destinations, users can be routed depending on whether they have a mobile app installed. Se l'app è installata, viene visualizzata una pagina di destinazione interstiziale.

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

      Per ulteriori informazioni, vedi [Creare una nuova destinazione](/help/using/acquisition-main/c-manage-link-destinations/t-create-new-app-deep-link-destination.md)di collegamento.




1. Per salvare il collegamento di marketing, fate clic su ![elipses](assets/icon_elipses.png) , quindi su **[!UICONTROL Save (Salva]**).
