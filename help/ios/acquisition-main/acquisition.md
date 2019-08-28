---
description: In Adobe Mobile Services è possibile generare collegamenti di acquisizione con codici di tracciamento univoci. Quando un utente scarica ed esegue un'app dall'Apple App Store dopo aver fatto clic sul collegamento generato, l'SDK raccoglie e invia automaticamente i dati di acquisizione ad Adobe Mobile Services.
seo-description: In Adobe Mobile Services è possibile generare collegamenti di acquisizione con codici di tracciamento univoci. Quando un utente scarica ed esegue un'app dall'Apple App Store dopo aver fatto clic sul collegamento generato, l'SDK raccoglie e invia automaticamente i dati di acquisizione ad Adobe Mobile Services.
seo-title: Acquisizione da app mobile
solution: Marketing Cloud, Analytics
title: Acquisizione da app mobile
topic: Sviluppatore e implementazione
uuid: 5 fece 619-e 4 b 8-4 d 06-9250-dcb 66 fa 32 ce 0
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Mobile app acquisition {#mobile-app-acquisition}

In Adobe Mobile Services è possibile generare collegamenti di acquisizione con codici di tracciamento univoci. Quando un utente scarica ed esegue un'app dall'Apple App Store dopo aver fatto clic sul collegamento generato, l'SDK raccoglie e invia automaticamente i dati di acquisizione ad Adobe Mobile Services.

Per usare Acquisition, **devi** disporre della versione SDK 4.1 o successiva.

I collegamenti di acquisizione devono essere creati in Adobe Mobile Services. For more information, see [Acquisition](/help/using/acquisition-main/acquisition-main.md).

Le informazioni contenute in questa sezione consentono all'SDK di inviare dati di acquisizione da un collegamento di acquisizione.

## Tracking mobile app acquisition {#section_CEA30C652AC8470784B8054E299B80FA}

1. Aggiungi la libreria al tuo progetto e implementa le funzioni di ciclo di vita (lifecycle).

   Per ulteriori informazioni, vedi *Aggiungere l'SDK e il file di configurazione al progetto* in [Implementazione e ciclo di vita di base](/help/ios/getting-started/dev-qs.md).
1. Importa la libreria:

   ```objective-c
   #import "ADBMobile.h"
   ```

1. Verify that the `ADBMobileConfig.json` file contains the required acquisition settings:

   ```xml
   "acquisition": { 
      "server": "c00.adobe.com", 
      "appid": "0652024f-adcd-49f9-9bd7-2552a4565d2f" 
   }, 
   "analytics": { 
     "referrerTimeout": 5, 
     ...
   ```

   >[!IMPORTANT]
   >
   >Se invii dati a più suite di rapporti, usa le impostazioni di acquisizione (server di acquisizione e appid) dall'app associata alla prima suite di rapporti nell'elenco degli ID suite di rapporti.

   `acquisition` Le impostazioni sono generate da Adobe Mobile Services e non devono essere modificate. For more information about how to download a customized `ADBMobileConfig.json` file with the `acquisition` settings pre-configured, see [Before You Start](/help/ios/getting-started/requirements.md).

Una volta che queste impostazioni saranno state abilitate, i dati di acquisizione vengono inviati automaticamente con la chiamata "lifecycle" iniziale, dopo il primo avvio dell'app.

>[!CAUTION]
>
>`referrerTimeout` devono essere impostati su un valore maggiore di 0 per abilitare l'acquisizione da app.

## Abilitazione dell'app iOS per i collegamenti universali

Se utilizzi collegamenti universali nell'app, aggiungi il dominio dei collegamenti Adobe Marketing all'elenco Domini associati per l'app.

In Xcode, per aggiungere il dominio dei collegamenti Adobe Marketing all'elenco Domini associati:

1. Andate alla destinazione del progetto e fate clic sulla **[!UICONTROL scheda Capacità]** .
2. Scorri verso il basso fino **[!UICONTROL alla sezione Domini]** associati e poi attivala.
3. Aggiungi una voce nell'elenco **[!UICONTROL Domini]** per il dominio Collegamento marketing dall'URL dei collegamenti di marketing.

La tua voce sarà `applinks:5848561889a02a6996aea62b.c00.adobe.com`simile.