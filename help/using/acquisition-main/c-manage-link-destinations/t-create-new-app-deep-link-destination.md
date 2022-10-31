---
description: Puoi creare una nuova destinazione di collegamento che indirizza gli utenti a un collegamento web o a un collegamento profondo all’interno dell’app.
keywords: dispositivi mobili
solution: Experience Cloud Services,Analytics
title: Creare una nuova destinazione di collegamento
topic-fix: Metrics
uuid: 390e3dea-0221-4f97-980d-a90ca9f162fa
exl-id: 2d2f5938-1461-43e2-a375-45c18afc9d5a
source-git-commit: 7cfaa5f6d1318151e87698a45eb6006f7850aad4
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 100%

---

# Creare una nuova destinazione di collegamento {#create-new-link-destination}

{#eol}

Puoi creare una nuova destinazione di collegamento che indirizza gli utenti a un collegamento web o a un collegamento profondo all’interno dell’app.

1. Nell’interfaccia utente di Mobile Services, fai clic su **[!UICONTROL Gestione app]**.
1. Fai clic sul nome dell’app per visualizzare la pagina Informazioni app corrispondente.
1. Fai clic su **[!UICONTROL Gestione destinazioni collegamenti]**.
1. Fai clic su **[!UICONTROL Crea nuovo]**.
1. Digita le informazioni nei campi seguenti:
   * **[!UICONTROL Titolo]**

      Digita un nome descrittivo per la destinazione di collegamento dell’app. Il titolo viene visualizzato solo sulla pagina Gestione destinazioni collegamenti dell’interfaccia utente di Adobe Mobile Services. Un nome descrittivo può essere utile per trovare rapidamente una destinazione di collegamento specifica e può fornire indicazioni sulla sua funzione.

   * **[!UICONTROL Tipo di collegamento]**

      Elenco dei tipi di collegamento disponibili:

      * **[!UICONTROL Collegamento profondo app]**

         Specifica un collegamento diretto con schema URI (ad esempio `yourapp://section`). Le destinazioni di collegamento profondo nelle app sono collegamenti profondi con schema URI che indirizzano l’utente a un collegamento “in profondità” all’interno dell’app, ad esempio a una linea di prodotti specifica nell’app mobile di un retailer online.

      * **[!UICONTROL Collegamento web]**

         Digita un URL web di tipo HTTP o HTTPS, ad esempio,`https://adobe.com`. La destinazione di un collegamento web indirizza gli utenti a un URL, ad esempio a una linea di prodotti specifica nel sito web di un retailer online.

      * **[!UICONTROL Collegamento ibrido]**

         Digita un collegamento universale iOS o un collegamento ad app Android (ad esempio `https://yourwebsite.com`). I collegamenti ibridi supportano i collegamenti universali iOS o i collegamenti ad app Android.
   * **[!UICONTROL App]**
Seleziona l’app che è associata al collegamento che stai impostando.

      >[!TIP]
      >
      >Questa informazione è necessaria solo se hai selezionato Collegamento profondo app o Collegamento ibrido nel campo **[!UICONTROL Tipo di collegamento]**. Se l’app desiderata non figura nell’elenco di selezione, fai clic su **[!UICONTROL Aggiungi nuova app]** per indicare una nuova app da un app store.

   * **[!UICONTROL Tipo di collegamento]**

      Digita l’URL effettivo per il collegamento selezionato. L’etichetta di questo campo varia a seconda del tipo di collegamento selezionato.

   * **[!UICONTROL Note]**

      Inserisci eventuali note aggiuntive sulla destinazione. Le note aggiuntive vengono visualizzate solo sulla pagina Gestione destinazioni collegamenti dell’interfaccia utente di Adobe Mobile Services. Possono essere utili per aiutare altri utenti della tua organizzazione a trovare rapidamente una destinazione di collegamento specifica e fornire indicazioni sulla sua funzione, sulla campagna alla quale è associata o altre informazioni importanti.


1. Fai clic su **Salva**.
