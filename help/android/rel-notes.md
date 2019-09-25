---
description: Note sulla versione e problemi noti per la versione 4.x dell'SDK per Android per le soluzioni Experience Cloud.
seo-description: Note sulla versione e problemi noti per la versione 4.x dell'SDK per Android per le soluzioni Experience Cloud.
seo-title: Note sulla versione
solution: Marketing Cloud,Analytics
title: Note sulla versione
topic: Sviluppatore e implementazione
uuid: 16bb4de8-a216-47a8-928c-0b1e1421adcf
translation-type: tm+mt
source-git-commit: 7fe7c78262a6d35dd27787554bb4f9ee92faa952

---


# Note sulla versione {#release-notes}

Here is the release notes, known issues, and hot fix information for Android SDK 4.x for Experience Cloud Solutions:

**September 20, 2019: Version 4.17.10**

* General: Fixed locale string generation for some regions on Android API level 21 or newer.

**18 luglio 2019: Versione 4.17.8**

* Adobe Target: Tutte le richieste ora includono client e sessionId nei parametri di query URL.
* Messaggistica in-app: è stato corretto un problema a causa del quale, quando un messaggio veniva attivato con un URL clickthrough vuoto, si verificava un arresto anomalo delle app Android.
* Servizio Visitor ID: le API `Visitor.appendToURL` e `Visitor.getUrlVariablesAsync` non applicano più la doppia codifica ai valori restituiti.

   A causa della doppia codifica, i valori restituiti da tali API venivano segnalati da parte di alcuni servizi di sicurezza.

**6 giugno 2019: Versione 4.17.7**

* Generale - Le chiamate di rete su livelli API Android inferiori a 20 ora utilizzano TLS 1.1 o TLS 1.2.
* Analytics - Stato di consenso push aggiunto ai dati del ciclo di vita quando le notifiche push sono abilitate.

**24 maggio 2019: Versione 4.17.6**

* servizio ID visitatore - Il
   `setPushIdentifier` La chiamata API ora invia una chiamata asincrona al servizio ID visitatori ogni volta che viene chiamata.

* Servizio ID visitatori - Sono stati aumentati i tempi di connessione e di lettura da 2 a 5 secondi.


Per ulteriori informazioni sulle note sulle versioni attuale e precedenti di tutte le soluzioni, vedi [Note sulla versione di Adobe Experience Cloud](https://marketing.adobe.com/resources/help/en_US/whatsnew/).
