---
description: A partire da WatchOS 2, le estensioni WatchKit possono essere eseguite sui dispositivi Apple Watch. Le applicazioni che vengono eseguite in questo ambiente richiedono la condivisione di dati tra il framework WatchConnectivity e l’app iOS che le contiene.
seo-description: A partire da WatchOS 2, le estensioni WatchKit possono essere eseguite sui dispositivi Apple Watch. Le applicazioni che vengono eseguite in questo ambiente richiedono la condivisione di dati tra il framework WatchConnectivity e l’app iOS che le contiene.
seo-title: Implementazione Apple Watch con WatchOS 2
solution: Experience Cloud,Analytics
title: Implementazione Apple Watch con WatchOS 2
topic-fix: Developer and implementation
uuid: 9498467e-db5e-411e-a00e-d19841f485de
exl-id: 9fc9b799-1081-42e4-acf3-569fdeb07aff
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '542'
ht-degree: 100%

---

# Implementazione Apple Watch con WatchOS 2 {#apple-watch-implementation-with-watchos}

A partire da WatchOS 2, le estensioni WatchKit possono essere eseguite sui dispositivi Apple Watch. Le applicazioni che vengono eseguite in questo ambiente richiedono la condivisione di dati tra il framework `WatchConnectivity` e l&#39;app iOS che le contiene.

>[!TIP]
>
>A partire dalla versione v4.6.0 di `AdobeMobileLibrary`, `WatchConnectivity` è supportato.

## Nuova versione dell&#39;SDK per dispositivi mobili di Adobe Experience Platform

Hai bisogno di informazioni e documentazione relative all’SDK per dispositivi mobili di Adobe Experience Platform? Fai clic [qui](https://aep-sdks.gitbook.io/docs/) per la documentazione più recente.

A settembre 2018 è stata rilasciata una nuova versione principale dell&#39;SDK. Questi nuovi SDK per dispositivi mobili di Adobe Experience Platform sono configurabili tramite [Experience Platform Launch](https://www.adobe.com/it/experience-platform/launch.html).

* Per iniziare, vai su Adobe Experience Platform Launch.
* Per visualizzare cosa è compreso negli archivi Experience Platform SDK, passa a [Github: SDK di Adobe Experience Platform](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

## Introduzione {#section_70BC28BB69414F169196953D3D264BC1}

>[!IMPORTANT]
>
>Assicurati di avere un progetto con almeno le seguenti destinazioni:
>
>* L’app contenitore
>* L’app WatchKit
>* L’estensione WatchKit
>



Per ulteriori informazioni sullo sviluppo di app WatchKit, consulta [The Watch App Architecture](https://developer.apple.com/library/ios/documentation/General/Conceptual/WatchKitProgrammingGuide/DesigningaWatchKitApp.html#//apple_ref/doc/uid/TP40014969-CH3-SW1).

## Configurare l&#39;app contenitore {#section_0A2A3995575B4E2ABD12E426BA06AEFF}

Completa i seguenti passaggi nel progetto Xcode:

1. Trascina nel progetto la cartella `AdobeMobileLibrary`.
1. Assicurati che il file `ADBMobileConfig.json` sia un membro della destinazione dell&#39;app contenitore.
1. Nella scheda **[!UICONTROL Build Phases]** della destinazione dell’app contenitore, espandi la sezione **[!UICONTROL Collega binario a librerie]** e aggiungi le seguenti librerie:

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

1. Prima di effettuare una chiamata alla libreria `ADBMobile`, in `application:didFinishLaunchingWithOptions:` dell&#39;app delegate, configura la `WCSession`.

   ```objective-c
   // check for session availability 
   if ([WCSession isSupported]) { 
       WCSession *session = [WCSession defaultSession]; 
       session.delegate = self; 
       [session activateSession]; 
   }
   ```

1. Nell&#39;app delegate, implementa i metodi `session:didReceiveMessage:` e `session:didReceiveUserInfo:`.

   `syncSettings:` viene invocato nella libreria `ADBMobile`, che restituisce un valore booleano che indica se il dizionario deve essere utilizzato dalla libreria `ADBMobile`. Se restituisce `No`, il messaggio non era stato avviato dall&#39;SDK Adobe.

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

## Configurare l’estensione WatchKit {#section_5ADE31741E514330A381F2E3CFD4A814}

1. Assicurati che il file `ADBMobileConfig.json` sia un membro della destinazione dell&#39;estensione WatchKit.
1. Nella scheda **[!UICONTROL Fasi build]** della destinazione dell’estensione WatchKit, espandi la sezione **[!UICONTROL Collega binario a librerie]** e aggiungi le seguenti librerie:

   * `AdobeMobileLibrary_Watch.a`
   * `libsqlite3.tbd`

1. Nella classe che implementa il protocollo `WKExtensionDelegate`, importa `WatchConnectivity` e aggiungi il protocollo `WCSessionDelegate`.

   ```objective-c
   #import <WatchConnectivity/WatchConnectivity.h> 
   @interface ExtensionDelegate : NSObject <WKExtensionDelegate, WCSessionDelegate>
   ```

1. Nel file di implementazione della classe dell&#39;extension delegate, importa `AdobeMobileLibrary`.

   ```objective-c
   #import “ADBMobile.h”
   ```

1. In `applicationDidFinishLaunching` dell&#39;extension delegate, configura `WCSession` prima di effettuare chiamate alla libreria `ADBMobile`.

   ```objective-c
   // check for session availability 
   if ([WCSession isSupported]) { 
       WCSession *session = [WCSession defaultSession]; 
       session.delegate = self; 
       [session activateSession]; 
   }
   ```

1. In `applicationDidFinishLaunching` dell&#39;extension delegate, inizializza l&#39;app Watch per l&#39;SDK.

   ```objective-c
   [ADBMobile initializeWatch];
   ```

1. Nell&#39;estensione delegate, implementa i metodi `session:didReceiveMessage:` e `session:didReceiveUserInfo:`.

   `syncSettings:` viene invocato nella libreria `ADBMobile`, che restituisce un valore booleano che indica se il dizionario deve essere utilizzato dalla libreria `ADBMobile`. Se restituisce `NO`, il messaggio non era stato avviato dall&#39;SDK Adobe.

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

* Per le app WatchKit, `a.RunMode` sarà impostato su `Extension`.
* Poiché le app WatchKit vengono eseguite sull&#39;orologio, le app segnalano correttamente il loro nome in `a.AppID`.
* Sulle app WatchOS2 non viene attivata alcuna chiamata &quot;lifecycle&quot; (ciclo di vita).
