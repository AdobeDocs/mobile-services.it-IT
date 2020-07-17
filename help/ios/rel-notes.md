---
description: Note sulla versione e problemi noti per gli SDK 4.x iOS per le soluzioni Experience Cloud.
seo-description: Note sulla versione e problemi noti per gli SDK 4.x iOS per le soluzioni Experience Cloud.
seo-title: Note sulla versione
solution: Marketing Cloud,Analytics
title: Note sulla versione
topic: Developer and implementation
uuid: e1613dc5-02a4-43a7-997a-29b4de98b4d1
translation-type: tm+mt
source-git-commit: 48c3addeb929f3356990ef55b44f93dd4bb2f728
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 95%

---


# Note sulla versione {#release-notes}

Di seguito sono riportate le note sulla versione, i problemi noti e le informazioni sulle correzioni rapide per gli SDK iOS 4.x per le soluzioni Experience Cloud:

**16 luglio 2020: Versione 4.19.3**

* Generale - È stato corretto un bug che impediva la gestione corretta degli URL di collegamento profondo con più parametri di accesso uguali nel param di query.

**24 marzo 2020: versione 4.19.2**

* Generale: sono stati corretti alcuni problemi nel codice di Target.

**12 marzo 2020: versione 4.19.1**

* Generale: è stato risolto un potenziale arresto anomalo provocato dall’inclusione degli enum di Swift nei dati contestuali per il tracciamento delle chiamate.
* Target: l’ID della sessione di Target verrà ora aggiunto come parametro dei dati contestuali “a.target.sessionId” nel risultato interno di Analytics for Target inviato ad Adobe Analytics.

**4 febbraio 2020: versione 4.19.0**

* Ciclo di vita: è stata aggiunta la nuova API pauseCollectingLifecycleData per attenuare il problema relativo ai dati anormali della lunghezza di sessione segnalati da alcuni dispositivi iOS precedenti.

**8 novembre 2019: versione 4.18.9**

* Messaggistica in app: è stato corretto un bug che impediva di caricare nei messaggi a schermo intero le immagini memorizzate nella cache o nel bundle.

**20 settembre 2019: versione 4.18.8**

* Messaggistica in-app:

   * Sui dispositivi con iOS 10 o più recenti, il framework `UserNotifications` è ora utilizzato per pianificare le notifiche locali per le applicazioni che sono collegate al `UserNotifications.framework`.
   * I messaggi a schermo intero ora utilizzano WKWebViews da `WebKit.framework`, che deve essere collegato nel progetto Xcode.
   * È stato corretto un bug a causa del quale il payload click-through push non poteva essere utilizzato come caratteristica dei i messaggi in-app.
   * Risolto un problema di arresto anomalo.

* Generale: è stato corretto un bug a causa del quale i dati dell&#39;SDK venivano sincronizzati con l&#39;app watchOS associata a ogni chiamata di Analytics.

**2 agosto 2019: versione 4.18.7**

* Ripristinato un cambiamento introdotto nella versione 4.18.6 che, in alcuni ambienti, ha causato un arresto anomalo dei dispositivi che utilizzavano una versione iOS più vecchia di 11.0.

* Adobe Target: aggiunta la proprietà `requestLocationParameters` in `ADBTargetRequestObject`, che consente di inviare l&#39;impressionId con le richieste di Target.

**18 luglio 2019: versione 4.18.6**

* Adobe Target: tutte le richieste ora includono il client e il valore `sessionId` nei parametri di query URL.
* Adobe Target: è stato risolto un problema di perdita di memoria.
* Servizio Visitor ID: le API `visitorAppendToURL` e `visitorGetUrlVariablesAsync` non applicano più la doppia codifica ai valori restituiti.

   A causa della doppia codifica, i valori restituiti da tali API venivano segnalati da parte di alcuni servizi di sicurezza.

**5 giugno 2019: versione 4.18.5**

* Analytics: aggiungi lo stato di consenso push ai dati del ciclo di vita quando le notifiche push sono abilitate.

**24 maggio 2019: versione 4.18.4**

* Servizio ID visitatore: aumentato il timeout di ritorno per l&#39;API
   `visitorGetUrlVariablesAsync` a 30 secondi.

* Servizio ID visitatore: la chiamata API `setPushIdentifier` ora invia una chiamata di sincronizzazione al servizio ID visitatore ogni volta che viene chiamata.

Per ulteriori informazioni sulle note sulle versioni attuale e precedenti di tutte le soluzioni, consulta [Note sulla versione di Adobe Experience Cloud](https://docs.adobe.com/content/help/it-IT/release-notes/experience-cloud/current.html).
