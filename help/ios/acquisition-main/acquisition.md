---
description: In Adobe Mobile Services è possibile generare collegamenti di acquisizione con codici di tracciamento univoci. Quando un utente scarica ed esegue un’app dall’Apple App Store dopo aver fatto clic sul collegamento generato, l’SDK raccoglie e invia automaticamente i dati di acquisizione ad Adobe Mobile Services.
seo-description: In Adobe Mobile Services è possibile generare collegamenti di acquisizione con codici di tracciamento univoci. Quando un utente scarica ed esegue un’app dall’Apple App Store dopo aver fatto clic sul collegamento generato, l’SDK raccoglie e invia automaticamente i dati di acquisizione ad Adobe Mobile Services.
seo-title: Acquisizione da app mobile
solution: Experience Cloud,Analytics
title: Acquisizione da app mobile
topic: Developer and implementation
uuid: 5fece619-e4b8-4d06-9250-dcb66fa32ce0
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '414'
ht-degree: 100%

---


# Acquisizione da app mobile {#mobile-app-acquisition}

In Adobe Mobile Services è possibile generare collegamenti di acquisizione con codici di tracciamento univoci. Quando un utente scarica ed esegue un’app dall’Apple App Store dopo aver fatto clic sul collegamento generato, l’SDK raccoglie e invia automaticamente i dati di acquisizione ad Adobe Mobile Services.

Per usare la funzione Acquisizione, **è necessario** disporre della versione SDK 4.1 o successiva.

I collegamenti di acquisizione devono essere creati in Adobe Mobile Services. Per ulteriori informazioni, vedi [Acquisizione](/help/using/acquisition-main/acquisition-main.md).

Le informazioni in questa sezione consentono all&#39;SDK di inviare dati di acquisizione da un collegamento di acquisizione.

## Tracciamento dell&#39;acquisizione da app mobile {#section_CEA30C652AC8470784B8054E299B80FA}

1. Aggiungi la libreria al tuo progetto e implementa le funzioni di ciclo di vita (lifecycle).

   Per ulteriori informazioni, consulta *Aggiungere l’SDK e il file di configurazione al progetto* in [Implementazione e ciclo di vita di base](/help/ios/getting-started/dev-qs.md).
1. Importa la libreria:

   ```objective-c
   #import "ADBMobile.h"
   ```

1. Verifica che il file `ADBMobileConfig.json` contenga le impostazioni di acquisizione necessarie:

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
   >se invii dati a suite di rapporti multiple, usa le impostazioni di acquisizione (server di acquisizione e appid) dell&#39;app associata alla prima suite di rapporti nell&#39;elenco degli ID di suite di rapporti.

   Le impostazioni `acquisition` sono generate da Adobe Mobile Services e non devono essere modificate. Per ulteriori informazioni sul download di un file `ADBMobileConfig.json` personalizzato con le impostazioni `acquisition` pre-configurate, vedi [Prima di iniziare](/help/ios/getting-started/requirements.md).

Una volta che queste impostazioni saranno state abilitate, i dati di acquisizione vengono inviati automaticamente con la chiamata &quot;lifecycle&quot; iniziale, dopo il primo avvio dell&#39;app.

>[!CAUTION]
>
>`referrerTimeout` deve essere impostato su un valore maggiore di 0 per abilitare l&#39;acquisizione da parte dell&#39;app.

## Abilitazione dell&#39;app iOS per i collegamenti universali

Se utilizzi collegamenti universali nell’app, aggiungi il dominio dei collegamenti Adobe Marketing all’elenco Domini associati per la tua app.

In Xcode, per aggiungere il dominio dei collegamenti Adobe Marketing all&#39;elenco Domini associati:

1. Vai alla destinazione del progetto e fai clic sulla scheda **[!UICONTROL Capacità]**.
2. Scorri verso il basso fino alla sezione **[!UICONTROL Domini associati]** e attivala.
3. Aggiungi una voce all’elenco **[!UICONTROL Domini]** per il dominio dei collegamenti di marketing dall’URL di Collegamenti marketing.

La voce si presenterà simile a questa: `applinks:5848561889a02a6996aea62b.c00.adobe.com`.