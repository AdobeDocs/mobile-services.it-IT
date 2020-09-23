---
description: A partire da iOS 10, Apple consente di creare un’estensione denominata estensione autonoma che può essere distribuita senza un’app contenitore. Con questa estensione, non è necessario un gruppo di app, in quanto non esiste un'app contenitore con cui condividere i dati.
seo-description: A partire da iOS 10, Apple consente di creare un’estensione denominata estensione autonoma che può essere distribuita senza un’app contenitore. Con questa estensione, non è necessario un gruppo di app, in quanto non esiste un'app contenitore con cui condividere i dati.
seo-title: Implementazione di un'estensione autonoma
solution: Experience Cloud,Analytics
title: Implementazione di un'estensione autonoma
topic: Developer and implementation
uuid: 9b47f082-b78f-4611-968d-014c32ede6bc
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '268'
ht-degree: 44%

---


# Implementazione di un&#39;estensione autonoma {#stand-alone-extension-implementation}

A partire da iOS 10, Apple consente di creare un’estensione denominata estensione autonoma che può essere distribuita senza un’app contenitore. Con questa estensione, non è necessario un gruppo di app, in quanto non esiste un&#39;app contenitore con cui condividere i dati.

>[!IMPORTANT]
>
>Per usare un’estensione autonoma, devi disporre della versione SDK Mobile 4.13.0 o successiva.

## Configurare l&#39;estensione autonoma da usare con l&#39;SDK {#section_B7A84603BB9D4B48BB46BE8D3B9E3CF0}

Per configurare l&#39;estensione autonoma:

1. Assicurati che il file `ADBMobileConfig.json` sia un membro della destinazione della tua estensione.
1. Collega le librerie e i framework seguenti:

   * `AdobeMobileLibrary_Extension.a`
   * `libsqlite3.tbd`
   * `SystemConfiguration.framework`

1. Nel controller della vista principale dell&#39;estensione, imposta il tipo di estensione su `ADBMobileAppExtensionTypeStandAlone` nell&#39;SDK prima di completare eventuali attività relative all&#39;SDK.

   ```objective-c
   [ADBMobile setAppExtensionType:ADBMobileAppExtensionTypeStandAlone];
   ```

1. Conferma che l&#39;app possa essere generata senza errori imprevisti.

## Note aggiuntive {#section_1C9A55E2309A44BF842310F735702B3D}

Seguono alcune informazioni aggiuntive:

* È stato aggiunto il valore di dati di contesto aggiuntivo `a.RunMode` per indicare se i dati provengono dall&#39;app contenitore o dall&#39;estensione:

   * `a.RunMode = Application`

      Questo valore significa che l&#39;hit proviene dall&#39;app contenitore.
   * `a.RunMode = Extension`

      Questo valore significa che l’hit proviene dall’estensione.

* Sulle app di estensione iOS non viene attivata alcuna chiamata &quot;lifecycle&quot; (ciclo di vita).

