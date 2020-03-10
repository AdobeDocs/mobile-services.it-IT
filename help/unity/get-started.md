---
description: Questo plug-in consente di inviare chiamate ad Adobe Analytics dalle applicazioni Unity.
keywords: Unity
seo-description: Questo plug-in consente di inviare chiamate ad Adobe Analytics dalle applicazioni Unity.
seo-title: Plug-in di Unity per gli SDK iOS e Android 4.x
solution: Marketing Cloud,Developer
title: Plug-in di Unity per gli SDK iOS e Android 4.x
uuid: 83289a73-982d-4472-a8c8-00b562dc80f5
translation-type: tm+mt
source-git-commit: 0d50c7e6674de33b8190e74c113ae010ff226e97

---


# Plug-in di Unity per gli SDK iOS e Android 4.x {#unity-plug-in-for-the-ios-and-android-x-sdks}

Questo plug-in consente di inviare chiamate ad Adobe Analytics dalle applicazioni Unity.

Last Update: **March 10, 2020**
* [Unity-v4.19.0](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases/tag/v4.19.0-Unity)

## Introduzione {#section_246D1F9B32ED47EABC41BDA8D0BD0CC7}

Scarica il file ADBMobile.unitypackage da GitHub.

Below are the contents of the `ADBMobile.unitypackage` file:

* Risorse (root)

   * ADBMobile

   * Plug-in

      * ADBMobile.cs
      * Android

         * adobeMobileLibrary-{version}.jar
         * AndroidManifest.xml
         * risorse

            * ADBMobileConfig.json
      * iOS

         * ADBMobile.h
         * ADBMobileConfig.json
         * ADBMobileWrapper.h
         * ADBMobileWrapper.mm
         * AdobeMobileLibrary.a


**Cartelle** facoltative: La cartella *Demo* contiene scene Unity e codice di esempio.

## Importazione del plug-in ADBMobile nel progetto Unity  {#section_35FB6DAE49FB4FA1ACB749A1F9480FE0}

1. Apri il progetto Unity.
1. Fai doppio clic su **[!UICONTROL ADBMobile.unitypackage]**.
1. Seleziona le cartelle da importare.
