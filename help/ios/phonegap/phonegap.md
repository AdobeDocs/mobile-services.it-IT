---
description: Questo plug-in consente di inviare chiamate iOS AppMeasurement da un progetto PhoneGap.
keywords: phonegap
seo-description: Questo plug-in consente di inviare chiamate iOS AppMeasurement da un progetto PhoneGap.
seo-title: Plug-in PhoneGap
solution: Experience Cloud,Analytics
title: Plug-in PhoneGap
topic: Sviluppatore e implementazione
uuid: f88bcf10-1f9e-4c97-b348-40db797c9923
translation-type: ht
source-git-commit: 517ae533864aebe9c6a20d877a9638d5d3e2a071

---


# Plug-in PhoneGap{#phonegap-plug-in}

Questo plug-in consente di inviare chiamate iOS AppMeasurement da un progetto PhoneGap.

## Nuova versione dell'SDK per dispositivi mobili di Adobe Experience Platform

Stai cercando informazioni e documentazione sull’SDK per dispositivi mobili di Adobe Experience Platform? Fai clic [qui](https://aep-sdks.gitbook.io/docs/) per la documentazione più recente.

A settembre 2018 è stata rilasciata una nuova versione principale dell'SDK. Questi nuovi SDK per dispositivi mobili di Adobe Experience Platform sono configurabili tramite [Experience Platform Launch](https://www.adobe.com/it/experience-platform/launch.html).

* Per iniziare, vai su Adobe Experience Platform Launch.
* Per visualizzare cosa è compreso negli archivi Experience Platform SDK, passa a [Github: SDK di Adobe Experience Platform](https://github.com/Adobe-Marketing-Cloud/acp-sdks).


## Crea un progetto PhoneGap

Per creare un progetto PhoneGap, consulta [PhoneGap](https://helpx.adobe.com/it/experience-manager/6-4/mobile/using/phonegap.html).

## Installare il plug-in utilizzando npm: {#section_43229E57C16944C0B51531CB92089189}

1. Esegui il comando seguente:

   ```
   cordova plugin add adobe-mobile-services
   ```

## Installare il plug-in manualmente  {#section_D53BA60D488C4DB8AD2BDF90439C180A}

### Includere la libreria AppMeasurement

Per includere la libreria AppMeasurement:

1. Trascina `ADBMobile_PhoneGap.h` e `ADBMobile_PhoneGap.m` nella cartella **[!UICONTROL Plugin]** del progetto Xcode.
1. Completa le impostazioni seguenti:

   1. Seleziona **[!UICONTROL Copia elementi nella cartella del gruppo di destinazione (se necessario).]**
   1. Seleziona le destinazioni in cui desideri usare il codice AppMeasurement Code.

1. Trascina `ADB_Helper.js` nella cartella `www` del progetto Xcode.
1. Nella cartella `res/xml`, apri `config.xml` e registra un nuovo plug-in aggiungendo gli elementi seguenti:

   ```
   <feature name="ADBMobile_PhoneGap"> 
     <param name="ios-package" value="ADBMobile_PhoneGap" /> 
   </feature>
   ```

### Aggiungere le autorizzazioni dell'app

La libreria AppMeasurement richiede quanto segue:

1. Avvia l'IDE di Xcode e apri la tua app.
1. Trascina la cartella **[!UICONTROL Adobe Mobile]** nel progetto Xcode e completa le impostazioni seguenti:

   1. Seleziona **[!UICONTROL Copia elementi nella cartella del gruppo di destinazione (se necessario).]**
   1. Seleziona **[!UICONTROL Crea gruppi per le cartelle aggiunte]**.
   1. Seleziona le destinazioni in cui desideri usare il codice AppMeasurement Code e fai clic su **[!UICONTROL Fine]**.
   ![](assets/xcode-settings.png){larghezza="672"}

1. Nella scheda **[!UICONTROL Fasi build]** della destinazione del progetto, espandi la sezione **[!UICONTROL Collega binario a librerie]** e aggiungi le seguenti librerie:

   * `libsqlite3.dylib`
   * `SystemConfiguration.framework`

1. Conferma che l'app possa essere generata senza errori imprevisti.

## Implementare il tracciamento personalizzato {#section_FD102B3CDAA4492FB04E56BF17E28663}

Nei file `html` in cui desideri usare il tracciamento, aggiungi quanto segue al tag `<head>`:

```html
<script type="text/javascript" charset="utf-8" src="ADB_Helper.js"></script>
```

