---
audience: end-user
user-guide-title: Guida di Mobile Services per Android
breadcrumb-title: Guida Android
source-git-commit: 78b7a623a7811cf0ede789c74b3ca7a80372c9f4
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 99%

---


# Guida di Mobile Services per Android{#android}

+ [SDK 4.x per Android per le soluzioni Experience Cloud](overview.md)
+ [Note sulla versione](rel-notes.md)
+ Introduzione {#getting-started-android}
   + [Introduzione](getting-started/getting-started.md)
   + [Prima di iniziare](getting-started/requirements.md)
   + [Implementazione e ciclo di vita di base](getting-started/dev-qs.md)
   + [Regole di elaborazione e dati contestuali ](getting-started/proc-rules.md)
   + [Migrazione alla libreria Android 4.x](getting-started/migration-v3.md)
+ Configurazione{#configuration-android}
   + [Panoramica sulla configurazione](configuration/configuration.md)
   + [File di configurazione ADBMobile JSON](configuration/json-config/json-config.md)
   + [Escludere il percorso del file di configurazione ADBMobile JSON](configuration/json-config/json-config-remote.md)
   + [Gestione degli hit in batch](configuration/hit-batching.md)
   + [Metodi di configurazione](configuration/methods.md)
+ [Metriche del ciclo di vita](metrics.md)
+ Analytics {#analytics-android}
   + [Panoramica di Analytics](analytics-main/analytics-main.md)
   + [Tracciare gli stati dell’app](analytics-main/states.md)
   + [Tracciare le azioni eseguite nell’app](analytics-main/actions.md)
   + [Tracciare gli arresti anomali dell’app](analytics-main/crashes.md)
   + [Azioni temporizzate](analytics-main/timed-actions.md)
   + [Valore &quot;lifetime&quot; del ciclo di vita del visitatore](analytics-main/lifetime-value.md)
   + Variabile dei prodotti {#products-variable}
      + [Variabile &quot;products&quot; ](analytics-main/products/products.md)
      + [Variabile &quot;products&quot; con eVar per merchandising ed eventi per singoli prodotti](analytics-main/products/products-variable-evars-events.md)
   + [Serializzazione degli eventi](analytics-main/event-serialization.md)
   + [Analisi dei video](analytics-main/video-qs.md)
   + Postback {#postbacks}
      + [Panoramica sui postback](analytics-main/postbacks/postbacks.md)
      + [Esempi di postback](analytics-main/postbacks/postback-example.md)
      + [Postback PII](analytics-main/postbacks/c-pii-postbacks.md)
   + [Metodi di Analytics](analytics-main/analytics-methods.md)
+ Acquisizione {#acquisition-android}
   + [Panoramica acquisizione](acquisition-main/acquisition-main-android.md)
   + [Acquisizione da app mobile](acquisition-main/acquisition.md)
   + [Metodi di acquisizione ](acquisition-main/acquisition-methods.md)
   + Tracciamento dei collegamenti profondi {#tracking-deep-links}
      + [Tracciamento dei collegamenti profondi](acquisition-main/tracking-deep-links/tracking-deep-links.md)
      + [Tracciamento dei collegamenti profondi differiti (deferred deep link) di terze parti ](acquisition-main/tracking-deep-links/c-tracking-3rd-party-deferred-deep-links.md)
   + [Verifica dell’acquisizione da collegamenti marketing](acquisition-main/t-testing-marketing-link-acquisition.md)
   + [Verifica dell’acquisizione V3 ](acquisition-main/t-testing-version-3-acquisition.md)
   + [Verifica di acquisizioni legacy](acquisition-main/t-testing-acquisition.md)
   + [Risoluzione dei problemi del test di acquisizione](acquisition-main/troubleshoot-acquisition-testing.md)
+ Messaggistica {#messaging-android}
   + [Panoramica sulla messaggistica](messaging-main/messaging-main-android.md)
   + Messaggistica in-app {#inapp-messaging}
      + [Messaggistica in-app ](messaging-main/messaging/messaging.md)
      + [Risoluzione dei problemi di messaggistica in-app ](messaging-main/messaging/in-apps-ts.md)
   + Messaggi push {#push-messaging}
      + [Messaggi push](messaging-main/push-messaging/push-messaging.md)
      + [Implementare i messaggi push con collegamenti profondi](messaging-main/push-messaging/t-mob-impl-push-deeplinking-android-4x.md)
      + [Ricevere notifiche push potenziate](messaging-main/push-messaging/c-set-up-rich-push-notif-android.md)
      + [Risolvere i problemi dei messaggi push](messaging-main/push-messaging/c-troubleshooting-push-messaging.md)
+ Posizione {#location}
   + [Panoramica sulla posizione](location/location.md)
   + [Geolocalizzazione e punti di interesse](location/geo-poi.md)
   + [Tracciamento dei beacon](location/beacon.md)
+ Target {#target-android}
   + [Panoramica di Target](target-main/target-main.md)
   + [Configurazione di Target](target-main/target.md)
   + [Metodi di Target](target-main/c-target-methods.md)
   + [Preacquisizione del contenuto delle offerte in Android](target-main/c-mob-target-prefetch-android.md)
   + [Anteprima Target in Android](target-main/c-mob-target-preview-android.md)
+ Experience Cloud {#experience-cloud-android}
   + [Panoramica di Experience Cloud](c-marketing-cloud/c-marketing-cloud.md)
   + [Configurazione del servizio Experience Cloud ID](c-marketing-cloud/mcvid.md)
   + [Metodi di Adobe Experience Platform Identity](c-marketing-cloud/mc-methods.md)
+ Audience Manager {#audience-manager-android}
   + [Panoramica di Audience Manager](audience-manager/audience-manager.md)
   + [Configurazione di Audience Manager](audience-manager/audiencemgmt.md)
   + [Metodi di Audience Manager](audience-manager/c-audience-manager-methods.md)
+ Wearable {#wearables-android}
   + [Panoramica su Wearable](wearables/wearables.md)
   + [Android Wearable: guida introduttiva ](wearables/android-wearable.md)
   + [Wearable Android: note aggiuntive ](wearables/c-android-wearables--additional-notes.md)
+ Guida di riferimento dell&#39;SDK per Android {#sdk-reference-android}
   + [Panoramica di riferimento dell’SDK per Android](/help/android/reference/reference.md)
   + [ID delle app](/help/android/reference/app-ids.md)
   + [Tracciamento dei visitatori tra app e contenuti web per dispositivi mobili](/help/android/reference/hybrid-app.md)
   + [Widget Android](/help/android/reference/widgets.md)
+ Privacy e Regolamento generale sulla protezione dei dati (RGPD) {#gdpr-privacy-android}
   + [Panoramica sulla privacy e sul RGPD](c-mob-privacy-gdpr-android/c-mob-privacy-gdpr-android.md)
   + [Recupero di ID memorizzati](c-mob-privacy-gdpr-android/c-mob-gdpr-ret-stored-ids-android.md)
   + [Impostazione dello stato di consenso o rinuncia dell’utente](c-mob-privacy-gdpr-android/privacy.md)
+ Plug-in PhoneGap {#phonegap-android}
   + [Panoramica del plug-in PhoneGap](phonegap/phonegap.md)
   + [Metodi del plug-in PhoneGap](phonegap/phonegap-methods.md)
