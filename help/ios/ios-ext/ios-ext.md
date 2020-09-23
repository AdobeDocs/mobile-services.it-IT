---
description: L'uso di un'estensione iOS facilita la raccolta dei dati di utilizzo dalle app per Apple Watch (WatchOS 1), dai widget Oggi, dai widget per ritocco foto e da altre app di estensione iOS.
seo-description: L'uso di un'estensione iOS facilita la raccolta dei dati di utilizzo dalle app per Apple Watch (WatchOS 1), dai widget Oggi, dai widget per ritocco foto e da altre app di estensione iOS.
seo-title: Implementazione di un'estensione iOS
solution: Experience Cloud,Analytics
title: Implementazione di un'estensione iOS
topic: Developer and implementation
uuid: 8afc03fe-403e-4643-ada1-30e403ede238
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '721'
ht-degree: 76%

---


# Implementazione di un&#39;estensione iOS {#ios-extension-implementation}

L&#39;uso di un&#39;estensione iOS facilita la raccolta dei dati di utilizzo dalle app per Apple Watch (WatchOS 1), dai widget Oggi, dai widget per ritocco foto e da altre app di estensione iOS.

## Nuova versione dell&#39;SDK per dispositivi mobili di Adobe Experience Platform

Hai bisogno di informazioni e documentazione relative all’SDK per dispositivi mobili di Adobe Experience Platform? Fai clic [qui](https://aep-sdks.gitbook.io/docs/) per la documentazione più recente.

A settembre 2018 è stata rilasciata una nuova versione principale dell&#39;SDK. Questi nuovi SDK per dispositivi mobili di Adobe Experience Platform sono configurabili tramite [Experience Platform Launch](https://www.adobe.com/it/experience-platform/launch.html).

* Per iniziare, vai su Adobe Experience Platform Launch.
* Per visualizzare cosa è compreso negli archivi Experience Platform SDK, passa a [Github: SDK di Adobe Experience Platform](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

## Raccomandazioni per l&#39;utilizzo dell&#39;SDK per iOS invece del wrapper {#section_97577331FD9E4FFBBE05D402C67AEE69}

>[!IMPORTANT]
>
>Consigliamo vivamente di usare l&#39;SDK per iOS invece del wrapper.

Apple fornisce un set di API che consente all’app Watch di comunicare con l’app contenitore inviando richieste all’app contenitore e ricevendo le risposte. Sebbene sia possibile inviare i dati di tracciamento come dizionario dall’app Watch all’app contenitore e invocare qualsiasi metodo di tracciamento nell’app contenitore per inviare i dati, questa soluzione presenta delle limitazioni.

Nella maggior parte dei casi, quando un utente usa un&#39;app Watch, l&#39;app contenitore viene eseguita in background e le sole chiamate sicure sono `TrackLocation`, `TrackActionInBackground` e `TrackBeacon`. L&#39;invocazione di altri metodi di tracciamento interferisce con i dati del ciclo di vita; pertanto, per inviare i dati dall&#39;app Watch, usa solo questi tre metodi.

Anche se questi tre metodi di tracciamento soddisfano le tue esigenze, usa comunque l&#39;SDK per iOS: l&#39;SDK per app Watch, infatti, include tutte le funzioni Mobile eccetto quelle per i messaggi in-app.

## Guida introduttiva {#section_D0BE4F780C9C4CD8ADD2AD4EE0BD5FD4}

>[!IMPORTANT]
>
>Assicurati di avere un progetto con almeno le seguenti destinazioni:
>
>* Una destinazione per contenere l&#39;app.
>* Una destinazione per l&#39;estensione.

>



Se state lavorando su un&#39;app WatchKit, dovreste avere una terza destinazione. Per ulteriori informazioni sullo sviluppo per Apple Watch, consulta [Developing for Apple Watch](https://developer.apple.com/library/ios/documentation/General/Conceptual/WatchKitProgrammingGuide/index.html#//apple_ref/doc/uid/TP40014969-CH8-SW1).

## Configurare l&#39;app contenitore {#section_0BAB0842E4C04A62B5E03DFC4BA77851}

Completa i seguenti passaggi nel progetto Xcode:

1. Trascina nel progetto la cartella AdobeMobileLibrary.
1. Assicurati che il file `ADBMobileConfig.json` sia un membro della destinazione dell&#39;app contenitore.
1. Nella scheda **[!UICONTROL Fasi build]** della destinazione dell&#39;app contenitore, espandi la sezione **[!UICONTROL Collega binario a librerie]** e aggiungi le seguenti librerie:

   * `AdobeMobileLibrary.a`
   * `libsqlite3.dylib`
   * `SystemConfiguration.framework`

1. Apri la scheda **[!UICONTROL Capacità]** della destinazione dell&#39;app contenitore, abilita **[!UICONTROL Gruppi app]** e aggiungi un nuovo gruppo di app (ad esempio, `group.com.adobe.testAp`).

1. Nell&#39;app delegate, imposta il gruppo di app in `application:didFinishLaunchingWithOptions` prima di eseguire qualsiasi interazione con la libreria Adobe Mobile:

   ```objective-c
   [ADBMobile 
         setAppGroup:@"group.com.adobe.testApp"];
   ```

1. Conferma che l&#39;app possa essere generata senza errori imprevisti.

## Configura l&#39;estensione {#section_28C994B7892340AC8D1F07AF26FF3946}

1. Assicurati che il file `ADBMobileConfig.json` sia un membro della destinazione della tua estensione.
1. Nella scheda **[!UICONTROL Fasi build]** della destinazione dell&#39;estensione, espandi la sezione **[!UICONTROL Collega binario a librerie]** e aggiungi le seguenti librerie:

   * `AdobeMobileLibrary_Extension.a`
   * `libsqlite3.dylib`
   * `SystemConfiguration.framework`

1. Apri la scheda **[!UICONTROL Capacità]** della destinazione dell&#39;estensione, abilita **[!UICONTROL Gruppi di app]** e seleziona il gruppo di app aggiunto al passaggio 4 della precedente sezione *Configurazione dell&#39;app contenitore*.

1. In InterfaceController, imposta il gruppo di app in `awakeWithContext:` prima di eseguire qualsiasi altra interazione con la libreria Adobe Mobile:

   ```objective-c
   [ADBMobile 
         setAppGroup:@"group.com.adobe.testApp"];
   ```

1. Conferma che l&#39;app possa essere generata senza errori imprevisti.

## Note aggiuntive {#section_21497E81231549CB9F164DEECFF5BA0D}

Seguono alcune considerazioni da tenere a mente:

* È stato aggiunto il valore di dati di contesto aggiuntivo `a.RunMode` per indicare se i dati provengono dall&#39;app contenitore o dall&#39;estensione:

   * `a.RunMode = Application`

      Questo valore significa che l&#39;hit proviene dall&#39;app contenitore.
   * `a.RunMode = Extension`

      Questo valore significa che l’hit proviene dall’estensione.

* Se esegui l’aggiornamento da una versione precedente dell’SDK, quando viene avviata l’app contenitore,  Adobe migra automaticamente tutti i valori predefiniti utente e i file memorizzati nella cache dalla cartella dell’app contenitore alla cartella condivisa del gruppo di app.
* Se l’app contenitore non viene mai avviata, gli hit dell’estensione vengono scartati.
* Il numero di versione e di build deve essere lo stesso tra l&#39;app contenitore e l&#39;app di estensione.
* Sulle app di estensione iOS non viene attivata alcuna chiamata &quot;lifecycle&quot; (ciclo di vita).

