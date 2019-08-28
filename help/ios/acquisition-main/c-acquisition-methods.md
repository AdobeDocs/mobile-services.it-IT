---
description: 'La libreria iOS fornisce i seguenti metodi di acquisizione '
seo-description: 'La libreria iOS fornisce i seguenti metodi di acquisizione '
seo-title: Metodi di acquisizione
solution: Marketing Cloud, Analytics
title: Metodi di acquisizione
uuid: 6 f 88 de 57-793 d -4 d 33-9 a 54-f 6714289 fd 2 c
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Acquisition methods {#acquisition-methods}

La libreria iOS fornisce i seguenti metodi di acquisizione:

È supportato il seguente metodo:

* **acquisitionCampaignStartForApp:data:**

   Consente agli sviluppatori di avviare una campagna di acquisizione app, come se l'utente avesse fatto clic su un collegamento. È utile per creare collegamenti di acquisizione manuali e per gestire direttamente il reindirizzamento all'App Store, ad esempio con `SKStoreView`.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      + (void)acquisitionCampaignStartForApp:(NSString *) appId data:(NSDictionary *)data; 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      [ADBMobile acquisitionCampaignStartForApp:@"0652024f-adcd-49f9-9bd7-2552a4564d2f" data:@{@"custom.key":@"value"}]; 
      ```


