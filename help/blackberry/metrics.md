---
description: Queste sono le metriche e le dimensioni che possono essere misurate automaticamente dalla libreria mobile dopo che il ciclo di vita è stato implementato; è presente inoltre un collegamento per la risoluzione dei problemi dei dati del ciclo di vita.
keywords: android,libreria,mobile,sdk
solution: Experience Cloud Services,Analytics
title: Metriche del ciclo di vita
topic-fix: Developer and implementation
uuid: 5a371f11-6521-410f-a01f-fc3b285b050f
exl-id: d7436411-65bd-4cf7-ae3e-cec829a7690a
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '864'
ht-degree: 77%

---

# Metriche del ciclo di vita {#lifecycle-metrics}

Queste sono le metriche e le dimensioni che possono essere misurate automaticamente dalla libreria mobile dopo che il ciclo di vita è stato implementato; è presente inoltre un collegamento per la risoluzione dei problemi dei dati del ciclo di vita.

Per ulteriori informazioni, visitare la Knowledge Base all&#39;indirizzo [Risolvere i problemi dei dati del ciclo di vita](https://helpx.adobe.com/it/analytics/kb/troubleshoot-lifecycle-data.html).

## Metriche e dimensioni del ciclo di vita {#section_78F036C4296F4BA3A47C2044F79C86C1}

Una volta configurate, le metriche del ciclo di vita vengono inviate ad Analytics in parametri di dati contestuali, a Target in parametri con ogni chiamata Mbox e a Audience Manager come segnali. Analytics e Target usano lo stesso formato; la funzione di gestione dell’audience usa invece un prefisso diverso per ogni metrica.

Per Analytics, i dati contestuali inviati con ciascuna chiamata di tracciamento del ciclo di vita vengono acquisiti automaticamente e segnalati mediante l&#39;uso della metrica o della dimensione.

### Metriche

* **a.media.name**

   Attivazione alla prima esecuzione dopo l&#39;installazione o reinstallazione.

   * Dati contestuali di Analytics/Parametro di Target: `a.InstallEvent`
   * Segnale di Audience Manager: `c_a_InstallEvent`

* **Aggiornamenti**

   Attivazione alla prima esecuzione dopo un aggiornamento o quando cambia il numero di versione.

   * Dati contestuali di Analytics/Parametro di Target: `a.UpgradeEvent`
   * Segnale di Audience Manager: `c_a_UpgradeEvent`

* **Utenti giornalieri coinvolti**

   Attivazione quando l’applicazione viene utilizzata in un giorno particolare.

   >[!IMPORTANT]
   >
   >Questa metrica non viene memorizzata automaticamente in una metrica Analytics. Devi creare una regola di elaborazione che imposti un evento personalizzato per la cattura di questa metrica.

   * Dati contestuali di Analytics/Parametro di Target: `a.DailyEngUserEvent`
   * Segnale di Audience Manager: `c_a_DailyEngUserEvent`

* **Utenti mensili coinvolti**

   Attivazione quando l&#39;applicazione viene utilizzata in un mese particolare.  >>>>

   >[!IMPORTANT]
   >
   >Questa metrica non viene memorizzata automaticamente in una metrica Analytics. Devi creare una regola di elaborazione che imposti un evento personalizzato per la cattura di questa metrica.

   * Dati contestuali di Analytics/Parametro di Target: `a.MonthlyEngUserEvent`
   * Segnale di Audience Manager: `c_a_MonthlyEngUserEvent`

* **Avvii**

   Attivazione a ogni esecuzione, comprese quelle a seguito di arresti anomali e installazioni. Questa metrica viene attivata anche in seguito alla ripresa dal background oltre il tempo di timeout della sessione del ciclo di vita.

   * Dati contestuali di Analytics/Parametro di Target: `a.LaunchEvent`
   * Segnale di Audience Manager: `c_a_LaunchEvent`

* **Arresti anomali**

   Attivazione quando l&#39;applicazione non viene messa in background prima della chiusura. L&#39;evento è inviato all&#39;avvio dell&#39;applicazione in seguito a un arresto anomalo. La reportistica di Adobe Mobile sugli arresti anomali non implementa un handler globale per eccezioni non rilevate.

   * Dati contestuali di Analytics/Parametro di Target: `a.CrashEvent`
   * Segnale di Audience Manager: `c_a_CrashEvent`

* **Durata sessione precedente**

   Segnala la durata di una precedente sessione dell&#39;applicazione in base a quanto tempo l&#39;applicazione è stata aperta e in primo piano.

   * Dati contestuali di Analytics/Parametro di Target: `a.PrevSessionLength`
   * Segnale di Audience Manager: `c_a_PrevSessionLength`

### Dimensioni

* **Data di installazione**

   Data del primo avvio dopo l&#39;installazione. Il formato della data è `MM/DD/YYYY`.

   * Dati contestuali di Analytics/Parametro di Target: `a.InstallDate`
   * Segnale di Audience Manager: `c_a_InstallDate`

* **ID app**

   Memorizza il nome e la versione dell&#39;applicazione nel seguente formato:
   `[AppName] [BundleVersion]`.

   Un esempio di questo formato è `myapp 1.1`.

   * Dati contestuali di Analytics/Parametro di Target: `a.AppID`
   * Segnale di Audience Manager: `c_a_AppID`

* **Numero di avvii**

   Numero di volte per cui l’applicazione è stata avviata o portata in primo piano.

   * Dati contestuali di Analytics/Parametro di Target: `a.Launches`
   * Segnale di Audience Manager: `c_a_Launches`

