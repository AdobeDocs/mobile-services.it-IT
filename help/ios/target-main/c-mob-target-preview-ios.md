---
description: Con Anteprima Target puoi eseguire facilmente test di controllo qualità end-to-end per le attività di Target e vedere in anteprima tali attività sul tuo dispositivo.
title: Anteprima Target in iOS
uuid: d92867a4-0569-4732-a928-28f9e2f8b21e
exl-id: d5695156-59cd-42c5-b9a3-d8e0ebbb89d0
source-git-commit: d1ebb2bbc4742f5288f90a90e977d252f3f30aa3
workflow-type: tm+mt
source-wordcount: '121'
ht-degree: 76%

---

# Anteprima Target in iOS{#target-preview-on-ios}

Con Anteprima Target puoi eseguire facilmente test di controllo qualità end-to-end per le attività di Target e vedere in anteprima tali attività sul tuo dispositivo.

Per ulteriori informazioni su come impostare e utilizzare Anteprima Target, consulta [Anteprima mobile di Target](https://experienceleague.adobe.com/docs/target/using/implement-target/mobile-apps/target-mobile-preview.html) nella documentazione di Adobe Target.

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
      [ADBMobile targetPreviewRestartDeepLink:@"myapp://myhost"]; 
      ```
