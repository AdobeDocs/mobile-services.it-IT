---
description: Queste estensioni offrono un modo molto più semplice di aggiungere il riferimento dell’SDK Windows 4.x delle soluzioni Experience Cloud nel progetto.
seo-description: Queste estensioni offrono un modo molto più semplice di aggiungere il riferimento dell’SDK Windows 4.x delle soluzioni Experience Cloud nel progetto.
seo-title: Estensioni Windows Visual Studio per SDK 4. x delle soluzioni Experience Cloud
solution: Marketing Cloud, Analytics
title: Estensioni Windows Visual Studio per SDK 4. x delle soluzioni Experience Cloud
topic: Sviluppatore e implementazione
uuid: e 48 faf 54-8 b 08-4224-9 d 80-e 553 a 983129 e
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Windows Visual Studio extensions for Experience Cloud Solutions 4.x SDK {#windows-visual-studio-extensions-for-experience-cloud-solutions-x-sdk}

Questa estensione fornisce un modo molto più semplice per aggiungere il riferimento dell'SDK Windows 4. x di soluzioni Experience Cloud al progetto.

## Installare la libreria da github {#section_F55DB6241EF1475286C05FEAEBF996A3}

1. Scarica l’SDK universale Windows da [GitHub](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases).
1. Estrai il file scaricato in locale.
1. Fai doppio clic sul **[!UICONTRTOL file adbmobileuniversalwindowsvsix. vsix]** per aprire il programma di installazione.
1. Selezionate **[!UICONTROL Posizione globale]** e installate la libreria.

## Add references to your project {#section_00C14FE9243D4330BE1F4BB56FCF08B1}

1. Apri il progetto Windows 10.
1. Aprite la finestra di dialogo Gestione riferimento.

   ![](assets/ref_manager.png)

1. Nella scheda **[!UICONTROL Estensioni]** , individua e seleziona **[UICONTROL Adobe Mobile SDK]**.
1. Fai clic su **[!UICONTROL OK]per salvarlo.**

   L'SDK di Adobe Mobile verrà aggiunto al progetto. Se **[il pacchetto UICONTROL Microsoft Visual C + + Runtime]** non è stato ancora aggiunto, il pacchetto verrà aggiunto anche al progetto.

1. In Gestione configurazione, seleziona un tipo di piattaforma e inizia a testare l'app.

