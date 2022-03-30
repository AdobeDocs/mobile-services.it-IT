---
description: Queste estensioni forniscono un modo molto più semplice per aggiungere il riferimento dell’SDK Windows 4.x delle soluzioni Experience Cloud nel progetto.
solution: Experience Cloud Services,Analytics
title: Estensioni Windows Visual Studio per l’SDK 4.x delle soluzioni Experience Cloud
topic-fix: Developer and implementation
uuid: 7d0ea312-340b-46ea-a737-b70a6766a536
exl-id: 63e9e5c7-2a12-47b3-a712-bf51e12821aa
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 13%

---

# Estensioni Windows Visual Studio per l’SDK 4.x delle soluzioni Experience Cloud {#windows-visual-studio-extensions-for-experience-cloud-solutions-x-sdk}

Queste estensioni forniscono un modo molto più semplice per aggiungere il riferimento dell’SDK Windows 4.x delle soluzioni Experience Cloud nel progetto.

## Installare la libreria da GitHub {#section_F55DB6241EF1475286C05FEAEBF996A3}

1. Scarica l’SDK universale di Windows da [GitHub](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases).
1. Estrai il file scaricato localmente.
1. Fai doppio clic sul file ADBMobileWindowsStoreVSIX.vsix o ADBMobileWindowsPhoneVSIX.vsix per aprire il programma di installazione.

1. Seleziona **[!UICONTROL Posizione globale]** e installa la libreria.

## Aggiungere riferimenti al progetto {#section_00C14FE9243D4330BE1F4BB56FCF08B1}

1. Apri il progetto Windows 8.1 o Windows Phone 8.1.
1. Apre la finestra di dialogo Gestione riferimenti.

   ![](assets/ref_manager.png)

1. Sulla **[!UICONTROL Estensioni]** scheda di Windows 8.1 o Windows Phone 8.1, individuare e selezionare **[!UICONTROL Adobe Mobile SDK]**.
1. Fai clic su **[!UICONTROL OK]** per salvarlo.

   L’SDK di Adobe Mobile verrà aggiunto al progetto e, se non è già stato aggiunto, il **[!UICONTROL Runtime di Microsoft Visual C++]** viene aggiunto anche il pacchetto .

1. In Gestione configurazione, seleziona un tipo di piattaforma e inizia a testare l’app.
