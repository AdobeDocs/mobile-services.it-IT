---
description: Queste estensioni offrono un modo molto più semplice di aggiungere il riferimento dell’SDK Windows 4.x delle soluzioni Experience Cloud nel progetto.
seo-description: Queste estensioni offrono un modo molto più semplice di aggiungere il riferimento dell’SDK Windows 4.x delle soluzioni Experience Cloud nel progetto.
seo-title: Estensioni di Windows Visual Studio per l’SDK 4.x per soluzioni Experience Cloud
solution: Marketing Cloud,Analytics
title: Estensioni di Windows Visual Studio per l’SDK 4.x per soluzioni Experience Cloud
topic: Sviluppatore e implementazione
uuid: e48faf54-8b08-4224-9d80-e553a983129e
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Windows Visual Studio extensions for Experience Cloud Solutions 4.x SDK {#windows-visual-studio-extensions-for-experience-cloud-solutions-x-sdk}

Questa estensione fornisce un modo molto più semplice per aggiungere nel progetto il riferimento dell’SDK Windows 4.x per soluzioni Experience Cloud.

## Installare la libreria da GitHub {#section_F55DB6241EF1475286C05FEAEBF996A3}

1. Scarica l’SDK universale Windows da [GitHub](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases).
1. Estrai il file scaricato in locale.
1. Fai doppio clic sul file **[!UICONTRTOL ADBMobileUniversalWindowsVSIX.vsix]** per aprire il programma di installazione.
1. Selezionate Posizione **** globale e installate la libreria.

## Add references to your project {#section_00C14FE9243D4330BE1F4BB56FCF08B1}

1. Apri il progetto Windows 10.
1. Aprire la finestra di dialogo Gestione riferimenti.

   ![](assets/ref_manager.png)

1. Nella scheda **[!UICONTROL Estensioni]** , individua e seleziona **[UICONTROL Adobe Mobile SDK]**.
1. Fai clic su **[!UICONTROL OK]per salvarlo.**

   L’SDK di Adobe Mobile verrà aggiunto al progetto. Se il pacchetto **[UICONTROL Microsoft Visual C+ Runtime]** non è ancora stato aggiunto, anche questo pacchetto verrà aggiunto al progetto.

1. In Gestione configurazione, seleziona un tipo di piattaforma e inizia il test dell’app.

