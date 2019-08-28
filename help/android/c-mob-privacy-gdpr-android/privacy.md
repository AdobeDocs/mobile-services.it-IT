---
description: Queste informazioni aiutano a gestire una richiesta di cancellazione dati in conformità ai requisiti RGPD.
seo-description: Queste informazioni aiutano a gestire una richiesta di cancellazione dati in conformità ai requisiti RGPD.
seo-title: Impostazione dello stato di consenso dell'utente
solution: Marketing Cloud, Analytics
title: Impostazione dello stato di consenso dell'utente
topic: Sviluppatore e implementazione
uuid: f 8 a 3 e 6 be -44 dd -494 e -9 cda-dbbac 86 d 6772
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Setting the user's opt status{#setting-the-user-s-opt-status}

Queste informazioni aiutano a gestire una richiesta di cancellazione dati in conformità ai requisiti RGPD.

>[!IMPORTANT]
>
>Starting with Android SDK 4.15 , setting the privacy status to `unknown` holds Audience Manager and Experience Cloud ID hits.

Puoi verificare se l'attività di Analytics, Target e Audience Manager è consentita su un dispositivo utilizzando le seguenti impostazioni:

* `privacyDefault` nel [file di configurazione adbmobile JSON](/help/android/configuration/json-config/json-config.md).

   Questa impostazione controlla l'impostazione iniziale che persiste finché non viene modificata nel codice.

* Il `Config.setPrivacyStatus` metodo.

   Dopo che l'impostazione della privacy è stata modificata utilizzando questo metodo, la modifica resta in vigore finché non la cambi nuovamente oppure finché non disinstalli e reinstalli l'app. Per ulteriori informazioni sui metodi, vedi [Metodi di Configurazione](/help/android/configuration/methods.md).

La seguente tabella descrive ogni stato di privacy:

* **Consenso accordato**

   * **Analytics**: gli hit vengono inviati.
   * **Target**: le richieste Mbox vengono inviate.
   * **Audience Manager**: i segnali e le sincronizzazioni ID vengono inviati.
   * Value in the JSON Config file: `optedin`
   * Valore in `setPrivacyStatus`: `MOBILE_PRIVACY_STATUS_OPT_IN`

* **Consenso negato**

   * **Analytics**: gli hit vengono scartati.
   * **Target**: le richieste Mbox non sono consentite.
   * **Audience Manager**: i segnali e le sincronizzazioni ID non sono consentiti.
   * Value in the JSON config file: `optedout`
   * Valore in `setPrivacyStatus`: `MOBILE_PRIVACY_STATUS_OPT_OUT`

* **Sconosciuto**

   * **Analytics**: Se il tracciamento offline **è abilitato**, gli hit vengono salvati finché lo stato di privacy non cambia quando l'utente acconsente (optedin, gli hit vengono inviati) o rinuncia (gli hit vengono eliminati).

      Se il tracciamento offline <b>non è</b> abilitato, gli hit vengono scartati finché lo stato di privacy non cambia in optedin.
   * **Target**: le richieste Mbox vengono inviate.
   * **Audience Manager**: i segnali e le sincronizzazioni ID vengono inviati.
   * Value in the JSON config file: `optunknown`
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

