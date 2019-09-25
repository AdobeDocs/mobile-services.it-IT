---
description: Acquisition tracking must be enabled in the SDK configuration before you can track and report on Marketing Links.
keywords: dispositivi mobili
seo-description: Per poter tenere traccia dei collegamenti marketing e generare rapporti su di essi, è necessario abilitare il tracciamento dell'acquisizione nella configurazione SDK.
seo-title: Configurare l'acquisizione
solution: Marketing Cloud,Analytics
title: Configurare l'acquisizione
topic: Metrics (Metriche)
uuid: e996e43e-8a77-47a3-a6fb-53f676f92bef
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Configurare l'acquisizione {#configure-acquisition}

Per poter tenere traccia dei collegamenti marketing e generare rapporti su di essi, è necessario abilitare il tracciamento dell'acquisizione nella configurazione SDK.

1. Nella pagina Gestione impostazioni app dell'app, scorri fino alla sezione **[!UICONTROL Opzioni SDK acquisizione.]**
1. Completa le attività seguenti:

   * To enable Acquisition, select the **[!UICONTROL Enable]** check box.

      When you select this check box, the **[!UICONTROL Referrer Timeout]** field becomes active, and the value changes from 0 to 5.

   * Enter a value in the Referrer Timeout (seconds) field ****

      (**Optional**) If you enabled the **[!UICONTROL Enable]** check box, this field is optional. Puoi cambiare il valore del timeout, specificato in secondi. Questa impostazione specifica il periodo di attesa delle informazioni di acquisizione prima di inviare l'hit Primo avvio.
   >[!IMPORTANT]
   >You must enter a non-zero value. Se attivi Acquisizione ma lasci il valore zero, i collegamenti di acquisizione non funzioneranno. È consigliabile utilizzare il valore predefinito di 5 secondi.

1. Scarica e usa il nuovo file di configurazione SDK nella tua app.

   A questo punto hai configurato correttamente l'acquisizione su **iOS**.
To enable Acquisition on **Android**, complete the steps in [Tracking Mobile Acquisition](/help/android/acquisition-main/acquisition.md).
