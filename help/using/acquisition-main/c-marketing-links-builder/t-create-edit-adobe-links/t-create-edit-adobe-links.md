---
description: Puoi creare o modificare i collegamenti di marketing per indirizzare gli utenti verso collegamenti diretti nella tua app mobile o sul tuo sito web.
keywords: dispositivi mobili
solution: Experience Cloud,Analytics
title: Creare o modificare collegamenti di marketing
topic-fix: Metrics
uuid: 305a8265-38de-4d19-8c79-b3912f5aae7c
exl-id: a9b5c98d-77c1-4a40-96e5-f9e234d55ec5
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '614'
ht-degree: 96%

---

# Creare o modificare collegamenti di marketing {#create-or-edit-marketing-links}

Puoi creare o modificare i collegamenti di marketing per indirizzare gli utenti verso collegamenti diretti nella tua app mobile o sul tuo sito web. Per ulteriori informazioni, consulta [Collegamenti universali Apple e Collegamenti app Android](/help/using/c-manage-app-settings/c-mob-confg-app/c-universal-app-links.md).

1. Nell’app, espandi la sezione **[!UICONTROL Acquisizione]** nel pannello di navigazione a sinistra e fai clic su **[!UICONTROL Marketing Link Builder]**.
1. Completa una delle seguenti attività:

   * Per creare un collegamento di marketing, fai clic su **[!UICONTROL Crea nuovo]**.
   * Per modificare un collegamento, fai clic sul nome del collegamento nella colonna **[!UICONTROL Titolo]**.

1. Digita le informazioni nei campi seguenti:

   * **[!UICONTROL Nome collegamento marketing]**:

      (**Obbligatorio**) Specifica un nome descrittivo per il collegamento di marketing. Il nome viene visualizzato solo sulla pagina Collegamenti marketing dell’interfaccia utente di Adobe Mobile Services. Un nome descrittivo può essere utile per trovare rapidamente un collegamento specifico e può fornire indicazioni sulla sua funzione.

   * **[!UICONTROL Codice di tracciamento univoco]**:

      (**Obbligatorio**) Specifica il codice di tracciamento desiderato o fai clic su ( ![genera icona](assets/icon_generate.png) ) per creare un nuovo codice di tracciamento. Puoi visualizzare i rapporti che forniscono informazioni dettagliate sull’utilizzo del codice di tracciamento.

   * **[!UICONTROL Aggiungi dati contestuali tracciamento]**:

      (**Facoltativo**) Fai clic sull’icona **[!UICONTROL +]** e digita le informazioni richieste per tracciare la campagna utilizzando i dati contestuali. Nell’elenco a discesa **[!UICONTROL Dati contestuali personalizzati]**, seleziona un tag predefinito o uno dei tuoi tag personalizzati. I dati contestuali vengono utilizzati per registrare quando viene distribuito il collegamento di marketing.

      Sono disponibili i seguenti tag preimpostati:

      * **Dati contestuali personalizzati**
Specifica la chiave e il valore. Se aggiungi dei dati contestuali personalizzati, devi creare una regola di elaborazione. Per ulteriori informazioni, consulta [Panoramica delle regole di elaborazione](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/processing-rules/processing-rules.html) nella documentazione di Adobe Analytics.

      * **Origine**
Specifica il referente originale, ad esempio “newsletter” o “homepage”.

      * **Canale**
Specifica il canale di marketing, ad esempio “banner” o “e-mail”.

      * **Contenuto**
Specifica il nome o l’ID dell’annuncio che contiene il collegamento.

      * **Termine**
Specifica i termini a pagamento o altri termini di ricerca per l’annuncio.
1. Fai clic su **[!UICONTROL Salva]**.
1. Digita le informazioni nei campi seguenti:

   * **(Obbligatorio)** In **[!UICONTROL URL di fallback]**, specifica l’URL a cui vengono indirizzati gli utenti quando una destinazione non trova corrispondenza (ad esempio, se l’utente usa un sistema desktop o altra piattaforma che non soddisfa una regola di destinazione).
   * In **[!UICONTROL Opzioni collegamento di marketing]**, seleziona **[!UICONTROL Interstiziali]** o **[!UICONTROL Collegamenti universali o alle app]**.

      Per ulteriori informazioni, vedi [Interstiziali](/help/using/acquisition-main/c-marketing-links-builder/t-create-edit-adobe-links/t-interstitials.md) o [Collegamenti universali Apple e collegamenti alle app Android](/help/using/c-manage-app-settings/c-mob-confg-app/c-universal-app-links.md).

   * **(Condizionale)** Se è selezionata l’opzione **[!UICONTROL Collegamenti universali o alle app]**, in **[!UICONTROL Percorso personalizzato]** gli utenti possono definire l’URL dopo il dominio ed eventuali parametri di query. Per ulteriori informazioni, consulta [Collegamenti universali Apple e Collegamenti app Android](/help/using/c-manage-app-settings/c-mob-confg-app/c-universal-app-links.md).

1. Fai clic su **[!UICONTROL Modifica interstiziale collegamento diretto]** e configura il collegamento.

   (**Facoltativo**) Nelle situazioni in cui sono presenti più destinazioni, gli utenti possono essere indirizzati a seconda che abbiano installato un’app mobile o meno. Se l’app è installata, viene visualizzata una pagina di destinazione interstiziale.

   Per ulteriori informazioni, vedi   [Interstiziali](/help/using/acquisition-main/c-marketing-links-builder/t-create-edit-adobe-links/t-interstitials.md).

1. Fai clic su **[!UICONTROL Salva]** e poi su **[!UICONTROL Avanti]**.
1. Nella pagina Destinazione, configura il collegamento.

   1. Fai clic sull’icona **[!UICONTROL Decisione]** ( ![icona decisione](assets/icon_decision.png) ) e seleziona una delle posizioni di decisione seguenti:

      * **[!UICONTROL Aggiungi decisione]**
      * **[!UICONTROL Aggiungi percorso]**
   1. Se hai selezionato **[!UICONTROL Aggiungi decisione]**, seleziona uno dei seguenti tipi di decisione:

      * **[!UICONTROL Sistema operativo]**

         I sistemi operativi supportati sono: iOS, Android, AMX e altri.

      * **[!UICONTROL Tipo di dispositivo]**

         I tipi di dispositivi possono essere desktop, eReader, console giochi, telefoni cellulari, decoder e altri.
   1. Fai clic sull’icona **[!UICONTROL Destinazione]** ( ![icona quadrata](assets/icon_square.png) ) e seleziona uno dei tipi di destinazione seguenti:

      * **[!UICONTROL App store]**
      * **[!UICONTROL Collegamento web]**
      * **[!UICONTROL Collegamento profondo app]**
      * **[!UICONTROL Collegamento ibrido]**

      >[!TIP]
      >
      >Quando usi il tipo di destinazione **[!UICONTROL Collegamento web]** con un collegamento all’app store, non è possibile tenere traccia delle acquisizioni. A tale scopo, usa piuttosto il tipo di destinazione **[!UICONTROL App store]**.

      Per ulteriori informazioni, vedi [Creare una nuova destinazione di collegamento](/help/using/acquisition-main/c-manage-link-destinations/t-create-new-app-deep-link-destination.md).




1. Per salvare il collegamento di marketing, fai clic su ![ellissi](assets/icon_elipses.png), quindi su **[!UICONTROL Salva]**.
