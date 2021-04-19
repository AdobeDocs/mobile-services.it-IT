---
description: In questo argomento vengono fornite informazioni su come risolvere eventuali problemi che potrebbero verificarsi durante il test di acquisizione.
keywords: android,libreria,mobile,sdk
seo-description: In questo argomento vengono fornite informazioni su come risolvere eventuali problemi che potrebbero verificarsi durante il test di acquisizione.
seo-title: Risoluzione dei problemi del test di acquisizione
solution: Experience Cloud,Analytics
title: Risoluzione dei problemi del test di acquisizione
topic-fix: Developer and implementation
exl-id: 1ed2ad89-4e89-43da-aa21-f688b4d1c0d1
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 100%

---

# Risoluzione dei problemi del test di acquisizione {#troubleshoot-acquisition-testing}

In questo argomento vengono fornite informazioni su come risolvere eventuali problemi che potrebbero verificarsi durante il test di acquisizione.

* Se non viene specificato diversamente, il file ADBMobileConfig.json deve trovarsi nella cartella `assets`.

   Poiché il nome distingue tra maiuscole e minuscole, non utilizzare lettere maiuscole e minuscole.

* Accertati che `Config.setContext(this.getApplicationContext())` venga chiamato dall&#39;attività principale.

   Per ulteriori informazioni, consulta [Metodi di configurazione](https://docs.adobe.com/content/help/it-IT/mobile-services/android/configuration-android/methods.html).

* Verifica che nel file `AndroidManifest.xml` siano presenti le autorizzazioni richieste per l&#39;SDK di Mobile:

   ```html
   <manifest ..>
   ... 
   <uses-permission android:name="android.permission.INTERNET" />
   <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
   </manifest>
   ```

* Se `referrerTimeout` è impostato su 5 nel file ADMobileConfig.json, devi inviare l&#39;intento di installazione in un arco temporale di 5 secondi dopo la prima installazione e il primo avvio dell&#39;applicazione per visualizzare le informazioni sul referente aggiunte all&#39;hit di installazione.

   Per il test manuale, consigliamo di aumentare il `referrerTimeout` a 10-15 secondi, in modo da disporre di tempo sufficiente per inviare le informazioni sul referente prima che l&#39;hit di installazione venga elaborato.

* Esegui tutti i passaggi in [Verifica dell’acquisizione di Marketing Link](https://docs.adobe.com/content/help/it-IT/mobile-services/android/acquisition-android/t-testing-marketing-link-acquisition.html) e accertati di eseguire prima il comando `adb shell` e quindi quanto segue:

   ```java
   am broadcast -a com.android.vending.INSTALL_REFERRER -n nl.postnl.app/.tracking.AdobeAcquisitionLinkBroadcastReceiver --es "referrer" "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<the newly generated id at step #7>"
   ```

>[!IMPORTANT]
>
>Per elaborare correttamente l&#39;intento del referente, è necessario eseguire questi due comandi in modo indipendente. In caso contrario, il `adb` sottrarrà due volte le informazioni del referente e i dati ricevuti dal destinatario della trasmissione risulteranno incompleti.
