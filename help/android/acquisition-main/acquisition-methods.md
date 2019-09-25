---
description: 'I seguenti metodi di acquisizione sono forniti dalla libreria di Android '
keywords: android;library;mobile;sdk
seo-description: 'I seguenti metodi di acquisizione sono forniti dalla libreria di Android '
seo-title: Metodi di acquisizione
solution: Marketing Cloud,Analytics
title: Metodi di acquisizione
topic: Sviluppatore e implementazione
uuid: 22ec432f-e7ae-4e89-be07-26206bbeacf8
translation-type: tm+mt
source-git-commit: bf076aa8e59d5c3e634fc4ae21f0de0d4541a83f

---


# Acquisition methods{#acquisition-methods}

The following Acquisition method is provided by the Android library:

* **campaignStartForApp**

   Consente agli sviluppatori di avviare una campagna di acquisizione app, come se l'utente avesse fatto clic su un collegamento. È utile per creare collegamenti di acquisizione manuali e gestire autonomamente il ridirezionamento all'app store.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void campaignStartForApp(final String appId final Map<String Object> data); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      Acquisition.campaignStartForApp("0652024f-adcd-49f9-9bd7-2552a4564d2f" new 
      HashMap<String Object (){{
           put("custom.key" "value");
      }}); 
      ```
