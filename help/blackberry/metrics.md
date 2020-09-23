---
description: Queste sono le metriche e le dimensioni che possono essere misurate automaticamente dalla libreria mobile dopo che il ciclo di vita è stato implementato; è presente inoltre un collegamento per la risoluzione dei problemi dei dati del ciclo di vita.
keywords: android;library;mobile;sdk
seo-description: Queste sono le metriche e le dimensioni che possono essere misurate automaticamente dalla libreria mobile dopo che il ciclo di vita è stato implementato; è presente inoltre un collegamento per la risoluzione dei problemi dei dati del ciclo di vita.
seo-title: Metriche del ciclo di vita
solution: Experience Cloud,Analytics
title: Metriche del ciclo di vita
topic: Developer and implementation
uuid: 5a371f11-6521-410f-a01f-fc3b285b050f
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '888'
ht-degree: 70%

---


# Metriche del ciclo di vita {#lifecycle-metrics}

Queste sono le metriche e le dimensioni che possono essere misurate automaticamente dalla libreria mobile dopo che il ciclo di vita è stato implementato; è presente inoltre un collegamento per la risoluzione dei problemi dei dati del ciclo di vita.

Per ulteriori informazioni, consulta la Knowledge Base in [Risoluzione dei problemi dei dati](https://helpx.adobe.com/it/analytics/kb/troubleshoot-lifecycle-data.html)del ciclo di vita.

## Metriche e dimensioni del ciclo di vita {#section_78F036C4296F4BA3A47C2044F79C86C1}

Una volta configurate, le metriche del ciclo di vita vengono inviate nei parametri dei dati contestuali ad Analytics, nei parametri a Target con ciascuna chiamata Mbox e come segnale a Gestione dell&#39;audience. Analytics e Target usano lo stesso formato, mentre Gestione dell&#39;audience usa un prefisso diverso per ogni metrica.

Per Analytics, i dati contestuali inviati con ciascuna chiamata di tracciamento del ciclo di vita vengono catturati automaticamente e segnalati utilizzando la metrica o la dimensione.

### Metriche

* **a.media.name**

   Attivazione alla prima esecuzione dopo l&#39;installazione o reinstallazione.

   * Analytics context data/Target parameter: `a.InstallEvent`
   * Segnale di Audience Manager: `c_a_InstallEvent`

* **Aggiornamenti**

   Attivazione alla prima esecuzione dopo un aggiornamento o quando cambia il numero di versione.

   * Analytics context data/Target parameter: `a.UpgradeEvent`
   * Segnale di Audience Manager: `c_a_UpgradeEvent`

* **Utenti giornalieri coinvolti**

   Attivazione quando l&#39;applicazione viene utilizzata in un giorno particolare.

   >[!IMPORTANT]
   >
   >Questa metrica non viene memorizzata automaticamente in una metrica Analytics. Devi creare una regola di elaborazione che imposti un evento personalizzato per la cattura di questa metrica.

   * Analytics context data/Target parameter: `a.DailyEngUserEvent`
   * Segnale di Audience Manager: `c_a_DailyEngUserEvent`

* **Utenti mensili coinvolti**

   Attivazione quando l&#39;applicazione viene utilizzata in un mese particolare.  >>>>

   >[!IMPORTANT]
   >
   >Questa metrica non viene memorizzata automaticamente in una metrica Analytics. Devi creare una regola di elaborazione che imposti un evento personalizzato per la cattura di questa metrica.

   * Analytics context data/Target parameter: `a.MonthlyEngUserEvent`
   * Segnale di Audience Manager: `c_a_MonthlyEngUserEvent`

* **Avvii**

   Attivazione a ogni esecuzione, compresi arresti anomali e installazioni. Viene attivata anche alla ripresa in background quando viene superato il timeout della sessione del ciclo di vita.

   * Analytics context data/Target parameter: `a.LaunchEvent`
   * Segnale di Audience Manager: `c_a_LaunchEvent`

* **Arresti anomali**

   Attivazione quando l&#39;applicazione non viene messa in background prima della chiusura. L&#39;evento è inviato all&#39;avvio dell&#39;applicazione in seguito a un arresto anomalo. La reportistica di Adobe Mobile sugli arresti anomali non implementa un handler globale per eccezioni non rilevate.

   * Analytics context data/Target parameter: `a.CrashEvent`
   * Segnale di Audience Manager: `c_a_CrashEvent`

* **Durata sessione precedente**

   Segnala la durata di una precedente sessione dell&#39;applicazione in base a quanto tempo l&#39;applicazione è stata aperta e in primo piano.

   * Analytics context data/Target parameter: `a.PrevSessionLength`
   * Segnale di Audience Manager: `c_a_PrevSessionLength`

### Dimensioni

* **Data di installazione**

   Data del primo avvio dopo l&#39;installazione. Il formato della data è `MM/DD/YYYY`.

   * Analytics context data/Target parameter: `a.InstallDate`
   * Segnale di Audience Manager: `c_a_InstallDate`

* **ID app**

   Memorizza il nome e la versione dell’applicazione nel seguente formato:
   `[AppName] [BundleVersion]`.

   Un esempio di questo formato è `myapp 1.1`.

   * Analytics context data/Target parameter: `a.AppID`
   * Segnale di Audience Manager: `c_a_AppID`

* **Numero di avvii**

   Numero di volte per cui l&#39;applicazione è stata avviata o portata in primo piano.

   * Analytics context data/Target parameter: `a.Launches`
   * Segnale di Audience Manager: `c_a_Launches`

* **Giorni dal primo utilizzo**

   Numero di giorni dalla prima esecuzione.

   * Analytics context data/Target parameter: `a.DaysSinceFirstUse`
   * Segnale di Audience Manager: `c_a_DaysSinceFirstUse`

* **Giorni dall&#39;ultimo utilizzo**

   Numero di giorni dall&#39;ultimo utilizzo.

   * Analytics context data/Target parameter: `a.DaysSinceLastUse`
   * Segnale di Audience Manager: `c_a_DaysSinceLastUse`

* **Ora del giorno**

   Misura l&#39;ora in cui è stata avviata l&#39;app. Questa metrica usa il formato numerico a 24 ore e viene utilizzata per la suddivisione del tempo per determinare le ore di utilizzo di picco.

   * Analytics context data/Target parameter: `a.HourOfDay`
   * Segnale di Audience Manager: `c_a_HourOfDay`

* **Giorno della settimana**

   Numero del giorno della settimana in cui è stata avviata l&#39;app.

   * Analytics context data/Target parameter: `a.DayOfWeek`
   * Segnale di Audience Manager: `c_a_DayOfWeek`

* **Versione sistema operativo**

   Versione del sistema operativo.

   * Analytics context data/Target parameter: `a.OSVersion`
   * Segnale di Audience Manager: `c_a_OSVersion`

* **Giorni dall&#39;ultimo aggiornamento**

   Numero di giorni dalla modifica del numero di versione dell&#39;applicazione.

   >[!IMPORTANT]
   >
   >Questa metrica non viene memorizzata automaticamente in una variabile di Analytics. È necessario creare una regola di elaborazione per copiare questo valore in una variabile di Analytics da usare nei rapporti.

   * Analytics context data/Target parameter: `a.DaysSinceLastUpgrade`
   * Segnale di Audience Manager: `c_a_DaysSinceLastUpgrade`

* **Avvii dall&#39;ultimo aggiornamento**

   Numero di avvii dalla modifica del numero di versione dell&#39;applicazione.

   >[!IMPORTANT]
   >
   >Questa metrica non viene memorizzata automaticamente in una variabile di Analytics. È necessario creare una regola di elaborazione per copiare questo valore in una variabile di Analytics da usare nei rapporti.

   * Analytics context data/Target parameter: `a.LaunchesSinceUpgrade`
   * Segnale di Audience Manager: `c_a_LaunchesSinceUpgrade`

* **Nome del dispositivo**

   Memorizza il nome del dispositivo.

   * Analytics context data/Target parameter: `a.DeviceName`
   * Segnale di Audience Manager: `c_a_DeviceName`

* **Nome gestore**

   Memorizza il nome del gestore del servizio mobile, così come viene fornito dal dispositivo.

   >[!IMPORTANT]
   >
   >Questa metrica non viene memorizzata automaticamente in una variabile di Analytics. È necessario creare una regola di elaborazione per copiare questo valore in una variabile di Analytics da usare nei rapporti.

   * Analytics context data/Target parameter: `a.CarrierName`
   * Segnale di Audience Manager: `c_a_CarrierName`

* **Risoluzione**

   Larghezza x altezza in pixel reali.

   * Analytics context data/Target parameter: `a.Resolution`
   * Segnale di Audience Manager: `c_a_Resolution`

## Metriche e dimensioni aggiuntive per soluzioni mobile {#section_0B32BBF9CA734103BEDB5E755FFE5B31}

Le metriche e le dimensioni seguenti vengono acquisite nelle variabili di soluzioni mobile tramite il metodo elencato.

* **Posizione (fino a 10 chilometri)**

   Viene compilata dai metodi `trackLocation`.

   * Dati contestuali di Analytics/parametro Target:

      * `a.loc.lat.a`
      * `a.loc.lon.a`
   * Caratteristica di Gestione dell&#39;audience:

      * `c_a_loc_lat_a`
      * `c_a_loc_lon_a`


* **Posizione (fino a 100 m)**

   Viene compilata dai metodi `trackLocation`.

   * Dati contestuali di Analytics/parametro Target:

      * `a.loc.lat.b`
      * `a.loc.lon.b`
   * Caratteristica di Gestione dell&#39;audience:

      * `c_a_loc_lat_b`
      * `c_a_loc_lon_b`


* **Posizione (fino a 1 m)**

   Viene compilata dai metodi `trackLocation`.

   * Dati contestuali di Analytics/parametro Target:

      * `a.loc.lat.c`
      * `a.loc.lon.c`
   * Caratteristica di Gestione dell&#39;audience:

      * `c_a_loc_lat_c`
      * `c_a_loc_lon_c`


* **Nome del punto di interesse**

   Populated by `trackLocation` methods when device is within a defined POI.

   * Dati contestuali di Analytics/parametro Target:

      * `a.loc.poi`
   * Caratteristica di Gestione dell&#39;audience:

      * `c_a_loc_poi`


* **Distanza dal centro del punto di interesse**

   Populated by `trackLocation` methods when device is within a defined POI.

   * Dati contestuali di Analytics/parametro Target:

      * `a.loc.dist`
   * Caratteristica di Gestione dell&#39;audience:

      * `c_a_loc_dist`
