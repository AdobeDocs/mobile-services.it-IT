---
description: Queste informazioni sono utili per implementare la libreria iOS e raccogliere metriche sul ciclo di vita, come avvii, aggiornamenti, sessioni, utenti attivi e così via.
seo-description: Queste informazioni sono utili per implementare la libreria iOS e raccogliere metriche sul ciclo di vita, come avvii, aggiornamenti, sessioni, utenti attivi e così via.
seo-title: Implementazione e ciclo di vita di base
solution: Marketing Cloud, Analytics
title: Implementazione e ciclo di vita di base
topic: Sviluppatore e implementazione
uuid: 96 d 06325-e 424-4770-8659-4 b 5431318 ee 3
translation-type: tm+mt
source-git-commit: f39c18e48dc72e0ed8e8e35d962a1ae028055b87

---


# Core implementation and lifecycle {#core-implementation-and-lifecycle}

Queste informazioni sono utili per implementare la libreria iOS e raccogliere metriche sul ciclo di vita, come avvii, aggiornamenti, sessioni, utenti attivi e così via.

## Scaricare l'SDK {#section_99FE1A17A36D4A2C943939023CF6265C}

>[!IMPORTANT]
>
>To download the SDKs, you **must** use iOS 6 or later.

**Prerequisito**

Prima di scaricare l'SDK, completa i passaggi descritti in *Crea una suite di rapporti* in [implementazione e ciclo di vita core](/help/ios/getting-started/requirements.md) per impostare una suite di rapporti per la fase di sviluppo e scaricare una versione precompilata del file di configurazione.

Per scaricare l'SDK:

1. Download, unzip the `[Your_App_Name_]AdobeMobileLibrary-4.*-iOS.zip` file and verify that you have the following software components:

   * `ADBMobile.h`, file di intestazione Objective-C usato per iOS AppMeasurement.
   * `ADBMobileConfig.json`, file di configurazione dell’SDK personalizzato per la tua app.
   * `AdobeMobileLibrary.a`, fat binary abilitato per bitcode contenente le build della libreria per dispositivi (armv 7, armv 7 s, arm 64) e simulatori (i 386, x 86_ 64) iOS.

      Se la destinazione sarà un'app iOS, il fat binary deve essere collegato.

   * `AdobeMobileLibrary_Extension.a`, fat binary abilitato per bitcode contenente le build della libreria per dispositivi (armv7, armv7s, arm64) e simulatori (i386, x86_64) iOS.

      Se la destinazione sarà un'estensione iOS, il fat binary deve essere collegato.

   * `AdobeMobileLibrary_Watch.a`, fat binary abilitato per bitcode contenente le build della libreria per dispositivi (armv7k) e simulatori (i386, x86_64) Apple Watch.

      Se la destinazione sarà un'app estensione Apple Watch (watchOS 2), il fat binary deve essere collegato.

   * `AdobeMobileLibrary_TV.a`, fat binary abilitato per bitcode contenente le build della libreria per dispositivi (arm 64) e simulatore (x 86_ 64) Apple TV.

      Se la destinazione sarà un'app estensione Apple TV (tvOS), il fat binary deve essere collegato.

>[!IMPORTANT]
>
>If you download the SDK outside the Adobe Mobile services UI, the `ADBMobileConfig.json` file must be manually configured. If you are new to Analytics and the Mobile SDK, see [Before You Start](/help/ios/getting-started/requirements.md) to set up a development report suite and download a pre-populated version of the configuration file.

## Add the SDK and config file to your project {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. Avvia l'IDE di Xcode e apri la tua app.
1. In Navigatore progetti, trascina la cartella `AdobeMobileLibrary` e rilasciala sotto al tuo progetto.
1. Verifica quanto segue:

   * La casella **[!UICONTROL Copia elementi se necessario]deve essere selezionata.**
   * **[!UICONTROL Crea gruppi]** deve essere selezionato.
   * Nessuna delle caselle della sezione **[!UICONTROL Aggiungi a destinazioni]deve essere selezionata.**
   ![](assets/step_3.png)

