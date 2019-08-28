---
description: Queste informazioni spiegano come recuperare identità Experience Cloud SDK memorizzate localmente dalla tua app iOS e come gestire le richieste di accesso ai dati in conformità ai requisiti RGPD.
seo-description: Queste informazioni spiegano come recuperare identità Experience Cloud SDK memorizzate localmente dalla tua app iOS e come gestire le richieste di accesso ai dati in conformità ai requisiti RGPD.
seo-title: Recupero di ID memorizzati
title: Recupero di ID memorizzati
uuid: 4 fb 2 c 166-6700-4 f 8 b-b 60 b -137 b 199 e 0509
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Retrieving stored identifiers{#retrieving-stored-identifiers}

Queste informazioni spiegano come recuperare identità Experience Cloud SDK memorizzate localmente dalla tua app iOS e come gestire le richieste di accesso ai dati in conformità ai requisiti RGPD.

Per ulteriori informazioni sul regolamento RGPD, consulta la pagina dedicata all'[RGPD e il tuo business](https://www.adobe.com/privacy/general-data-protection-regulation.html).

>[!IMPORTANT]
>
>Il `getAllIdentifiersAsync` metodo recupera le identità memorizzate negli SDK di Experience Cloud. È necessario utilizzare questo metodo **prima** che l'utente neghi il consenso.

Le identità Experience Cloud SDK (come applicabile) vengono memorizzate localmente e restituite in una stringa JSON che può contenere:

* Contesto aziendale - ID organizzazione IMS
* ID utente
* Experience Cloud ID (MID), già noto come Marketing Cloud ID
* Codici di integrazione (ADID, ID push)
* ID di origine dati (DPID, DPUUID)
* ID Analytics (AVID, AID, VID e RSID associati)
* ID Target legacy (TNTID, TNT3rdpartyID)
* ID Audience Manager (UUID)

Ecco un esempio del metodo `ADBMobile getAllIdentifiersAsync` in iOS:

```objective-c
[ADBMobile getAllIdentifiersAsync:^(NSString * _Nullable content){
      NSLog(content) 
}]
```

