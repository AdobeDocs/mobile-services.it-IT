---
description: Usa l'SDK per iOS per implementare il tracciamento dei collegamenti profondi differiti (deferred deep link) di terze parti.
seo-description: Usa l'SDK per iOS per implementare il tracciamento dei collegamenti profondi differiti (deferred deep link) di terze parti.
seo-title: Tracciamento dei collegamenti profondi differiti (deferred deep link) di terze parti
title: Tracciamento dei collegamenti profondi differiti (deferred deep link) di terze parti
uuid: 5525b609-e926-44b9-b0f5-38e9dd7c9761
translation-type: tm+mt
source-git-commit: 4b5be6c51c716114e597a80d475f838e23abb1b1
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 90%

---


# Tracciamento dei collegamenti profondi differiti (deferred deep link) di terze parti {#tracking-third-party-deferred-deep-links}

Usa l&#39;SDK per iOS per implementare il tracciamento dei collegamenti profondi differiti (deferred deep link) di terze parti.

## Collegamenti diretti classici dell&#39;SDK di Adobe Mobile {#section_D114FA1EB9664EAA82E036A990694B26}

L&#39;SDK di Adobe Mobile attualmente supporta il deep linking, o creazione di collegamenti diretti, in cui lo sviluppatore di app deve chiamare l&#39;API `trackAdobeDeepLink` e passare l&#39;URL del collegamento diretto, che è l&#39;URL di creazione dell&#39;impronta digitale generato in Adobe Mobile Services durante la configurazione. L&#39;SDK invia un segnale ping al generatore dell&#39;impronta digitale per ottenere i dati di acquisizione e li aggiunge ai dati contestuali delle chiamate di analisi installazione/avvio, come parte del ciclo di vita. Inoltre, aggiunge i dati del collegamento diretto dai parametri dell&#39;URL di deep linking. Per ulteriori informazioni sul deep linking, vedi [Tracciamento dei collegamenti profondi (deep link)](/help/ios/acquisition-main/tracking-deep-links/tracking-deep-links.md).

## Collegamenti diretti di Facebook {#section_6A9DACB54A2F4CDEBE9C744DEFADFDED}

Il creatore di un&#39;inserzione può creare un&#39;inserzione su Facebook come collegamento profondo. Quando l&#39;utente fa clic sull&#39;inserzione su Facebook, passa direttamente alle informazioni di interesse nell&#39;app. Il collegamento profondo **non** è un URL di generazione di impronta digitale. Tuttavia, durante la configurazione dell&#39;annuncio, è disponibile l&#39;opzione per fornire un URL di collegamento profondo di terze parti. Lo sviluppatore di app che utilizza gli SDK e i servizi Mobile  Experience Cloud deve immettere in questo campo l&#39;URL di generazione di impronte digitali configurato da Mobile Services. Se è tutto impostato correttamente, l&#39;SDK di Facebook passa questo URL all&#39;applicazione quando l&#39;app viene installata o avviata.

## Configurare gli SDK  {#section_834CD3109175432B8173ECB6EA7DE315}

1. Imposta l&#39;SDK di Facebook.

   Per ulteriori informazioni vedi quanto segue:

   * [Introduzione all&#39;SDK di Facebook per iOS](https://developers.facebook.com/docs/ios/getting-started)
   * [Impostazione deep linking](https://developers.facebook.com/docs/app-ads/deep-linking#os)

1. Per impostare l’SDK, chiama `trackAdobeDeepLink` e passa l’URL agli SDK:

   ```objective-c
   - (BOOL)application:(UIApplication *)application openURL:(NSURL *)url sourceApplication:(NSString *)sourceApplication annotation:(id)annotation 
   { 
     [ADBMobile trackAdobeDeepLink:url]; 
     return YES; 
   }
   ```

   >[!TIP]
   >
   >Accertati che l&#39;URL del collegamento diretto disponga di una chiave denominata `a.deeplink.id`. Se nell&#39;URL manca il parametro `a.deeplink.id`, nessun parametro URL potrà essere aggiunto ai dati.

Se l&#39;applicazione è impostata come descritto qui sopra, la versione SDK di Adobe Mobile corrente funzionerà correttamente e i dati del collegamento profondo verranno aggiunti alle chiamate di installazione o avvio.

## Abilitare la funzione in un’applicazione di esempio {#section_64C15E269E89424B8E3D029F88094620}

1. Registra uno schema URL.

   Assicurati di registrare uno schema URL, corrispondente all&#39;URL di collegamento profondo.

   ```objective-c
   <key>CFBundleURLTypes</key> 
       <array> 
           <dict> 
               <key>CFBundleURLSchemes</key> 
               <array> 
                   <string>sampleapptest</string> 
               </array> 
           </dict> 
       </array>
   ```

1. Collegare gli SDK di Facebook.

   ![Risorse Facebook](assets/link-fb-sdk.jpg)

1. Modifica `AppDelegate`.

   1. Importa le intestazioni.

      ```objective-c
      /************************************************************************* 
      ADOBE SYSTEMS INCORPORATED 
      Copyright 2015 Adobe Systems Incorporated 
      All Rights Reserved. 
      NOTICE:  Adobe permits you to use, modify, and distribute this file in accordance with the 
      terms of the Adobe license agreement accompanying it.  If you have received this file from a 
      source other than Adobe, then your use, modification, or distribution of it requires the prior 
      written permission of Adobe. 
      
      **************************************************************************/ 
      
      #import "AppDelegate.h" 
      #import "GalleryViewController.h" 
      #import "SimpleTrackingController.h" 
      #import "PostbackController.h" 
      #import "InAppMessageViewController.h" 
      #import "LifetimeValueController.h" 
      #import "LocationTargetingController.h" 
      #import "MediaViewController.h" 
      #import "TimedActionController.h"
      
      // Uncomment after including the facebook sdks. 
      @import FBSDKCoreKit; 
      @import Bolts;
      ```

   1. Aggiungi un handle per il deferred deep linking.

      ```objective-c
      - (BOOL) application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions { 
          /* 
           * Adobe Tracking - Analytics 
           * 
           * turn on debug logging for the ADBMobile SDK 
           * enable the collection of lifecycle data 
           */ 
              if (launchOptions[UIApplicationLaunchOptionsURLKey] == nil) { 
                  if (NSClassFromString(@"FBSDKAppLinkUtility") != nil) 
                  { 
                      [NSClassFromString(@"FBSDKAppLinkUtility") performSelector:@selector(fetchDeferredAppLink:) withObject:^(NSURL *url, NSError *error) { 
                          if (error) { 
                              NSLog(@"Received error while fetching deferred app link %@", error); 
                          } 
                          if (url) { 
                              [[UIApplication sharedApplication] openURL:url]; 
                          } 
                      }]; 
                  } 
          } 
          ..... 
          ..... 
          return YES; 
      }
      ```

   1. Chiama l&#39;API `trackAdobeDeepLink` e passa l&#39;URL del collegamento diretto agli SDK.

      ```objective-c
      - (BOOL)application:(UIApplication *)app openURL:(NSURL *)url options:(NSDictionary<NSString *, id> *)options { 
          [self handleDeepLink:url]; 
      
          return YES; 
      }
      ```

