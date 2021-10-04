---
description: Queste informazioni spiegano come recuperare identità Experience Cloud SDK memorizzate localmente dalla tua app iOS e come gestire le richieste di accesso ai dati in conformità ai requisiti GDPR.
title: Recupero di ID memorizzati
uuid: 4fb2c166-6700-4f8b-b60b-137b199e0509
exl-id: ec8592af-fb08-4ab3-99a1-51ac5697a3d8
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 51%

---

# Recupero di ID memorizzati{#retrieving-stored-identifiers}

Queste informazioni spiegano come recuperare identità Experience Cloud SDK memorizzate localmente dalla tua app iOS e come gestire le richieste di accesso ai dati in conformità ai requisiti GDPR.

Per ulteriori informazioni sul RGPD, consulta [RGPD e la tua azienda](https://www.adobe.com/it/privacy/general-data-protection-regulation.html).

>[!IMPORTANT]
>
>Il metodo `getAllIdentifiersAsync` recupera le identità memorizzate negli SDK di Experience Cloud. È necessario chiamare questo metodo **prima** che l&#39;utente rinunci.

Le identità SDK di Experience Cloud (come applicabile) vengono memorizzate localmente e restituite in una stringa JSON che potrebbe contenere:

* Contesto aziendale - ID organizzazione IMS
* ID utente
* Experience Cloud ID (MID), già noto come Experience Cloud ID
* Codici di integrazione (ADID, ID push)
* ID sorgente dati (DPID, DPUUID)
* ID di Analytics (AVID, AID, VID e RSID associati)
* ID legacy di Target (TNTID, TNT3rdpartyID)
* ID Audience Manager (UUID)

Ecco un esempio del metodo `ADBMobile getAllIdentifiersAsync` in iOS:

```objective-c
[ADBMobile getAllIdentifiersAsync:^(NSString * _Nullable content){
      NSLog(content) 
}]
```
