---
product: servizi mobili
audience: utente finale
user-guide-title: Guida di Mobile Services Android
translation-type: tm+mt
source-git-commit: e3bbde6c27d583ff3ee8b7e86c8e6e73595f5067

---


# Guida di Mobile Services Android{#android}

+ [Android SDK 4.x per soluzioni Experience Cloud](overview.md)
+ [Note sulla versione](rel-notes.md)
+ Getting started{#getting-started-android}
   + [Guida introduttiva](getting-started/getting-started.md)
   + [Prima di iniziare](getting-started/requirements.md)
   + [Implementazione e ciclo di vita di base](getting-started/dev-qs.md)
   + [Regole di elaborazione e dati contestuali](getting-started/proc-rules.md)
   + [Migrazione alla libreria Android 4.x](getting-started/migration-v3.md)
+ Configurazione{#configuration-android}
   + [Configuration overview](configuration/configuration.md)
   + [File di configurazione ADBMobile JSON](configuration/json-config/json-config.md)
   + [Escludere il percorso di configurazione ADBMobile JSON](configuration/json-config/json-config-remote.md)
   + [Invio in batch di hit](configuration/hit-batching.md)
   + [Metodi di configurazione](configuration/methods.md)
+ [Lifecycle metrics](metrics.md)
+ Analytics{#analytics-android}
   + [Panoramica di Analytics](analytics-main/analytics-main.md)
   + [Track app states](analytics-main/states.md)
   + [Tracciare le azioni dell'app](analytics-main/actions.md)
   + [Tracciare gli arresti anomali dell’app](analytics-main/crashes.md)
   + [Azioni temporizzate](analytics-main/timed-actions.md)
   + [Valore del ciclo di vita del visitatore](analytics-main/lifetime-value.md)
   + Products variable{#products-variable}
      + [Variabile "products"](analytics-main/products/products.md)
      + [Variabile "products" con eVar per merchandising ed eventi per singoli prodotti](analytics-main/products/products-variable-evars-events.md)
   + [Serializzazione degli eventi](analytics-main/event-serialization.md)
   + [Analisi del video](analytics-main/video-qs.md)
   + Postback{#postbacks}
      + [Panoramica sui postback](analytics-main/postbacks/postbacks.md)
      + [Esempio di postback](analytics-main/postbacks/postback-example.md)
      + [Postback PII](analytics-main/postbacks/c-pii-postbacks.md)
   + [Metodi di analisi](analytics-main/analytics-methods.md)
+ Acquisizione{#acquisition-android}
   + [Acquisition overview](acquisition-main/acquisition-main-android.md)
   + [Acquisizione da app mobile](acquisition-main/acquisition.md)
   + [Metodi di acquisizione](acquisition-main/acquisition-methods.md)
   + Tracking deep links{#tracking-deep-links}
      + [Tracciamento dei collegamenti profondi](acquisition-main/tracking-deep-links/tracking-deep-links.md)
      + [Tracciamento dei collegamenti profondi differiti (deferred deep link) di terze parti](acquisition-main/tracking-deep-links/c-tracking-3rd-party-deferred-deep-links.md)
   + [Verifica dell’acquisizione da collegamento marketing](acquisition-main/t-testing-marketing-link-acquisition.md)
   + [Verifica dell'acquisizione V3](acquisition-main/t-testing-version-3-acquisition.md)
   + [Verifica dell’acquisizione legacy](acquisition-main/t-testing-acquisition.md)
   + [Risoluzione dei problemi di test di acquisizione](acquisition-main/troubleshoot-acquisition-testing.md)
+ Messaggistica{#messaging-android}
   + [Panoramica sulla messaggistica](messaging-main/messaging-main-android.md)
   + In-app messaging{#inapp-messaging}
      + [Messaggistica in-app](messaging-main/messaging/messaging.md)
      + [Risoluzione dei problemi dei messaggi in-app](messaging-main/messaging/in-apps-ts.md)
   + Push messaging{#push-messaging}
      + [Push messaging](messaging-main/push-messaging/push-messaging.md)
      + [Implement push messaging with deep linking](messaging-main/push-messaging/t-mob-impl-push-deeplinking-android-4x.md)
      + [Receive rich push notifications](messaging-main/push-messaging/c-set-up-rich-push-notif-android.md)
      + [Risoluzione dei problemi dei messaggi push](messaging-main/push-messaging/c-troubleshooting-push-messaging.md)
+ Posizione{#location}
   + [Panoramica sulla posizione](location/location.md)
   + [Geolocalità e punti di interesse](location/geo-poi.md)
   + [Tracciamento dei beacon](location/beacon.md)
+ Target{#target-android}
   + [Target overview](target-main/target-main.md)
   + [Target configuration](target-main/target.md)
   + [Metodi di Target](target-main/c-target-methods.md)
   + [Preacquisizione del contenuto delle offerte in Android](target-main/c-mob-target-prefetch-android.md)
   + [Anteprima Target in Android](target-main/c-mob-target-preview-android.md)
+ Experience Cloud{#experience-cloud-android}
   + [Panoramica di Experience Cloud](c-marketing-cloud/c-marketing-cloud.md)
   + [Configurazione Experience Cloud ID](c-marketing-cloud/mcvid.md)
   + [Metodi di Adobe Experience Platform Identity](c-marketing-cloud/mc-methods.md)
   + [Experience Cloud Device Co-op](c-marketing-cloud/t-mob-mc-device-coop-android-.md)
+ Audience Manager{#audience-manager-android}
   + [Panoramica di Audience Manager](audience-manager/audience-manager.md)
   + [Configurazione di Audience Manager](audience-manager/audiencemgmt.md)
   + [Metodi di Audience Manager](audience-manager/c-audience-manager-methods.md)
+ Wearable{#wearables-android}
   + [Panoramica sulle indossabili](wearables/wearables.md)
   + [Android Wearables: getting started](wearables/android-wearable.md)
   + [Android Wearables: additional notes](wearables/c-android-wearables--additional-notes.md)
+ Android SDK reference{#sdk-reference-android}
   + [Panoramica di riferimento dell’SDK per Android](/help/android/reference/reference.md)
   + [ID delle app](/help/android/reference/app-ids.md)
   + [Tracciamento dei visitatori tra app e Web per dispositivi mobili](/help/android/reference/hybrid-app.md)
   + [Widget Android](/help/android/reference/widgets.md)
+ Privacy e Regolamento generale sulla protezione dei dati (RGPD){#gdpr-privacy-android}
   + [Privacy and GDPR overview](c-mob-privacy-gdpr-android/c-mob-privacy-gdpr-android.md)
   + [Recupero di identificatori memorizzati](c-mob-privacy-gdpr-android/c-mob-gdpr-ret-stored-ids-android.md)
   + [Impostazione dello stato di consenso dell'utente](c-mob-privacy-gdpr-android/privacy.md)
+ Plug-in PhoneGap{#phonegap-android}
   + [Panoramica del plug-in PhoneGap](phonegap/phonegap.md)
   + [Metodi del plug-in PhoneGap](phonegap/phonegap-methods.md)
