---
description: Con Anteprima Target puoi eseguire facilmente test di controllo qualità end-to-end per le attività di Target e vedere in anteprima tali attività sul tuo dispositivo.
seo-description: Con Anteprima Target puoi eseguire facilmente test di controllo qualità end-to-end per le attività di Target e vedere in anteprima tali attività sul tuo dispositivo.
seo-title: Anteprima Target in iOS
title: Anteprima Target in iOS
uuid: d92867a4-0569-4732-a928-28f9e2f8b21e
translation-type: tm+mt
source-git-commit: c198ae57b05f8965a8e27191443ee2cd552d6c50
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 100%

---


# Anteprima Target in iOS {#target-preview-on-ios}

Con Anteprima Target puoi eseguire facilmente test di controllo qualità end-to-end per le attività di Target e vedere in anteprima tali attività sul tuo dispositivo.

Per ulteriori informazioni su come impostare e utilizzare la funzione Anteprima Target, consulta [Anteprima mobile di Target](https://docs.adobe.com/content/help/it-IT/target/using/implement-target/mobile-apps/target-mobile-preview.html).

>[!IMPORTANT]
>
>Per usare Anteprima Target è necessaria la versione 4.14.0 o successiva dell’SDK.

## Metodo di anteprima Target

* **setPreviewRestartDeeplink**

   Imposta un collegamento diretto all’app che verrà attivato quando le selezioni di anteprima vengono applicate in modalità Anteprima.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
       + (void) targetPreviewRestartDeepLink:(nullable NSString *)callbackURL;
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      [ADBMobile targetPreviewRestartDeepLink:@" myapp://myhost"]; 
      ```
