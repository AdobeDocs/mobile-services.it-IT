---
description: Queste informazioni sono utili per implementare Apple TV con tvOS.
seo-description: Queste informazioni sono utili per implementare Apple TV con tvOS.
seo-title: Implementazione Apple TV con tvOS
solution: Marketing Cloud,Analytics
title: Implementazione Apple TV con tvOS
topic: Sviluppatore e implementazione
uuid: d1571ea2-a5de-4b96-a527-72abbf51fab8
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Apple TV implementation with tvOS {#apple-tv-implementation-with-tvos}

Queste informazioni sono utili per implementare Apple TV con tvOS.

## Nuova versione di Adobe Experience Cloud SDK

Stai cercando informazioni e documentazione sull’SDK per dispositivi mobili di Adobe Experience Platform? Fai clic [qui](https://aep-sdks.gitbook.io/docs/) per la documentazione più recente.

A settembre 2018 è stata rilasciata una nuova versione principale dell’SDK. Questi nuovi SDK per dispositivi mobili di Adobe Experience Platform sono configurabili tramite [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* Per iniziare, passa ad Launch.
* Per visualizzare cosa è compreso negli archivi Experience Platform SDK, passa a [Github: SDK di Adobe Experience Platform](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

>[!IMPORTANT]
>
> If you are using the Adobe Experience Platform Mobile SDKs with Adobe Launch, you **must** also install the Adobe Analytics Mobile Services extension to use Adobe Mobile Services features such as in-App messaging, push notifications or Acquisition links. Per ulteriori informazioni, consulta [Adobe Analytics - Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services).

Con Apple TV, è ora possibile creare applicazioni da eseguire nell'ambiente nativo tvOS. Puoi creare un'app nativa utilizzando diversi framework in iOS, oppure puoi creare un'app utilizzando modelli XML e JavaScript.

>[!TIP]
>
>tvOS support is available starting in  version 4.7.0.`AdobeMobileLibrary`

## Getting started {#section_CAB40A5B5FC745068C8A5DF8F9AB6199}

>[!TIP]
>
>Presupponiamo che il progetto abbia una destinazione che sia un'app Apple TV che esegue il targeting di tvOS. Per ulteriori informazioni, consulta [tvOS](https://developer.apple.com/tvos/documentation/).

## Configure a native app for tvOS {#section_5095F19B3C4545F68E8C1E37A7E303AE}

Completa i seguenti passaggi nel progetto Xcode:

1. Trascina nel progetto la cartella AdobeMobileLibrary.
1. Ensure that the `ADBMobileConfig.json` file is a member of your target.
1. Nella scheda **[!UICONTROL Fasi build]** della destinazione dell'app tvOS, espandi la sezione **Collega binario a librerie]e aggiungi le seguenti librerie:[!UICONTROL **

   * `AdobeMobileLibrary_TV.a`
   * `libsqlite3.0.tbd`
   * `SystemConfiguration.framework`

Per informazioni, vedi la documentazione di iOS in [iOS](https://developer.apple.com/ios/resources/).

## Configure a TVML/TVJS app for tvOS {#section_AB2EC8C326654F3387658EBBD990BB12}

1. Trascina nel progetto la cartella `AdobeMobileLibrary`.
1. Ensure that the `ADBMobileConfig.json` file is a member of your target.
1. Nella scheda **[!UICONTROL Fasi build]** della destinazione dell'app tvOS, espandi la sezione **Collega binario a librerie]e aggiungi le seguenti librerie:[!UICONTROL **

   * `AdobeMobileLibrary_TV.a`
   * `libsqlite3.0.tbd`
   * `SystemConfiguration.framework`

1. Nel file di implementazione della classe `TVApplicationControllerDelegate`, importa l'SDK.

   ```objective-c
   #import “ADBMobile.h"
   ```

1. In the `application:didFinishLaunchWithOptions:` method of your `TVApplicationControllerDelegate` class, pass your `TVApplicationController` object to the SDK with the `installTVMLHooks:` method.

   Per registrarsi nel JSContext dell'app, l'SDK di Adobe deve poter accedere alla classe `TVApplicationController` dell'app. Questo passaggio consente di invocare i metodi nativi nell'SDK di Adobe dai file JavaScript.

   ```objective-c
   [ADBMobile installTVMLHooks:appController];
   ```

1. Nei file JavaScript, usa l'oggetto `ADBMobile` per accedere ai metodi nativi dell'SDK di Adobe.

   For a complete listing of the available methods, see [TVJS Methods](/help/ios/apple-tv-implementation-tvos/tvjs-methods.md).

