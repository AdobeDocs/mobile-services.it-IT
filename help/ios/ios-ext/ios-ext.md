---
description: L'uso di un'estensione iOS facilita la raccolta dei dati di utilizzo dalle app per Apple Watch (WatchOS 1), dai widget Oggi, dai widget per ritocco foto e da altre app di estensione iOS.
seo-description: L'uso di un'estensione iOS facilita la raccolta dei dati di utilizzo dalle app per Apple Watch (WatchOS 1), dai widget Oggi, dai widget per ritocco foto e da altre app di estensione iOS.
seo-title: Implementazione di un'estensione iOS
solution: Marketing Cloud,Analytics
title: Implementazione di un'estensione iOS
topic: Sviluppatore e implementazione
uuid: 8afc03fe-403e-4643-ada1-30e403ede238
translation-type: tm+mt
source-git-commit: 718e336b9002fe3d5282697d4302d12a89297181

---


# iOS extension implementation {#ios-extension-implementation}

L'uso di un'estensione iOS facilita la raccolta dei dati di utilizzo dalle app per Apple Watch (WatchOS 1), dai widget Oggi, dai widget per ritocco foto e da altre app di estensione iOS.

## Nuova versione SDK per Adobe Experience Platform Mobile

Stai cercando informazioni e documentazione sull’SDK per dispositivi mobili di Adobe Experience Platform? Fai clic [qui](https://aep-sdks.gitbook.io/docs/) per la documentazione più recente.

A settembre 2018 è stata rilasciata una nuova versione principale dell’SDK. Questi nuovi SDK per dispositivi mobili di Adobe Experience Platform sono configurabili tramite [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* Per iniziare, vai ad Adobe Experience Platform Launch.
* Per visualizzare cosa è compreso negli archivi Experience Platform SDK, passa a [Github: SDK di Adobe Experience Platform](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

## Recommendations for using the iOS SDK instead of your wrapper {#section_97577331FD9E4FFBBE05D402C67AEE69}

>[!IMPORTANT]
>
>È consigliabile utilizzare l’SDK per iOS invece del wrapper.

Apple fornisce un set di API che permette all'app Watch di comunicare con l'app contenitore inviando richieste e ricevendo risposte. Benché sia possibile inviare dati di tracciamento come dizionario dall'app Watch all'app contenitore e invocare qualsiasi metodo di tracciamento nell'app contenitore per l'invio dei dati, questa soluzione presenta alcune limitazioni.

In most cases when a user is using the Watch app, the containing app is running in the background, and it is only safe to call `TrackActionInBackground`, `TrackLocation`, and `TrackBeacon`. L'invocazione di altri metodi di tracciamento interferisce con i dati del ciclo di vita; pertanto, per inviare i dati dall'app Watch, usa solo questi tre metodi.

Anche se questi tre metodi di tracciamento soddisfano le tue esigenze, usa comunque l'SDK per iOS: l'SDK per app Watch, infatti, include tutte le funzioni Mobile eccetto quelle per i messaggi in-app.

## Getting started {#section_D0BE4F780C9C4CD8ADD2AD4EE0BD5FD4}

>[!IMPORTANT]
>
>Accertatevi di disporre di un progetto con almeno le seguenti destinazioni:
>
>* Una destinazione che dovrà contenere l'app.
>* Una destinazione per l'estensione.
>



Se lavori su un'app WatchKit, è necessaria anche una terza destinazione. For more information on developing for Apple Watch, see [Developing for Apple Watch](https://developer.apple.com/library/ios/documentation/General/Conceptual/WatchKitProgrammingGuide/index.html#//apple_ref/doc/uid/TP40014969-CH8-SW1).

## Configurare l'app contenitore {#section_0BAB0842E4C04A62B5E03DFC4BA77851}

Completa i seguenti passaggi nel progetto Xcode:

1. Trascina nel progetto la cartella AdobeMobileLibrary.
1. Ensure that the `ADBMobileConfig.json` file is a member of the containing app's target.
1. Nella scheda **[!UICONTROL Fasi build]** della destinazione dell'app contenitore, espandi la sezione **Collega binario a librerie]e aggiungi le seguenti librerie:[!UICONTROL **

   * `AdobeMobileLibrary.a`
   * `libsqlite3.dylib`
   * `SystemConfiguration.framework`

1. Open the **[!UICONTROL Capabilities]** tab of the containing app's target, enable **[!UICONTROL App Groups]**, and add a new app group (for example, `group.com.adobe.testAp`).

1. Nell'app delegate, imposta il gruppo di app in `application:didFinishLaunchingWithOptions` prima di eseguire qualsiasi interazione con la libreria Adobe Mobile:

   ```objective-c
   [ADBMobile 
         setAppGroup:@"group.com.adobe.testApp"];
   ```

1. Conferma che l'app possa essere generata senza errori imprevisti.

## Configura l'estensione {#section_28C994B7892340AC8D1F07AF26FF3946}

1. Ensure that the `ADBMobileConfig.json` file is a member of the extension's target.
1. Nella scheda **[!UICONTROL Fasi build]** della destinazione dell'estensione, espandi la sezione **Collega binario a librerie]e aggiungi le seguenti librerie:[!UICONTROL **

   * `AdobeMobileLibrary_Extension.a`
   * `libsqlite3.dylib`
   * `SystemConfiguration.framework`

1. Open the **[!UICONTROL Capabilities]** tab of the extension's target, enable **[!UICONTROL App Groups]**, and select the app group that you added in step 4 of *Configuring the Containing App* above.

1. In your InterfaceController, set the app group in `awakeWithContext:` before making any other interactions with the Adobe Mobile library:

   ```objective-c
   [ADBMobile 
         setAppGroup:@"group.com.adobe.testApp"];
   ```

1. Conferma che l'app possa essere generata senza errori imprevisti.

## Additional notes {#section_21497E81231549CB9F164DEECFF5BA0D}

Seguono alcune considerazioni da tenere a mente:

* È stato aggiunto il valore di dati di contesto aggiuntivo `a.RunMode` per indicare se i dati provengono dall'app contenitore o dall'estensione:

   * `a.RunMode = Application`

      Questo valore significa che l'hit proviene dall'app contenitore.
   * `a.RunMode = Extension`

      Questo valore significa che l'hit proviene dall'estensione.

* Se esegui l'aggiornamento da una precedente versione dell'SDK, quando l'app contenitore viene avviata, tutte le impostazioni utente predefinite e tutti i file memorizzati nella cache vengono automaticamente migrati dalla cartella dell'app contenitore alla cartella condivisa del gruppo di app.
* Se l'app contenitore non viene mai avviata, gli hit provenienti dall'estensione vengono eliminati.
* L'app contenitore e l'app estensione devono avere gli stessi numeri di versione e di build.
* Sulle app di estensione iOS non viene attivata alcuna chiamata "lifecycle".

