---
description: Per poter tener traccia dei collegamenti di acquisizione e generare i relativi rapporti, nella configurazione SDK deve essere attivato il tracciamento dell’acquisizione.
keywords: dispositivi mobili
solution: Experience Cloud Services,Analytics
title: Configurare l’acquisizione
topic-fix: Metrics
uuid: e996e43e-8a77-47a3-a6fb-53f676f92bef
exl-id: 3a12dfab-70d0-41e6-8d4e-5aba21bb8606
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 100%

---

# Configurare l’acquisizione {#configure-acquisition}

Per poter tener traccia dei collegamenti di acquisizione e generare i relativi rapporti, nella configurazione SDK deve essere attivato il tracciamento dell’acquisizione.

1. Nella pagina Gestione impostazioni app dell’app, scorri fino alla sezione **[!UICONTROL Opzioni SDK acquisizione.]**
1. Completa le attività seguenti:

   * Per abilitare l’acquisizione, seleziona la casella di controllo **[!UICONTROL Abilita]**.

      Quando selezioni questa casella di controllo, viene attivato il campo **[!UICONTROL Timeout referente]** e il valore cambia da 0 a 5.

   * Immetti un valore nel campo **[!UICONTROL Timeout referente (secondi)]**.

      (**Facoltativo**) Se hai attivato la casella di controllo **[!UICONTROL Abilita]**, questo campo è facoltativo. Puoi cambiare il valore del timeout, specificato in secondi. Questa impostazione specifica il tempo di attesa per le informazioni di acquisizione prima che venga inviato l’hit Primo avvio.
   >[!IMPORTANT]
   >È necessario immettere un valore diverso da zero. Se attivi l’acquisizione ma lasci il valore impostato su zero, i collegamenti di acquisizione non funzioneranno. È consigliabile utilizzare il valore predefinito di cinque secondi.

1. Scarica e usa il nuovo file di configurazione SDK nella tua app.

   A questo punto hai configurato correttamente l’acquisizione su **iOS**.
Per attivarla anche su **Android**, completa i passaggi nella sezione [Tracciamento dell’acquisizione mobile](/help/android/acquisition-main/acquisition.md).
