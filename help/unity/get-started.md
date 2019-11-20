---
description: Questo plug-in consente di inviare chiamate ad Adobe Analytics dalle applicazioni Unity.
keywords: Unity
seo-description: Questo plug-in consente di inviare chiamate ad Adobe Analytics dalle applicazioni Unity.
seo-title: Plug-in di Unity per gli SDK iOS e Android 4.x
solution: Experience Cloud, Developer
title: Plug-in di Unity per gli SDK iOS e Android 4.x
uuid: 83289a73-982d-4472-a8c8-00b562dc80f5
translation-type: ht
source-git-commit: df4ff7128357a18c56d840eb5697f9c8813ad751

---


# Plug-in di Unity per gli SDK iOS e Android 4.x {#unity-plug-in-for-the-ios-and-android-x-sdks}

Questo plug-in consente di inviare chiamate ad Adobe Analytics dalle applicazioni Unity.

Ultimo aggiornamento: **12 novembre 2019**

## Guida introduttiva {#section_246D1F9B32ED47EABC41BDA8D0BD0CC7}

Scarica il file [ADBMobile.unitypackage](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases) da GitHub o Developer Connection.

Di seguito sono elencati i contenuti del `ADBMobile.unitypackage` file:

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


Cartelle facoltative: la cartella Demo contiene scene Unity e codice di esempio per ciascuno dei linguaggi di scripting supportati.

## Importazione del plug-in ADBMobile nel progetto Unity  {#section_35FB6DAE49FB4FA1ACB749A1F9480FE0}

1. Apri il progetto Unity.
1. Fai doppio clic su **[!UICONTROL ADBMobile.unitypackage]**.
1. Seleziona le cartelle da importare.

