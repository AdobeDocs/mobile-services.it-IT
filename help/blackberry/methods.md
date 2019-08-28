---
description: Classi e metodi forniti dalla libreria BlackBerry.
seo-description: Classi e metodi forniti dalla libreria BlackBerry.
seo-title: Guida di riferimento delle classi e dei metodi per Adobe Mobile
title: Guida di riferimento delle classi e dei metodi per Adobe Mobile
uuid: 1 e 42 d 759-be 43-4 bb 3-ac 1 a-c 7 d 64133 d 61 c
translation-type: tm+mt
source-git-commit: 68bc21f1c6dba2faeed332495592114af90c8f61

---


# Adobe Mobile class and method reference {#adobe-mobile-class-and-method-reference}

Classi e metodi forniti dalla libreria BlackBerry.

L'SDK supporta attualmente Adobe Analytics e i metodi si trovano in classi separate in base alla soluzione.

## SDK settings {#section_C1EB977043C04D2B93E5A63DB72828B6}

* **getPrivacyStatus**

   Restituisce la rappresentazione enum dello stato di privacy per l’utente corrente.

   * ADBMobilePrivacyStatusOptIn: gli hit vengono inviati immediatamente.
   * ADBMobilePrivacyStatusOptOut: gli hit vengono eliminati.
   * ADBMobilePrivacyStatusUnknown - Se le marche temporali sono abilitate nella suite di rapporti, gli hit vengono salvati fino alla modifica dello stato di privacy, quando l’utente acconsente (optedin, gli hit vengono inviati) o rinuncia (optedout, gli hit vengono eliminati). Se le marche temporali non sono abilitate nella suite di rapporti, gli hit vengono eliminati fino alla modifica dello stato di privacy, quando l’utente acconsente (optedin).

      Il valore predefinito è impostato nel file `ADBMobileConfig.json`.

   * Di seguito è riportata la sintassi per questo metodo:

      ```cpp
      static ADBMobilePrivacyStatus getPrivacyStatus();
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```cpp
      ADBMobilePrivacyStatus privacyStatus = ADBMobile::getPrivacyStatus();
      ```

* Il metodo **setPrivacyStatus**

   Imposta lo stato di privacy per l'utente corrente su `status`. Imposta uno dei valori seguenti:

   * `ADBMobilePrivacyStatusOptIn` - gli hit vengono inviati immediatamente.
   * `ADBMobilePrivacyStatusOptOut` - gli hit vengono eliminati.
   * Per `ADBMobilePrivacyStatusUnknown`, se le marche temporali sono abilitate nella suite di rapporti, gli hit vengono salvati fino alla modifica dello stato di privacy, quando l’utente acconsente (optedin, gli hit vengono inviati) o rinuncia (optedout, gli hit vengono eliminati). Se le marche temporali non sono abilitate nella suite di rapporti, gli hit vengono eliminati fino alla modifica dello stato di privacy, quando l’utente acconsente (optedin).

   * Di seguito è riportata la sintassi per questo metodo:

      ```cpp
      static void setPrivacyStatus(ADBMobilePrivacyStatus status);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```cpp
      ADBMobile::setPrivacyStatus(ADBMobilePrivacyStatusOptIn);
      ```

* **getUserIdentifier**

   Restituisce l'identificatore utente se è stato impostato un identificatore personalizzato. Returns `null` if a custom identifier is not set. Il valore predefinito è `null`.

   * Di seguito è riportata la sintassi per questo metodo:

      ```cpp
      static QString getUserIdentifier();
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```cpp
      QString userId = ADBMobile::getUserIdentifier(); 
      ```

* **setUserIdentifier**

   Imposta l'identificatore utente su `identifier`.

   * Di seguito è riportata la sintassi per questo metodo:

      ```cpp
      static void setUserIdentifier(QString identifier);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```cpp
      ADBMobile::setUserIdentifier("billybob");
      ```

* **getDebugLogging**

   Restituisce l'attuale preferenza di accesso di debug. Il valore predefinito è `false`.

   * Di seguito è riportata la sintassi per questo metodo:

      ```cpp
      static bool getDebugLogging();
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```cpp
       bool debugging = ADBMobile::getDebugLogging(); 
      ```

* **setDebugLogging**

   Imposta la preferenza per l'accesso di su `debugLogging`debug.

   * Di seguito è riportata la sintassi per questo metodo:

      ```cpp
      static void setDebugLogging(bool debugLogging);
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```cpp
        ADBMobile::setDebugLogging(true); 
      ```

* **collectLifecycleData**

   Indica all'SDK che i dati del ciclo di vita devono essere raccolti per l'utilizzo in tutte le soluzioni dell'SDK. Per ulteriori informazioni, vedi [Metriche del ciclo di vita](/help/blackberry/metrics.md).

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

## Analytics methods {#section_91F4AD0A045D4E4E8F9A93450503E49E}

Ciascuno di questi metodi viene usato per inviare dati alla suite di rapporti di Adobe Analytics.

