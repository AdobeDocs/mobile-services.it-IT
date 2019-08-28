---
description: Queste informazioni aiutano a gestire una richiesta di cancellazione dati in conformità ai requisiti RGPD.
seo-description: Queste informazioni aiutano a gestire una richiesta di cancellazione dati in conformità ai requisiti RGPD.
seo-title: Impostazione dello stato di consenso o diniego dell'utente
solution: Marketing Cloud, Analytics
title: Impostazione dello stato di consenso o diniego dell'utente
topic: Sviluppatore e implementazione
uuid: 44 a 09 a 25-93 c 6-4 e 1 a-b 69 e -710018 e 8 b 6 c 3
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Setting the user's opt status {#setting-the-user-s-opt-status}

Queste informazioni aiutano a gestire una richiesta di cancellazione dati in conformità ai requisiti RGPD.

>[!IMPORTANT]
>
>Starting with Experience Cloud iOS SDKs 4.15, setting the privacy status to `unknown` holds Audience Manager and Experience Cloud ID hits.

Per definire se le attività di Analytics, Target e Audience Manager sono consentite su un dispositivo, usa le seguenti impostazioni:

* `privacyDefault` nel [file di configurazione adbmobile JSON](/help/ios/configuration/json-config/json-config.md).

   Questa impostazione controlla l'impostazione iniziale che viene mantenuta finché non viene modificata nel codice.

* `setPrivacyStatus`.

   Quando l'impostazione della privacy viene modificata utilizzando questo metodo, la modifica diventa permanente finché non viene nuovamente cambiata con questo metodo, oppure finché non disinstalli e reinstalli l'app.

   Per ulteriori informazioni sui metodi, vedi [Metodi di Configurazione](/help/ios/configuration/json-config/json-config.md).

Seguono informazioni su ciascun stato di privacy:

* **Consenso accordato**

   * Analytics: gli hit vengono inviati.
   * Target: le richieste Mbox vengono inviate.
   * Audience Manager: i segnali e le sincronizzazioni ID vengono inviati.
   * Value in the JSON config file: `optedin`
   * Valore in `setPrivacyStatus`: `ADBMobilePrivacyStatusOptIn`

* **Consenso negato**

   * Analytics: gli hit vengono scartati.
   * Target: le richieste Mbox non sono consentite.
   * Audience Manager: i segnali e le sincronizzazioni ID non sono consentiti.
   * Value in the JSON config file: `optedout`
   * Valore in `setPrivacyStatus`: `ADBMobilePrivacyStatusOptOut`

* **Sconosciuto**

   * Analytics: se **è** abilitato il tracciamento offline, gli hit vengono salvati finché lo stato di privacy non cambia in optedin (gli hit vengono inviati) o in optedout (gli hit vengono scartati).

      Se il tracciamento offline **non è** abilitato, gli hit vengono scartati finché lo stato di privacy non cambia in optedin.

   * Target: le richieste Mbox vengono inviate.
   * Audience Manager: i segnali e le sincronizzazioni ID vengono inviati.
   * Value in the JSON config file: `optunknown`
   * Valore in `setPrivacyStatus`: `ADBMobilePrivacyStatusUnknown`

## Esempi {#section_128AC455EE024193B5D4E5A565B53D00}

```objective-c
- (IBAction) setPrivacyOptIn { 
 [ADBMobile setPrivacyStatus:ADBMobilePrivacyStatusOptIn]; 
} 
- (IBAction) setPrivacyOptOut { 
 [ADBMobile setPrivacyStatus:ADBMobilePrivacyStatusOptOut]; 
} 
- (IBAction) setPrivacyOptUnknown { 
 [ADBMobile setPrivacyStatus:ADBMobilePrivacyStatusUnknown]; 
}
```

