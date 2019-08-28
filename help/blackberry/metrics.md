---
description: Queste sono le metriche e le dimensioni che possono essere misurate automaticamente dalla libreria mobile dopo che il ciclo di vita è stato implementato; è presente inoltre un collegamento per la risoluzione dei problemi dei dati del ciclo di vita.
keywords: android; libreria; mobile; sdk
seo-description: Queste sono le metriche e le dimensioni che possono essere misurate automaticamente dalla libreria mobile dopo che il ciclo di vita è stato implementato; è presente inoltre un collegamento per la risoluzione dei problemi dei dati del ciclo di vita.
seo-title: Metriche del ciclo di vita
solution: Marketing Cloud, Analytics
title: Metriche del ciclo di vita
topic: Sviluppatore e implementazione
uuid: 5 a 371 f 11-6521-410 f-a 01 f-fc 3 b 285 b 050 f
translation-type: tm+mt
source-git-commit: 6c440c2130781943796cdfb581a39a8167f5ba13

---


# Lifecycle metrics {#lifecycle-metrics}

Queste sono le metriche e le dimensioni che possono essere misurate automaticamente dalla libreria mobile dopo che il ciclo di vita è stato implementato; è presente inoltre un collegamento per la risoluzione dei problemi dei dati del ciclo di vita.

