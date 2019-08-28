---
description: Note sulla versione e problemi noti per le versioni 4.x degli SDK per iOS per le soluzioni Experience Cloud.
seo-description: Note sulla versione e problemi noti per le versioni 4.x degli SDK per iOS per le soluzioni Experience Cloud.
seo-title: Note sulla versione
solution: Marketing Cloud,Analytics
title: Note sulla versione
topic: Sviluppatore e implementazione
uuid: e 1613 dc 5-02 a 4-43 a 7-997 a -29 b 4 de 98 b 4 d 1
translation-type: tm+mt
source-git-commit: 80a60276f9926177c8958b8e87e9393a83e7e6a9

---


# Note sulla versione {#release-notes}

Di seguito sono riportate le note sulla versione, i problemi noti e le informazioni sulla correzione per iOS SDK 4. x per soluzioni Experience Cloud:

**2 agosto 2019: Versione 4.18.7**

* Modificata una modifica introdotta nella versione 4.18.6 che, in alcuni ambienti, causava un arresto anomalo sui dispositivi che eseguivano una versione iOS precedente alla 11.0.

* Adobe Target: Aggiunta la `requestLocationParameters` proprietà in `ADBTargetRequestObject`, che consente l'invio di impressionid con le richieste Target.

**18 luglio 2019: Versione 4.18.6**

* Adobe Target: tutte le richieste ora includono il client e il valore `sessionId` nei parametri di query URL.
* Adobe Target: è stato risolto un problema di perdita di memoria.
* Servizio Visitor ID: le API `visitorAppendToURL` e `visitorGetUrlVariablesAsync` non applicano più la doppia codifica ai valori restituiti.

   A causa della doppia codifica, i valori restituiti da tali API venivano segnalati da parte di alcuni servizi di sicurezza.

**5 giugno 2019: Versione 4.18.5**

* Analytics - Aggiungi lo stato di consenso push ai dati del ciclo di vita quando sono attivate le notifiche push.

**24 maggio 2019: Versione 4.18.4**

* Servizio ID visitatore: è stato aumentato il timeout restituito per il
   `visitorGetUrlVariablesAsync` API a 30 secondi.

* Servizio ID visitatore - La chiamata `setPushIdentifier` API invia ora una chiamata di sincronizzazione al servizio ID visitatore ogni volta che viene chiamato.

Per ulteriori informazioni sulle note sulle versioni attuale e precedenti di tutte le soluzioni, vedi [Note sulla versione di Adobe Experience Cloud](https://marketing.adobe.com/resources/help/en_US/whatsnew/).
