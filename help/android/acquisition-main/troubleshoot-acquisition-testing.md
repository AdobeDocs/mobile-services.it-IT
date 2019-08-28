---
description: Questo argomento fornisce informazioni su come risolvere eventuali problemi riscontrati durante il test di acquisizione.
keywords: android; libreria; mobile; sdk
seo-description: Questo argomento fornisce informazioni su come risolvere eventuali problemi riscontrati durante il test di acquisizione.
seo-title: Risoluzione dei problemi di test acquisizione
solution: Marketing Cloud, Analytics
title: Risoluzione dei problemi di test acquisizione
topic: Sviluppatore e implementazione
translation-type: tm+mt
source-git-commit: 97202c672d7349496f83b9ac0c365dd8b3e13eda

---


# Risoluzione dei problemi di test acquisizione {#troubleshoot-acquisition-testing}

Questo argomento fornisce informazioni su come risolvere eventuali problemi riscontrati durante il test di acquisizione.

* Se non diversamente specificato, il file adbmobileconfig. json deve trovarsi nella `assets` cartella.

   Il nome fa distinzione tra maiuscole e minuscole e non utilizza lettere maiuscole o minuscole.

* Accertati che `Config.setContext(this.getApplicationContext())` venga richiamata dalla tua attività principale.

   Per ulteriori informazioni, consultate [Metodi di configurazione](https://docs.adobe.com/content/help/en/mobile-services/android/configuration-android/methods.html).

* Assicurati che nel `AndroidManifest.xml` file siano presenti le autorizzazioni necessarie per l'SDK di Mobile:

   ```html
   <manifest ..>
   ... 
   <uses-permission android:name="android.permission.INTERNET" />
   <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
   </manifest>
   ```

* Se il `referrerTimeout` valore è 5 nel file admobileconfig. json, devi inviare l'intento di installazione in un intervallo temporale di 5 secondi dopo che l'applicazione è stata installata e avviata per la prima volta in modo da visualizzare le informazioni di riferimento aggiunte all'hit di installazione.

   Per eseguire il test manuale, si consiglia di aumentare `referrerTimeout` a 10-15 secondi, in modo che sia sufficiente inviare le informazioni di riferimento prima dell'elaborazione dell'hit di installazione.

* Eseguite tutti i passaggi nel [test Acquisizione collegamento marketing](https://docs.adobe.com/content/help/en/mobile-services/android/acquisition-android/t-testing-marketing-link-acquisition.html) e assicuratevi di eseguire prima il `adb shell` comando e quindi quanto segue:

   ```java
   am broadcast -a com.android.vending.INSTALL_REFERRER -n nl.postnl.app/.tracking.AdobeAcquisitionLinkBroadcastReceiver --es "referrer" "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<the newly generated id at step #7>"
   ```

>[!IMPORTANT]
>
>Per elaborare correttamente l'intento referente, è necessario eseguire questi due comandi in modo indipendente. In caso contrario `adb` , scorrete due volte le informazioni sul referente e i dati ricevuti dal destinatario della trasmissione non saranno completi.

