---
description: Queste informazioni spiegano come recuperare identità SDK memorizzate localmente dalla tua app Android e come gestire le richieste di accesso ai dati in conformità ai requisiti RGPD.
seo-description: Queste informazioni spiegano come recuperare identità SDK memorizzate localmente dalla tua app Android e come gestire le richieste di accesso ai dati in conformità ai requisiti RGPD.
seo-title: Recupero di identificatori memorizzati
title: Recupero di identificatori memorizzati
uuid: 6 fd 3 d 202-b 0 a 1-4 c 80-96 f 4-369 fc 24 ac 0 a 3
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Retrieving stored identifiers{#retrieving-stored-identifiers}

Queste informazioni spiegano come recuperare identità SDK memorizzate localmente dalla tua app Android e come gestire le richieste di accesso ai dati in conformità ai requisiti RGPD.

>[!IMPORTANT]
>
>The `getAllIdentifiersAsync` method retrieves identities stored in the SDK. È necessario utilizzare questo metodo **prima** che l'utente neghi il consenso.

Le identità SDK (come applicabile) vengono memorizzate localmente e restituite in una stringa JSON che può contenere:

* Contesto aziendale - ID organizzazione IMS
* ID utente
* Experience Cloud ID (MID), già noto come Marketing Cloud ID
* Codici di integrazione (ADID, ID push)
* ID di origine dati (DPID, DPUUID)
* ID Analytics (AVID, AID, VID e RSID associati)
* ID Target legacy (TNTID, TNT3rdpartyID)
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
