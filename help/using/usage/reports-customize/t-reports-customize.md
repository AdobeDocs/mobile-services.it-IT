---
description: Queste informazioni sono utili per personalizzare i rapporti incorporati aggiungendo altri filtri (segmenti).
keywords: dispositivi mobili
seo-description: Queste informazioni sono utili per personalizzare i rapporti incorporati aggiungendo altri filtri (segmenti).
seo-title: Aggiungere filtri ai rapporti
solution: Marketing Cloud,Analytics
title: Aggiungere filtri ai rapporti
topic: Rapporti, Metriche
uuid: 19c395cc-2e07-4588-825b-f2f8b10a87c1
translation-type: tm+mt
source-git-commit: d028fe0f9477bc011aa8fda21a0a389808df0fce

---


# Add filters to reports{#add-filters-to-reports}

Queste informazioni sono utili per personalizzare i rapporti incorporati aggiungendo altri filtri (segmenti).

>[!IMPORTANT]
>
>Le metriche delle app mobili sono disponibili anche in reporting e analisi di marketing, analisi ad hoc, data warehouse e altre interfacce di reporting di Analytics. Se una suddivisione o un tipo di rapporto non è disponibile in Adobe Mobile, può essere generato utilizzando un'altra interfaccia di reporting.

In questo esempio personalizzeremo il rapporto **[!UICONTROL Utenti e sessioni], ma le istruzioni sono valide per qualsiasi tipo di rapporto.**

1. Apri l'app e fai clic su **Utilizzo** &gt; **[!UICONTROL Utenti e sessioni]**.

   ![](assets/customize1.png)

   Questo rapporto fornisce una vista completa degli utenti dell'app nel corso del tempo. Tuttavia, le metriche per le versioni iOS e Android dell'app vengono raccolte nella stessa suite di rapporti. Possiamo segmentare gli utenti per sistema operativo mobile aggiungendo un filtro personalizzato alla metrica Utenti.

1. Click **[!UICONTROL Customize]**.

   ![](assets/customize2.png)

1. Under **[!UICONTROL Users]**, click **[!UICONTROL Add Filter]** and click **[!UICONTROL Add Rule]**.

1. Select **[!UICONTROL Operating Systems]**, and from the drop-down list, and select **[!UICONTROL iOS]**.

   ![](assets/customize3.png)

   To add Android as a filter, you need to repeat this step.

1. Click **[!UICONTROL And]**, select **[!UICONTROL Operating Systems]** from the drop-down list, and select **[!UICONTROL Android]**.

   A questo punto i filtri dovrebbero essere come nell'esempio seguente:

   ![](assets/customize4.png)

1. Fai clic su **[!UICONTROL Aggiorna]**.
1. To regenerate the report, click **[!UICONTROL Run]**.

   Il rapporto ora mostra gli utenti suddivisi per sistema operativo. Il titolo del rapporto è stato modificato in modo da corrispondere ai filtri applicati al rapporto.

   ![](assets/customize5.png)

   Puoi personalizzare ulteriormente il rapporto. Da iOS 8.3, potete aggiungere la metrica Primi avvii con un filtro di versione del sistema operativo iOS 8.3 per vedere quanti clienti iOS 8.3 hanno aggiornato le app ed eseguito un primo avvio.
1. Under **[!UICONTROL First Launches]**, click **[!UICONTROL Add Filter]**, click **[!UICONTROL Add Rule]**, select **[!UICONTROL Operating Systems]** from the drop-down list, and select **[!UICONTROL iOS]**.
1. Click **[!UICONTROL And]**, select **[!UICONTROL Operating System Versions]** from the drop-down list, and select **[!UICONTROL iOS 8.3]**.

   A questo punto i filtri dovrebbero essere come in questo esempio:

   ![](assets/customize6.png)

1. Click **[!UICONTROL Update]** and **[!UICONTROL Run]**.

   Il rapporto aggiornato mostra gli utenti con iOS 8.3 che hanno avviato l'app per la prima volta.

   ![](assets/customize7.png)

   Dedica un po' di tempo a provare le diverse opzioni nel menu di personalizzazione dei rapporti e provvedi ad aggiungere ai segnalibri i tuoi preferiti. Gli URL dei rapporti in Adobe Mobile funzionano e possono essere inviati via e-mail o aggiunti ai preferiti.
