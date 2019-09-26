---
description: Questo plug-in consente di inviare chiamate iOS AppMeasurement da un progetto PhoneGap.
keywords: phonegap
seo-description: Questo plug-in consente di inviare chiamate iOS AppMeasurement da un progetto PhoneGap.
seo-title: Plug-in PhoneGap
solution: Marketing Cloud,Analytics
title: Plug-in PhoneGap
topic: Sviluppatore e implementazione
uuid: f88bcf10-1f9e-4c97-b348-40db797c9923
translation-type: tm+mt
source-git-commit: 517ae533864aebe9c6a20d877a9638d5d3e2a071

---


# PhoneGap plug-in{#phonegap-plug-in}

Questo plug-in consente di inviare chiamate iOS AppMeasurement da un progetto PhoneGap.

## Nuova versione SDK per Adobe Experience Platform Mobile

Stai cercando informazioni e documentazione sull’SDK per dispositivi mobili di Adobe Experience Platform? Fai clic [qui](https://aep-sdks.gitbook.io/docs/) per la documentazione più recente.

A settembre 2018 è stata rilasciata una nuova versione principale dell’SDK. Questi nuovi SDK per dispositivi mobili di Adobe Experience Platform sono configurabili tramite [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* Per iniziare, vai ad Adobe Experience Platform Launch.
* Per visualizzare cosa è compreso negli archivi Experience Platform SDK, passa a [Github: SDK di Adobe Experience Platform](https://github.com/Adobe-Marketing-Cloud/acp-sdks).


## Creare un progetto PhoneGap

To create a PhoneGap project, see [PhoneGap](https://helpx.adobe.com/experience-manager/6-4/mobile/using/phonegap.html).

## Installare il plug-in utilizzando npm: {#section_43229E57C16944C0B51531CB92089189}

1. Esegui il comando seguente:

   ```
   cordova plugin add adobe-mobile-services
   ```

## Installare il plug-in manualmente {#section_D53BA60D488C4DB8AD2BDF90439C180A}

### Includere la libreria AppMeasurement

Per includere la libreria AppMeasurement:

1. Drag `ADBMobile_PhoneGap.h` and  `ADBMobile_PhoneGap.m` into the **[!UICONTROL Plugins]** folder in your Xcode project.
1. Completa le impostazioni seguenti:

   1. Select **[!UICONTROL Copy items into destination group's folder (if needed)]**.
   1. Seleziona le destinazioni in cui desideri usare il codice AppMeasurement Code.

1. Drag `ADB_Helper.js` into the `www` folder in your project.
1. In the `res/xml` folder, open `config.xml` and register an new plugin by adding the following:

   ```
   <feature name="ADBMobile_PhoneGap"> 
     <param name="ios-package" value="ADBMobile_PhoneGap" /> 
   </feature>
   ```

### Aggiungi autorizzazioni app

La libreria AppMeasurement richiede quanto segue:

1. Avvia l'IDE di Xcode e apri la tua app.
1. Trascina la cartella **[!UICONTROL Adobe Mobile]nel progetto Xcode e completa le impostazioni seguenti:**

   1. Select **[!UICONTROL Copy items into destination group's folder (if needed)]**.
   1. Seleziona **[!UICONTROL Crea gruppi per le cartelle aggiunte]**.
   1. Seleziona le destinazioni in cui desideri usare il codice AppMeasurement Code e fai clic su **[!UICONTROL Fine]**.
   ![](assets/xcode-settings.png){width="672"}

1. Nella scheda **[!UICONTROL Fasi build]** della destinazione del progetto, espandi la sezione **Collega binario a librerie]e aggiungi le seguenti librerie:[!UICONTROL **

   * `libsqlite3.dylib`
   * `SystemConfiguration.framework`

1. Conferma che l'app possa essere generata senza errori imprevisti.

## Implement custom tracking {#section_FD102B3CDAA4492FB04E56BF17E28663}

In `html` files where you want to use tracking, add the following to the `<head>` tag:

```html
<script type="text/javascript" charset="utf-8" src="ADB_Helper.js"></script>
```

