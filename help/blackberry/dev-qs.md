---
title: Guida rapida per sviluppatori
seo-title: BlackBerry Developer Quick Start per  Adobe Mobile Services
description: La Guida di avvio rapido per sviluppatori BlackBerry aiuta a comprendere il processo di implementazione della libreria BlackBerry per  Adobe Mobile Services.
seo-description: La Guida di avvio rapido per sviluppatori BlackBerry aiuta a comprendere il processo di implementazione della libreria BlackBerry per  Adobe Mobile Services.
translation-type: tm+mt
source-git-commit: 19264af3f4a675add6f61c27f4cdaf20033b9bb7
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 2%

---


# Guida rapida per sviluppatori

Queste informazioni sono utili per comprendere il processo di implementazione della libreria BlackBerry.

## Scaricare l&#39;SDK 

**L’SDK richiede BlackBerry 10 o versione successiva.**

Dopo aver decompresso l’SDK scaricato, verifica che in una `AdobeMobile` cartella siano presenti i file seguenti:

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

1. Fai clic con il pulsante destro del mouse sul progetto e seleziona **[!UICONTROL Configura]** > **[!UICONTROL Aggiungi libreria]**.
1. Selezionate Libreria **** esterna e fate clic su **[!UICONTROL Avanti]**.
1. Fate clic su **[!UICONTROL Sfoglia]** accanto al campo Libreria **** dispositivo.
1. Navigate to the `ADBMobile-4.0.0BETA-BlackBerry` folder.
1. Nella `Device-Debug` cartella, selezionate `libADBMobileShared.so` e fate clic su **[!UICONTROL Apri]**.
1. Fate clic su **[!UICONTROL Sfoglia]** accanto al campo Libreria **** simulatore.
1. Navigate to the `ADBMobile-4.0.0BETA-BlackBerry` folder.
1. Nella `Device-Debug` cartella, selezionate `libADBMobileShared.so` e fate clic su **[!UICONTROL Apri]**.
1. Fate clic su **[!UICONTROL Aggiungi]** accanto al campo **[!UICONTROL Includi cartelle]** .
1. Navigate to the `ADBMobile-4.0.0BETA-BlackBerry` folder.
1. Aggiungi la `public` cartella alle cartelle incluse.
1. Nella `ADBMobile-4.0.0BETA-BlackBerry` cartella è presente un `.json` file di configurazione denominato `ADBMobileConfig.json`.

   Copiate il file nella directory principale del progetto.
1. Fai clic con il pulsante destro del mouse sul progetto e seleziona **[!UICONTROL Aggiorna]**.

   Il `.json` file deve ora essere visibile in Esplora **[!UICONTROL progetti]**.
1. Aprite il `bar-descriptor.xml` file del progetto.
1. Nella parte inferiore della finestra, selezionate la scheda **[!UICONTROL Risorse]** .
1. Verificate che **[!UICONTROL (Tutte le configurazioni)]** sia selezionato, quindi fate clic su **[!UICONTROL Aggiungi file]** nella sezione **[!UICONTROL Risorse]** della finestra.
   >[!TIP]
   >
   >Esiste un bug nell&#39;IDE Momentics QNX che a volte impedisce la visualizzazione di tali pulsanti. Se i pulsanti non sono visibili, ridimensionare le finestre finché non vengono visualizzate.

1. Fare clic su **[!UICONTROL Area di lavoro]**.
1. Individuate il `ADBMobileConfig.json` file nel progetto e fate clic su **[!UICONTROL OK]**.

L&#39;applicazione può importare le classi/interfacce dalla `adobeMobileLibrary.jar` libreria utilizzando `#include <ADBMobile.hpp>`.

## Aggiungere le autorizzazioni dell&#39;app

Nella directory `bar-descriptor.xml` del progetto, aggiungete la riga `<permission>access_internet</permission>`oppure, in QNX Momentics IDE, selezionate la casella **[!UICONTROL Internet]** nella sezione delle autorizzazioni della scheda **[!UICONTROL Applicazione]** .

## Aggiornare il file di `ADBMobileConfig.json` configurazione

Il `ADBMobileConfig.json` file contiene impostazioni SDK globali. Per iniziare devi aggiornare alcuni valori.

The following is an example of an `ADBMobileConfig.json` file:

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

È necessario almeno aggiornare i `rsids` parametri e `server` . Per ulteriori dettagli, vedete [Adobe Riferimento](/help/blackberry/methods.md)classe e metodo Mobile.

Ora puoi implementare Analytics nella tua app BlackBerry 10.
