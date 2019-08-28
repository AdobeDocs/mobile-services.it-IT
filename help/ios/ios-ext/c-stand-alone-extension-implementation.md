---
description: A partire da iOS 10, Apple consente di creare un'estensione "autonoma" che può essere distribuita senza la relativa app contenitore. Con questa estensione, non è necessario un gruppo di app e i dati non devono essere condivisi con alcuna app contenitore.
seo-description: A partire da iOS 10, Apple consente di creare un'estensione "autonoma" che può essere distribuita senza la relativa app contenitore. Con questa estensione, non è necessario un gruppo di app e i dati non devono essere condivisi con alcuna app contenitore.
seo-title: Implementazione di un'estensione autonoma
solution: Marketing Cloud, Analytics
title: Implementazione di un'estensione autonoma
topic: Sviluppatore e implementazione
uuid: 9 b 47 f 082-b 78 f -4611-968 d -014 c 32 ede 6 bc
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Stand-alone extension implementation {#stand-alone-extension-implementation}

A partire da iOS 10, Apple consente di creare un'estensione "autonoma" che può essere distribuita senza la relativa app contenitore. Con questa estensione, non è necessario un gruppo di app e i dati non devono essere condivisi con alcuna app contenitore.

>[!IMPORTANT]
>
>Per utilizzare le estensioni autonome, devi disporre della versione SDK di Mobile 4.13.0 o successiva.

## Configurare l'estensione autonoma da usare con l'SDK {#section_B7A84603BB9D4B48BB46BE8D3B9E3CF0}

Per configurare l'estensione autonoma:

1. Ensure that the `ADBMobileConfig.json` file is a member of your extension's target.
1. Collega le librerie e i framework seguenti:

   * `AdobeMobileLibrary_Extension.a`
   * `libsqlite3.tbd`
   * `SystemConfiguration.framework`

1. Nel controller della vista principale dell'estensione, imposta il tipo di estensione su `ADBMobileAppExtensionTypeStandAlone` nell'SDK prima di completare eventuali attività relative all'SDK.

   ```objective-c
   [ADBMobile setAppExtensionType:ADBMobileAppExtensionTypeStandAlone];
   ```

1. Conferma che l'app possa essere generata senza errori imprevisti.

## Additional notes {#section_1C9A55E2309A44BF842310F735702B3D}

Seguono alcune informazioni aggiuntive:

* È stato aggiunto il valore di dati di contesto aggiuntivo `a.RunMode` per indicare se i dati provengono dall'app contenitore o dall'estensione:

   * `a.RunMode = Application`

      Questo valore significa che l'hit proviene dall'app contenitore.
   * `a.RunMode = Extension`

      Questo valore significa che l'hit proviene dall'estensione.

* Sulle app di estensione iOS non viene attivata alcuna chiamata "lifecycle".

