---
description: Queste estensioni forniscono un modo molto più semplice per aggiungere il riferimento dell’SDK Windows 4.x delle soluzioni Experience Cloud nel progetto.
solution: Experience Cloud Services,Analytics
title: Estensioni Windows Visual Studio per l’SDK 4.x delle soluzioni Experience Cloud
topic-fix: Developer and implementation
uuid: e48faf54-8b08-4224-9d80-e553a983129e
exl-id: 8ed91dc1-8f30-4788-8471-21bb54256b0b
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 14%

---

# Estensioni Windows Visual Studio per l’SDK 4.x delle soluzioni Experience Cloud {#windows-visual-studio-extensions-for-experience-cloud-solutions-x-sdk}

Questa estensione fornisce un modo molto più semplice per aggiungere nel progetto il riferimento dell’SDK Windows 4.x delle soluzioni Experience Cloud.

## Installare la libreria da GitHub {#section_F55DB6241EF1475286C05FEAEBF996A3}

1. Scarica l’SDK universale di Windows da [GitHub](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases).
1. Estrai il file scaricato localmente.
1. Fai doppio clic sul pulsante **[!UICONTROL ADBMobileUniversalWindowsVSIX.vsix]** per aprire il programma di installazione.
1. Seleziona **[!UICONTROL Posizione globale]** e installa la libreria.

## Aggiungere riferimenti al progetto {#section_00C14FE9243D4330BE1F4BB56FCF08B1}

1. Apri il progetto Windows 10.
1. Apre la finestra di dialogo Gestione riferimenti.

   ![](assets/ref_manager.png)

1. Sulla **[!UICONTROL Estensioni]** , individua e seleziona **[!UICONTROL Adobe Mobile SDK]**.
1. Fai clic su **[!UICONTROL OK]** per salvarlo.

   L’SDK Adobe Mobile verrà aggiunto al tuo progetto. Se la **[!UICONTROL Runtime di Microsoft Visual C++]** il pacchetto non è ancora stato aggiunto, verrà aggiunto anche al progetto.

1. In Gestione configurazione, seleziona un tipo di piattaforma e inizia a testare l’app.
