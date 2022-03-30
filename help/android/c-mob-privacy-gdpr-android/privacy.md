---
description: Queste informazioni aiutano a gestire una richiesta di cancellazione dati in conformità ai requisiti GDPR.
solution: Experience Cloud Services,Analytics
title: Impostazione dello stato di consenso o rinuncia dell’utente
topic-fix: Developer and implementation
uuid: f8a3e6be-44dd-494e-9cda-dbbac86d6772
exl-id: ef5160ac-5a73-4433-b217-1bd990f8456b
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 100%

---

# Impostazione dello stato di consenso o rinuncia dell’utente{#setting-the-user-s-opt-status}

Queste informazioni aiutano a gestire una richiesta di cancellazione dati in conformità ai requisiti GDPR.

>[!IMPORTANT]
>
>A partire da Android SDK 4.15, l&#39;impostazione dello stato di privacy su `unknown` blocca gli hit di Audience Manager ed Experience Cloud ID.

Puoi verificare se l&#39;attività di Analytics, Target e Audience Manager è consentita su un dispositivo utilizzando le seguenti impostazioni:

* `privacyDefault` nel [file di configurazione ADBMobile JSON](/help/android/configuration/json-config/json-config.md).

   Questa impostazione controlla l&#39;impostazione iniziale che persiste finché non viene modificata nel codice.

* Il metodo `Config.setPrivacyStatus`.

   Dopo che l&#39;impostazione della privacy è stata modificata utilizzando questo metodo, la modifica resta in vigore finché non la cambi nuovamente oppure finché non disinstalli e reinstalli l&#39;app. Per ulteriori informazioni sui metodi, vedi   [Metodi di Configurazione](/help/android/configuration/methods.md).

La seguente tabella descrive ogni stato di privacy:

* **Consenso accordato**

   * **Analytics**: gli hit vengono inviati.
   * **Target**: le richieste Mbox vengono inviate.
   * **Audience Manager**: i segnali e le sincronizzazioni ID vengono inviati.
   * Valore nel file di configurazione JSON: `optedin`
   * Valore in `setPrivacyStatus`: `MOBILE_PRIVACY_STATUS_OPT_IN`

* **Consenso negato**

   * **Analytics**: gli hit vengono scartati.
   * **Target**: le richieste Mbox non sono consentite.
   * **Audience Manager**: i segnali e le sincronizzazioni ID non sono consentiti.
   * Valore nel file di configurazione JSON: `optedout`
   * Valore in `setPrivacyStatus`: `MOBILE_PRIVACY_STATUS_OPT_OUT`

* **Sconosciuto**

   * **Analytics**: se è **abilitato** il tracciamento offline, gli hit vengono salvati finché lo stato di privacy non cambia quando l’utente acconsente (optedin, gli hit vengono inviati) o rinuncia (optedout, gli hit vengono eliminati).

      Se il tracciamento offline <b>non è</b> abilitato, gli hit vengono scartati finché lo stato di privacy non cambia in optedin.
   * **Target**: le richieste Mbox vengono inviate.
   * **Audience Manager**: i segnali e le sincronizzazioni ID vengono inviati.
   * Valore nel file di configurazione JSON: `optunknown`
   * Valore in `setPrivacyStatus`: `MOBILE_PRIVACY_STATUS_UNKNOWN`

## Esempi {#section_128AC455EE024193B5D4E5A565B53D00}

```java
public void setOptIn(View view) { 
  Config.setPrivacyStatus(MobilePrivacyStatus.MOBILE_PRIVACY_STATUS_OPT_IN); 
 currentStatus = Config.getPrivacyStatus(); 
} 
public void setOptOut(View view) { 
 Config.setPrivacyStatus(MobilePrivacyStatus.MOBILE_PRIVACY_STATUS_OPT_OUT); 
 currentStatus = Config.getPrivacyStatus(); 
} 
public void setOptUnknown(View view) { 
  Config.setPrivacyStatus(MobilePrivacyStatus.MOBILE_PRIVACY_STATUS_UNKNOWN); 
 currentStatus = Config.getPrivacyStatus(); 
}
```
