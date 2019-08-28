---
description: Per poter tracciare e segnalare i collegamenti di marketing, nella configurazione dell'SDK deve essere attivato il tracciamento dell'acquisizione.
keywords: dispositivi mobili
seo-description: Per poter tracciare e segnalare i collegamenti di marketing, nella configurazione dell'SDK deve essere attivato il tracciamento dell'acquisizione.
seo-title: Configurare l'acquisizione
solution: Marketing Cloud, Analytics
title: Configurare l'acquisizione
topic: Metrics (Metriche)
uuid: e 996 e 43 e -8 a 77-47 a 3-a 6 fb -53 f 676 f 92 bef
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Configurare l'acquisizione {#configure-acquisition}

Per poter tracciare e segnalare i collegamenti di marketing, nella configurazione dell'SDK deve essere attivato il tracciamento dell'acquisizione.

1. Nella pagina Gestione impostazioni app dell'app, scorri fino alla sezione **[!UICONTROL Opzioni SDK acquisizione.]**
1. Completa le attività seguenti:

   * To enable Acquisition, select the **[!UICONTROL Enable]** check box.

      When you select this check box, the **[!UICONTROL Referrer Timeout]** field becomes active, and the value changes from 0 to 5.

   * Immettete un valore nel campo Timeout **[!UICONTROL referente (secondi)]**

      **(Facoltativo**) Se avete abilitato la casella **[!UICONTROL di]** controllo Abilita, questo campo è facoltativo. Puoi cambiare il valore del timeout, specificato in secondi. Questa impostazione specifica il periodo di attesa per le informazioni di acquisizione prima di inviare l'hit Primo avvio.
   >[!IMPORTANT]
   >Dovete immettere un valore diverso da zero. Se attivi Acquisizione ma lasci il valore come zero, i collegamenti di acquisizione non funzioneranno. È consigliabile utilizzare il valore predefinito di 5 secondi.

1. Scarica e usa il nuovo file di configurazione SDK nella tua app.

   A questo punto hai configurato correttamente l'acquisizione su **iOS**.
To enable Acquisition on **Android**, complete the steps in [Tracking Mobile Acquisition](/help/android/acquisition-main/acquisition.md).
