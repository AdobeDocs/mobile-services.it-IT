---
description: Queste informazioni aiutano a gestire una richiesta di cancellazione dati in conformità ai requisiti GDPR.
solution: Experience Cloud Services,Analytics
title: Impostazione dello stato di consenso o rinuncia dell’utente
topic-fix: Developer and implementation
uuid: 44a09a25-93c6-4e1a-b69e-710018e8b6c3
exl-id: 8fd30bea-6316-46ac-9787-8ca594545d1b
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 100%

---

# Impostazione dello stato di consenso o rinuncia dell’utente {#setting-the-user-s-opt-status}

Queste informazioni aiutano a gestire una richiesta di cancellazione dati in conformità ai requisiti GDPR.

>[!IMPORTANT]
>
>A partire da Experience Cloud iOS SDK 4.15, l&#39;impostazione dello stato di privacy su `unknown` blocca gli hit di Audience Manager ed Experience Cloud ID.

Per definire se le attività di Analytics, Target e Audience Manager sono consentite su un dispositivo, usa le seguenti impostazioni:

* `privacyDefault` nel [file di configurazione ADBMobile JSON](/help/ios/configuration/json-config/json-config.md).

   Questa impostazione controlla l&#39;impostazione iniziale che viene mantenuta finché non viene modificata nel codice.

* `setPrivacyStatus`.

   Quando l&#39;impostazione della privacy viene modificata utilizzando questo metodo, la modifica diventa permanente finché non viene nuovamente cambiata con questo metodo, oppure finché non disinstalli e reinstalli l&#39;app.

   Per ulteriori informazioni sui metodi, vedi   [Metodi di Configurazione](/help/ios/configuration/json-config/json-config.md).

Di seguito sono riportate informazioni su ogni stato di privacy:

* **Consenso accordato**

   * Analytics: gli hit vengono inviati.
   * Target: le richieste Mbox vengono inviate.
   * Audience Manager: i segnali e le sincronizzazioni ID vengono inviati.
   * Valore nel file di configurazione JSON: `optedin`
   * Valore in `setPrivacyStatus`: `ADBMobilePrivacyStatusOptIn`

* **Consenso negato**

   * Analytics: gli hit vengono scartati.
   * Target: le richieste Mbox non sono consentite.
   * Audience Manager: i segnali e le sincronizzazioni ID non sono consentiti.
   * Valore nel file di configurazione JSON: `optedout`
   * Valore in `setPrivacyStatus`: `ADBMobilePrivacyStatusOptOut`

* **Sconosciuto**

   * Analytics: se **è** abilitato il tracciamento offline, gli hit vengono salvati finché lo stato di privacy non cambia in optedin (gli hit vengono inviati) o in optedout (gli hit vengono scartati).

      Se il tracciamento offline **non è** abilitato, gli hit vengono scartati finché lo stato di privacy non cambia in optedin.

   * Target: le richieste Mbox vengono inviate.
   * Audience Manager: i segnali e le sincronizzazioni ID vengono inviati.
   * Valore nel file di configurazione JSON: `optunknown`
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
