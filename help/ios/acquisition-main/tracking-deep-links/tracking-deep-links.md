---
description: Queste informazioni sono utili per tenere traccia dei collegamenti profondi (deep link) e di quelli profondi differiti (deferred deep link) nelle app mobili, mediante l'SDK di Adobe Mobile per iOS.
seo-description: Queste informazioni sono utili per tenere traccia dei collegamenti profondi (deep link) e di quelli profondi differiti (deferred deep link) nelle app mobili, mediante l'SDK di Adobe Mobile per iOS.
seo-title: Tracciamento dei collegamenti profondi
solution: Experience Cloud,Analytics
title: Tracciamento dei collegamenti profondi
uuid: 08dc2820-7fd3-419f-ac2d-dcf12532578a
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 100%

---


# Tracciamento dei collegamenti profondi {#tracking-deep-links}

Queste informazioni sono utili per tenere traccia dei collegamenti profondi (deep link) e di quelli profondi differiti (deferred deep link) nelle app mobili, mediante l&#39;SDK di Adobe Mobile per iOS.

Per ulteriori informazioni sul modo in cui i professionisti del marketing utilizzano i collegamenti profondi nelle loro applicazioni, consulta la sezione [Acquisizione](/help/ios/acquisition-main/acquisition.md) nella documentazione di Mobile Services.

## Tracciamento dei collegamenti profondi

1. Aggiungi l&#39;SDK al tuo progetto e implementa le metriche del ciclo di vita.

   Per ulteriori informazioni, consulta *Aggiungere l’SDK e il file di configurazione al progetto* in [Implementazione e ciclo di vita di base](/help/ios/getting-started/dev-qs.md).
1. Registra l&#39;applicazione per la gestione di comunicazioni tra app o supporto di collegamenti universali.

   Per ulteriori informazioni, consulta [Comunicazioni tra app](https://developer.apple.com/library/ios/documentation/iPhone/Conceptual/iPhoneOSProgrammingGuide/Inter-AppCommunication/Inter-AppCommunication.html#//apple_ref/doc/uid/TP40007072-CH6-SW10) o [Collegamenti universali di supporto](https://developer.apple.com/library/ios/documentation/General/Conceptual/AppSearch/UniversalLinks.html)

1. Tieni traccia dei collegamenti profondi in openURL.

   Ecco un esempio di tracciamento di un collegamento profondo:

   ```objective-c
   - (BOOL)application:(UIApplication *)application handleOpenURL:(NSURL *)url { 
       [ADBMobile trackAdobeDeepLink:url]; 
       /* 
        Handle deep link 
        */ 
       return YES; 
   } 
   - (BOOL)application:(UIApplication *)app openURL:(NSURL *)url options:(NSDictionary<NSString *, id> *)options { 
       [ADBMobile trackAdobeDeepLink:url]; 
       /* 
        Handle deep link 
        */ 
   
       return YES; 
   }
   ```

SDK di Adobe Mobile può analizzare le coppie chiave-valore di dati aggiunti alla fine di un collegamento diretto o universale, purché questo contenga una chiave con l&#39;etichetta `a.deeplink.id` e un valore corrispondente non nullo e generato dall&#39;utente. Tutte le coppie di dati chiave-valore aggiunte alla fine del collegamento vengono analizzate, allegate all&#39;hit del ciclo di vita e inviate ad Adobe Analytics, purché il collegamento contenga la chiave-valore `a.deeplink.id`.

Puoi anche scegliere di aggiungere al collegamento diretto o universale una o più delle seguenti chiavi riservate (con valori generati dall&#39;utente):

* `a.launch.campaign.trackingcode`
* `a.launch.campaign.source`
* `a.launch.campaign.medium`
* `a.launch.campaign.term`
* `a.launch.campaign.content`

Queste chiavi sono variabili premappate per il reporting in Adobe Analytics. Per maggiori informazioni sulle regole di mappatura ed elaborazione, vedi [Regole di elaborazione e dati contestuali](/help/ios/getting-started/proc-rules.md).

### Tracciamento dei collegamenti profondi differiti (deferred deep link)

1. Registra il callback di dati Adobe.

   ```objective-c
   [ADBMobile registerAdobeDataCallback:^(ADBMobileDataEvent event, NSDictionary * _Nullable adobeData) { 
   }];
   ```

1. Gestisci `ADBMobileDataEventDeepLink` in `AdobeDataCallback`.

   ```objective-c
   [ADBMobile registerAdobeDataCallback:^(ADBMobileDataEvent event, NSDictionary * _Nullable adobeData) { 
       if (event == ADBMobileDataEventDeepLink) { 
           [self handleDeepLink:adobeData[ADBConfigKeyCallbackDeepLink]]; 
       } 
   }];
   ```

## Informazioni pubbliche sui collegamenti diretti {#section_44600E9AA68D4A53AA0C14BD86CC5284}

### Metodi

```objective-c
/** 
 * @brief Tracks a Adobe Deep Link click-through 
 * @param url The URL resource received from UIApplication delegate method. 
 * @note Adobe Link data will be appended to the lifecycle call if it is a launch event, otherwise an extra call will be sent. 
 */ 
+ (void) trackAdobeDeepLink:(nullable NSURL *)url;
```

#### Costanti

```objective-c
/* 
 * Used within ADBMobileDataCallback 
 * Key for deep link URL. 
 */ 
FOUNDATION_EXPORT NSString *const __nonnull ADBConfigKeyCallbackDeepLink;
```

