---
title: Guida introduttiva per sviluppatori
seo-title: Avvio rapido sviluppatore BlackBerry per Adobe Mobile Services
description: La Guida di avvio rapido per sviluppatori BlackBerry aiuta a comprendere il processo di implementazione della libreria BlackBerry per Adobe Mobile Services.
seo-description: La Guida di avvio rapido per sviluppatori BlackBerry aiuta a comprendere il processo di implementazione della libreria BlackBerry per Adobe Mobile Services.
translation-type: tm+mt
source-git-commit: 19264af3f4a675add6f61c27f4cdaf20033b9bb7

---


# Guida rapida per sviluppatori

Queste informazioni sono utili per comprendere come implementare la libreria BlackBerry.

## Scaricare l'SDK

**L'SDK richiede BlackBerry 10 o versione successiva.**

Dopo aver decompresso l'SDK scaricato, controlla che i seguenti file si trovino nella cartella `AdobeMobile`:

* `Device-Coverage/libADBMobileShared.so`
* `Device-Debug/libADBMobileShared.so`
* `Device-Profile/libADBMobileShared.so`
* `Device-Release/libADBMobileShared.so`
* `public/ADBMediaAnalytics.hpp`
* `public/ADBMediaSharedHeader.hpp`
* `public/ADBMediaState.hpp`
* `public/ADBMobile.hpp`
* `Simulator-Coverage/libADBMobileShared.so`
* `Simulator-Debug/libADBMobileShared.so`
* `Simulator-Profile/libADBMobileShared.so`

## Aggiungere gli SDK al progetto

1. Right-click on your project and select **[!UICONTROL Configure]** &gt; **[!UICONTROL Add Library]**.
1. Seleziona **[!UICONTROL Libreria esterna]** e fai clic su **[!UICONTROL Avanti]**.
1. Fai clic su **[!UICONTROL Sfoglia]** accanto a **Libreria dispositivo[!UICONTROL .]**
1. Navigate to the `ADBMobile-4.0.0BETA-BlackBerry` folder.
1. In the `Device-Debug` folder, select `libADBMobileShared.so` and click **[!UICONTROL Open]**.
1. Fai clic su **[!UICONTROL Sfoglia]** accanto a **Libreria emulatore[!UICONTROL .]**
1. Navigate to the `ADBMobile-4.0.0BETA-BlackBerry` folder.
1. In the `Device-Debug` folder, select `libADBMobileShared.so` and click **[!UICONTROL Open]**.
1. Fai clic su **[!UICONTROL Aggiungi]** accanto al campo **Includi cartelle[!UICONTROL .]**
1. Navigate to the `ADBMobile-4.0.0BETA-BlackBerry` folder.
1. Aggiungi la cartella `public` alle cartelle da includere.
1. In the `ADBMobile-4.0.0BETA-BlackBerry` folder, there is a `.json` config file named `ADBMobileConfig.json`.

   Copia tale file nella directory principale del progetto.
1. Fai clic con il pulsante destro del mouse sul progetto e seleziona **[!UICONTROL Aggiorna]**.

   The `.json` file should now be visible in your **[!UICONTROL Project Explorer]**.
1. Apri il file `bar-descriptor.xml` per il progetto.
1. In fondo alla finestra, seleziona la scheda **[!UICONTROL Risorse].**
1. Verifica che **[!UICONTROL (Tutte le configurazioni)]** sia selezionato, quindi fai clic su **[!UICONTROL Aggiungi file]nella sezione** Risorse] della finestra.**[!UICONTROL **
   >[!TIP]
   >
   >Esiste un bug nell'IDE Momentics QNX che a volte impedisce la visualizzazione di tali pulsanti. Se i pulsanti non sono visibili, ridimensionare le finestre finché non vengono visualizzate.

1. Fare clic su **[!UICONTROL Workspace]**.
1. Individua il file `ADBMobileConfig.json`**nel progetto e fai clic su[!UICONTROL OK]**.

Your application can import the classes/interfaces from the `adobeMobileLibrary.jar` library by using `#include <ADBMobile.hpp>`.

## Aggiungi autorizzazioni app

In `bar-descriptor.xml` in the project directory, add the line `<permission>access_internet</permission>`, or in the QNX Momentics IDE, select the **[!UICONTROL Internet]** box on the permissions section of the **[!UICONTROL Application]** tab.

## Update the `ADBMobileConfig.json` config file

Il file `ADBMobileConfig.json` contiene impostazioni SDK globali. Per iniziare devi aggiornare alcuni valori.

Di seguito viene indicato un esempio del file `ADBMobileConfig.json`:

```json
{
    "version" : "1.0",
    "analytics" : {
        "rsids" : "coolApp",
        "server" : "my.CoolApp.com",
        "charset" : "UTF-8",
        "ssl" : true,
        "offlineEnabled" : true,
        "lifecycleTimeout" : 5,
        "privacyDefault" : "optedin",
    }
}
```

You must at least update the `rsids` and `server` parameters. Per ulteriori dettagli, consultate Guida di riferimento [di classe e metodo per](/help/blackberry/methods.md)Adobe Mobile.

A questo punto puoi implementare Analytics nella tua app BlackBerry 10.
