---
description: Queste informazioni sono utili per gestire i messaggi in-app nelle app iOS.
seo-description: Queste informazioni sono utili per gestire i messaggi in-app nelle app iOS.
seo-title: Messaggistica in-app
solution: Experience Cloud,Analytics
title: Messaggistica in-app
topic: Sviluppatore e implementazione
uuid: 21fa6a94-bb7f-4c78-843b-a50f1974db22
translation-type: ht
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Messaggistica in-app {#in-app-messaging}

Queste informazioni sono utili per gestire i messaggi in-app nelle app iOS.

Per usare la funzione per messaggi in-app, **devi** disporre della versione SDK 4.2 o successiva.

Alcune considerazioni da tenere a mente:

* I messaggi e le regole che definiscono quando questi debbano essere visualizzati vengono creati in Adobe Mobile Services. Per ulteriori informazioni, consulta [Creare un messaggio in-app](/help/using/in-app-messaging/t-in-app-message/t-in-app-message.md).
* Affinché i messaggi in-app possano essere visualizzati, è necessario applicare all'SDK gli aggiornamenti descritti in questa sezione.

   >[!TIP]
   >
   >Puoi completare questi passaggi anche in assenza di messaggi definiti. Una volta definiti, i messaggi verranno inviati in modo dinamico all'app e visualizzati senza che sia necessario un aggiornamento dell'App Store.

## Abilitare i messaggi in-app {#section_79F984271C3B4366B7B04F864F4FF8C2}

1. Aggiungi la libreria al tuo progetto e implementa le funzioni di ciclo di vita (lifecycle).

   Per ulteriori informazioni, consulta *Aggiungere l’SDK e il file di configurazione al progetto* in [Implementazione e ciclo di vita di base](/help/ios/getting-started/requirements.md).

1. Importa la libreria:

   ```objective-c
   #import "ADBMobile.h"
   ```

1. Verifica che il file `ADBMobileConfig.json` contenga le impostazioni richieste per la messaggistica in-app.
1. Affinché i messaggi in-app possano essere aggiornati all'avvio in modo dinamico, l'oggetto `remotes` deve essere presente e configurato correttamente:

   ```js
   “messages”: [ 
       { 
           “messageId”: “de45c43c-37bf-441f-8cbd-cc3ba3469ebe”, 
           “template”: “fullscreen”, 
           “showOffline”: false, 
           “showRule”: “always”, 
           “endDate”: 2524730400, 
           “startDate”: 0, 
           “audiences”: [], 
           “triggers”: [], 
           “payload”: { // contents change depending on template 
               “html”: “<html>html code goes here</html>” 
           }, 
       }, 
       … 
   ] 
   “remotes” : { 
       “analytics.poi”: “https://assets.adobedtm.com/…/yourfile.json”, 
       “messages”: “https://assets.adobedtm.com/…/yourfile.json” 
   }
   ```

   >[!TIP]
   >
   >`messages` o `remotes` è obbligatorio.

   Se tali oggetti non sono configurati, scarica un file `ADBMobileConfig.json` aggiornato da Adobe Mobile Services. Per ulteriori informazioni, vedi [Implementazione e ciclo di vita di base](/help/ios/getting-started/requirements.md).

## Tracciamento dei messaggi in-app {#section_B85CDF6929564AAEA79338B55E5CB1E8}

Gli SDK per Mobile Services iOS tengono traccia delle metriche seguenti per i messaggi in-app:

* Per messaggi in-app a schermo intero e in stile avviso:

   * **[!UICONTROL Impression]**: quando l'utente attiva un messaggio in-app.
   * **[!UICONTROL Click-through]**: quando l'utente preme il pulsante **[!UICONTROL Click-through]**.
   * **[!UICONTROL Annulla]**: quando l'utente preme il pulsante **[!UICONTROL Annulla]**.

* Per i messaggi in-app personalizzati a schermo intero, nel contenuto HTML del messaggio deve essere presente il codice corretto per trasmettere informazioni alla funzione di tracciamento dell'SDK per i seguenti pulsanti:

   * Esempio di tracciamento **[!UICONTROL Click-through]** (reindirizzamento): `adbinapp://confirm/?url=https://www.yoursite.com`
   * **[!UICONTROL Esempio di tracciamento per annullamento]** (chiusura): `adbinapp://cancel`

* Per le notifiche locali (remote):

   * **[!UICONTROL Impression]**: quando l'utente attiva la notifica.
   * **[!UICONTROL Aperture]**: quando l'utente apre l'app da una notifica.
   Esempio di come includere il tracciamento delle operazioni di apertura:

   ```objective-c
   - (BOOL) application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions { 
     // handle local notification click-throughs for iOS 10 and older 
     NSDictionary *localNotificationDictionary = launchOptions[UIApplicationLaunchOptionsLocalNotificationKey]; 
     if ([localNotificationDictionary isKindOfClass:[NSDictionary class]]) { 
          [ADBMobile trackLocalNotificationClickThrough:localNotificationDictionary]; 
     } 
   } 
   - (void) application:(UIApplication *)application didReceiveLocalNotification:(UILocalNotification *)notification { 
      [ADBMobile trackLocalNotificationClickThrough:notification.userInfo]; 
   }
   ```

## Immagine di fallback locale {#section_DEACC1CE549B4573B556A44A52409941}

Quando crei un messaggio a schermo intero in Adobe Mobile Services, puoi facoltativamente specificare un'immagine di fallback. Qualora non sia possibile recuperare l'immagine del messaggio dal web, l'SDK tenta di caricare un'immagine con lo stesso nome dal pacchetto dell'applicazione. In questo modo, anche se l'utente è offline o se l'immagine non è accessibile, sarà comunque possibile visualizzare il messaggio nella sua forma originale.

Il nome della risorsa da usare come immagine di fallback deve essere specificato quando si configura il messaggio in Adobe Mobile Services.

>[!IMPORTANT]
>
>Assicurati che la risorsa specificata sia disponibile.

