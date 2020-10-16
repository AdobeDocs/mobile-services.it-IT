---
description: 'La libreria iOS fornisce i seguenti metodi di acquisizione '
seo-description: 'La libreria iOS fornisce i seguenti metodi di acquisizione '
seo-title: Metodi di acquisizione
solution: Experience Cloud,Analytics
title: Metodi di acquisizione
uuid: 6f88de57-793d-4d33-9a54-f6714289fd2c
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '93'
ht-degree: 100%

---


# Metodi di acquisizione {#acquisition-methods}

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


