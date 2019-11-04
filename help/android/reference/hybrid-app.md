---
description: Se la tua app apre contenuto web per mobile, accertati che i visitatori non vengano identificati separatamente mentre si spostano tra contenuto nativo e web per mobile.
seo-description: Se la tua app apre contenuto web per mobile, accertati che i visitatori non vengano identificati separatamente mentre si spostano tra contenuto nativo e web per mobile.
seo-title: Tracciamento dei visitatori tra app e contenuti web per dispositivi mobili
solution: Experience Cloud,Analytics
title: Tracciamento dei visitatori tra app e contenuti web per dispositivi mobili
topic: Sviluppatore e implementazione
uuid: 073572e4-4c55-4b27-b4a7-e4349ccde7bf
translation-type: ht
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Tracciamento dei visitatori tra app e dei contenuti web per dispositivi mobili {#visitor-tracking-between-an-app-and-mobile-web}

Se la tua app apre contenuto web per mobile, accertati che i visitatori non vengano identificati separatamente mentre si spostano tra contenuto nativo e web per mobile.

## ID visitatore nelle app

L'SDK per Android genera un ID visitatore univoco quando viene installata un'app. L'ID viene memorizzato nella memoria del dispositivo mobile, inviato a ogni hit e rimosso solo quando l'utente disinstalla l'app.

>[!TIP]
>
>Gli ID visitatore dell'app restano memorizzati anche da un aggiornamento all'altro.

## ID visitatore nei contenuti web per dispositivi mobili

Le implementazioni web per mobile tipiche usano lo stesso codice standard per Analytics `s_code.js` o `AppMeasurement.js` che viene utilizzato nei siti per desktop. Poiché le librerie JavaScript hanno metodi propri per la generazione di ID visitatore univoci, quando dall'app si aprono contenuti Web per dispositivi mobili viene generato un diverso ID visitatore.

## Implementazione del tracciamento dei visitatori tra app e dei contenuti web per dispositivi mobili {#section_1755BCCFD42D456EB2319141030FDDFF}

Per usare lo stesso ID visitatore nell'app e nel contenuto Web per dispositivi mobili:

1. Aggiungi la libreria al tuo progetto e implementa le funzioni di ciclo di vita (lifecycle).

   Per ulteriori informazioni, consulta *Aggiungere l’SDK e il file di configurazione al progetto IntelliJ IDEA o Eclipse* in [Implementazione e ciclo di vita di base](/help/android/getting-started/dev-qs.md).

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

## Risoluzione dei problemi di tracciamento dei visitatori {#section_9B641F8569E34A089C52AA28EA4C891D}

### Non vedo `Visitor.appendToURL`.

Controlla che la versione dell'SDK di Adobe fornito in bundle con l'applicazione principale sia 4.12.0 o successiva.

**Non vedo gli Adobe ID nell'URL.**

* Verifica quanto segue:
   * La stringa dell'URL utilizzata per aprire la visualizzazione web è stata generata da `Visitor.appendToURL(urlString)`.
   * Gli Adobe ID sono codificati. 
Per assicurare che gli ID siano collegati all'URL che viene aperto, verifica che il parametro della query `adobe_mc` sia presente nell'URL.

### Il mio `mid` non è identico tra app e visualizzazione web.

* Verifica quanto segue:

   * La stringa dell'URL che viene utilizzata per aprire la visualizzazione web è stata generata da `Visitor.appendToURL(urlString)`.
   * La stringa URL contiene i parametri Adobe.

      La stringa deve contenere `adobe_mc="SAMPLE_ID_DATA"`, dove `"SAMPLE_ID_DATA"` contiene gli ID generati nell'SDK di Adobe Mobile.
   * La versione di `VisitorAPI.js` è 1.7.0 o successiva.

Se questi passaggi non consentono di risolvere i problemi, contatta l'assistenza Adobe Experience.

>[!IMPORTANT]
>
>Per consentire ad Adobe di convalidare l'implementazione, devi condividere un'applicazione di esempio e il sito associato.

