---
description: Questo plug-in consente di inviare chiamate ad Adobe Analytics dalle applicazioni Unity.
keywords: Unity
seo-description: Questo plug-in consente di inviare chiamate ad Adobe Analytics dalle applicazioni Unity.
seo-title: Plug-in di Unity per gli SDK iOS e Android 4.x
solution: Marketing Cloud, Sviluppatore
title: Plug-in di Unity per gli SDK iOS e Android 4.x
uuid: 83289 a 73-982 d -4472-a 8 c 8-00 b 562 dc 80 f 5
translation-type: tm+mt
source-git-commit: 5fbba02eb61679344f638b6465e47b0d9ae5a988

---


# Plug-in di Unity per gli SDK iOS e Android 4.x {#unity-plug-in-for-the-ios-and-android-x-sdks}

Questo plug-in consente di inviare chiamate ad Adobe Analytics dalle applicazioni Unity.

Ultimo aggiornamento: **20 ottobre 2016**

## Getting started {#section_246D1F9B32ED47EABC41BDA8D0BD0CC7}

Scarica il file [ADBMobile.unitypackage](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases) da GitHub o Developer Connection.

I contenuti del `ADBMobile.unitypackage` file sono:

* Risorse (root)

   * ADBMobile

      * Demo

         * ADBMobileDemo.cs
         * BooDemo.boo
         * BooScene.unity
         * CSharpScene.unity
         * JavaScriptDemo.js
         * JavaScriptScene.unity
         * SecondScene.unity
         * SecondSceneScript.cs
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

## Importazione del plug-in ADBMobile nel progetto Unity {#section_35FB6DAE49FB4FA1ACB749A1F9480FE0}

1. Apri il progetto Unity.
1. Fai doppio clic su **[!UICONTROL ADBMobile.unitypackage]**.
1. Seleziona le cartelle da importare.

