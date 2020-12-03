---
description: Con Anteprima Target puoi eseguire facilmente test di controllo qualità end-to-end per le attività di Target e vedere in anteprima tali attività sul tuo dispositivo.
seo-description: Con Anteprima Target puoi eseguire facilmente test di controllo qualità end-to-end per le attività di Target e vedere in anteprima tali attività sul tuo dispositivo.
seo-title: Anteprima Target in Android
title: Anteprima Target in Android
uuid: f3c82d64-009c-4929-a5e6-3677b2977889
translation-type: tm+mt
source-git-commit: 83e6968efb0ed1b4ef504286c6cb2e8e4d2eaf94
workflow-type: tm+mt
source-wordcount: '139'
ht-degree: 87%

---


# Anteprima Target in Android {#target-preview-on-android}

Con Anteprima Target puoi eseguire facilmente test di controllo qualità end-to-end per le attività di Target e vedere in anteprima tali attività sul tuo dispositivo.

For more information on how to set up and use Target Preview, go to [Target Mobile Preview](https://docs.adobe.com/content/help/it-IT/target/using/implement-target/mobile-apps/target-mobile-preview.html).

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
      Target.setPreviewRestartDeeplink(“myapp://myhost”); 
      ```

