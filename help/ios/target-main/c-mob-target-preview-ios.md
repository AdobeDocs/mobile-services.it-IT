---
description: Con Anteprima Target puoi eseguire facilmente test di controllo qualità end-to-end per le attività di Target e vedere in anteprima tali attività sul tuo dispositivo.
seo-description: Con Anteprima Target puoi eseguire facilmente test di controllo qualità end-to-end per le attività di Target e vedere in anteprima tali attività sul tuo dispositivo.
seo-title: Anteprima Target in iOS
title: Anteprima Target in iOS
uuid: d92867a4-0569-4732-a928-28f9e2f8b21e
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Anteprima Target in iOS{#target-preview-on-ios}

Con Anteprima Target puoi eseguire facilmente test di controllo qualità end-to-end per le attività di Target e vedere in anteprima tali attività sul tuo dispositivo.

For more information on how to set up and use Target Preview, see [Target Mobile Preview](https://docs.adobe.com/content/help/en/target/using/implement-target/mobile-apps/target-mobile-preview.html).

>[!IMPORTANT]
>
>Per utilizzare Anteprima destinazione, è necessario disporre della versione SDK 4.14.0 o successiva.

## Metodo di anteprima di Target

* **setPreviewRestartDeeplink**

   Imposta un collegamento profondo per app che verrà attivato quando le selezioni di anteprima sono applicate in modalità Anteprima.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
       + (void) targetPreviewRestartDeepLink:(nullable NSString *)callbackURL;
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      [ADBMobile targetPreviewRestartDeepLink:@" myapp://myhost"]; 
      ```
