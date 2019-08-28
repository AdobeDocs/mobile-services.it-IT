---
description: Nelle tabelle che seguono sono elencate le metriche e dimensioni che possono essere misurate automaticamente dalla libreria mobile dopo l'implementazione delle funzioni "lifecycle" sul ciclo di vita.
seo-description: Nelle tabelle che seguono sono elencate le metriche e dimensioni che possono essere misurate automaticamente dalla libreria mobile dopo l'implementazione delle funzioni "lifecycle" sul ciclo di vita.
seo-title: Metriche del ciclo di vita
solution: Marketing Cloud, Analytics
title: Metriche del ciclo di vita
topic: Sviluppatore e implementazione
uuid: b 795 e 383-d 59 b -4 a 3 c -9 e 14-ffe 8 fb 58412 c
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Lifecycle metrics {#lifecycle-metrics}

Queste sono le metriche e le dimensioni che possono essere misurate automaticamente dalla libreria mobile dopo l'implementazione del ciclo di vita.

## Nuova versione di Adobe Experience Cloud SDK

Stai cercando informazioni e documentazione sull’SDK per dispositivi mobili di Adobe Experience Platform? Fai clic [qui](https://aep-sdks.gitbook.io/docs/) per la documentazione più recente.

A settembre 2018 è stata rilasciata una nuova versione principale dell’SDK. Questi nuovi SDK per dispositivi mobili di Adobe Experience Platform sono configurabili tramite [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* Per iniziare, passa ad Launch.
* Per visualizzare cosa è compreso negli archivi Experience Platform SDK, passa a [Github: SDK di Adobe Experience Platform](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

>[!IMPORTANT]
>
> If you are using the Adobe Experience Platform Mobile SDKs with Adobe Launch, you **must** also install the Adobe Analytics Mobile Services extension to use Adobe Mobile Services features such as in-App messaging, push notifications or Acquisition links. Per ulteriori informazioni, consulta [Adobe Analytics - Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services).


## Lifecycle metrics and dimensions {#section_78F036C4296F4BA3A47C2044F79C86C1}

Una volta configurate le metriche del ciclo di vita, queste vengono inviate ad Analytics in parametri di dati contestuali, a Target in parametri con ogni chiamata Mbox e a Audience Manager come segnali. Analytics e Target usano lo stesso formato; Audience Manager usa invece un prefisso diverso per ogni metrica.

Per Analytics, i dati contestuali inviati con ciascuna chiamata di tracciamento del ciclo di vita sono catturati automaticamente e segnalati mediante l'uso della metrica o della dimensione indicata nella prima colonna, con le eccezioni indicate nella prima colonna.

>[!TIP]
>
>Le eccezioni sono fornite nella descrizione.

### Metrics (Metriche)

* **Primi avvii**

   Attivazione alla prima esecuzione dopo l'installazione o reinstallazione.

   * Analytics Context Data/Target parameter: `a.InstallEvent`
   * Audience Manager signal: `c_a_InstallEvent`

* **Aggiornamenti**

   Attivazione alla prima esecuzione dopo l'aggiornamento ogni volta che cambia il numero di versione.

   * Analytics Context Data/Target parameter: `a.UpgradeEvent`
   * Audience Manager signal: `c_a_UpgradeEvent`

* **Utenti giornalieri coinvolti**

   Attivazione quando l'applicazione viene utilizzata in un giorno particolare.

   * Analytics Context Data/Target parameter: `a.DailyEngUserEvent`
   * Audience Manager signal: `c_a_DailyEngUserEvent`

* **Utenti mensili coinvolti**

   Attivazione quando l'applicazione viene utilizzata in un mese particolare.

   * Analytics Context Data/Target parameter: `a.MonthlyEngUserEvent`
   * Audience Manager signal: `c_a_MonthlyEngUserEvent`

* **Avvii**

   Attivazione a ogni esecuzione, compresi arresti anomali e installazioni. Viene attivata anche alla ripresa dell'app dopo un periodo in background se viene superato il timeout di una sessione ciclo di vita.

   * Analytics Context Data/Target parameter: `a.LaunchEvent`
   * Audience Manager signal: `c_a_LaunchEvent`

* **Arresti anomali**

   Attivazione quando l'applicazione non viene messa in background prima della chiusura. L'evento viene inviato quando si riavvia l'applicazione dopo l'arresto anomalo.  La reportistica di Adobe Mobile sugli arresti anomali non implementa un handler globale per eccezioni non rilevate.

   * Analytics Context Data/Target parameter: `a.CrashEvent`
   * Audience Manager signal: `c_a_CrashEvent`

* **Durata sessione precedente**

   Segnala la durata di una precedente sessione dell'applicazione in base a quanto tempo l'applicazione è stata aperta e in primo piano.

   * Analytics Context Data/Target parameter: `a.PrevSessionLength`
   * Audience Manager signal: `c_a_PrevSessionLength`

>[!IMPORTANT]
>
> Le *metriche Utenti* giornalieri coinvolti e *Utenti* mensili coinvolti non vengono memorizzate automaticamente in una metrica Analytics. Devi creare una regola di elaborazione che imposti un evento personalizzato per acquisire queste metriche.

### Dimensioni

* **Data di installazione**

   Data del primo avvio dopo l'installazione.  Il formato della data `MM/DD/YYYY`è.

   * Dati contestuali di Analytics/Target: `a.InstallDate`
   * Gestione dell'audience: `c_a_InstallDate`

* **ID app**

   Stores the Application name and version in the `[AppName] [BundleVersion]` format. Ad esempio, `myapp 1.1`.

   * Dati contestuali di Analytics/Target: `a.AppID`
   * Gestione dell'audience: `c_a_AppID`

* **Numero di avvii**

   Numero di volte per cui l'applicazione è stata avviata o portata in primo piano.

   * Dati contestuali di Analytics/Target: `a.Launches`
   * Gestione dell'audience: `c_a_Launches`

* **Giorni dal primo utilizzo**

   Numero di giorni dalla prima esecuzione.

   * Dati contestuali di Analytics/Target: `a.DaysSinceFirstUse`
   * Gestione dell'audience: `c_a_DaysSinceFirstUse`

* **Giorni dall'ultimo utilizzo**

   Numero di giorni dall'ultimo utilizzo.

   * Dati contestuali di Analytics/Target: `a.DaysSinceLastUse`
   * Gestione dell'audience: `c_a_DaysSinceLastUse`

* **Ora del giorno**

   Calcola l'ora di avvio dell'app e utilizza il formato numerico 24 ore. Utilizzato per la suddivisione del tempo per determinare le ore di utilizzo di picco.

   * Dati contestuali di Analytics/Target: `a.HourOfDay`
   * Gestione dell'audience: `c_a_HourOfDay`

* **Giorno della settimana**

   Numero del giorno della settimana in cui è stata avviata l'app.

   * Dati contestuali di Analytics/Target: `a.DayOfWeek`
   * Gestione dell'audience: `c_a_DayOfWeek`

* **Versione sistema operativo**

   Numero di giorni dalla modifica del numero di versione dell'applicazione.

   * Dati contestuali di Analytics/Target: `a.OSVersion`
   * Gestione dell'audience: `c_a_OSVersion|OS version`

* **Giorni dall'ultimo aggiornamento**

   Giorni dall'ultimo aggiornamento.

   * Dati contestuali di Analytics/Target: `a.DaysSinceLastUpgrade`
   * Gestione dell'audience: `c_a_DaysSinceLastUpgrade`

* **Avvii dall'ultimo aggiornamento**

   Numero di avvii dalla modifica del numero di versione dell'applicazione.

   * Dati contestuali di Analytics/Target: `a.LaunchesSinceUpgrade`
   * Gestione dell'audience: `c_a_LaunchesSinceUpgrade`

* **Nome del dispositivo**

   Memorizza il nome del dispositivo.  Stringa di due cifre separate da virgola che identifica il dispositivo iOS. Di norma il primo numero rappresenta la generazione del dispositivo e il secondo numero indica membri diversi della famiglia di dispositivi. Per un elenco dei nomi dei dispositivi più comuni, vedi  Versioni dei dispositivi iOS.

   * Dati contestuali di Analytics/Target: `a.DeviceName`
   * Gestione dell'audience: `c_a_DeviceName`

* **Nome gestore**

   Memorizza il nome del gestore del servizio mobile, così come viene fornito dal dispositivo.

   * Dati contestuali di Analytics/Target: `a.CarrierName`
   * Gestione dell'audience: `c_a_CarrierName`

* **Risoluzione**

   Larghezza x altezza in pixel reali.

   * Dati contestuali di Analytics/Target: `a.Resolution`
   * Gestione dell'audience: `c_a_Resolution`
   >[!IMPORTANT]
   >
   >*I giorni dall'ultimo aggiornamento*, *gli avvii dall'ultimo aggiornamento* e *le dimensioni Nome* gestore non vengono memorizzate automaticamente in una variabile Analytics. Devi creare una regola di elaborazione per copiare i valori in una variabile di Analytics a scopo di reportistica.


## Additional mobile metrics and dimensions {#section_0B32BBF9CA734103BEDB5E755FFE5B31}

Le metriche e le dimensioni seguenti vengono acquisite in variabili di soluzioni mobili in base al metodo indicato.

### Metrics (Metriche)

* **Tempo azione totale**

   Viene compilata dai metodi trackTimedAction.

   * Analytics Context Data/Target parameter: `a.action.time.total`
   * Audience Management trait: `c_a_action_time_total`

* **Tempo azione in-app**

   Viene compilata dai metodi trackTimedAction.

   * Analytics Context Data/Target parameter: `a.action.time.inapp`
   * Audience Management trait: `c_a_action_time_inapp`

* **Valore "lifetime" del ciclo di vita (evento)**

   Viene compilata dai metodi trackLifetimeValue.

   * Analytics Context Data/Target parameter: `a.ltv.amount`
   * Audience Management trait: `c_a_ltv_amount`


### Dimensioni

* **Posizione (fino a 10 chilometri)**

   Populated by `trackLocation` methods.

   * Parametro dati contestuali/Target di Analytics:

      * `a.loc.lat.a`
      * `a.loc.lon.a`
   * Caratteristica Gestione dell'audience:

      * `c_a_loc_lat_a`
      * `c_a_loc_lon_a`


* **Posizione (fino a 100 m)**

   Viene compilata dai metodi trackLocation.

   * Parametro dati contestuali/Target di Analytics:

      * `a.loc.lat.b`
      * `a.loc.lon.b`
   * Caratteristica Gestione dell'audience:

      * `c_a_loc_lat_b`
      * `c_a_loc_lon_b`


* **Posizione (fino a 1 m)**

   Populated by `trackLocation` methods.

   * Parametro dati contestuali/Target di Analytics:

      * `a.loc.lat.c`
      * `a.loc.lon.c`
   * Caratteristica Gestione dell'audience:

      * `c_a_loc_lat_c`
      * `c_a_loc_lon_c`


* **Nome del punto di interesse**

   Viene compilata dai metodi trackLocation quando il dispositivo si trova entro un POI definito.

   * Analytics Context Data/Target parameter: `a.loc.poi`
   * Audience Management trait: `c_a_loc_poi`

* **Distanza dal centro del punto di interesse**

   Viene compilata dai metodi trackLocation quando il dispositivo si trova entro un POI definito.

   * Analytics Context Data/Target parameter: `a.loc.dist`
   * Audience Management trait: `c_a_loc_dist`

* **Valore "lifetime" del ciclo di vita (variabile di conversione)**

   Viene compilata dai metodi trackLifetimeValue.

   * Analytics Context Data/Target parameter: `a.ltv.amount`
   * Audience Management trait: `c_a_ltv_amount`

* **Codice di tracciamento**

   Viene compilata dalla funzione Acquisizione da app mobile. Viene generata automaticamente da Adobe Mobile Services.

   * Analytics Context Data/Target parameter: `a.referrer.campaign.trackingcode`
   * Audience Management trait: `c_a_referrer_campaign_trackingcode`

* **Campaign**

   Nome della campagna, memorizzato anche nella variabile della campagna. Viene compilata dalla funzione Acquisizione da app mobile.

   * Analytics Context Data/Target parameter: `a.referrer.campaign.name`
   * Audience Management trait: `c_a_referrer_campaign_name`

* **Contenuto campagna**

   Nome o ID del contenuto in cui è stato visualizzato il collegamento. Viene compilata dalla funzione Acquisizione da app mobile.

   * Analytics Context Data/Target parameter: `a.referrer.campaign.content`
   * Audience Management trait: `c_a_referrer_campaign_content`

* **Canale campagna**

   Canale di marketing, ad esempio banner o e-mail. Viene compilata dalla funzione Acquisizione da app mobile.

   * Analytics Context Data/Target parameter: `a.referrer.campaign.medium`
   * Audience Management trait: `c_a_referrer_campaign_medium`

* **Origine campagna**

   Referente originale, ad esempio una newsletter o una rete social media. Viene compilata dalla funzione Acquisizione da app mobile.

   * Analytics Context Data/Target parameter: `a.referrer.campaign.source`
   * Audience Management trait: `c_a_referrer_campaign_source`

* **Termine campagna**

   Keyword a pagamento o altri termini di cui si desidera tenere traccia con questa acquisizione. Viene compilata dalla funzione Acquisizione da app mobile.

   * Analytics Context Data/Target parameter: `a.referrer.campaign.term`
   * Audience Management trait: `c_a_referrer_campaign_term`