Per ulteriori informazioni, accedi alla sezione della Knowledge Base [Risoluzione dei problemi dei dati del ciclo di vita](https://helpx.adobe.com/analytics/kb/troubleshoot-lifecycle-data.html).

## Lifecycle metrics and dimensions {#section_78F036C4296F4BA3A47C2044F79C86C1}

Quando sono configurate, le metriche del ciclo di vita vengono inviate nei parametri dei dati contestuali ad Analytics, nei parametri a Target con ciascuna chiamata Mbox e come segnale a Gestione dell'audience. Analytics e Target usano lo stesso formato; Gestione dell'audience usa invece un prefisso diverso per ogni metrica.

Per Analytics, i dati contestuali inviati con ciascuna chiamata di tracciamento del ciclo di vita vengono catturati automaticamente e segnalati utilizzando la metrica o dimensione.

### Metrics (Metriche)

* **a.media.name**

   Attivazione alla prima esecuzione dopo l'installazione o reinstallazione.

   * Analytics context data/Target parameter: `a.InstallEvent`
   * Audience Manager signal: `c_a_InstallEvent`

* **Aggiornamenti**

   Attivazione alla prima esecuzione dopo un aggiornamento o quando cambia il numero di versione.

   * Analytics context data/Target parameter: `a.UpgradeEvent`
   * Audience Manager signal: `c_a_UpgradeEvent`

* **Utenti giornalieri coinvolti**

   Attivazione quando l'applicazione viene utilizzata in un giorno particolare.

   >[!IMPORTANT]
   >
   >Questa metrica non viene memorizzata automaticamente in una metrica Analytics. Devi creare una regola di elaborazione che imposti un evento personalizzato per la cattura di questa metrica.

   * Analytics context data/Target parameter: `a.DailyEngUserEvent`
   * Audience Manager signal: `c_a_DailyEngUserEvent`

* **Utenti mensili coinvolti**

   Attivazione quando l'applicazione viene utilizzata in un mese particolare.  &gt;&gt;&gt;&gt;

   >[!IMPORTANT]
   >
   >Questa metrica non viene memorizzata automaticamente in una metrica Analytics. Devi creare una regola di elaborazione che imposti un evento personalizzato per la cattura di questa metrica.

   * Analytics context data/Target parameter: `a.MonthlyEngUserEvent`
   * Audience Manager signal: `c_a_MonthlyEngUserEvent`

* **Avvii**

   Attivazione a ogni esecuzione, compresi arresti anomali e installazioni. Viene attivata anche alla ripresa dopo un periodo in background se viene superato il timeout di una sessione ciclo di vita.

   * Analytics context data/Target parameter: `a.LaunchEvent`
   * Audience Manager signal: `c_a_LaunchEvent`

* **Arresti anomali**

   Attivazione quando l'applicazione non viene messa in background prima della chiusura. L'evento è inviato all'avvio dell'applicazione in seguito a un arresto anomalo. La reportistica di Adobe Mobile sugli arresti anomali non implementa un handler globale per eccezioni non rilevate.

   * Analytics context data/Target parameter: `a.CrashEvent`
   * Audience Manager signal: `c_a_CrashEvent`

* **Durata sessione precedente**

   Segnala la durata di una precedente sessione dell'applicazione in base a quanto tempo l'applicazione è stata aperta e in primo piano.

   * Analytics context data/Target parameter: `a.PrevSessionLength`
   * Audience Manager signal: `c_a_PrevSessionLength`

### Dimensioni

* **Data di installazione**

   Data del primo avvio dopo l'installazione. Il formato della data `MM/DD/YYYY`è.

   * Analytics context data/Target parameter: `a.InstallDate`
   * Audience Manager signal: `c_a_InstallDate`

* **ID app**

   Memorizza il nome e la versione dell'applicazione nel seguente formato:
   `[AppName] [BundleVersion]`.

   Un esempio di questo formato è `myapp 1.1`.

   * Analytics context data/Target parameter: `a.AppID`
   * Audience Manager signal: `c_a_AppID`

* **Numero di avvii**

   Numero di volte per cui l'applicazione è stata avviata o portata in primo piano.

   * Analytics context data/Target parameter: `a.Launches`
   * Audience Manager signal: `c_a_Launches`

* **Giorni dal primo utilizzo**

   Numero di giorni dalla prima esecuzione.

   * Analytics context data/Target parameter: `a.DaysSinceFirstUse`
   * Audience Manager signal: `c_a_DaysSinceFirstUse`

* **Giorni dall'ultimo utilizzo**

   Numero di giorni dall'ultimo utilizzo.

   * Analytics context data/Target parameter: `a.DaysSinceLastUse`
   * Audience Manager signal: `c_a_DaysSinceLastUse`

* **Ora del giorno**

   Misura l'ora in cui è stata avviata l'app. Questa metrica usa il formato numerico a 24 ore e viene utilizzata per la suddivisione del tempo per determinare le ore di utilizzo di picco.

   * Analytics context data/Target parameter: `a.HourOfDay`
   * Audience Manager signal: `c_a_HourOfDay`

* **Giorno della settimana**

   Numero del giorno della settimana in cui è stata avviata l'app.

   * Analytics context data/Target parameter: `a.DayOfWeek`
   * Audience Manager signal: `c_a_DayOfWeek`

* **Versione sistema operativo**

   Versione del sistema operativo.

   * Analytics context data/Target parameter: `a.OSVersion`
   * Audience Manager signal: `c_a_OSVersion`

* **Giorni dall'ultimo aggiornamento**

   Numero di giorni dalla modifica del numero di versione dell'applicazione.

   >[!IMPORTANT]
   >
   >Questa metrica non viene memorizzata automaticamente in una variabile di Analytics. È necessario creare una regola di elaborazione per copiare questo valore in una variabile di Analytics da usare nei rapporti.

   * Analytics context data/Target parameter: `a.DaysSinceLastUpgrade`
   * Audience Manager signal: `c_a_DaysSinceLastUpgrade`

* **Avvii dall'ultimo aggiornamento**

   Numero di avvii dalla modifica del numero di versione dell'applicazione.

   >[!IMPORTANT]
   >
   >Questa metrica non viene memorizzata automaticamente in una variabile di Analytics. È necessario creare una regola di elaborazione per copiare questo valore in una variabile di Analytics da usare nei rapporti.

   * Analytics context data/Target parameter: `a.LaunchesSinceUpgrade`
   * Audience Manager signal: `c_a_LaunchesSinceUpgrade`

* **Nome del dispositivo**

   Memorizza il nome del dispositivo.

   * Analytics context data/Target parameter: `a.DeviceName`
   * Audience Manager signal: `c_a_DeviceName`

* **Nome gestore**

   Memorizza il nome del gestore del servizio mobile, così come viene fornito dal dispositivo.

   >[!IMPORTANT]
   >
   >Questa metrica non viene memorizzata automaticamente in una variabile di Analytics. È necessario creare una regola di elaborazione per copiare questo valore in una variabile di Analytics da usare nei rapporti.

   * Analytics context data/Target parameter: `a.CarrierName`
   * Audience Manager signal: `c_a_CarrierName`

* **Risoluzione**

   Larghezza x altezza in pixel reali.

   * Analytics context data/Target parameter: `a.Resolution`
   * Audience Manager signal: `c_a_Resolution`

## Additional mobile metrics and dimensions {#section_0B32BBF9CA734103BEDB5E755FFE5B31}

Le metriche e le dimensioni seguenti vengono acquisite in variabili di soluzioni mobili in base al metodo indicato.

* **Posizione (fino a 10 chilometri)**

   Populated by `trackLocation` methods.

   * Parametro di dati contestuali/Target di Analytics:

      * `a.loc.lat.a`
      * `a.loc.lon.a`
   * Caratteristica Gestione dell'audience:

      * `c_a_loc_lat_a`
      * `c_a_loc_lon_a`


* **Posizione (fino a 100 m)**

   Populated by `trackLocation` methods.

   * Parametro di dati contestuali/Target di Analytics:

      * `a.loc.lat.b`
      * `a.loc.lon.b`
   * Caratteristica Gestione dell'audience:

      * `c_a_loc_lat_b`
      * `c_a_loc_lon_b`


* **Posizione (fino a 1 m)**

   Populated by `trackLocation` methods.

   * Parametro di dati contestuali/Target di Analytics:

      * `a.loc.lat.c`
      * `a.loc.lon.c`
   * Caratteristica Gestione dell'audience:

      * `c_a_loc_lat_c`
      * `c_a_loc_lon_c`


* **Nome del punto di interesse**

   Viene compilata dai metodi `trackLocation` quando il dispositivo si trova entro un POI definito.

   * Parametro di dati contestuali/Target di Analytics:

      * `a.loc.poi`
   * Caratteristica Gestione dell'audience:

      * `c_a_loc_poi`


* **Distanza dal centro del punto di interesse**

   Viene compilata dai metodi `trackLocation` quando il dispositivo si trova entro un POI definito.

   * Parametro di dati contestuali/Target di Analytics:

      * `a.loc.dist`
   * Caratteristica Gestione dell'audience:

      * `c_a_loc_dist`
