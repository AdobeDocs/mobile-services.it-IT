---
description: Note sulla versione e problemi noti per la versione 4.x dell'SDK per Android per le soluzioni Experience Cloud.
seo-description: Note sulla versione e problemi noti per la versione 4.x dell'SDK per Android per le soluzioni Experience Cloud.
seo-title: Note sulla versione
solution: Experience Cloud,Analytics
title: Note sulla versione
topic: Sviluppatore e implementazione
uuid: 16bb4de8-a216-47a8-928c-0b1e1421adcf
translation-type: ht
source-git-commit: 7fe7c78262a6d35dd27787554bb4f9ee92faa952

---


# Note sulla versione {#release-notes}

Di seguito sono riportate le note sulla versione, i problemi noti e le informazioni sulla correzione per l’SDK 4.x per Android per le soluzioni Experience Cloud:

**20 settembre 2019: versione 4.17.10**

* Generale: corretta la generazione di stringhe locali per alcune aree dell'API Android livello 21 o successivo.

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


Per ulteriori informazioni sulle note sulle versioni attuale e precedenti di tutte le soluzioni, consulta [Note sulla versione di Adobe Experience Cloud](https://marketing.adobe.com/resources/help/it_IT/whatsnew/).
