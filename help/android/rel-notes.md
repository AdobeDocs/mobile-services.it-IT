---
description: Note sulla versione e problemi noti per gli SDK 4.x per Android per le soluzioni Experience Cloud.
solution: Experience Cloud,Analytics
title: Note sulla versione
topic-fix: Developer and implementation
uuid: 16bb4de8-a216-47a8-928c-0b1e1421adcf
exl-id: 5cc3d031-5952-4e9b-b551-9402d3c05ccb
source-git-commit: d1ebb2bbc4742f5288f90a90e977d252f3f30aa3
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 72%

---

# Note sulla versione {#release-notes}

Di seguito sono riportate le note sulla versione, i problemi noti e le informazioni sulla correzione per l’SDK 4.x per Android per le soluzioni Experience Cloud:

## 3 aprile 2020: 4.18.2

* Messaggi in-app: per motivi di sicurezza, WebViews creato dall’SDK ora imposta la proprietà `setAllowFileAccess` su `false`.

## 12 marzo 2020: 4.18.1

* Target - L’ID della sessione di Target viene ora aggiunto come parametro dei dati contestuali `a.target.sessionId` nell’hit interno Analytics-for-Target inviato ad Adobe Analytics.

## 16 gennaio 2020: 4.18.0

* Acquisizione - Aggiunta una nuova API, `Analytics.processGooglePlayInstallReferrerUrl(final String url)`, per supportare l’installazione delle API Google Play Referrer.

   Per ulteriori informazioni sull’Installazione delle API di riferimento, consulta [Stai ancora usando InstallBroadcast? Passa all’Esecuzione dell’API di riferimento entro il 1° marzo 2020](https://android-developers.googleblog.com/2019/11/still-using-installbroadcast-switch-to.html).

## 20 settembre 2019: versione 4.17.10

* Generale: corretta la generazione di stringhe locali per alcune aree dell&#39;API Android livello 21 o successivo.

## 18 luglio 2019: versione 4.17.8

* Adobe Target: tutte le richieste ora includono il client e il sessionId nei parametri di query URL.
* Messaggistica in-app: È stato risolto un problema che causava l’arresto anomalo delle app Android quando veniva attivato un messaggio con un URL click-through vuoto.
* Servizio Visitor ID: le API `Visitor.appendToURL` e `Visitor.getUrlVariablesAsync` non applicano più la doppia codifica ai valori restituiti.

   A causa della doppia codifica, i valori restituiti da tali API venivano segnalati da parte di alcuni servizi di sicurezza.

## 6 giugno 2019: versione 4.17.7

* Generale: le chiamate di rete su livelli API Android inferiori a 20 ora utilizzano TLS 1.1 o TLS 1.2.
* Analytics: aggiunto lo stato di consenso push ai dati del ciclo di vita quando le notifiche push sono abilitate.

## 24 maggio 2019: versione 4.17.6

* servizio ID visitatore: la chiamata API `setPushIdentifier` ora invia una chiamata di sincronizzazione al servizio ID visitatore ogni volta che viene chiamata.
* Servizio ID visitatore: sono stati aumentati i tempi di connessione e di lettura da 2 a 5 secondi.

Per ulteriori informazioni sulle note sulle versioni attuale e precedenti di tutte le soluzioni, consulta [Note sulla versione di Adobe Experience Cloud](https://experienceleague.adobe.com/docs/release-notes/experience-cloud/current.html?lang=it).
