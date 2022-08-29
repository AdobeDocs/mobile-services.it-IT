---
audience: end-user
user-guide-title: Guida di Mobile Services per iOS
breadcrumb-title: Guida di iOS
source-git-commit: 78b7a623a7811cf0ede789c74b3ca7a80372c9f4
workflow-type: tm+mt
source-wordcount: '284'
ht-degree: 99%

---


# Guida di Mobile Services per iOS {#ios}

+ [SDK 4.x per iOS per le soluzioni Experience Cloud](overview.md)
+ [Note sulla versione](rel-notes.md)
+ Introduzione {#getting-started-ios}
   + [Introduzione - Panoramica](getting-started/getting-started.md)
   + [Prima di iniziare](getting-started/requirements.md)
   + [Implementazione e ciclo di vita di base](getting-started/dev-qs.md)
   + [Regole di elaborazione e dati contestuali ](getting-started/proc-rules.md)
   + [Integrazione Swift](getting-started/swift-integration.md)
   + [Migrazione alla libreria iOS 4.x](getting-started/migration-v3.md)
+ Configurazione {#config-ios}
   + [Panoramica sulla configurazione](configuration/configuration.md)
   + [File di configurazione ADBMobile JSON](configuration/json-config/json-config.md)
   + [Escludere il percorso del file di configurazione ADBMobile JSON](configuration/json-config/json-config-remote.md)
   + [Gestione degli hit in batch](configuration/hit-batching.md)
   + [Metodi di configurazione](configuration/sdk-methods.md)
   + [App Transport Security](configuration/app-transport-security.md)
+ [Metriche del ciclo di vita](metrics.md)
+ Analytics {#analytics-ios}
   + [Panoramica di Analytics](analytics-main/analytics-main.md)
   + [Tracciare gli stati dell’app](analytics-main/states.md)
   + [Tracciare le azioni eseguite nell’app](analytics-main/actions.md)
   + [Tracciare gli arresti anomali dell’app](analytics-main/crashes.md)
   + [Azioni temporizzate](analytics-main/timed-actions.md)
   + [Valore &quot;lifetime&quot; del ciclo di vita del visitatore](analytics-main/lifetime-value.md)
   + Variabile &quot;products&quot; {#products-variable}
      + [Variabile &quot;products&quot; ](analytics-main/products/products.md)
      + [Variabile &quot;products&quot; con eVar per merchandising ed eventi per singoli prodotti](analytics-main/products/products-variable-evars-events.md)
   + [Serializzazione degli eventi](analytics-main/event-serialization.md)
   + [Analisi dei video](analytics-main/video-qs.md)
   + Postback {#postbacks}
      + [Panoramica sui postback](analytics-main/postback/postback.md)
      + [Esempio di postback](analytics-main/postback/postback-example.md)
      + [Postback PII](analytics-main/postback/c-pii-postbacks.md)
   + [Metodi di Analytics](analytics-main/analytics-methods.md)
+ Acquisizione {#acquisition-ios}
   + [Panoramica acquisizione](acquisition-main/acquisition-main.md)
   + [Acquisizione da app mobile](acquisition-main/acquisition.md)
   + [Metodi di acquisizione ](acquisition-main/c-acquisition-methods.md)
   + Tracciamento dei collegamenti profondi {#tracking-deep-links}
      + [Tracciamento dei collegamenti profondi](acquisition-main/tracking-deep-links/tracking-deep-links.md)
      + [Tracciamento dei collegamenti profondi differiti (deferred deep link) di terze parti ](acquisition-main/tracking-deep-links/c-tracking-3rd-party-deep-deferred-links.md)
   + [Verifica dell’acquisizione da collegamenti marketing](acquisition-main/t-testing-marketing-link-acquisition.md)
   + [Verifica dell’acquisizione V3 ](acquisition-main/t-testing-version-3-acquisition.md)
   + [Verifica di acquisizioni legacy](acquisition-main/t-testing-acquisition.md)
   + [Apple Search Ads](acquisition-main/c-apple-search-ads.md)
+ Messaggistica {#messaging-ios}
   + [Panoramica sulla messaggistica](messaging-main/messaging-main.md)
   + Messaggistica in-app {#in-app-messaging}
      + [Messaggistica in-app ](messaging-main/messaging/messaging.md)
      + [Risoluzione dei problemi dei messaggi in-app ](messaging-main/messaging/in-apps-ts.md)
   + Messaggi push {#push-messaging}
      + [Messaggi push](messaging-main/push-messaging/push-messaging.md)
      + [Implementare i messaggi push con collegamenti profondi](messaging-main/push-messaging/t-mob-imp-push-deeplinking-ios-4x.md)
      + [Ricevere notifiche push potenziate](messaging-main/push-messaging/c-set-up-rich-push-notif-ios.md)
      + [Risoluzione dei problemi dei messaggi push](messaging-main/push-messaging/c-troubleshooting-push-messaging.md)
+ Posizione {#location-ios}
   + [Panoramica sulla posizione](location/location.md)
   + [Geolocalizzazione e punti di interesse](location/geo-poi.md)
   + [Tracciamento iBeacon](location/ibeacon.md)
+ Target {#target-ios}
   + [Panoramica di Target](target-main/target-main.md)
   + [Metodi di Target](target-main/c-target-methods.md)
   + [Preacquisizione del contenuto delle offerte in iOS](target-main/c-mob-target-prefetch-ios.md)
   + [Anteprima Target in iOS](target-main/c-mob-target-preview-ios.md)
+ Experience Cloud {#exp-cloud-ios}
   + [Panoramica di Experience Cloud](marketing-cloud/marketing-cloud.md)
   + [Experience Cloud ID](marketing-cloud/mcvid.md)
   + [Metodi di Adobe Experience Platform Identity](marketing-cloud/mc-methods.md)
+ [Metodi di Audience Manager](amm/aam-methods.md)
+ Implementazione Apple TV con tvOS {#apple-tv-implementation-tvos-ios}
   + [Implementazione Apple TV con tvOS](apple-tv-implementation-tvos/apple-tv-implementation-tvos.md)
   + [Adobe Target per TVML/TVJS](apple-tv-implementation-tvos/target-for-tvml-tvjs.md)
   + [Metodi TVJS](apple-tv-implementation-tvos/tvjs-methods.md)
+ Implementazione di un’estensione iOS {#ios-ext}
   + [Implementazione di un’estensione iOS](ios-ext/ios-ext.md)
   + [Implementazione di un’estensione autonoma](ios-ext/c-stand-alone-extension-implementation.md)
+ [Implementazione Apple Watch con WatchOS 2 ](apple-watch-implementation-watchkit.md)
+ Guida di riferimento dell’SDK per iOS {#sdk-reference-ios}
   + [Guida di riferimento dell’SDK per iOS](reference/reference.md)
   + [ID delle app](reference/app-ids.md)
   + [Tracciamento dei visitatori tra app e contenuti web per dispositivi mobili](reference/hybrid-app.md)
   + [Versioni dei dispositivi iOS](reference/device-versions.md)
+ Privacy e Regolamento generale sulla protezione dei dati (RGPD) {#privacy-gdpr-ios}
   + [Privacy e Regolamento generale sulla protezione dei dati (GDPR)](c-mob-privacy-gdpr-ios/c-mob-privacy-gdpr-ios.md)
   + [Recupero di ID memorizzati](c-mob-privacy-gdpr-ios/c-mob-gdpr-ret-stored-ids-ios.md)
   + [Impostazione dello stato di consenso o rinuncia dell’utente](c-mob-privacy-gdpr-ios/privacy.md)
+ Plug-in PhoneGap {#phonegap-ios}
   + [Plug-in PhoneGap ](phonegap/phonegap.md)
   + [Metodi del plug-in PhoneGap](phonegap/phonegap-methods.md)