* **Giorni dal primo utilizzo**

   Numero di giorni dalla prima esecuzione.

   * Dati contestuali di Analytics/Parametro di Target: `a.DaysSinceFirstUse`
   * Segnale di Audience Manager: `c_a_DaysSinceFirstUse`

* **Giorni dall’ultimo utilizzo**

   Numero di giorni dall’ultimo utilizzo.

   * Dati contestuali di Analytics/Parametro di Target: `a.DaysSinceLastUse`
   * Segnale di Audience Manager: `c_a_DaysSinceLastUse`

* **Ora del giorno**

   Misura l&#39;ora in cui è stata avviata l&#39;app. Questa metrica usa il formato numerico a 24 ore e viene utilizzata per la suddivisione del tempo per determinare le ore di utilizzo di picco.

   * Dati contestuali di Analytics/Parametro di Target: `a.HourOfDay`
   * Segnale di Audience Manager: `c_a_HourOfDay`

* **Giorno della settimana**

   Numero del giorno della settimana in cui è stata avviata l&#39;app.

   * Dati contestuali di Analytics/Parametro di Target: `a.DayOfWeek`
   * Segnale di Audience Manager: `c_a_DayOfWeek`

* **Versione sistema operativo**

   Versione del sistema operativo.

   * Dati contestuali di Analytics/Parametro di Target: `a.OSVersion`
   * Segnale di Audience Manager: `c_a_OSVersion`

* **Giorni dall’ultimo aggiornamento**

   Numero di giorni dalla modifica del numero di versione dell’applicazione.

   >[!IMPORTANT]
   >
   >Questa metrica non viene memorizzata automaticamente in una variabile di Analytics. È necessario creare una regola di elaborazione per copiare questo valore in una variabile di Analytics da usare nei rapporti.

   * Dati contestuali di Analytics/Parametro di Target: `a.DaysSinceLastUpgrade`
   * Segnale di Audience Manager: `c_a_DaysSinceLastUpgrade`

* **Avvii dall’ultimo aggiornamento**

   Numero di avvii dalla modifica del numero di versione dell’applicazione.

   >[!IMPORTANT]
   >
   >Questa metrica non viene memorizzata automaticamente in una variabile di Analytics. È necessario creare una regola di elaborazione per copiare questo valore in una variabile di Analytics da usare nei rapporti.

   * Dati contestuali di Analytics/Parametro di Target: `a.LaunchesSinceUpgrade`
   * Segnale di Audience Manager: `c_a_LaunchesSinceUpgrade`

* **Nome del dispositivo**

   Memorizza il nome del dispositivo.

   * Dati contestuali di Analytics/Parametro di Target: `a.DeviceName`
   * Segnale di Audience Manager: `c_a_DeviceName`

* **Nome gestore**

   Memorizza il nome del gestore del servizio mobile, così come viene fornito dal dispositivo.

   >[!IMPORTANT]
   >
   >Questa metrica non viene memorizzata automaticamente in una variabile di Analytics. È necessario creare una regola di elaborazione per copiare questo valore in una variabile di Analytics da usare nei rapporti.

   * Dati contestuali di Analytics/Parametro di Target: `a.CarrierName`
   * Segnale di Audience Manager: `c_a_CarrierName`

* **Risoluzione**

   Larghezza x altezza in pixel reali.

   * Dati contestuali di Analytics/Parametro di Target: `a.Resolution`
   * Segnale di Audience Manager: `c_a_Resolution`

## Metriche e dimensioni aggiuntive per soluzioni mobile {#section_0B32BBF9CA734103BEDB5E755FFE5B31}

Le metriche e le dimensioni seguenti vengono acquisite nelle variabili di soluzioni mobile tramite il metodo elencato.

* **Posizione (fino a 10 chilometri)**

   Viene compilata dai metodi `trackLocation`.

   * Dati contestuali di Analytics/Parametro di Target:

      * `a.loc.lat.a`
      * `a.loc.lon.a`
   * Caratteristica di Gestione dell&#39;audience:

      * `c_a_loc_lat_a`
      * `c_a_loc_lon_a`


* **Posizione (fino a 100 m)**

   Viene compilata dai metodi `trackLocation`.

   * Dati contestuali di Analytics/Parametro di Target:

      * `a.loc.lat.b`
      * `a.loc.lon.b`
   * Caratteristica di Gestione dell&#39;audience:

      * `c_a_loc_lat_b`
      * `c_a_loc_lon_b`


* **Posizione (fino a 1 m)**

   Viene compilata dai metodi `trackLocation`.

   * Dati contestuali di Analytics/Parametro di Target:

      * `a.loc.lat.c`
      * `a.loc.lon.c`
   * Caratteristica di Gestione dell&#39;audience:

      * `c_a_loc_lat_c`
      * `c_a_loc_lon_c`


* **Nome del punto di interesse**

   Popolato da `trackLocation` metodi quando il dispositivo si trova entro un POI definito.

   * Dati contestuali di Analytics/Parametro di Target:

      * `a.loc.poi`
   * Caratteristica di Gestione dell&#39;audience:

      * `c_a_loc_poi`


* **Distanza dal centro del punto di interesse**

   Popolato da `trackLocation` metodi quando il dispositivo si trova entro un POI definito.

   * Dati contestuali di Analytics/Parametro di Target:

      * `a.loc.dist`
   * Caratteristica di Gestione dell&#39;audience:

      * `c_a_loc_dist`
