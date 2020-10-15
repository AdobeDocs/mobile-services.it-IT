---
description: 'I seguenti metodi di acquisizione sono forniti dalla libreria di Android '
keywords: android;library;mobile;sdk
seo-description: 'I seguenti metodi di acquisizione sono forniti dalla libreria di Android '
seo-title: Metodi di acquisizione
solution: Experience Cloud,Analytics
title: Metodi di acquisizione
topic: Developer and implementation
uuid: 22ec432f-e7ae-4e89-be07-26206bbeacf8
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '82'
ht-degree: 100%

---


# Metodi di acquisizione {#acquisition-methods}

I seguenti metodi di acquisizione sono forniti dalla libreria di Android:

* **campaignStartForApp**

   Consente agli sviluppatori di avviare una campagna di acquisizione app, come se l&#39;utente avesse fatto clic su un collegamento. È utile per creare collegamenti di acquisizione manuali e gestire autonomamente il ridirezionamento all&#39;app store.

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
