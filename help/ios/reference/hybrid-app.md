---
description: Se l'app apre contenuti Web per dispositivi mobili, è necessario che i visitatori non vengano identificati separatamente quando passano dai contenuti nativi a quelli Web.
seo-description: Se l'app apre contenuti Web per dispositivi mobili, è necessario che i visitatori non vengano identificati separatamente quando passano dai contenuti nativi a quelli Web.
seo-title: Tracciamento dei visitatori tra app e contenuti web per dispositivi mobili
solution: Marketing Cloud, Analytics
title: Tracciamento dei visitatori tra app e contenuti web per dispositivi mobili
topic: Sviluppatore e implementazione
uuid: 2 d 951 de 6-3954-4379-a 4 ff -99 b 9695 b 9869
translation-type: tm+mt
source-git-commit: 9257d6b6c2c14d0422cda65fcc9c677ac5ac47a9

---


# Visitor tracking between an app and mobile web  {#visitor-tracking-between-an-app-and-mobile-web}

Se l'app apre contenuti Web per dispositivi mobili, è necessario che i visitatori non vengano identificati separatamente quando passano dai contenuti nativi a quelli Web.

## ID visitatore nelle app

L'SDK per iOS genera un ID visitatore univoco quando viene installata un'app. Questo ID viene registrato nella memoria persistente sul dispositivo mobile e viene inviato con ogni hit. L'ID viene rimosso solo quando l'utente disinstalla l'app..

>[!TIP]
>
>Gli ID visitatore dell'app restano invariati.

## ID visitatore nel Web per dispositivi mobili

Le implementazioni web per mobile tipiche usano lo stesso codice standard per Analytics `s_code.js` o `AppMeasurement.js` che viene utilizzato nei siti per desktop. Poiché le librerie JavaScript hanno metodi propri per la generazione di ID visitatore univoci, quando dall'app si aprono contenuti Web per dispositivi mobili viene generato un diverso ID visitatore.

Per utilizzare lo stesso ID visitatore nell'app e nel Web per dispositivi mobili e passare l'ID visitatore dell'app al Web per dispositivi mobili nell'URL:

## Implement visitor tracking between an app and mobile web {#section_EDC91D6C67AD43999227707C2769C65D}

1. Aggiungi la libreria al tuo progetto e implementa le funzioni di ciclo di vita (lifecycle).

   Per ulteriori informazioni, vedi *Aggiungere l'SDK e il file di configurazione al progetto* in [Implementazione e ciclo di vita di base](/help/ios/getting-started/dev-qs.md).
1. Per aggiungere le informazioni sul visitatore all'URL con cui si apre la visualizzazione Web, invoca `visitorAppendToURL`:

   ```objective-c
   NSURL *url = [NSURL URLWithString:@”https://www.mydomain.com/index.php"]; 
   NSURL *urlWithVisitorData = [ADBMobile visitorAppendToURL:url]; 
   [[UIApplication sharedApplication] openURL:urlWithVisitorData];
   ```

   In alternativa, avviando l'SDK versione 4.16.0, puoi invocare `visitorGetUrlVariablesAsync:` e generare il tuo URL:

   ```objective-c
   NSString *urlString = @"https://www.mydomain.com/index.php"; 
   [ADBMobile visitorGetUrlVariablesAsync:^(NSString * _Nullable urlVariables) { 
       NSString *urlStringWithVisitorData = [NSString stringWithFormat:@"%@?%@", urlString, urlVariables]; 
       NSURL *urlWithVisitorData = [NSURL URLWithString:urlStringWithVisitorData]; 
       [[UIApplication sharedApplication] openURL:urlWithVisitorData options:@{} completionHandler:^(BOOL success) { 
           // handle openURL success 
       }]; 
   }];
   ```

Invece di inviare ad Adobe la richiesta di un nuovo ID, il codice del servizio ID sul dominio di destinazione estrae l'identificatore MID dall'URL. Il codice del servizio ID sulla pagina di destinazione usa quindi questo stesso identificatore MID per tenere traccia del visitatore.

Negli hit da contenuti Web per dispositivi mobili, verifica che il parametro `mid` sia presente in ciascun hit e che il suo valore corrisponda al `mid` inviato dal codice dell'app.

## Risoluzione dei problemi del tracciamento dei visitatori {#section_C070AE85E3CE4E9893FD4F40E73F2C92}

### I do not see `[ADBMobile visitorAppendToURL:]`.

Controlla che la versione dell'SDK di Adobe fornito in bundle con l'applicazione principale sia 4.12.0 o successiva.

### Non vedo gli Adobe ID nell'URL.

Verifica quanto segue:

* La stringa dell'URL che viene utilizzata per aprire la visualizzazione web è stata generata da  `[ADBMobile visitorAppendToURL:]`

* Gli Adobe ID sono codificati.

   To verify that IDs are appended to the URL that is being opened, look for the `adobe_mc` query parameter.

### Il "mid" nell'app non è identico a quello della visualizzazione Web.*

Verifica quanto segue:

* La stringa dell'URL che viene utilizzata per aprire la visualizzazione web è stata generata da `[ADBMobile visitorAppendToURL:]`

   La stringa URL contiene i parametri Adobe.

   The string should contain `adobe_mc="SAMPLE_ID_DATA"` where `"SAMPLE_ID_DATA"` contains the IDs that are generated in the Adobe Mobile SDK.

* La versione di `VisitorAPI.js` è 1.7.0 o successiva.

Se il problema persiste, contatta il servizio di assistenza clienti Adobe. Preparati a condividere un'applicazione di esempio e il sito associato, per consentire ad Adobe di verificare la validità dell'implementazione.
