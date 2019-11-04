---
description: La tabella seguente descrive i diversi identificatori di app utilizzati dall'SDK per iOS e da Adobe Mobile Services.
seo-description: La tabella seguente descrive i diversi identificatori di app utilizzati dall'SDK per iOS e da Adobe Mobile Services.
seo-title: ID delle app
solution: Experience Cloud,Analytics
title: ID delle app
topic: Sviluppatore e implementazione
uuid: 24ebc716-23c7-4ee8-8256-b534210367e0
translation-type: ht
source-git-commit: 0e22d5e080b680ff6b23462f1bc12f27d99e6d42

---


# ID delle app {#app-ids}

La tabella seguente descrive i diversi identificatori di app utilizzati dall'SDK per iOS e da Adobe Mobile Services.

| ID | Descrizione |
|--- |--- |
| ID inviato con metriche del ciclo di vita | Si tratta di una combinazione del nome dell'app e della versione del bundle inviata all'app store.  Questo valore viene usato per il rapporto Versioni in Adobe Mobile Services e lo puoi usare per filtrare i risultati per una specifica versione dell'app. |
| ID dell'App Store | Questo ID è assegnato alla tua app da parte dell'app store ed è fornito in Adobe Mobile Services quando crei collegamenti di acquisizione. |
| AppID nella configurazione JSON ADBMobile | Questo ID è univoco e viene assegnato all'istanza dell'app da Adobe Mobile Services per tutti i metadati associati nel tuo sistema.  Questo ID viene usato per creare URL univoci per il tracciamento acquisizione o il collegamento di tracciamento; viene aggiunto automaticamente al file di configurazione ADBMobile JSON quando viene scaricato dall'interfaccia utente; e si trova in Gestione impostazioni app nelle impostazioni Acquisizione dell'app. |

