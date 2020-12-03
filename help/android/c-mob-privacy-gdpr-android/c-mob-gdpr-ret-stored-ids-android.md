---
description: Queste informazioni spiegano come recuperare identità SDK memorizzate localmente dalla tua app Android e come gestire le richieste di accesso ai dati in conformità ai requisiti GDPR.
seo-description: Queste informazioni spiegano come recuperare identità SDK memorizzate localmente dalla tua app Android e come gestire le richieste di accesso ai dati in conformità ai requisiti GDPR.
seo-title: Recupero di ID memorizzati
title: Recupero di ID memorizzati
uuid: 6fd3d202-b0a1-4c80-96f4-369fc24ac0a3
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 60%

---


# Recupero di ID memorizzati{#retrieving-stored-identifiers}

Queste informazioni spiegano come recuperare identità SDK memorizzate localmente dalla tua app Android e come gestire le richieste di accesso ai dati in conformità ai requisiti RGPD.

>[!IMPORTANT]
>
>Il metodo `getAllIdentifiersAsync` recupera le identità memorizzate nell&#39;SDK. È necessario chiamare questo metodo **prima** che l&#39;utente si rifiuti.

Le identità SDK (nei casi in cui sono richieste) vengono memorizzate localmente e restituite in una stringa JSON che può contenere:

* Contesto aziendale - ID organizzazione IMS
* ID utente
* Experience Cloud ID (MID), già noto come Experience Cloud ID
* Codici di integrazione (ADID, ID push)
* ID origine dati (DPID, DPUUID)
* ID di Analytics (AVID, AID, VID e RSID associati)
* ID legacy di destinazione (TNTID, TNT3rdpartyID)
* ID Audience Manager  (UUID)

Ecco un esempio del metodo `ADBMobile getAllIdentifiersAsync` in Android:

```java
Config.getAllIdentifiersAsync(new ConfigCallback<String>() { 
     @Override 
     public void call(String identitiesJson) {                 
         Log.d("ADBMobile Identities", identitiesJson); 
     } 
});
```