* **trackState**

   Tiene traccia dello stato di un'app con dati contestuali facoltativi. Gli stati sono le visualizzazioni disponibili nell'app, ad esempio “dashboard iniziale”, “impostazioni dell'app”, “carrello” e così via. Questi stati sono simili alle pagine di un sito Web e le chiamate `trackState` incrementano le visualizzazioni di pagina.

   >[!TIP]
   >
   >Questa è l'unica chiamata di tracciamento che incrementa le visualizzazioni di pagina.

   * Di seguito è riportata la sintassi per questo metodo:

      ```cpp
      static void trackState(QString state, QHash<QString, QString> contextData = QHash<QString, QString>()); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```cpp
         ADBMobile::trackState("loginScreen", null);
      ```

* **trackAction**

   Tiene traccia di un'azione nell'applicazione. Le azioni sono gli eventi che avvengono nell’applicazione e che desideri misurare, come “accessi”, “tap sui banner”, “abbonamenti ai feed” e altre metriche.

   * Di seguito è riportata la sintassi per questo metodo:

      ```cpp
      static void trackAction(QString action, QHash<QString, QString> contextData = QHash<QString, QString>()); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```cpp
        ADBMobile::trackAction("heroBannerTouched", null); 
      ```

* **trackLocation**

   Invia le coordinate x,y correnti. Sostituisci “event” con l'evento ricevuto dal sottoscrittore a BPS.

   * Di seguito è riportata la sintassi per questo metodo:

      ```cpp
      static void trackLocation(bps_event_t *geoEvent, QHash<QString, QString> contextData = QHash<QString, QString> ());
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```cpp
        ADBMobile::trackLocation(event, null);
      ```

## `ADBMobileConfig.json` riferimento file di configurazione {#section_5AD4EDF87E304980B4AC4A5657FDA8B9}

`ADBMobileConfig.json` Il file deve essere posizionato nella cartella *delle risorse* .

* **rsids**

   (Obbligatorio) Una o più suite di rapporti che dovrà ricevere i dati Analytics. Nel caso di più suite di rapporti, i rispettivi ID devono essere separati da una virgola, senza spazio.

   Di seguito è riportato l'esempio di codice per questa variabile:

   ```js
   "rsids" : "rsid"
   ```

   ```js
   "rsids" : "rsid1,rsid2"
   ```

* **server**

   (Obbligatorio). Server di Analytics. This variable should be populated with the server domain, without an `https://` or `https://` protocol prefix. Il prefisso del protocollo viene gestito automaticamente dalla libreria, in base alla variabile `ssl`. Se `ssl` è `true`, viene eseguita una connessione sicura al server. Se `ssl` è `false`, viene eseguita una connessione non sicura.

* **charset**

   Definisce il set di caratteri utilizzato per i dati inviati ad Analytics. Il set di caratteri serve per convertire i dati in entrata in UTF-8 per l'archiviazione e la generazione di rapporti.

* **ssl**

   Enables (`true`) or disables (`false`) sending measurement data via SSL (HTTPS). Il valore predefinito è `false`.

* **offlineEnabled**

   When enabled (`true`), hits are queued while the device is offline and sent later when the device is online. Per poter usare il tracciamento offline, nella suite di rapporti devono essere abilitate le marche temporali.

   >[!TIP]
   >
   >If timestamps are enabled on your report suite, your `offlineEnabled` configuration property *must* be `true`. Se le marche temporali non sono abilitate nella suite di rapporti, la proprietà di configurazione `offlineEnabled` *deve* essere false. Se questo non viene configurato correttamente, i dati andranno perduti. Se non sei sicuro se le marche temporali sono abilitate o meno nella suite di rapporti, contatta [Supporto Enterprise](https://helpx.adobe.com/contact/enterprise-support.ec.html).

   Se i dati AppMeasurement vengono inviati a una suite di rapporti che raccoglie anche dati da JavaScript, potrebbe essere necessario impostare una suite di rapporti distinta per i dati mobile o includere una marca temporale personalizzata in tutti gli hit JavaScript che usano la variabile `s.timestamp`.

   Il valore predefinito è `false`.

* **lifecycleTimeout**

   Specifica l’intervallo di tempo, in secondi, che deve trascorrere tra un avvio dell’app e quello successivo affinché questo sia considerato come una nuova sessione. Il timeout viene applicato anche quando l’applicazione viene lasciata in background e poi riattivata. Il tempo durante il quale l’app rimane in background non viene incluso nella durata della sessione.

   Il valore predefinito è 300 secondi.

* **batchLimit**

   Numero massimo di hit offline memorizzati nella coda. Il valore predefinito è 0 (nessun limite).

* **privacyDefault**

   * `optedin` - gli hit vengono inviati immediatamente.
   * `optedout` - gli hit vengono eliminati.
   * Per `optunknown`, se le marche temporali sono abilitate nella suite di rapporti, gli hit vengono salvati fino alla modifica dello stato di privacy, quando l’utente acconsente (optedin, gli hit vengono inviati) o rinuncia (optedout, gli hit vengono eliminati). 

      Se le marche temporali non sono abilitate nella suite di rapporti, gli hit vengono eliminati fino alla modifica dello stato di privacy, quando l’utente acconsente (optedin).
   Questa variabile imposta solo il valore iniziale. Se questo valore viene impostato o modificato nel codice, il nuovo valore viene usato finché non viene nuovamente modificato oppure finché l'app non viene disinstallata e reinstallata.

   Il valore predefinito è `optedin`.

Di seguito viene indicato un esempio del file `ADBMobileConfig.json`:

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
