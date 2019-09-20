---
description: Note sulla versione e problemi noti per le versioni 4.x degli SDK per iOS per le soluzioni Experience Cloud.
seo-description: Note sulla versione e problemi noti per le versioni 4.x degli SDK per iOS per le soluzioni Experience Cloud.
seo-title: Note sulla versione
solution: Marketing Cloud,Analytics
title: Note sulla versione
topic: Sviluppatore e implementazione
uuid: e1613dc5-02a4-43a7-997a-29b4de98b4d1
translation-type: tm+mt
source-git-commit: 7fe7c78262a6d35dd27787554bb4f9ee92faa952

---


# Note sulla versione {#release-notes}

Note sulla versione, problemi noti e informazioni sulla correzione per gli SDK 4.x per iOS per le soluzioni Experience Cloud:

**20 settembre 2019: Versione 4.18.8**

* Messaggi in-app:

   * Sui dispositivi con iOS 10 o versione successiva, il `UserNotifications` framework ora viene utilizzato per pianificare le notifiche locali per le app collegate al `UserNotifications.framework`.
   * I messaggi a schermo intero ora utilizzano WKWebViews da `WebKit.framework`, che deve essere collegato nel progetto Xcode.
   * È stato corretto un bug a causa del quale il payload di click-through push non poteva essere utilizzato come caratteristiche per i messaggi in-app.
   * È stato risolto un problema di arresto anomalo.

* Generale - È stato corretto un bug a causa del quale i dati SDK venivano sincronizzati con l'app watchOS associata a ogni chiamata di Analytics.

**2 agosto 2019: Versione 4.18.7**

* È stata ripristinata una modifica introdotta nella versione 4.18.6 che, in alcuni ambienti, causava un arresto anomalo sui dispositivi con una versione iOS precedente alla 11.0.

* Adobe Target: Aggiunta la `requestLocationParameters` proprietà in `ADBTargetRequestObject`, che consente l'invio di impressionId con le richieste Target.

**18 luglio 2019: Versione 4.18.6**

* Adobe Target: tutte le richieste ora includono il client e il valore `sessionId` nei parametri di query URL.
* Adobe Target: è stato risolto un problema di perdita di memoria.
* Servizio Visitor ID: le API `visitorAppendToURL` e `visitorGetUrlVariablesAsync` non applicano più la doppia codifica ai valori restituiti.

   A causa della doppia codifica, i valori restituiti da tali API venivano segnalati da parte di alcuni servizi di sicurezza.

**5 giugno 2019: Versione 4.18.5**

* Analytics - Aggiungi lo stato di consenso push ai dati del ciclo di vita quando le notifiche push sono abilitate.

**24 maggio 2019: Versione 4.18.4**

* Servizio ID visitatori - È stato aumentato il timeout di ritorno per il
   `visitorGetUrlVariablesAsync` API a 30 secondi.

* Servizio ID visitatore - La chiamata `setPushIdentifier` API ora invia una chiamata di sincronizzazione al servizio ID visitatore ogni volta che viene chiamata.

Per ulteriori informazioni sulle note sulle versioni attuale e precedenti di tutte le soluzioni, vedi [Note sulla versione di Adobe Experience Cloud](https://marketing.adobe.com/resources/help/en_US/whatsnew/).
