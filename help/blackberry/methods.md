---
description: Classi e metodi forniti dalla libreria BlackBerry.
seo-description: Classi e metodi forniti dalla libreria BlackBerry.
seo-title: Documentazione su classi e metodi per Adobe Mobile
title: Documentazione su classi e metodi per Adobe Mobile
uuid: 1e42d759-be43-4bb3-ac1a-c7d64133d61c
translation-type: tm+mt
source-git-commit: c198ae57b05f8965a8e27191443ee2cd552d6c50
workflow-type: tm+mt
source-wordcount: '988'
ht-degree: 60%

---


# Documentazione su classi e metodi per Adobe Mobile {#adobe-mobile-class-and-method-reference}

Classi e metodi forniti dalla libreria BlackBerry.

Al momento l’SDK supporta  Adobe Analytics e i metodi si trovano in classi separate in base alla soluzione.

## Impostazioni SDK {#section_C1EB977043C04D2B93E5A63DB72828B6}

* **getPrivacyStatus**

   Restituisce la rappresentazione enum dello stato di privacy per l’utente corrente.

   * ADBMobilePrivacyStatusOptIn: gli hit vengono inviati immediatamente.
   * ADBMobilePrivacyStatusOptOut: gli hit vengono scartati.
   * ADBMobilePrivacyStatusUnknown - Se le marche temporali sono abilitate nella suite di rapporti, gli hit vengono salvati fino alla modifica dello stato di privacy, quando l’utente acconsente (opt in, gli hit vengono inviati) o rinuncia (opt out, gli hit vengono eliminati). Se le marche temporali non sono abilitate nella suite di rapporti, gli hit vengono eliminati fino alla modifica dello stato di privacy, quando l&#39;utente acconsente (optedin).

      Il valore predefinito è impostato nel file `ADBMobileConfig.json`.

   * Di seguito è riportata la sintassi per questo metodo:

      ```cpp
      static ADBMobilePrivacyStatus getPrivacyStatus();
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```cpp
      ADBMobilePrivacyStatus privacyStatus = ADBMobile::getPrivacyStatus();
      ```

* **setPrivacyStatus**

   Imposta lo stato di privacy per l&#39;utente corrente su `status`. Imposta uno dei valori seguenti:

   * `ADBMobilePrivacyStatusOptIn` - gli hit vengono inviati immediatamente.
   * `ADBMobilePrivacyStatusOptOut` - gli hit vengono eliminati.
   * `ADBMobilePrivacyStatusUnknown` - Se le marche temporali sono abilitate nella suite di rapporti, gli hit vengono salvati fino alla modifica dello stato di privacy, quando l’utente acconsente (optedin, gli hit vengono inviati) o rinuncia (optedout, gli hit vengono eliminati). Se le marche temporali non sono abilitate nella suite di rapporti, gli hit vengono eliminati fino alla modifica dello stato di privacy, quando l&#39;utente acconsente (optedin).

   * Di seguito è riportata la sintassi per questo metodo:

      ```cpp
      static void setPrivacyStatus(ADBMobilePrivacyStatus status);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```cpp
      ADBMobile::setPrivacyStatus(ADBMobilePrivacyStatusOptIn);
      ```

* **getUserIdentifier**

   Restituisce l&#39;identificatore utente se è stato impostato un identificatore personalizzato. Returns `null` if a custom identifier is not set. Il valore predefinito è `null`.

   * Di seguito è riportata la sintassi per questo metodo:

      ```cpp
      static QString getUserIdentifier();
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```cpp
      QString userId = ADBMobile::getUserIdentifier(); 
      ```

* **setUserIdentifier**

   Imposta l&#39;identificatore utente su `identifier`.

   * Di seguito è riportata la sintassi per questo metodo:

      ```cpp
      static void setUserIdentifier(QString identifier);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```cpp
      ADBMobile::setUserIdentifier("billybob");
      ```

* **getDebugLogging**

   Restituisce l&#39;attuale preferenza di accesso di debug. Il valore predefinito è `false`.

   * Di seguito è riportata la sintassi per questo metodo:

      ```cpp
      static bool getDebugLogging();
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```cpp
       bool debugging = ADBMobile::getDebugLogging(); 
      ```

* **setDebugLogging**

   Imposta la preferenza per l&#39;accesso di su `debugLogging` debug.

   * Di seguito è riportata la sintassi per questo metodo:

      ```cpp
      static void setDebugLogging(bool debugLogging);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```cpp
        ADBMobile::setDebugLogging(true); 
      ```

* **collectLifecycleData**

   Indica all&#39;SDK che i dati del ciclo di vita devono essere raccolti per l&#39;utilizzo in tutte le soluzioni dell&#39;SDK. Per ulteriori informazioni, vedi [Metriche del ciclo di vita](/help/blackberry/metrics.md).

   * Di seguito è riportata la sintassi per questo metodo:

      ```cpp
      static void collectLifecycleData();
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```cpp
      ApplicationUI::ApplicationUI(bb::cascades::Application *app):  QObject(app)  { 
      //... 
      ADBMobile::collectLifecycleData(); 
      }
      ```

## Metodi di Analytics {#section_91F4AD0A045D4E4E8F9A93450503E49E}

Ciascuno di questi metodi viene usato per inviare dati alla suite di rapporti di Adobe Analytics.

* **trackState**

   Tiene traccia dello stato di un&#39;app con dati contestuali facoltativi. Gli stati sono le visualizzazioni disponibili nell’app, ad esempio &quot;dashboard iniziale&quot;, &quot;impostazioni dell’app&quot;, &quot;carrello&quot; e così via. Questi stati sono simili alle pagine di un sito Web e le chiamate `trackState` incrementano le visualizzazioni di pagina.

   >[!TIP]
   >
   >Questa è l&#39;unica chiamata di tracciamento che incrementa le visualizzazioni pagina.

   * Di seguito è riportata la sintassi per questo metodo:

      ```cpp
      static void trackState(QString state, QHash<QString, QString> contextData = QHash<QString, QString>()); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```cpp
         ADBMobile::trackState("loginScreen", null);
      ```

