---
title: Guida introduttiva per sviluppatori
description: La Guida rapida per sviluppatori di BlackBerry aiuta a comprendere il processo di implementazione della libreria BlackBerry per Adobe Mobile Services.
exl-id: 65f39667-541a-4bbd-af9b-823638aa6f42
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 2%

---

# Guida rapida per sviluppatori

Queste informazioni sono utili per comprendere il processo di implementazione della libreria BlackBerry.

## Scaricare l&#39;SDK 

**L&#39;SDK richiede BlackBerry 10 o versione successiva.**

Dopo aver decompresso l&#39;SDK scaricato, verifica che i seguenti file siano presenti in una cartella `AdobeMobile` :

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
1. Seleziona **[!UICONTROL Libreria esterna]** e fai clic su **[!UICONTROL Avanti]**.
1. Fai clic su **[!UICONTROL Sfoglia]** accanto al campo **[!UICONTROL Libreria dispositivi]** .
1. Passa alla cartella `ADBMobile-4.0.0BETA-BlackBerry` .
1. Nella cartella `Device-Debug`, seleziona `libADBMobileShared.so` e fai clic su **[!UICONTROL Apri]**.
1. Fai clic su **[!UICONTROL Sfoglia]** accanto al campo **[!UICONTROL Libreria simulatore]** .
1. Passa alla cartella `ADBMobile-4.0.0BETA-BlackBerry` .
1. Nella cartella `Device-Debug`, seleziona `libADBMobileShared.so` e fai clic su **[!UICONTROL Apri]**.
1. Fare clic su **[!UICONTROL Aggiungi]** accanto al campo **[!UICONTROL Includi cartelle]**.
1. Passa alla cartella `ADBMobile-4.0.0BETA-BlackBerry` .
1. Aggiungi la cartella `public` alle cartelle incluse.
1. Nella cartella `ADBMobile-4.0.0BETA-BlackBerry` è presente un file di configurazione `.json` denominato `ADBMobileConfig.json`.

   Copia il file nella directory principale del progetto.
1. Fai clic con il pulsante destro del mouse sul progetto e seleziona **[!UICONTROL Aggiorna]**.

   Il file `.json` deve ora essere visibile nel **[!UICONTROL Project Explorer]**.
1. Apri il file `bar-descriptor.xml` del progetto.
1. Nella parte inferiore della finestra, seleziona la scheda **[!UICONTROL Risorse]** .
1. Conferma che sia selezionato **[!UICONTROL (All Configurations)]**, quindi fai clic su **[!UICONTROL Aggiungi file]** nella sezione **[!UICONTROL Risorse]** della finestra.
   >[!TIP]
   >
   >C&#39;è un bug nell&#39;IDE di QNX Momentics che a volte impedisce che tali pulsanti siano visibili. Se i pulsanti non vengono visualizzati, ridimensionare le finestre finché non vengono visualizzati.

1. Fare clic su **[!UICONTROL Area di lavoro]**.
1. Trova il file `ADBMobileConfig.json` nel progetto e fai clic su **[!UICONTROL OK]**.

L&#39;applicazione può importare le classi/interfacce dalla libreria `adobeMobileLibrary.jar` utilizzando `#include <ADBMobile.hpp>`.

## Aggiungere le autorizzazioni dell&#39;app

In `bar-descriptor.xml` nella directory del progetto, aggiungi la riga `<permission>access_internet</permission>`, oppure in QNX Momentics IDE, seleziona la casella **[!UICONTROL Internet]** nella sezione delle autorizzazioni della scheda **[!UICONTROL Applicazione]**.

## Aggiorna il file di configurazione `ADBMobileConfig.json`

Il file `ADBMobileConfig.json` contiene impostazioni SDK globali. Per iniziare, devi aggiornare alcuni valori.

Di seguito è riportato un esempio di file `ADBMobileConfig.json` :

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

È necessario almeno aggiornare i parametri `rsids` e `server`. Per ulteriori dettagli, consulta [Guida di riferimento delle classi e dei metodi per Adobe Mobile](/help/blackberry/methods.md).

Ora puoi implementare Analytics nella tua app BlackBerry 10.