1. Fai clic su **[!UICONTROL Fine]**.
1. In **[!UICONTROL Project Navigator]**, select **[!UICONTROL`ADBMobileConfig.json`]**.
1. In **[!UICONTROL File Inspector]**, add the JSON file to any targets in your project that will use the Adobe SDK.

   ![](assets/step_4.png)

1. In **[!UICONTROL Project Navigator]**, complete the following steps:

   1. Fai clic sull'app.
   1. Nella scheda **[!UICONTROL Generale]**, seleziona le destinazioni e collega le librerie e i framework necessari nelle sezioni **[!UICONTROL Framework collegati]e** Librerie **.**
   * **Destinazioni di app iOS**
      * `SystemConfiguration.framework`
      * `libsqlite3.0.tbd`
      * `AdobeMobileLibrary.a`
   * **Destinazioni di estensioni iOS**

      * `SystemConfiguration.framework`
      * `libsqlite3.0.tbd`
      * `AdobeMobileLibrary\_Extension.a`
   * **Destinazioni Apple Watch (watchOS 2)**

      * `libsqlite3.0.tbd`
      * `AdobeMobileLibrary\_Watch.a`
   * **Destinazioni Apple TV (tvOS)**

      * `SystemConfiguration.framework`
      * `libsqlite3.0.tbd`
      * `AdobeMobileLibrary\_TV.a`
   >[!CAUTION]
   >
   > Linking more than one `AdobeMobileLibrary*.a` file in the same target will result in unexpected behavior or the inability to build.

1. Conferma che l'app possa essere generata senza errori.

## Implement lifecycle metrics {#section_532702562A7A43809407C9A2CBA80E1E}

>[!IMPORTANT]
>
>iOS will send lifecycle information with or without calling `collectlifecycledata`, and `collectlifecycledata` is only a way to initiate lifecycle earlier in the application's launch sequence.

After you enable lifecycle, each time your app is launched, one hit is sent to measure launches, upgrades, sessions, engaged users, and other [Lifecycle Metrics](/help/ios/metrics.md).

Aggiungi una `collectLifecycleData`/ `collectLifecycleDataWithAdditionalData` chiamata in `application:didFinishLaunchingWithOptions`:

```objective-c
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions { 
 [ADBMobile collectLifecycleData]; 
    return YES; 
}
```

### Includere dati aggiuntivi con le chiamate lifecycle

Per includere dati aggiuntivi con le chiamate delle metriche "lifecycle", usa `collectLifecycleDataWithAdditionalData`:

>[!IMPORTANT]
>
>Any data that is passed to the SDK through `collectLifecycleDataWithAdditionalData:` is persisted in `NSUserDefaults` by the SDK. L'SDK elimina dal parametro `NSDictionary` i valori che non sono di tipo `NSString` o `NSNumber`.

```objective-c
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions { 
    NSMutableDictionary *contextData = [NSMutableDictionary dictionary]; 
    [contextData setObject:@"Game" forKey:@"myapp.category"]; 
    [ADBMobile collectLifecycleDataWithAdditionalData:contextData]; 
    return YES; 
}
```

Eventuali valori di dati di contesto aggiuntivi inviati con `collectLifecycleDataWithAdditionalData` devono essere mappati su variabili personalizzate in Adobe Mobile Services:

![](assets/map-variable-lifecycle.png)

Altre metriche "lifecycle" vengono raccolte automaticamente. Per ulteriori informazioni, vedi [Metriche del ciclo di vita](/help/ios/metrics.md).

## Passi successivi {#section_A24DC703359D4B5C8F493D6421306FD3}

Completa le attività seguenti:

* [Tracciare gli stati dell'app](/help/ios/analytics-main/states.md)
* [Tracciare le azioni eseguite nell'app](/help/ios/analytics-main/actions.md)
