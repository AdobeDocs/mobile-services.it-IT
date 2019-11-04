---
description: Se l'app apre contenuti web per dispositivi mobili, è necessario che i visitatori non vengano identificati separatamente quando passano dai contenuti nativi a quelli web.
seo-description: Se l'app apre contenuti web per dispositivi mobili, è necessario che i visitatori non vengano identificati separatamente quando passano dai contenuti nativi a quelli web.
seo-title: Tracciamento dei visitatori tra app e contenuti web per dispositivi mobili
solution: Experience Cloud,Analytics
title: Tracciamento dei visitatori tra app e contenuti web per dispositivi mobili
topic: Sviluppatore e implementazione
uuid: 2d951de6-3954-4379-a4ff-99b9695b9869
translation-type: ht
source-git-commit: 9257d6b6c2c14d0422cda65fcc9c677ac5ac47a9

---


# Tracciamento dei visitatori tra app e contenuti web per dispositivi mobili {#visitor-tracking-between-an-app-and-mobile-web}

Se l'app apre contenuti Web per dispositivi mobili, è necessario che i visitatori non vengano identificati separatamente quando passano dai contenuti nativi a quelli Web.

## ID visitatore nelle app

L'SDK per iOS genera un ID visitatore univoco quando viene installata un'app. Questo ID viene registrato nella memoria persistente sul dispositivo mobile e viene inviato con ogni hit. L'ID viene rimosso solo quando l'utente disinstalla l'app.

>[!TIP]
>
>Gli ID visitatore dell'app restano memorizzati anche da un aggiornamento all'altro.

## ID visitatore nei contenuti web per dispositivi mobili

Le implementazioni web per mobile tipiche usano lo stesso codice standard per Analytics `s_code.js` o `AppMeasurement.js` che viene utilizzato nei siti per desktop. Poiché le librerie JavaScript hanno metodi propri per la generazione di ID visitatore univoci, quando dall'app si aprono contenuti Web per dispositivi mobili viene generato un diverso ID visitatore.

Per usare lo stesso ID visitatore nell'app e nella pagina web per dispositivi mobili e passare nell'URL l'ID visitatore dell'app al contenuto web per dispositivi mobili:

## Implementa il tracciamento dei visitatori tra app e contenuti web per dispositivi mobili {#section_EDC91D6C67AD43999227707C2769C65D}

1. Aggiungi la libreria al tuo progetto e implementa le funzioni di ciclo di vita (lifecycle).

   Per ulteriori informazioni, consulta *Aggiungere l’SDK e il file di configurazione al progetto* in [Implementazione e ciclo di vita di base](/help/ios/getting-started/dev-qs.md).
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

## Risolvere i problemi di tracciamento dei visitatori {#section_C070AE85E3CE4E9893FD4F40E73F2C92}

### Non vedo `[ADBMobile visitorAppendToURL:]`.

Controlla che la versione dell'SDK di Adobe fornito in bundle con l'applicazione principale sia 4.12.0 o successiva.

### Non vedo gli Adobe ID nell'URL.

Verifica quanto segue:

* La stringa dell'URL che viene utilizzata per aprire la visualizzazione web è stata generata da  `[ADBMobile visitorAppendToURL:]`

* Gli Adobe ID sono codificati.

   Per verificare che gli ID siano aggiunti all'URL che si apre, individua il parametro di query `adobe_mc`.

### Il "mid" nell'app non è identico a quello della visualizzazione Web.*

Verifica quanto segue:

* La stringa dell'URL che viene utilizzata per aprire la visualizzazione web è stata generata da `[ADBMobile visitorAppendToURL:]`

   La stringa URL contiene i parametri Adobe.

   La stringa deve contenere `adobe_mc="SAMPLE_ID_DATA"`, dove `"SAMPLE_ID_DATA"` contiene gli ID generati nell'SDK di Adobe Mobile.

* La versione di `VisitorAPI.js` è 1.7.0 o successiva.

Se il problema persiste, contatta il servizio di assistenza clienti Adobe. Preparati a condividere un'applicazione di esempio e il sito associato, per consentire ad Adobe di verificare la validità dell'implementazione.
