---
description: Le seguenti informazioni sono utili per risolvere eventuali problemi di test di acquisizione.
keywords: android;Acquisition;testing
seo-description: Le seguenti informazioni sono utili per risolvere eventuali problemi di test di acquisizione.
seo-title: Risoluzione dei problemi dei test di acquisizione
solution: Experience Cloud,Analytics
title: Risoluzione dei problemi dei test di acquisizione
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 100%

---


# Risoluzione dei problemi dei test di acquisizione {#aquistion-testing-troubleshooting}

Di seguito sono riportati alcuni problemi che potresti riscontrare durante il test di acquisizione e alcune possibili soluzioni:

* Se non viene specificato diversamente, il file ADBMobileConfig.json deve trovarsi nella cartella delle risorse.

* Poiché il nome fa distinzione tra maiuscole e minuscole, non utilizzare un nome con lettere minuscole.

   È necessario assicurarsi che `Config.setContext(this.getApplicationContext())` venga chiamato dall&#39;attività principale. Per ulteriori informazioni, consulta [Metodi di configurazione](https://docs.adobe.com/content/help/it-IT/mobile-services/android/configuration-android/methods.html).

* Mancano alcune autorizzazioni utente nel file AndroidManifest.xml fornito, necessarie per inviare dati e registrare le chiamate di tracciamento offline:

   ```html
   <manifest..>
   ... 
   <uses-permission android:name="android.permission.INTERNET" />
   <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
   </manifest>
   ```

* Nella configurazione, se il timeout del referente è impostato su `referrerTimeout: 5`, significa che devi inviare l&#39;intento di installazione in un arco temporale di 5 secondi dopo che l&#39;applicazione è stata installata e avviata per la prima volta per visualizzare le informazioni sul referente aggiunte all&#39;hit di installazione.

   Per il test manuale, aumenta il `referrerTimeout` a 10-15 secondi, in modo da disporre di tempo sufficiente per inviare le informazioni sul referente prima che l&#39;hit di installazione venga elaborato.

* È importante eseguire tutti i passaggi in [Verifica dell&#39;acquisizione da collegamenti marketing](https://docs.adobe.com/content/help/it-IT/mobile-services/android/acquisition-android/t-testing-marketing-link-acquisition.html) per assicurarti di eseguire la `adb` shell e quindi quanto segue:

   ```java
   am broadcast -a com.android.vending.INSTALL_REFERRER -n 
   nl.postnl.app/.tracking.AdobeAcquisitionLinkBroadcastReceiver --es "referrer"
   "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<the newly generated id at step #7>"
   ```

>[!IMPORTANT]
>
>È necessario eseguire questi due comandi in modo indipendente per elaborare correttamente l&#39;intento del referente.  In caso contrario, `adb` sottrarrà due volte le informazioni del referente e i dati ricevuti dal destinatario della trasmissione risulteranno incompleti.
