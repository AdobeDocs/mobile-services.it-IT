---
description: La tabella seguente descrive i diversi identificatori delle app utilizzati dall’SDK per Android e Adobe Mobile Services.
solution: Experience Cloud Services,Analytics
title: ID delle app
topic-fix: Developer and implementation
uuid: 3ac99489-6269-439e-a814-24102ef220b1
exl-id: 28358dd6-50dd-4ba9-9fb0-5271eae69d28
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 100%

---

# ID delle app{#app-ids}

La tabella seguente descrive i diversi identificatori delle app utilizzati dall’SDK per Android e Adobe Mobile Services.

| ID | Descrizione |
|--- |--- |
| ID inviato con le metriche del ciclo di vita | Si tratta di una combinazione del nome dell&#39;app e della versione del bundle inviata all&#39;app store. Questo valore è utilizzato per il rapporto delle Versioni in Adobe Mobile Services e puoi utilizzarlo per filtrare al fine di segmentare gli nbase alla versione specifica della release dell&#39;app. |
| ID dell&#39;App Store | Questo ID è assegnato alla tua app da parte dell&#39;app store ed è fornito in Adobe Mobile Services quando crei collegamenti di acquisizione. |
| AppID nella configurazione JSON ADBMobile | Si tratta di un ID univoco assegnato all&#39;istanza dell&#39;app da Adobe Mobile Services per tutti i metadati associati nel sistema. Questo ID è utilizzato per creare gli URL univoci per il tracciamento dell’acquisizione o il collegamento per tracciamento. Questo ID viene aggiunto automaticamente al file di configurazione ADBMobile JSON quando tale file viene scaricato dall&#39;interfaccia utente; si trova in Gestione impostazioni app nelle impostazioni di Acquisizione della tua app. |
