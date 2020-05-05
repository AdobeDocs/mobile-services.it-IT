---
description: Note sulla versione e problemi noti per l’SDK 4.x Android per le soluzioni Experience Cloud.
seo-description: Note sulla versione e problemi noti per l’SDK 4.x Android per le soluzioni Experience Cloud.
seo-title: Note sulla versione
solution: Marketing Cloud,Analytics
title: Note sulla versione
topic: Developer and implementation
uuid: 16bb4de8-a216-47a8-928c-0b1e1421adcf
translation-type: tm+mt
source-git-commit: 82b3dc38a0325b3aa733b491ddad9b59dbe84eaa

---


# Note sulla versione {#release-notes}

Di seguito sono riportate le note sulla versione, i problemi noti e le informazioni sulla correzione per l’SDK 4.x per Android per le soluzioni Experience Cloud:

**16 gennaio 2020: 4.18.0**

* Acquisizione - Aggiunta una nuova API, `Analytics.processGooglePlayInstallReferrerUrl(final String url)`, per supportare l’installazione delle API Google Play Referrer.

   Per ulteriori informazioni sull’Installazione delle API di riferimento, consulta [Stai ancora usando InstallBroadcast? Passa all’API Play Referrer entro il 1 marzo 2020](https://android-developers.googleblog.com/2019/11/still-using-installbroadcast-switch-to.html) .

**20 settembre 2019: versione 4.17.10**

* Generale: corretta la generazione di stringhe locali per alcune aree dell&#39;API Android livello 21 o successivo.

**18 luglio 2019: versione 4.17.8**

* Adobe Target: tutte le richieste ora includono il client e il sessionId nei parametri di query URL.
* Messaggistica in-app: è stato corretto un problema a causa del quale, quando un messaggio veniva attivato con un URL clickthrough vuoto, si verificava un arresto anomalo delle app Android.
* Servizio Visitor ID: le API `Visitor.appendToURL` e `Visitor.getUrlVariablesAsync` non applicano più la doppia codifica ai valori restituiti.

   A causa della doppia codifica, i valori restituiti da tali API venivano segnalati da parte di alcuni servizi di sicurezza.

**6 giugno 2019: versione 4.17.7**

* Generale: le chiamate di rete su livelli API Android inferiori a 20 ora utilizzano TLS 1.1 o TLS 1.2.
* Analytics: aggiunto lo stato di consenso push ai dati del ciclo di vita quando le notifiche push sono abilitate.

**24 maggio 2019: versione 4.17.6**

* Servizio ID visitatore: la
   chiamata API `setPushIdentifier` invia ora una chiamata sincrona al servizio ID visitatore ogni volta che viene chiamata.

* Servizio ID visitatore: sono stati aumentati i tempi di connessione e di lettura da 2 a 5 secondi.


Per ulteriori informazioni sulle note sulle versioni attuale e precedenti di tutte le soluzioni, consulta [Note sulla versione di Adobe Experience Cloud](hhttps://docs.adobe.com/content/help/en/release-notes/experience-cloud/current.html).
