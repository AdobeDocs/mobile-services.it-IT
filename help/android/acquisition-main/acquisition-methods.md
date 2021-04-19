---
description: 'I seguenti metodi di acquisizione sono forniti dalla libreria di Android '
keywords: android,libreria,mobile,sdk
seo-description: 'I seguenti metodi di acquisizione sono forniti dalla libreria di Android '
seo-title: Metodi di acquisizione
solution: Experience Cloud,Analytics
title: Metodi di acquisizione
topic-fix: Developer and implementation
uuid: 22ec432f-e7ae-4e89-be07-26206bbeacf8
exl-id: 0ce1b8fb-fd45-45de-8f97-e297e4c6529f
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '86'
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
