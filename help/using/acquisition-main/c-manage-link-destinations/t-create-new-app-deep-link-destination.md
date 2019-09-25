---
description: Puoi creare una nuova destinazione di collegamento che indirizza gli utenti a un collegamento web o a un collegamento profondo all'interno dell'app.
keywords: dispositivi mobili
seo-description: Puoi creare una nuova destinazione di collegamento che indirizza gli utenti a un collegamento web o a un collegamento profondo all'interno dell'app.
seo-title: Creare una nuova destinazione di collegamento
solution: Marketing Cloud,Analytics
title: Creare una nuova destinazione di collegamento
topic: Metrics (Metriche)
uuid: 390e3dea-0221-4f97-980d-a90ca9f162fa
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Create a new link destination {#create-new-link-destination}

Puoi creare una nuova destinazione di collegamento che indirizza gli utenti a un collegamento web o a un collegamento profondo all'interno dell'app.

1. In the Mobile Services UI, click **[!UICONTROL Manage Apps]**.
1. Fai clic sul nome dell'app per visualizzare la pagina Informazioni app corrispondente.
1. Fai clic su **[!UICONTROL Gestione destinazioni collegamenti]**.
1. Fai clic su **[!UICONTROL Crea nuovo]**.
1. Digita le informazioni nei campi seguenti:
   * **[!UICONTROL Titolo]**

      Type a descriptive name for your App Link destination. Il titolo viene visualizzato solo sulla pagina Gestione destinazioni collegamenti dell'interfaccia utente di Adobe Mobile Services. Un nome descrittivo può essere utile per trovare rapidamente una destinazione di collegamento specifica e può fornire indicazioni sulla sua funzione.

   * **[!UICONTROL Tipo di collegamento]**

      Elenco dei tipi di collegamento disponibili:

      * **[!UICONTROL Collegamento profondo app]**

         Provide a URI schema deep link (for example, `yourapp://section`). Le destinazioni di collegamento profondo nelle app sono collegamenti profondi con schema URI che indirizzano l'utente a un collegamento “in profondità” all'interno dell'app, ad esempio a una linea di prodotti specifica nell'app mobile di un retailer online.

      * **[!UICONTROL Collegamento web]**

         Type a web HTTP or HTTPS URL, for example,`https://adobe.com`. Le destinazioni di collegamento web indirizzano gli utenti a un URL, ad esempio una linea di prodotti specifica nel sito web di un retailer online.

      * **[!UICONTROL Collegamento ibrido]**

         Type an iOS Universal Link or an Android App Link (for example, `https://yourwebsite.com`). I collegamenti ibridi supportano i collegamenti universali iOS o i collegamenti ad app Android.
   * **[!UICONTROL App]** Selezionate l'app associata al collegamento che desiderate fornire.

      >[!TIP]
      >
      >This information is required only if you selected an App Deep Link or a Hybrid Link in **[!UICONTROL Link Type]**. Se l'app desiderata non figura nell'elenco di selezione, fai clic su **[!UICONTROL Aggiungi nuova app]per indicare una nuova app da un app store.**

   * **[!UICONTROL Tipo di collegamento]**

      Type the actual URL for the link you selected. L'etichetta di questo campo varia a seconda del tipo di collegamento selezionato.

   * **[!UICONTROL Note]**

      Inserisci eventuali note aggiuntive sulla destinazione. Le note aggiuntive vengono visualizzate solo sulla pagina Gestione destinazioni collegamenti dell'interfaccia utente di Adobe Mobile Services. Possono essere utili per aiutare altri utenti della tua organizzazione a trovare rapidamente una destinazione di collegamento specifica e fornire indicazioni sulla sua funzione, sulla campagna alla quale è associata o altre informazioni importanti.


1. Fai clic su **Salva**.
