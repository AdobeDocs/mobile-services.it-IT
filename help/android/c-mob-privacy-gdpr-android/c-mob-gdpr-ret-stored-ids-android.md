---
description: Queste informazioni spiegano come recuperare identità SDK memorizzate localmente dalla tua app Android e come gestire le richieste di accesso ai dati in conformità ai requisiti GDPR.
title: Recupero di ID memorizzati
uuid: 6fd3d202-b0a1-4c80-96f4-369fc24ac0a3
exl-id: 86c990d8-334b-4003-b0ac-d5404cb598e4
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '131'
ht-degree: 54%

---

# Recupero di ID memorizzati{#retrieving-stored-identifiers}

Queste informazioni spiegano come recuperare identità SDK memorizzate localmente dalla tua app Android e come gestire le richieste di accesso ai dati in conformità ai requisiti RGPD.

>[!IMPORTANT]
>
>Il metodo `getAllIdentifiersAsync` recupera le identità memorizzate nell&#39;SDK. È necessario chiamare questo metodo **prima** che l&#39;utente rinunci.

Le identità SDK (a seconda dei casi) vengono memorizzate localmente e restituite in una stringa JSON che potrebbe contenere:

* Contesto aziendale - ID organizzazione IMS
* ID utente
* Experience Cloud ID (MID), già noto come Experience Cloud ID
* Codici di integrazione (ADID, ID push)
* ID sorgente dati (DPID, DPUUID)
* ID di Analytics (AVID, AID, VID e RSID associati)
* ID legacy di Target (TNTID, TNT3rdpartyID)
* ID Audience Manager (UUID)

Ecco un esempio del metodo `ADBMobile getAllIdentifiersAsync` in Android:

```java
Config.getAllIdentifiersAsync(new ConfigCallback<String>() { 
     @Override 
     public void call(String identitiesJson) {                 
         Log.d("ADBMobile Identities", identitiesJson); 
     } 
});
```
