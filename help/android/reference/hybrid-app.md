---
description: Se la tua app apre contenuto web per mobile, accertati che i visitatori non vengano identificati separatamente mentre si spostano tra contenuto nativo e web per mobile.
seo-description: Se la tua app apre contenuto web per mobile, accertati che i visitatori non vengano identificati separatamente mentre si spostano tra contenuto nativo e web per mobile.
seo-title: Tracciamento dei visitatori tra un'app e un Web per dispositivi mobili
solution: Marketing Cloud, Analytics
title: Tracciamento dei visitatori tra un'app e un Web per dispositivi mobili
topic: Sviluppatore e implementazione
uuid: 073572 e 4-4 c 55-4 b 27-b 4 a 7-e 4349 ccde 7 bf
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Visitor tracking between an app and the mobile web {#visitor-tracking-between-an-app-and-mobile-web}

Se la tua app apre contenuto web per mobile, accertati che i visitatori non vengano identificati separatamente mentre si spostano tra contenuto nativo e web per mobile.

## ID visitatore nelle app

L'SDK per Android genera un ID visitatore univoco quando viene installata un'app. L'ID viene memorizzato nella memoria del dispositivo mobile, inviato a ogni hit e rimosso solo quando l'utente disinstalla l'app.

>[!TIP]
>
>Gli ID visitatore dell'app restano invariati.

## ID visitatore nel Web per dispositivi mobili

Le implementazioni web per mobile tipiche usano lo stesso codice standard per Analytics `s_code.js` o `AppMeasurement.js` che viene utilizzato nei siti per desktop. Poiché le librerie JavaScript hanno metodi propri per la generazione di ID visitatore univoci, quando dall'app si aprono contenuti Web per dispositivi mobili viene generato un diverso ID visitatore.

## Implementing visitor tracking between an app and the mobile web {#section_1755BCCFD42D456EB2319141030FDDFF}

Per usare lo stesso ID visitatore nell'app e nel contenuto Web per dispositivi mobili:

1. Aggiungi la libreria al tuo progetto e implementa le funzioni di ciclo di vita (lifecycle).

   Per ulteriori informazioni, vedi *Aggiungere l'SDK e il file di configurazione al progetto intellij IDEA o Eclipse* nell'implementazione [e nel ciclo di vita principali](/help/android/getting-started/dev-qs.md).

1. Per aggiungere le informazioni sul visitatore all'URL con cui si apre la visualizzazione Web, invoca `visitorAppendToURL`:

   ```java
   String urlString = "https://www.mydomain.com/index.php"; 
   String urlStringWithVisitorData = Visitor.appendToURL(urlString); 
   Intent browserIntent = new Intent(Intent.ACTION_VIEW, Uri.parse(urlStringWithVisitorData)); 
   startActivity(browserIntent);
   ```

   In alternativa, avviando l'SDK versione 4.16.0, puoi invocare `Visitor.getUrlVariablesAsync` e generare il tuo URL:

   ```java
   final String urlString = "https://www.mydomain.com/index.php"; 
   Visitor.getUrlVariablesAsync(new Visitor.VisitorCallback(){ 
       @Override 
       public void call(String urlVariables) { 
           final String urlStringWithVisitorData = String.format("%s?%s", urlString, urlVariables); 
           final Intent browserIntent = new Intent(Intent.ACTION_VIEW, Uri.parse(urlStringWithVisitorData)); 
           startActivity(browserIntent); 
       } 
   });
   ```

Invece di inviare ad Adobe la richiesta di un nuovo ID, il codice del servizio ID sul dominio di destinazione estrae l'identificatore MID dall'URL. Il codice usa il MID passato per tracciare il visitatore.

Sugli hit per il contenuto web per mobile, verifica che il parametro `mid` esista su ciascun hit, e che il valore corrisponda al parametro `mid` inviato dal codice dell'app.

## Troubleshooting visitor tracking {#section_9B641F8569E34A089C52AA28EA4C891D}

### I do not see `Visitor.appendToURL`.

Controlla che la versione dell'SDK di Adobe fornito in bundle con l'applicazione principale sia 4.12.0 o successiva.

**Non vedo gli Adobe ID nell'URL.**

* Verifica quanto segue:
   * La stringa dell'URL utilizzata per aprire la visualizzazione web è stata generata da `Visitor.appendToURL(urlString)`.
   * Gli Adobe ID sono codificati.
To ensure that the IDs that are appended to the URL that is being opened, verify that the `adobe_mc` query parameter appears in the URL.

### Il mio `mid` non è identico tra app e visualizzazione web.

* Verifica quanto segue:

   * La stringa dell'URL che viene utilizzata per aprire la visualizzazione web è stata generata da `Visitor.appendToURL(urlString)`.
   * La stringa URL contiene i parametri Adobe.

      The string should contain `adobe_mc="SAMPLE_ID_DATA"` where `"SAMPLE_ID_DATA"` contains the IDs that are generated in the Adobe Mobile SDK.
   * La versione di `VisitorAPI.js` è 1.7.0 o successiva.

Se questi passaggi non consentono di risolvere i problemi, contatta l'assistenza Adobe Experience.

>[!IMPORTANT]
>
>Per consentire ad Adobe di convalidare l'implementazione, devi condividere un'applicazione di esempio e il sito associato.

