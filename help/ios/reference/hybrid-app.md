---
description: Se l'app apre contenuti web per dispositivi mobili, è necessario che i visitatori non vengano identificati separatamente quando passano dai contenuti nativi a quelli web.
seo-description: Se l'app apre contenuti web per dispositivi mobili, è necessario che i visitatori non vengano identificati separatamente quando passano dai contenuti nativi a quelli web.
seo-title: Tracciamento dei visitatori tra app e contenuti web per dispositivi mobili
solution: Experience Cloud,Analytics
title: Tracciamento dei visitatori tra app e contenuti web per dispositivi mobili
topic: Developer and implementation
uuid: 2d951de6-3954-4379-a4ff-99b9695b9869
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '528'
ht-degree: 89%

---


# Tracciamento dei visitatori tra app e contenuti web per dispositivi mobili {#visitor-tracking-between-an-app-and-mobile-web}

Se l&#39;app apre contenuti Web per dispositivi mobili, è necessario che i visitatori non vengano identificati separatamente quando passano dai contenuti nativi a quelli Web.

## ID visitatore nelle app

L’SDK per iOS genera un ID visitatore univoco quando viene installata un’app. Questo ID viene memorizzato nella memoria persistente sul dispositivo mobile e inviato con ogni hit. L&#39;ID viene rimosso solo quando l&#39;utente disinstalla l&#39;app.

>[!TIP]
>
>Gli ID visitatore dell&#39;app restano memorizzati anche da un aggiornamento all&#39;altro.

## ID visitatore nei contenuti web per dispositivi mobili

Le implementazioni web per mobile tipiche usano lo stesso codice standard per Analytics `s_code.js` o `AppMeasurement.js` che viene utilizzato nei siti per desktop. Poiché le librerie JavaScript hanno metodi propri per la generazione di ID visitatore univoci, quando dall&#39;app si aprono contenuti Web per dispositivi mobili viene generato un diverso ID visitatore.

Per usare lo stesso ID visitatore nell&#39;app e nella pagina web per dispositivi mobili e passare nell&#39;URL l&#39;ID visitatore dell&#39;app al contenuto web per dispositivi mobili:

## Implementa il tracciamento dei visitatori tra app e contenuti web per dispositivi mobili {#section_EDC91D6C67AD43999227707C2769C65D}

1. Aggiungi la libreria al tuo progetto e implementa le funzioni di ciclo di vita (lifecycle).

   Per ulteriori informazioni, consulta *Aggiungere l’SDK e il file di configurazione al progetto* in [Implementazione e ciclo di vita di base](/help/ios/getting-started/dev-qs.md).
1. Per aggiungere le informazioni sul visitatore all&#39;URL con cui si apre la visualizzazione Web, invoca `visitorAppendToURL`:

   ```objective-c
   NSURL *url = [NSURL URLWithString:@”https://www.mydomain.com/index.php"]; 
   NSURL *urlWithVisitorData = [ADBMobile visitorAppendToURL:url]; 
   [[UIApplication sharedApplication] openURL:urlWithVisitorData];
   ```

   In alternativa, avviando l&#39;SDK versione 4.16.0, puoi invocare `visitorGetUrlVariablesAsync:` e generare il tuo URL:

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

Il codice del servizio ID sul dominio di destinazione estrae l’identificatore MID dall’URL invece di inviare una richiesta  Adobe per un nuovo ID. Il codice del servizio ID sulla pagina di destinazione usa il MID passato per tenere traccia del visitatore.

Negli hit da contenuti Web per dispositivi mobili, verifica che il parametro `mid` sia presente in ciascun hit e che il suo valore corrisponda al `mid` inviato dal codice dell&#39;app.

## Risolvere i problemi di tracciamento dei visitatori {#section_C070AE85E3CE4E9893FD4F40E73F2C92}

### Non vedo `[ADBMobile visitorAppendToURL:]`.

Controlla che la versione dell&#39;SDK di Adobe fornito in bundle con l&#39;applicazione principale sia 4.12.0 o successiva.

### Non vedo gli Adobe ID nell&#39;URL.

Verifica quanto segue:

* La stringa dell&#39;URL che viene utilizzata per aprire la visualizzazione web è stata generata da  `[ADBMobile visitorAppendToURL:]`

* Gli Adobe ID sono codificati.

   Per verificare che gli ID siano aggiunti all&#39;URL che si apre, individua il parametro di query `adobe_mc`.

### Il &quot;mid&quot; nell&#39;app non è identico a quello della visualizzazione Web.*

Verifica quanto segue:

* La stringa dell&#39;URL che viene utilizzata per aprire la visualizzazione web è stata generata da `[ADBMobile visitorAppendToURL:]`

   La stringa URL contiene i parametri Adobe.

   La stringa deve contenere `adobe_mc="SAMPLE_ID_DATA"`, dove `"SAMPLE_ID_DATA"` contiene gli ID generati nell&#39;SDK di Adobe Mobile.

* La versione di `VisitorAPI.js` è 1.7.0 o successiva.

Se il problema persiste, contatta il servizio di assistenza clienti Adobe. Preparati a condividere un&#39;applicazione di esempio e il sito associato, per consentire ad Adobe di verificare la validità dell&#39;implementazione.
