---
description: Con Anteprima Target puoi eseguire facilmente test di controllo qualità end-to-end per le attività di Target e vedere in anteprima tali attività sul tuo dispositivo.
seo-description: Con Anteprima Target puoi eseguire facilmente test di controllo qualità end-to-end per le attività di Target e vedere in anteprima tali attività sul tuo dispositivo.
seo-title: Anteprima Target in Android
title: Anteprima Target in Android
uuid: f 3 c 82 d 64-009 c -4929-a 5 e 6-3677 b 2977889
translation-type: tm+mt
source-git-commit: 83e6968efb0ed1b4ef504286c6cb2e8e4d2eaf94

---


# Anteprima Target in Android {#target-preview-on-android}

Con Anteprima Target puoi eseguire facilmente test di controllo qualità end-to-end per le attività di Target e vedere in anteprima tali attività sul tuo dispositivo.

Per ulteriori informazioni su come impostare e utilizzare la funzione Anteprima Target, consulta [Anteprima mobile di Target](https://docs.adobe.com/content/help/en/target/using/implement-target/mobile-apps/target-mobile-preview.html).

>[!IMPORTANT]
>
>Per utilizzare Preview Preview (Anteprima Target), è necessario disporre della versione SDK 4.14.0 o successiva.

* **setPreviewRestartDeeplink**

   Imposta un collegamento profondo per app che verrà attivato quando le selezioni di anteprima sono applicate in modalità Anteprima.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void setPreviewRestartDeeplink(String deeplink);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      Target.setPreviewRestartDeeplink(“myapp://myhost”); 
      ```

