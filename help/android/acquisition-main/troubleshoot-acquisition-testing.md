---
description: This topic provides information about how to troubleshoot issues you might face during Acquisition testing.
keywords: android;libreria;mobile;sdk
seo-description: This topic provides information about how to troubleshoot issues you might face during Acquisition testing.
seo-title: Troubleshoot Acquisition testing
solution: Marketing Cloud,Analytics
title: Troubleshoot Acquisition testing
topic: Sviluppatore e implementazione
translation-type: tm+mt
source-git-commit: 97202c672d7349496f83b9ac0c365dd8b3e13eda

---


# Risoluzione dei problemi di test di acquisizione {#troubleshoot-acquisition-testing}

This topic provides information about how to troubleshoot issues you might face during Acquisition testing.

* If not otherwise specified, the ADBMobileConfig.json file should be placed in the  folder.`assets`

   The name is case sensitive, so do not use upper or lower case letters.

* Ensure that  is called from your main activity.`Config.setContext(this.getApplicationContext())`

   Per ulteriori informazioni, vedere Metodi [di](https://docs.adobe.com/content/help/en/mobile-services/android/configuration-android/methods.html)configurazione.

* Verifica che nel `AndroidManifest.xml` file siano presenti le autorizzazioni richieste per l’SDK di Mobile:

   ```html
   <manifest ..>
   ... 
   <uses-permission android:name="android.permission.INTERNET" />
   <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
   </manifest>
   ```

* Se `referrerTimeout` è impostato su 5 nel file ADMobileConfig.json, è necessario inviare l’intento di installazione in un intervallo di 5 secondi dopo che l’applicazione è stata installata e avviata per la prima volta per visualizzare le informazioni sul referente aggiunte all’hit di installazione.

   Per il test manuale, consigliamo di aumentare i tempi `referrerTimeout` a 10-15 secondi, in modo da disporre di tempo sufficiente per inviare le informazioni sul referente prima che l’hit di installazione venga elaborato.

* Eseguite tutti i passaggi in [Verifica dell’acquisizione](https://docs.adobe.com/content/help/en/mobile-services/android/acquisition-android/t-testing-marketing-link-acquisition.html) di Marketing Link e accertatevi di eseguire prima il `adb shell` comando e quindi quanto segue:

   ```java
   am broadcast -a com.android.vending.INSTALL_REFERRER -n nl.postnl.app/.tracking.AdobeAcquisitionLinkBroadcastReceiver --es "referrer" "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<the newly generated id at step #7>"
   ```

>[!IMPORTANT]
>
>Per elaborare correttamente l'intento del referente, è necessario eseguire questi due comandi in modo indipendente. In caso contrario, `adb` l'escape raddoppia le informazioni del referente e i dati ricevuti dal destinatario della trasmissione risulteranno incompleti.

