---
description: Queste estensioni forniscono un modo molto più semplice per aggiungere al progetto il riferimento  SDK per Windows 4.x per soluzioni di Experience Cloud.
seo-description: Queste estensioni forniscono un modo molto più semplice per aggiungere al progetto il riferimento  SDK per Windows 4.x per soluzioni di Experience Cloud.
seo-title: Estensioni Windows Visual Studio per l’SDK 4.x delle soluzioni Experience Cloud
solution: Experience Cloud,Analytics
title: Estensioni Windows Visual Studio per l’SDK 4.x delle soluzioni Experience Cloud
topic: Developer and implementation
uuid: 7d0ea312-340b-46ea-a737-b70a6766a536
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '213'
ht-degree: 16%

---


# Estensioni Windows Visual Studio per l’SDK 4.x delle soluzioni Experience Cloud {#windows-visual-studio-extensions-for-experience-cloud-solutions-x-sdk}

Queste estensioni forniscono un modo molto più semplice per aggiungere al progetto il riferimento  SDK per Windows 4.x per soluzioni di Experience Cloud.

## Installare la libreria da GitHub {#section_F55DB6241EF1475286C05FEAEBF996A3}

1. Scarica l’SDK Windows Universal da [GitHub](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases).
1. Estrarre localmente il file scaricato.
1. Fai doppio clic sul file ADBMobileWindowsStoreVSIX.vsix o ADBMobileWindowsPhoneVSIX.vsix per aprire il programma di installazione.

1. Selezionate Posizione **** globale e installate la libreria.

## Aggiungere riferimenti al progetto {#section_00C14FE9243D4330BE1F4BB56FCF08B1}

1. Apri il progetto Windows 8.1 o Windows Phone 8.1.
1. Aprire la finestra di dialogo Gestione riferimenti.

   ![](assets/ref_manager.png)

1. Nella scheda **[!UICONTROL Estensioni]** di Windows 8.1 o Windows Phone 8.1, individua e seleziona **[!UICONTROL SDK]** Adobe Mobile.
1. Fate clic su **[!UICONTROL OK]** per salvarlo.

   L&#39;SDK di Mobile  Adobe verrà aggiunto al progetto e, se non è già stato aggiunto, viene aggiunto anche il pacchetto Runtime **[!UICONTROL di]** Microsoft Visual C++.

1. In Gestione configurazione, seleziona un tipo di piattaforma e inizia il test dell’app.

