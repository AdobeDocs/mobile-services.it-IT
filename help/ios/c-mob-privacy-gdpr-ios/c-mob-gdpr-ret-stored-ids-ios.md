---
description: Queste informazioni spiegano come recuperare identità Experience Cloud SDK memorizzate localmente dalla tua app iOS e come gestire le richieste di accesso ai dati in conformità ai requisiti GDPR.
seo-description: Queste informazioni spiegano come recuperare identità Experience Cloud SDK memorizzate localmente dalla tua app iOS e come gestire le richieste di accesso ai dati in conformità ai requisiti GDPR.
seo-title: Recupero degli identificatori memorizzati
title: Recupero degli identificatori memorizzati
uuid: 4fb2c166-6700-4f8b-b60b-137b199e0509
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 56%

---


# Recupero di ID memorizzati{#retrieving-stored-identifiers}

Queste informazioni spiegano come recuperare identità Experience Cloud SDK memorizzate localmente dalla tua app iOS e come gestire le richieste di accesso ai dati in conformità ai requisiti RGPD.

Per ulteriori informazioni sul GDPR, consulta [GDPR e la sezione dedicata agli affari](https://www.adobe.com/it/privacy/general-data-protection-regulation.html).

>[!IMPORTANT]
>
>Il metodo `getAllIdentifiersAsync` recupera le identità memorizzate negli SDK di Experience Cloud. È necessario chiamare questo metodo **prima** che l&#39;utente si rifiuti.

 identità SDK di Experience Cloud (nei casi in cui sono richieste) vengono memorizzate localmente e restituite in una stringa JSON che può contenere:

* Contesto aziendale - ID organizzazione IMS
* ID utente
* Experience Cloud ID (MID), già noto come Experience Cloud ID
* Codici di integrazione (ADID, ID push)
* ID origine dati (DPID, DPUUID)
* ID di Analytics (AVID, AID, VID e RSID associati)
* ID legacy di destinazione (TNTID, TNT3rdpartyID)
* ID Audience Manager  (UUID)

Ecco un esempio del metodo `ADBMobile getAllIdentifiersAsync` in iOS:

```objective-c
[ADBMobile getAllIdentifiersAsync:^(NSString * _Nullable content){
      NSLog(content) 
}]
```

