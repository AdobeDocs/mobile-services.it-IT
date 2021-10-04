---
description: Con Anteprima Target puoi eseguire facilmente test di controllo qualità end-to-end per le attività di Target e vedere in anteprima tali attività sul tuo dispositivo.
title: Anteprima Target in Android
uuid: f3c82d64-009c-4929-a5e6-3677b2977889
exl-id: 69103f3a-9521-4808-8ecd-7b960efca04d
source-git-commit: d1ebb2bbc4742f5288f90a90e977d252f3f30aa3
workflow-type: tm+mt
source-wordcount: '120'
ht-degree: 74%

---

# Anteprima Target in Android {#target-preview-on-android}

Con Anteprima Target puoi eseguire facilmente test di controllo qualità end-to-end per le attività di Target e vedere in anteprima tali attività sul tuo dispositivo.

Per ulteriori informazioni su come impostare e utilizzare Anteprima Target, passa a [Anteprima mobile di Target](https://experienceleague.adobe.com/docs/target/using/implement-target/mobile-apps/target-mobile-preview.html) nella guida utente di Adobe Target.

>[!IMPORTANT]
>
>Per usare Anteprima Target è necessaria la versione 4.14.0 o successiva dell’SDK.

* **setPreviewRestartDeeplink**

   Imposta un collegamento diretto all’app che verrà attivato quando le selezioni di anteprima vengono applicate in modalità Anteprima.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void setPreviewRestartDeeplink(String deeplink);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      Target.setPreviewRestartDeeplink("myapp://myhost"); 
      ```
