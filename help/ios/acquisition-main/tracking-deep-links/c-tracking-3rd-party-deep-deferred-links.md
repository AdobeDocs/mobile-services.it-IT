---
description: Usa l'SDK per iOS per implementare il tracciamento dei collegamenti profondi differiti (deferred deep link) di terze parti.
seo-description: Usa l'SDK per iOS per implementare il tracciamento dei collegamenti profondi differiti (deferred deep link) di terze parti.
seo-title: Tracciamento dei collegamenti profondi differiti (deferred deep link) di terze parti
title: Tracciamento dei collegamenti profondi differiti (deferred deep link) di terze parti
uuid: 5525 b 609-e 926-44 b 9-b 0 f 5-38 e 9 dd 7 c 9761
translation-type: tm+mt
source-git-commit: 4b5be6c51c716114e597a80d475f838e23abb1b1

---


# Tracking third-party deferred deep links {#tracking-third-party-deferred-deep-links}

Usa l'SDK per iOS per implementare il tracciamento dei collegamenti profondi differiti (deferred deep link) di terze parti.

## Classic Adobe Mobile SDK deep linking {#section_D114FA1EB9664EAA82E036A990694B26}

The Adobe Mobile SDK currently supports deep linking where the app developer is expected to call the `trackAdobeDeepLink` API and pass the deep linking URL, which is the fingerprinter URL that is generated in Adobe Mobile Services during configuration. L'SDK invia un segnale ping al generatore dell'impronta digitale per ottenere i dati di acquisizione e li aggiunge ai dati contestuali delle chiamate di analisi installazione/avvio, come parte del ciclo di vita. Inoltre, l'SDK aggiunge i dati di collegamento profondo dai parametri dell'URL con collegamento profondo. Per ulteriori informazioni sul deep linking, vedi [Tracciamento dei collegamenti profondi (deep link)](/help/ios/acquisition-main/tracking-deep-links/tracking-deep-links.md).

## Facebook deep linking {#section_6A9DACB54A2F4CDEBE9C744DEFADFDED}

Il creatore di un'inserzione può creare un'inserzione su Facebook come collegamento profondo. Quando l'utente fa clic sull'inserzione su Facebook, passa direttamente alle informazioni di interesse nell'app. Il collegamento profondo **non** è un URL di generazione di impronta digitale. Tuttavia, durante la configurazione dell'annuncio, è disponibile l'opzione per fornire un URL di collegamento profondo di terze parti. Lo sviluppatore di app che utilizza i servizi e l'SDK di Experience Cloud Mobile deve immettere in questo campo l'URL di generazione di impronte digitali configurato da Mobile Services. Se è tutto impostato correttamente, l'SDK di Facebook passa questo URL all'applicazione quando l'app viene installata o avviata.

## Configurare gli SDK {#section_834CD3109175432B8173ECB6EA7DE315}

1. Imposta l'SDK di Facebook.

   Per ulteriori informazioni, vedi:

   * [Introduzione all'SDK di Facebook per iOS](https://developers.facebook.com/docs/ios/getting-started)
   * [Impostazione del deep linking](https://developers.facebook.com/docs/app-ads/deep-linking#os)

1. Per configurare l'SDK, chiama `trackAdobeDeepLink` e passa l'URL agli SDK:

   ```objective-c
   - (BOOL)application:(UIApplication *)application openURL:(NSURL *)url sourceApplication:(NSString *)sourceApplication annotation:(id)annotation 
   { 
     [ADBMobile trackAdobeDeepLink:url]; 
     return YES; 
   }
   ```

   >[!TIP]
   >
   >Ensure that the deep link URL has a key with the name `a.deeplink.id`. Se nell'URL manca il parametro `a.deeplink.id`, nessun parametro URL potrà essere aggiunto ai dati.

Se l'applicazione è impostata come descritto qui sopra, la versione SDK di Adobe Mobile corrente funzionerà correttamente e i dati del collegamento profondo verranno aggiunti alle chiamate di installazione o avvio.

## Abilitare la funzionalità in un'applicazione di esempio {#section_64C15E269E89424B8E3D029F88094620}

1. Registra uno schema URL.

   Assicurati di registrare uno schema URL, corrispondente all'URL di collegamento profondo.

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

   1. Aggiungi la maniglia per il deep linking differito.

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

   1. Chiama `trackAdobeDeepLink` l'API e passa l'URL del collegamento profondo all'SDK.

      ```objective-c
      - (BOOL)application:(UIApplication *)app openURL:(NSURL *)url options:(NSDictionary<NSString *, id> *)options { 
          [self handleDeepLink:url]; 
      
          return YES; 
      }
      ```

