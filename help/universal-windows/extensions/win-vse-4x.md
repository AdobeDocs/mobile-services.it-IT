---
description: Queste estensioni forniscono un modo molto più semplice per aggiungere al progetto il riferimento  SDK per Windows 4.x per soluzioni di Experience Cloud.
seo-description: Queste estensioni forniscono un modo molto più semplice per aggiungere al progetto il riferimento  SDK per Windows 4.x per soluzioni di Experience Cloud.
seo-title: Estensioni di Windows Visual Studio per  SDK 4.x per soluzioni di Experience Cloud
solution: Marketing Cloud,Analytics
title: Estensioni di Windows Visual Studio per  SDK 4.x per soluzioni di Experience Cloud
topic: Developer and implementation
uuid: e48faf54-8b08-4224-9d80-e553a983129e
translation-type: tm+mt
source-git-commit: 97e6d24b75e770685d440d31aa5ee8924a079501
workflow-type: tm+mt
source-wordcount: '208'
ht-degree: 2%

---


# Windows Visual Studio extensions for Experience Cloud Solutions 4.x SDK {#windows-visual-studio-extensions-for-experience-cloud-solutions-x-sdk}

Questa estensione fornisce un modo molto più semplice per aggiungere al progetto il riferimento dell’SDK per Windows delle soluzioni di Experience Cloud  4.x.

## Installare la libreria da GitHub {#section_F55DB6241EF1475286C05FEAEBF996A3}

1. Scarica l’SDK Windows Universal da [GitHub](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases).
1. Estrarre localmente il file scaricato.
1. Fai doppio clic sul file **[!UICONTROL ADBMobileUniversalWindowsVSIX.vsix]** per aprire il programma di installazione.
1. Selezionate Posizione **** globale e installate la libreria.

## Aggiungere riferimenti al progetto {#section_00C14FE9243D4330BE1F4BB56FCF08B1}

1. Apri il progetto Windows 10.
1. Aprire la finestra di dialogo Gestione riferimenti.

   ![](assets/ref_manager.png)

1. Nella scheda **[!UICONTROL Estensioni]** , individua e seleziona **[!UICONTROL Adobe SDK]** Mobile.
1. Fate clic su **[!UICONTROL OK]** per salvarlo.

   L’SDK di Mobile  Adobe verrà aggiunto al progetto. Se il pacchetto **[!UICONTROL Microsoft Visual C++ Runtime]** non è ancora stato aggiunto, anche questo pacchetto verrà aggiunto al progetto.

1. In Gestione configurazione, seleziona un tipo di piattaforma e inizia il test dell’app.

