---
description: La tabella seguente descrive i diversi identificatori dell'app utilizzati dall'SDK iOS e  Adobe Mobile Services.
seo-description: La tabella seguente descrive i diversi identificatori dell'app utilizzati dall'SDK iOS e  Adobe Mobile Services.
seo-title: ID delle app
solution: Experience Cloud,Analytics
title: ID delle app
topic: Developer and implementation
uuid: 24ebc716-23c7-4ee8-8256-b534210367e0
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 61%

---


# ID delle app {#app-ids}

La tabella seguente descrive i diversi identificatori dell&#39;app utilizzati dall&#39;SDK iOS e  Adobe Mobile Services.

| ID | Descrizione |
|--- |--- |
| ID inviato con le metriche del ciclo di vita | Si tratta di una combinazione del nome dell&#39;app e della versione del bundle inviata all&#39;app store.  Questo valore viene usato per il rapporto Versioni in Adobe Mobile Services e lo puoi usare per filtrare i risultati per una specifica versione dell&#39;app. |
| ID dell&#39;App Store | Questo ID viene assegnato alla tua app dall&#39;app store ed è fornito in  Adobe Mobile Services quando crei collegamenti di acquisizione. |
| AppID nella configurazione JSON ADBMobile | Questo ID è univoco e viene assegnato all&#39;istanza dell&#39;app da Adobe Mobile Services per tutti i metadati associati nel tuo sistema.  Questo ID viene usato per creare URL univoci per il tracciamento acquisizione o il collegamento di tracciamento; viene aggiunto automaticamente al file di configurazione ADBMobile JSON quando viene scaricato dall&#39;interfaccia utente; e si trova in Gestione impostazioni app nelle impostazioni Acquisizione dell&#39;app. |

