---
description: Le seguenti informazioni sono utili per risolvere eventuali problemi di test di acquisizione.
keywords: android;Acquisizione;test
seo-description: Le seguenti informazioni sono utili per risolvere eventuali problemi di test di acquisizione.
seo-title: Risoluzione dei problemi di test di acquisizione
solution: Marketing Cloud, Analytics
title: Risoluzione dei problemi di test di acquisizione
translation-type: tm+mt
source-git-commit: 1c387b063eedb41a52e044dc824df6a51f173ad2

---


# Risoluzione dei problemi di test di acquisizione {#aquistion-testing-troubleshooting}

Di seguito sono riportati alcuni problemi che potresti incontrare durante il test di Acquisizione e alcune possibili soluzioni:

* Se non viene specificato diversamente, il file ADBMobileConfig.json deve trovarsi nella cartella assets.

* Poiché il nome fa distinzione tra maiuscole e minuscole, non specificate un nome in lettere minuscole.

   È necessario assicurarsi che `Config.setContext(this.getApplicationContext())` venga chiamato dall'attività principale. Per ulteriori informazioni, vedere Metodi [di](https://docs.adobe.com/content/help/en/mobile-services/android/configuration-android/methods.html)configurazione.

* Mancano alcune autorizzazioni utente nel file AndroidManifest.xml fornito, necessarie per inviare dati e registrare le chiamate di tracciamento offline:

   ```html
   <manifest..>
   ... 
   <uses-permission android:name="android.permission.INTERNET" />
   <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
   </manifest>
   ```

* Nella configurazione, se il timeout del referente è impostato su `referrerTimeout: 5`, significa che devi inviare l’intento di installazione in un intervallo di 5 secondi dopo che l’applicazione è stata installata e avviata per la prima volta per visualizzare le informazioni sul referente aggiunte all’hit di installazione.

   Per il test manuale, aumentate i `referrerTimeout` valori a 10-15 secondi, in modo da disporre di tempo sufficiente per inviare le informazioni sul referente prima che l’hit di installazione venga elaborato.

* È importante eseguire tutti i passaggi in [Verifica dell’acquisizione](https://docs.adobe.com/content/help/en/mobile-services/android/acquisition-android/t-testing-marketing-link-acquisition.html) di Marketing Link per essere certi di eseguire la `adb` shell e quindi quanto segue:

   ```java
   am broadcast -a com.android.vending.INSTALL_REFERRER -n 
   nl.postnl.app/.tracking.AdobeAcquisitionLinkBroadcastReceiver --es "referrer"
   "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<the newly generated id at step #7>"
   ```

>[!IMPORTANT]
>
>È necessario eseguire questi due comandi in modo indipendente per elaborare correttamente l'intento del referente.  In caso contrario, `adb` la doppia escape delle informazioni del referente, e i dati ricevuti dal destinatario della trasmissione saranno incompleti.
