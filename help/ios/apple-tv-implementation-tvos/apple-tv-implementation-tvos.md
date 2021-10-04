---
description: Queste informazioni sono utili per implementare Apple TV con tvOS.
solution: Experience Cloud,Analytics
title: Implementazione Apple TV con tvOS
topic-fix: Developer and implementation
uuid: d1571ea2-a5de-4b96-a527-72abbf51fab8
exl-id: 35b7f02d-ae48-4c6f-9a3a-6d106a1026ad
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 100%

---

# Implementazione Apple TV con tvOS {#apple-tv-implementation-with-tvos}

Queste informazioni sono utili per implementare Apple TV con tvOS.

## Nuova versione dell&#39;SDK per dispositivi mobili di Adobe Experience Platform

Hai bisogno di informazioni e documentazione relative all’SDK per dispositivi mobili di Adobe Experience Platform? Fai clic [qui](https://aep-sdks.gitbook.io/docs/) per la documentazione più recente.

A settembre 2018 è stata rilasciata una nuova versione principale dell&#39;SDK. Questi nuovi SDK per dispositivi mobili di Adobe Experience Platform sono configurabili tramite [Experience Platform Launch](https://www.adobe.com/it/experience-platform/launch.html).

* Per iniziare, vai su Adobe Experience Platform Launch.
* Per visualizzare cosa è compreso negli archivi Experience Platform SDK, passa a [Github: SDK di Adobe Experience Platform](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

## Panoramica

Con Apple TV, ora è possibile creare applicazioni da eseguire nell’ambiente nativo tvOS. Puoi creare un’app nativa utilizzando diversi framework in iOS, oppure puoi creare l’app utilizzando modelli XML e JavaScript.

>[!TIP]
>
>Il supporto per tvOS è disponibile a partire dalla versione 4.7.0 di `AdobeMobileLibrary`.

## Introduzione {#section_CAB40A5B5FC745068C8A5DF8F9AB6199}

>[!TIP]
>
>Si presuppone che il progetto abbia come destinazione un&#39;app Apple TV per tvOS. Per ulteriori informazioni, consulta [tvOS](https://developer.apple.com/tvos/documentation/).

## Configurare un&#39;app nativa per tvOS {#section_5095F19B3C4545F68E8C1E37A7E303AE}

Completa i seguenti passaggi nel progetto Xcode:

1. Trascina nel progetto la cartella AdobeMobileLibrary.
1. Assicurati che il file `ADBMobileConfig.json` sia un membro della tua destinazione.
1. Nella scheda **[!UICONTROL Fasi build]** della destinazione dell’app tvOS, espandi la sezione **[!UICONTROL Collega binario a librerie]** e aggiungi le seguenti librerie:

   * `AdobeMobileLibrary_TV.a`
   * `libsqlite3.0.tbd`
   * `SystemConfiguration.framework`

Per informazioni, consulta la documentazione di iOS in [iOS](https://developer.apple.com/ios/resources/).

## Configurare un&#39;app TVML/TVJS per tvOS {#section_AB2EC8C326654F3387658EBBD990BB12}

1. Trascina nel progetto la cartella `AdobeMobileLibrary`.
1. Assicurati che il file `ADBMobileConfig.json` sia un membro della tua destinazione.
1. Nella scheda **[!UICONTROL Fasi build]** della destinazione dell’app tvOS, espandi la sezione **[!UICONTROL Collega binario a librerie]** e aggiungi le seguenti librerie:

   * `AdobeMobileLibrary_TV.a`
   * `libsqlite3.0.tbd`
   * `SystemConfiguration.framework`

1. Nel file di implementazione della classe `TVApplicationControllerDelegate`, importa l&#39;SDK.

   ```objective-c
   #import "ADBMobile.h"
   ```

1. Nel metodo `application:didFinishLaunchWithOptions:` della classe `TVApplicationControllerDelegate`, passa l&#39;oggetto `TVApplicationController` all&#39;SDK con il metodo `installTVMLHooks:`.

   Per registrarsi nel JSContext dell&#39;app, l&#39;SDK di Adobe deve poter accedere alla classe `TVApplicationController` dell&#39;app. Questo passaggio consente di invocare i metodi nativi nell&#39;SDK di Adobe dai file JavaScript.

   ```objective-c
   [ADBMobile installTVMLHooks:appController];
   ```

1. Nei file JavaScript, usa l&#39;oggetto `ADBMobile` per accedere ai metodi nativi dell&#39;SDK di Adobe.

   Per un elenco completo dei metodi disponibili, vedi [Metodi TVJS](/help/ios/apple-tv-implementation-tvos/tvjs-methods.md).
