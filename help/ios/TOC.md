---
product: servizi mobili
audience: utente finale
user-guide-title: Guida di Mobile Services iOS
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Mobile Services iOS Help {#ios}

+ [SDK 4.x per iOS per le soluzioni Experience Cloud](overview.md)
+ [Note sulla versione](rel-notes.md)
+ Getting started {#getting-started-ios}
   + [Getting started overview](getting-started/getting-started.md)
   + [Prima di iniziare](getting-started/requirements.md)
   + [Core implementation and lifecycle](getting-started/dev-qs.md)
   + [Regole di elaborazione e dati contestuali](getting-started/proc-rules.md)
   + [Integrazione Swift](getting-started/swift-integration.md)
   + [Migrazione alla libreria iOS 4.x](getting-started/migration-v3.md)
+ Configurazione {#config-ios}
   + [Panoramica della configurazione](configuration/configuration.md)
   + [Configurazione ADBMobile JSON](configuration/json-config/json-config.md)
   + [Escludere il percorso di configurazione ADBMobile JSON](configuration/json-config/json-config-remote.md)
   + [Invio in batch di hit](configuration/hit-batching.md)
   + [Metodi di configurazione](configuration/sdk-methods.md)
   + [App Transport Security](configuration/app-transport-security.md)
+ [Metriche del ciclo di vita](metrics.md)
+ Analytics {#analytics-ios}
   + [Analytics overview](analytics-main/analytics-main.md)
   + [Tracciare gli stati delle app](analytics-main/states.md)
   + [Track app actions](analytics-main/actions.md)
   + [Track app crashes](analytics-main/crashes.md)
   + [Timed actions](analytics-main/timed-actions.md)
   + [Visitor lifetime value](analytics-main/lifetime-value.md)
   + Products variable {#products-variable}
      + [Products variable](analytics-main/products/products.md)
      + [Variabile "products" con eVar per merchandising ed eventi per singoli prodotti](analytics-main/products/products-variable-evars-events.md)
   + [Serializzazione degli eventi](analytics-main/event-serialization.md)
   + [Analisi del video](analytics-main/video-qs.md)
   + Postback {#postbacks}
      + [Postbacks overview](analytics-main/postback/postback.md)
      + [Esempio di postback](analytics-main/postback/postback-example.md)
      + [Postback PII](analytics-main/postback/c-pii-postbacks.md)
   + [Metodi di analisi](analytics-main/analytics-methods.md)
+ Acquisizione {#acquisition-ios}
   + [Acquisition overview](acquisition-main/acquisition-main.md)
   + [Mobile app acquisition](acquisition-main/acquisition.md)
   + [Acquisition methods](acquisition-main/c-acquisition-methods.md)
   + Tracking deep links {#tracking-deep-links}
      + [Tracciamento dei collegamenti profondi](acquisition-main/tracking-deep-links/tracking-deep-links.md)
      + [Tracciamento dei collegamenti profondi differiti (deferred deep link) di terze parti](acquisition-main/tracking-deep-links/c-tracking-3rd-party-deep-deferred-links.md)
   + [Verifica dell’acquisizione da collegamento marketing](acquisition-main/t-testing-marketing-link-acquisition.md)
   + [Verifica dell'acquisizione V3](acquisition-main/t-testing-version-3-acquisition.md)
   + [Testing legacy acquisition](acquisition-main/t-testing-acquisition.md)
   + [Apple Search Ads](acquisition-main/c-apple-search-ads.md)
+ Messaggistica {#messaging-ios}
   + [Panoramica sulla messaggistica](messaging-main/messaging-main.md)
   + In-app messaging {#in-app-messaging}
      + [Messaggistica in-app](messaging-main/messaging/messaging.md)
      + [Risoluzione dei problemi dei messaggi in-app](messaging-main/messaging/in-apps-ts.md)
   + Push messaging {#push-messaging}
      + [Messaggi push](messaging-main/push-messaging/push-messaging.md)
      + [Implement push messaging with deep linking](messaging-main/push-messaging/t-mob-imp-push-deeplinking-ios-4x.md)
      + [Ricevere notifiche push potenziate](messaging-main/push-messaging/c-set-up-rich-push-notif-ios.md)
      + [Risoluzione dei problemi dei messaggi push](messaging-main/push-messaging/c-troubleshooting-push-messaging.md)
+ Posizione {#location-ios}
   + [Location overview](location/location.md)
   + [Geolocalità e punti di interesse](location/geo-poi.md)
   + [Tracciamento iBeacon](location/ibeacon.md)
+ Target {#target-ios}
   + [Panoramica di Target](target-main/target-main.md)
   + [Metodi di Target](target-main/c-target-methods.md)
   + [Preacquisizione del contenuto delle offerte in iOS](target-main/c-mob-target-prefetch-ios.md)
   + [Anteprima Target in iOS](target-main/c-mob-target-preview-ios.md)
+ Experience Cloud {#exp-cloud-ios}
   + [Panoramica di Experience Cloud](marketing-cloud/marketing-cloud.md)
   + [Experience Cloud ID](marketing-cloud/mcvid.md)
   + [Metodi del servizio di identità Adobe Experience Platform](marketing-cloud/mc-methods.md)
   + [Experience Cloud Device Co-op](marketing-cloud/t-mob-mc-device-coop-ios-.md)
+ [Metodi di Audience Manager](amm/aam-methods.md)
+ Apple TV implementation with tvOS {#apple-tv-implementation-tvos-ios}
   + [Implementazione Apple TV con tvOS](apple-tv-implementation-tvos/apple-tv-implementation-tvos.md)
   + [Adobe Target per TVML/TVJS](apple-tv-implementation-tvos/target-for-tvml-tvjs.md)
   + [Metodi TVJS](apple-tv-implementation-tvos/tvjs-methods.md)
+ iOS extension implementation {#ios-ext}
   + [Implementazione estensione iOS](ios-ext/ios-ext.md)
   + [Implementazione dell'estensione autonoma](ios-ext/c-stand-alone-extension-implementation.md)
+ [Implementazione Apple Watch con WatchOS 2](apple-watch-implementation-watchkit.md)
+ iOS SDK reference {#sdk-reference-ios}
   + [Riferimento iOS SDK](reference/reference.md)
   + [ID delle app](reference/app-ids.md)
   + [Tracciamento dei visitatori tra app e Web per dispositivi mobili](reference/hybrid-app.md)
   + [iOS device versions](reference/device-versions.md)
+ Privacy e Regolamento generale sulla protezione dei dati (RGPD){#privacy-gdpr-ios}
   + [Privacy e Regolamento generale sulla protezione dei dati (RGPD)](c-mob-privacy-gdpr-ios/c-mob-privacy-gdpr-ios.md)
   + [Recupero di identificatori memorizzati](c-mob-privacy-gdpr-ios/c-mob-gdpr-ret-stored-ids-ios.md)
   + [Impostazione dello stato di consenso dell'utente](c-mob-privacy-gdpr-ios/privacy.md)
+ Plug-in PhoneGap {#phonegap-ios}
   + [Plug-in PhoneGap](phonegap/phonegap.md)
   + [Metodi del plug-in PhoneGap](phonegap/phonegap-methods.md)
