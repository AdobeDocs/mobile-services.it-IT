---
description: A partire da WatchOS 2, le estensioni WatchKit possono essere eseguite sui dispositivi Apple Watch. Le applicazioni che vengono eseguite in questo ambiente richiedono la condivisione di dati tra il framework WatchConnectivity e l'app iOS che le contiene.
seo-description: A partire da WatchOS 2, le estensioni WatchKit possono essere eseguite sui dispositivi Apple Watch. Le applicazioni che vengono eseguite in questo ambiente richiedono la condivisione di dati tra il framework WatchConnectivity e l'app iOS che le contiene.
seo-title: Implementazione Apple Watch con WatchOS 2
solution: Marketing Cloud, Analytics
title: Implementazione Apple Watch con WatchOS 2
topic: Sviluppatore e implementazione
uuid: 9498467 e-db 5 e -411 e-a 00 e-d 19841 f 485 de
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Apple Watch implementation with WatchOS 2{#apple-watch-implementation-with-watchos}

A partire da watchos 2, le estensioni watchkit possono essere eseguite su un Apple Watch. Applications that run in this environment require the `WatchConnectivity` framework to share data with their containing iOS app.

>[!TIP]
>
>A partire `AdobeMobileLibrary` dalla versione `WatchConnectivity` 4.6.0, è supportato.

## Getting started {#section_70BC28BB69414F169196953D3D264BC1}

>[!IMPORTANT]
>
>Assicurati di disporre di un progetto con almeno i seguenti target:
>
>* L'app contenitore
>* L'app WatchKit
>* L'estensione WatchKit
>



Per ulteriori informazioni sullo sviluppo di app WatchKit, vedi [The Watch App Architecture](https://developer.apple.com/library/ios/documentation/General/Conceptual/WatchKitProgrammingGuide/DesigningaWatchKitApp.html#//apple_ref/doc/uid/TP40014969-CH3-SW1).

## Configurare l'app contenitore {#section_0A2A3995575B4E2ABD12E426BA06AEFF}

Completa i seguenti passaggi nel progetto Xcode:

1. Trascina nel progetto la cartella `AdobeMobileLibrary`.
1. Ensure that the `ADBMobileConfig.json` file is a member of the containing app’s target.
1. Nella scheda **[!UICONTROL Fasi build]** della destinazione dell'app contenitore, espandi la sezione **Collega binario a librerie]e aggiungi le seguenti librerie:[!UICONTROL **

   * `AdobeMobileLibrary.a`
   * `libsqlite3.tbd`
   * `SystemConfiguration.framework`

1. Nella classe che implementa il protocollo `UIApplicationDelegate`, aggiungi il protocollo `WCSessionDelegate`.

   ```objective-c
   #import <WatchConnectivity/WatchConnectivity.h> 
   @interface AppDelegate : UIResponder <UIApplicationDelegate, WCSessionDelegate>
   ```

1. Nel file di implementazione della classe app delegate, importa `AdobeMobileLibrary`.

   ```objective-c
   #import “ADBMobile.h”
   ```

1. Before making a call to the `ADBMobile` library, in `application:didFinishLaunchingWithOptions:` of your app delegate, configure your `WCSession`.

   ```objective-c
   // check for session availability 
   if ([WCSession isSupported]) { 
       WCSession *session = [WCSession defaultSession]; 
       session.delegate = self; 
       [session activateSession]; 
   }
   ```

1. In your app delegate, implement the `session:didReceiveMessage:` and `session:didReceiveUserInfo:` methods.

   `syncSettings:` viene chiamato nella `ADBMobile` libreria, che restituisce un booleano che indica se il dizionario è destinato al consumo da parte della `ADBMobile` libreria. Se restituisce `No`, il messaggio non era stato avviato dall'SDK Adobe.

   ```objective-c
   - (void) session:(WCSession *)session didReceiveMessage:(NSDictionary<NSString *,id> *)message { 
       // pass message to ADBMobile 
       if (![ADBMobile syncSettings:message]) { 
           // handle your own custom messages 
       } 
   } 
   - (void) session:(WCSession *)session didReceiveUserInfo:(NSDictionary<NSString *,id> *)userInfo { 
       // pass userInfo to ADBMobile 
       if (![ADBMobile syncSettings:userInfo]) { 
           // handle your own custom messages 
       } 
   } 
   ```

## Configurare l'estensione watchkit {#section_5ADE31741E514330A381F2E3CFD4A814}

1. Ensure that the `ADBMobileConfig.json` file is a member of your WatchKit extension’s target.
1. Nella scheda **[!UICONTROL Fasi build]** della destinazione dell'estensione WatchKit, espandi la sezione **Collega binario a librerie]e aggiungi le seguenti librerie:[!UICONTROL **

   * `AdobeMobileLibrary_Watch.a`
   * `libsqlite3.tbd`

1. In your class that implements the `WKExtensionDelegate` protocol, import `WatchConnectivity` and add the `WCSessionDelegate` protocol.

   ```objective-c
   #import <WatchConnectivity/WatchConnectivity.h> 
   @interface ExtensionDelegate : NSObject <WKExtensionDelegate, WCSessionDelegate>
   ```

1. Nel file di implementazione della classe dell'extension delegate, importa `AdobeMobileLibrary`.

   ```objective-c
   #import “ADBMobile.h”
   ```

1. In `applicationDidFinishLaunching` of your extension delegate, configure your `WCSession` before making any calls to the `ADBMobile` library.

   ```objective-c
   // check for session availability 
   if ([WCSession isSupported]) { 
       WCSession *session = [WCSession defaultSession]; 
       session.delegate = self; 
       [session activateSession]; 
   }
   ```

1. In `applicationDidFinishLaunching` dell'extension delegate, inizializza l'app Watch per l'SDK.

   ```objective-c
   [ADBMobile initializeWatch];
   ```

1. In your extension delegate, implement the `session:didReceiveMessage:` and `session:didReceiveUserInfo:` methods.

   `syncSettings:` viene chiamato nella `ADBMobile` libreria, che restituisce un booleano che indica se il dizionario è destinato al consumo da parte della `ADBMobile` libreria. Se restituisce `NO`, il messaggio non era stato avviato dall'SDK Adobe.

   ```objective-c
   - (void) session:(WCSession *)session didReceiveMessage:(NSDictionary<NSString *,id> *)message { 
       // pass message to ADBMobile 
       if (![ADBMobile syncSettings:message]) { 
           // handle your own custom messages 
       } 
   } 
   - (void) session:(WCSession *)session didReceiveUserInfo:(NSDictionary<NSString *,id> *)userInfo { 
       // pass userInfo to ADBMobile 
       if (![ADBMobile syncSettings:userInfo]) { 
           // handle your own custom messages 
       } 
   } 
   ```

## Informazioni aggiuntive {#section_7BCDB5CF0D424DCA97883753D1881233}

Considerazioni da ricordare:

* For WatchKit apps, `a.RunMode` will be set to `Extension`.
* Poiché le app WatchKit vengono eseguite sull'orologio, le app segnalano correttamente il loro nome in `a.AppID`.
* Sulle app WatchOS2 non viene attivata alcuna chiamata "lifecycle" (ciclo di vita).

