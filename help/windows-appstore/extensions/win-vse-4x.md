---
description: Queste estensioni offrono un modo molto più semplice di aggiungere il riferimento dell’SDK Windows 4.x delle soluzioni Experience Cloud nel progetto.
seo-description: Queste estensioni offrono un modo molto più semplice di aggiungere il riferimento dell’SDK Windows 4.x delle soluzioni Experience Cloud nel progetto.
seo-title: Estensioni di Windows Visual Studio per l’SDK 4.x per soluzioni Experience Cloud
solution: Marketing Cloud,Analytics
title: Estensioni di Windows Visual Studio per l’SDK 4.x per soluzioni Experience Cloud
topic: Sviluppatore e implementazione
uuid: 7d0ea312-340b-46ea-a737-b70a6766a536
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Windows Visual Studio extensions for Experience Cloud Solutions 4.x SDK {#windows-visual-studio-extensions-for-experience-cloud-solutions-x-sdk}

Queste estensioni offrono un modo molto più semplice di aggiungere il riferimento dell’SDK Windows 4.x delle soluzioni Experience Cloud nel progetto.

## Installare la libreria da GitHub {#section_F55DB6241EF1475286C05FEAEBF996A3}

1. Scarica l’SDK universale Windows da [GitHub](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases).
1. Estrai il file scaricato in locale.
1. Double-click the ADBMobileWindowsStoreVSIX.vsix or ADBMobileWindowsPhoneVSIX.vsix file to open the installer.

1. Selezionate Posizione **** globale e installate la libreria.

## Add references to your project {#section_00C14FE9243D4330BE1F4BB56FCF08B1}

1. Apri il progetto Windows 8.1 o Windows Phone 8.1.
1. Aprire la finestra di dialogo Gestione riferimenti.

   ![](assets/ref_manager.png)

1. Nella scheda **[!UICONTROL Estensioni]** di Windows 8.1 o Windows Phone 8.1, individua e seleziona **[UICONTROL Adobe Mobile SDK]**.
1. Fai clic su **[!UICONTROL OK]per salvarlo.**

   L’SDK di Adobe Mobile verrà aggiunto al progetto e, se non è già stato aggiunto, verrà aggiunto anche il pacchetto runtime **[di Microsoft Visual C++]** UICONTROL.

1. In Gestione configurazione, seleziona un tipo di piattaforma e inizia il test dell’app.

