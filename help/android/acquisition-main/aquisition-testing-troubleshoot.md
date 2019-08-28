---
description: Le seguenti informazioni sono utili per risolvere i problemi di verifica acquisizione.
keywords: android; Acquisizione; test
seo-description: Le seguenti informazioni sono utili per risolvere i problemi di verifica acquisizione.
seo-title: Risoluzione dei problemi di test acquisizione
solution: Marketing Cloud, Analytics
title: Risoluzione dei problemi di test acquisizione
translation-type: tm+mt
source-git-commit: da8798d7ee1f05dcade31cced5404d78c9cf360a

---


# Risoluzione dei problemi di test acquisizione {#aquistion-testing-troubleshooting}

Di seguito sono riportati alcuni problemi che potresti affrontare durante il test Acquisizione e alcune soluzioni possibili:

* Se non viene specificato in modo alternativo, il file adbmobileconfig. json deve trovarsi nella cartella assets.

* Il nome fa distinzione tra maiuscole e minuscole e non fornisce un nome nelle lettere minuscole.

   Dovete accertarvi che `Config.setContext(this.getApplicationContext())` venga richiamata dall'attività principale. Per ulteriori informazioni, consultate [Metodi di configurazione](https://docs.adobe.com/content/help/en/mobile-services/android/configuration-android/methods.html).

* Mancano alcune autorizzazioni utente nel file AndroidManifest.xml fornito, questi sono necessari per inviare dati e registrare chiamate di tracciamento offline:

   ```html
   <manifest..>
   ... 
   <uses-permission android:name="android.permission.INTERNET" />
   <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
   </manifest>
   ```

* Nella configurazione, se il timeout referente è impostato su `referrerTimeout: 5`, significa che devi inviare l'intento di installazione entro un intervallo temporale di 5 secondi dopo che l'applicazione è stata installata e avviata per la prima volta in modo da visualizzare le informazioni di riferimento aggiunte all'hit di installazione.

   Per un test manuale, aumentate `referrerTimeout` i tempi di 10-15 secondi, in modo che vi sia tempo sufficiente per inviare le informazioni di riferimento prima dell'elaborazione dell'hit di installazione.

* È importante eseguire tutti i passaggi nel [test Acquisizione collegamento marketing](https://docs.adobe.com/content/help/en/mobile-services/android/acquisition-android/t-testing-marketing-link-acquisition.html) nell'ordine e assicurarsi di eseguire `adb` shell e quindi:

   ```java
   am broadcast -a com.android.vending.INSTALL_REFERRER -n 
   nl.postnl.app/.tracking.AdobeAcquisitionLinkBroadcastReceiver --es "referrer"
   "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<the newly generated id at step #7>"
   ```

>[!IMPORTANT]
>
>È necessario eseguire questi due comandi indipendentemente per elaborare correttamente l'intento del referente. In caso contrario `adb` , duplica le informazioni relative al referente e i dati ricevuti dal destinatario della trasmissione non saranno completi.
