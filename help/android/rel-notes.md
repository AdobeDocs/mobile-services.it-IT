---
description: Note sulla versione e problemi noti per gli SDK 4.x per Android per le soluzioni Experience Cloud.
seo-description: Note sulla versione e problemi noti per gli SDK 4.x per Android per le soluzioni Experience Cloud.
seo-title: Note sulla versione
solution: Experience Cloud,Analytics
title: Note sulla versione
topic: Developer and implementation
uuid: 16bb4de8-a216-47a8-928c-0b1e1421adcf
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '297'
ht-degree: 100%

---


# Note sulla versione {#release-notes}

Di seguito sono riportate le note sulla versione, i problemi noti e le informazioni sulla correzione per l’SDK 4.x per Android per le soluzioni Experience Cloud:

**3 aprile 2020: 4.18.2**

* Messaggi in-app: per motivi di sicurezza, WebViews creato dall’SDK ora imposta la proprietà “setAllowFileAccess” su false.

**12 marzo 2020: 4.18.1**

* Target: l’ID della sessione di Target verrà ora aggiunto come parametro dei dati contestuali “a.target.sessionId” nel risultato interno di Analytics - for Target inviato ad Adobe Analytics.

**16 gennaio 2020: 4.18.0**

* Acquisizione - Aggiunta una nuova API, `Analytics.processGooglePlayInstallReferrerUrl(final String url)`, per supportare l’installazione delle API Google Play Referrer.

   Per ulteriori informazioni sull’Installazione delle API di riferimento, consulta [Stai ancora usando InstallBroadcast? Passa all’API Play Referrer entro il 1 marzo 2020](https://android-developers.googleblog.com/2019/11/still-using-installbroadcast-switch-to.html).

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
