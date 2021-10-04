---
description: 'La libreria iOS fornisce i seguenti metodi di acquisizione '
solution: Experience Cloud,Analytics
title: Metodi di acquisizione
uuid: 6f88de57-793d-4d33-9a54-f6714289fd2c
exl-id: dd2721ae-b9a6-48b9-bc92-8e12ee551929
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '80'
ht-degree: 100%

---

# Metodi di acquisizione  {#acquisition-methods}

La libreria iOS fornisce i seguenti metodi di acquisizione:

È supportato il seguente metodo:

* **acquisitionCampaignStartForApp:data:**

   Consente agli sviluppatori di avviare una campagna di acquisizione app, come se l&#39;utente avesse fatto clic su un collegamento. È utile per creare collegamenti di acquisizione manuali e per gestire direttamente il reindirizzamento all&#39;App Store, ad esempio con `SKStoreView`.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      + (void)acquisitionCampaignStartForApp:(NSString *) appId data:(NSDictionary *)data; 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      [ADBMobile acquisitionCampaignStartForApp:@"0652024f-adcd-49f9-9bd7-2552a4564d2f" data:@{@"custom.key":@"value"}]; 
      ```
