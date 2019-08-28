---
description: Note sulla versione e problemi noti per la versione 4.x dell'SDK per Android per le soluzioni Experience Cloud.
seo-description: Note sulla versione e problemi noti per la versione 4.x dell'SDK per Android per le soluzioni Experience Cloud.
seo-title: Note sulla versione
solution: Marketing Cloud,Analytics
title: Note sulla versione
topic: Sviluppatore e implementazione
uuid: 16 bb 4 de 8-a 216-47 a 8-928 c -0 b 1 e 1421 adcf
translation-type: tm+mt
source-git-commit: 4c68e3fb3687a555fc7fdfa50a42e837b76a7d88

---


# Note sulla versione {#release-notes}

Di seguito sono riportate le note sulla versione, i problemi noti e le informazioni di correzione per l'SDK 4. x Android per Soluzioni Experience Cloud:

**2 agosto 2019: Versione 4.17.9**

* Servizio ID visitatori: Correzione della `StrictMode` violazione durante la chiamata di syncidentifiers.

   Questa violazione è stata causata dalle preferenze condivise di lettura sul thread principale.

* Adobe Target: È stato aggiunto l' `requestLocationParameters` attributo in `TargetRequestObject`, che consente l'invio di impressionid con le richieste Target.

**18 luglio 2019: Versione 4.17.8**

* Adobe Target: Tutte le richieste ora includono il client e sessionid nei parametri di query URL.
* Messaggistica in-app: è stato corretto un problema a causa del quale, quando un messaggio veniva attivato con un URL clickthrough vuoto, si verificava un arresto anomalo delle app Android.
* Servizio Visitor ID: le API `Visitor.appendToURL` e `Visitor.getUrlVariablesAsync` non applicano più la doppia codifica ai valori restituiti.

   A causa della doppia codifica, i valori restituiti da tali API venivano segnalati da parte di alcuni servizi di sicurezza.

**6 giugno 2019: Versione 4.17.7**

* Generale: le chiamate di rete sui livelli delle API Android inferiori a 20 utilizzeranno ora TLS 1.1 o TLS 1.2.
* Analytics: è stato aggiunto lo stato di consenso push ai dati del ciclo di vita quando sono attivate le notifiche push.

**24 maggio 2019: Versione 4.17.6**

* servizio ID visitatori - Il
   `setPushIdentifier` La chiamata API invia una chiamata di sincronizzazione al servizio ID visitatore ogni volta che viene chiamata.

* Servizio ID visitatori: è stato aumentato il timeout di connessione e di lettura
da 2 a 5 secondi.


Per ulteriori informazioni sulle note sulle versioni attuale e precedenti di tutte le soluzioni, vedi [Note sulla versione di Adobe Experience Cloud](https://marketing.adobe.com/resources/help/en_US/whatsnew/).