* **trackAction**

   Tiene traccia di un&#39;azione nell&#39;applicazione. Le azioni sono gli eventi che avvengono nell’app e che desideri misurare, come &quot;accessi&quot;, &quot;tap sui banner&quot;, &quot;abbonamenti ai feed&quot; e altre metriche.

   * Di seguito è riportata la sintassi per questo metodo:

      ```cpp
      static void trackAction(QString action, QHash<QString, QString> contextData = QHash<QString, QString>()); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```cpp
        ADBMobile::trackAction("heroBannerTouched", null); 
      ```

* **trackLocation**

   Invia le coordinate x,y correnti. Sostituire l&#39;evento con l&#39;evento ricevuto dal sottoscrittore a BPS.

   * Di seguito è riportata la sintassi per questo metodo:

      ```cpp
      static void trackLocation(bps_event_t *geoEvent, QHash<QString, QString> contextData = QHash<QString, QString> ());
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```cpp
        ADBMobile::trackLocation(event, null);
      ```

## `ADBMobileConfig.json` Guida di riferimento per il file di configurazione {#section_5AD4EDF87E304980B4AC4A5657FDA8B9}

The `ADBMobileConfig.json` file must be placed in the *assets* folder.

* **rsids**

   (Obbligatorio) Una o più suite di rapporti che dovrà ricevere i dati Analytics. Gli ID suite di rapporti multipli devono essere separati da virgole senza spazi intermedi.

   Esempio di codice per questa variabile:

   ```js
   "rsids" : "rsid"
   ```

   ```js
   "rsids" : "rsid1,rsid2"
   ```

* **server**

   (Obbligatorio). Server di Analytics. Questa variabile deve essere compilata con il dominio del server, senza il prefisso del protocollo `https://` o `https://`. Il prefisso del protocollo viene gestito automaticamente dalla libreria in base alla `ssl` variabile. Se `ssl` è `true`, viene eseguita una connessione sicura al server. Se `ssl` è `false`, viene eseguita una connessione non sicura.

* **charset**

   Definisce il set di caratteri utilizzato per i dati inviati ad Analytics. Il set di caratteri serve per convertire i dati in entrata in UTF-8 per l&#39;archiviazione e la generazione di rapporti.

* **ssl**

   Abilita (`true`) o disabilita (`false`) l’invio di dati di misurazione tramite SSL (HTTPS). Il valore predefinito è `false`.

* **offlineEnabled**

   When enabled (`true`), hits are queued while the device is offline and sent later when the device is online. Per poter usare il tracciamento offline, nella suite di rapporti devono essere abilitate le marche temporali.

   >[!TIP]
   >
   >Se le marche temporali sono abilitate nella suite di rapporti, la proprietà di configurazione `offlineEnabled` *deve* essere `true`. Se le marche temporali non sono abilitate nella suite di rapporti, la proprietà di configurazione `offlineEnabled` *deve* essere false. Se questo non viene configurato correttamente, i dati andranno perduti. Se non sei sicuro se le marche temporali sono abilitate o meno nella suite di rapporti,   contatta   [Supporto](https://helpx.adobe.com/it/contact/enterprise-support.ec.html)Enterprise.

   If you are currently reporting AppMeasurement data to a report suite that also collects data from JavaScript, you might need to set up a separate report suite for mobile data, or include a custom timestamp on all JavaScript hits using the `s.timestamp` variable.

   Il valore predefinito è `false`.

* **lifecycleTimeout**

   Specifica il tempo, in secondi, che deve trascorrere tra il momento in cui l’app viene avviata e quello in cui l’avvio viene considerato come una nuova sessione. Questo timeout si applica anche quando l’applicazione viene messa in background e riattivata. Il tempo trascorso in background dall’app non viene incluso nella durata della sessione.

   Il valore predefinito è 300 secondi.

* **batchLimit**

   Numero massimo di hit offline memorizzati nella coda. Il valore predefinito è 0 (nessun limite).

* **privacyDefault**

   * `optedin` - gli hit vengono inviati immediatamente.
   * `optedout` - gli hit vengono eliminati.
   * `optunknown` - Se le marche temporali sono abilitate nella suite di rapporti, gli hit vengono salvati fino alla modifica dello stato di privacy, quando l’utente acconsente (optedin, gli hit vengono inviati) o rinuncia (optedout, gli hit vengono eliminati).

      Se le marche temporali non sono abilitate nella suite di rapporti, gli hit vengono eliminati fino alla modifica dello stato di privacy, quando l&#39;utente acconsente (optedin).
   Questa variabile imposta solo il valore iniziale. Se questo valore viene impostato o modificato nel codice, il nuovo valore viene utilizzato finché non viene modificato oppure finché l&#39;app non viene disinstallata e reinstallata.

   Il valore predefinito è `optedin`.

The following is an example of an `ADBMobileConfig.json` file:

```js
{ 
    "version" : "1.0", 
    "analytics" : { 
        "rsids" : "coolApp", 
        "server" : "my.CoolApp.com", 
        "charset" : "UTF-8", 
        "ssl" : true, 
        "offlineEnabled" : true, 
        "lifecycleTimeout" : 5, 
        "privacyDefault" : "optedin", 
    } 
}
```
