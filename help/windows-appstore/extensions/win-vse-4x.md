---
description: Queste estensioni forniscono un modo molto più semplice per aggiungere il riferimento dell’SDK Windows 4.x delle soluzioni Experience Cloud nel progetto.
solution: Experience Cloud,Analytics
title: Estensioni Windows Visual Studio per l’SDK 4.x delle soluzioni Experience Cloud
topic-fix: Developer and implementation
uuid: 7d0ea312-340b-46ea-a737-b70a6766a536
exl-id: 63e9e5c7-2a12-47b3-a712-bf51e12821aa
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 13%

---

# Estensioni Windows Visual Studio per l’SDK 4.x delle soluzioni Experience Cloud {#windows-visual-studio-extensions-for-experience-cloud-solutions-x-sdk}

Queste estensioni forniscono un modo molto più semplice per aggiungere il riferimento dell’SDK Windows 4.x delle soluzioni Experience Cloud nel progetto.

## Installare la libreria da GitHub {#section_F55DB6241EF1475286C05FEAEBF996A3}

1. Scarica l&#39;SDK universale di Windows da [GitHub](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases).
1. Estrai il file scaricato localmente.
1. Fai doppio clic sul file ADBMobileWindowsStoreVSIX.vsix o ADBMobileWindowsPhoneVSIX.vsix per aprire il programma di installazione.

1. Seleziona **[!UICONTROL Posizione globale]** e installa la libreria.

## Aggiungere riferimenti al progetto {#section_00C14FE9243D4330BE1F4BB56FCF08B1}

1. Apri il progetto Windows 8.1 o Windows Phone 8.1.
1. Apre la finestra di dialogo Gestione riferimenti.

   ![](assets/ref_manager.png)

1. Nella scheda **[!UICONTROL Estensioni]** di Windows 8.1 o Windows Phone 8.1, individua e seleziona **[!UICONTROL Adobe Mobile SDK]**.
1. Fare clic su **[!UICONTROL OK]** per salvarlo.

   L’SDK di Adobe Mobile verrà aggiunto al progetto e, se non è già stato aggiunto, viene aggiunto anche il pacchetto **[!UICONTROL Microsoft Visual C++ Runtime]** .

1. In Gestione configurazione, seleziona un tipo di piattaforma e inizia a testare l’app.
