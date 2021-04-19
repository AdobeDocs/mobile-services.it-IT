---
description: In queste tabelle trovi le metriche e le dimensioni che possono essere misurate automaticamente dalla libreria mobile dopo l’implementazione delle funzioni "lifecycle" sul ciclo di vita.
seo-description: In queste tabelle trovi le metriche e le dimensioni che possono essere misurate automaticamente dalla libreria mobile dopo l’implementazione delle funzioni "lifecycle" sul ciclo di vita.
seo-title: Metriche del ciclo di vita
solution: Experience Cloud,Analytics
title: Metriche del ciclo di vita
topic-fix: Developer and implementation
uuid: b795e383-d59b-4a3c-9e14-ffe8fb58412c
exl-id: b51b6c41-843f-499d-9cf2-7ce96ed82fc0
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '1108'
ht-degree: 100%

---

# Metriche del ciclo di vita {#lifecycle-metrics}

Sono qui elencate le metriche e le dimensioni che possono essere misurate automaticamente dalla libreria mobile dopo l&#39;implementazione delle funzioni &quot;lifecycle&quot; sul ciclo di vita.

## Nuova versione dell&#39;SDK per dispositivi mobili di Adobe Experience Platform

Hai bisogno di informazioni e documentazione relative all’SDK per dispositivi mobili di Adobe Experience Platform? Fai clic [qui](https://aep-sdks.gitbook.io/docs/) per la documentazione più recente.

A settembre 2018 è stata rilasciata una nuova versione principale dell&#39;SDK. Questi nuovi SDK per dispositivi mobili di Adobe Experience Platform sono configurabili tramite [Experience Platform Launch](https://www.adobe.com/it/experience-platform/launch.html).

* Per iniziare, vai su [Experience Platform Launch](https://launch.adobe.com/).
* Per visualizzare cosa è compreso negli archivi Experience Platform SDK, passa a [Github: SDK di Adobe Experience Platform](https://github.com/Adobe-Marketing-Cloud/acp-sdks).


## Metriche e dimensioni del ciclo di vita {#section_78F036C4296F4BA3A47C2044F79C86C1}

Una volta configurate le metriche del ciclo di vita, queste vengono inviate ad Analytics in parametri di dati contestuali, a Target in parametri con ogni chiamata Mbox e a Audience Manager come segnali. Analytics e Target usano lo stesso formato; Audience Manager usa invece un prefisso diverso per ogni metrica.

Per Analytics, i dati contestuali inviati con ciascuna chiamata di tracciamento del ciclo di vita sono catturati automaticamente e segnalati mediante l&#39;uso della metrica o della dimensione indicata nella prima colonna, con le eccezioni indicate nella prima colonna.

>[!TIP]
>
>Le eccezioni sono fornite nella descrizione.

### Metriche

* **Primi avvii**

   Attivazione alla prima esecuzione dopo l&#39;installazione o reinstallazione.

   * Dati contestuali di Analytics/Parametro di Target: `a.InstallEvent`
   * Segnale di Audience Manager: `c_a_InstallEvent`

* **Aggiornamenti**

   Attivazione alla prima esecuzione dopo l&#39;aggiornamento ogni volta che cambia il numero di versione.

   * Dati contestuali di Analytics/Parametro di Target: `a.UpgradeEvent`
   * Segnale di Audience Manager: `c_a_UpgradeEvent`

* **Utenti giornalieri coinvolti**

   Attivazione quando l’applicazione viene utilizzata in un giorno particolare.

   * Dati contestuali di Analytics/Parametro di Target: `a.DailyEngUserEvent`
   * Segnale di Audience Manager: `c_a_DailyEngUserEvent`

* **Utenti mensili coinvolti**

   Attivazione quando l&#39;applicazione viene utilizzata in un mese particolare.

   * Dati contestuali di Analytics/Parametro di Target: `a.MonthlyEngUserEvent`
   * Segnale di Audience Manager: `c_a_MonthlyEngUserEvent`

* **Avvii**

   Attivazione a ogni esecuzione, comprese quelle a seguito di arresti anomali e installazioni. Questa metrica viene attivata anche quando l’app viene ripresa dal background oltre il tempo di timeout della sessione del ciclo di vita.

   * Dati contestuali di Analytics/Parametro di Target: `a.LaunchEvent`
   * Segnale di Audience Manager: `c_a_LaunchEvent`

* **Arresti anomali**

   Attivazione quando l&#39;applicazione non viene messa in background prima della chiusura. L&#39;evento viene inviato quando si riavvia l&#39;applicazione dopo l&#39;arresto anomalo.  La reportistica di Adobe Mobile sugli arresti anomali non implementa un handler globale per eccezioni non rilevate.

   * Dati contestuali di Analytics/Parametro di Target: `a.CrashEvent`
   * Segnale di Audience Manager: `c_a_CrashEvent`

* **Durata sessione precedente**

   Segnala la durata di una precedente sessione dell&#39;applicazione in base a quanto tempo l&#39;applicazione è stata aperta e in primo piano.

   * Dati contestuali di Analytics/Parametro di Target: `a.PrevSessionLength`
   * Segnale di Audience Manager: `c_a_PrevSessionLength`

>[!IMPORTANT]
>
> Le metriche *Utenti giornalieri coinvolti* e *Utenti mensili coinvolti* non vengono memorizzate automaticamente in una metrica di Analytics. Devi creare una regola di elaborazione che imposti un evento personalizzato per l’acquisizione di queste metriche.

#### Dimensioni

* **Data di installazione**

   Data del primo avvio dopo l&#39;installazione.  Il formato della data è `MM/DD/YYYY`.

   * Dati contestuali di Analytics/Target: `a.InstallDate`
   * Gestione dell&#39;audience: `c_a_InstallDate`

* **ID app**

   Memorizza il nome e la versione dell&#39;applicazione nel formato `[AppName] [BundleVersion]`. Ad esempio, `myapp 1.1`.

   * Dati contestuali di Analytics/Target: `a.AppID`
   * Gestione dell&#39;audience: `c_a_AppID`

* **Numero di avvii**

   Numero di volte per cui l’applicazione è stata avviata o portata in primo piano.

   * Dati contestuali di Analytics/Target: `a.Launches`
   * Gestione dell&#39;audience: `c_a_Launches`

* **Giorni dal primo utilizzo**

   Numero di giorni dalla prima esecuzione.

   * Dati contestuali di Analytics/Target: `a.DaysSinceFirstUse`
   * Gestione dell&#39;audience: `c_a_DaysSinceFirstUse`

* **Giorni dall’ultimo utilizzo**

   Numero di giorni dall’ultimo utilizzo.

   * Dati contestuali di Analytics/Target: `a.DaysSinceLastUse`
   * Gestione dell&#39;audience: `c_a_DaysSinceLastUse`

* **Ora del giorno**

   Misura l’ora in cui è stata avviata l’app (nel formato numerico a 24 ore). Utilizzato per la suddivisione del tempo per determinare le ore di utilizzo di picco.

   * Dati contestuali di Analytics/Target: `a.HourOfDay`
   * Gestione dell&#39;audience: `c_a_HourOfDay`

* **Giorno della settimana**

   Numero del giorno della settimana in cui è stata avviata l’app.

   * Dati contestuali di Analytics/Target: `a.DayOfWeek`
   * Gestione dell&#39;audience: `c_a_DayOfWeek`

* **Versione sistema operativo**

   Numero di giorni dalla modifica del numero di versione dell’applicazione.

   * Dati contestuali di Analytics/Target: `a.OSVersion`
   * Gestione dell&#39;audience: `c_a_OSVersion|OS version`

* **Giorni dall’ultimo aggiornamento**

   Giorni dall&#39;ultimo aggiornamento.

   * Dati contestuali di Analytics/Target: `a.DaysSinceLastUpgrade`
   * Gestione dell&#39;audience: `c_a_DaysSinceLastUpgrade`

* **Avvii dall’ultimo aggiornamento**

   Numero di avvii dalla modifica del numero di versione dell’applicazione.

   * Dati contestuali di Analytics/Target: `a.LaunchesSinceUpgrade`
   * Gestione dell&#39;audience: `c_a_LaunchesSinceUpgrade`

* **Nome del dispositivo**

   Memorizza il nome del dispositivo.  Stringa di due cifre separate da virgola che identifica il dispositivo iOS. Di norma il primo numero rappresenta la generazione del dispositivo e il secondo numero indica membri diversi della famiglia di dispositivi. Per un elenco dei nomi dei dispositivi più comuni, vedi      Versioni dei dispositivi iOS.

   * Dati contestuali di Analytics/Target: `a.DeviceName`
   * Gestione dell&#39;audience: `c_a_DeviceName`

* **Nome gestore**

   Memorizza il nome del gestore del servizio mobile, così come viene fornito dal dispositivo.

   * Dati contestuali di Analytics/Target: `a.CarrierName`
   * Gestione dell&#39;audience: `c_a_CarrierName`

* **Risoluzione**

   Larghezza x altezza in pixel reali.

   * Dati contestuali di Analytics/Target: `a.Resolution`
   * Gestione dell&#39;audience: `c_a_Resolution`
   >[!IMPORTANT]
   >
   >Le dimensioni *Giorni dall’ultimo aggiornamento*, *Avvii dall’ultimo aggiornamento* e *Nome gestore* non vengono memorizzate automaticamente in una variabile Analytics. È necessario creare una regola di elaborazione per copiare i valori in una variabile di Analytics da usare nei rapporti.


## Metriche e dimensioni aggiuntive per soluzioni mobile {#section_0B32BBF9CA734103BEDB5E755FFE5B31}

Le metriche e le dimensioni seguenti vengono acquisite nelle variabili di soluzioni mobile tramite il metodo elencato.

### Metriche

* **Tempo azione totale**

   Viene compilata dai metodi trackTimedAction.

   * Dati contestuali di Analytics/Parametro di Target: `a.action.time.total`
   * Caratteristica di Gestione dell&#39;audience: `c_a_action_time_total`

* **Tempo azione in-app**

   Viene compilata dai metodi trackTimedAction.

   * Dati contestuali di Analytics/Parametro di Target: `a.action.time.inapp`
   * Caratteristica di Gestione dell&#39;audience: `c_a_action_time_inapp`

* **Valore &quot;lifetime&quot; del ciclo di vita (evento)**

   Viene compilata dai metodi trackLifetimeValue.

   * Dati contestuali di Analytics/Parametro di Target: `a.ltv.amount`
   * Caratteristica di Gestione dell&#39;audience: `c_a_ltv_amount`


### Dimensioni

* **Posizione (fino a 10 chilometri)**

   Viene compilata dai metodi `trackLocation`.

   * Dati contestuali di Analytics/Parametro di Target:

      * `a.loc.lat.a`
      * `a.loc.lon.a`
   * Caratteristica di Gestione dell&#39;audience:

      * `c_a_loc_lat_a`
      * `c_a_loc_lon_a`


* **Posizione (fino a 100 m)**

   Viene compilata dai metodi trackLocation.

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

   Viene compilata dai metodi trackLocation quando il dispositivo si trova entro un POI definito.

   * Dati contestuali di Analytics/Parametro di Target: `a.loc.poi`
   * Caratteristica di Gestione dell&#39;audience: `c_a_loc_poi`

* **Distanza dal centro del punto di interesse**

   Viene compilata dai metodi trackLocation quando il dispositivo si trova entro un POI definito.

   * Dati contestuali di Analytics/Parametro di Target: `a.loc.dist`
   * Caratteristica di Gestione dell&#39;audience: `c_a_loc_dist`

* **Valore &quot;lifetime&quot; del ciclo di vita (variabile di conversione)**

   Viene compilata dai metodi trackLifetimeValue.

   * Dati contestuali di Analytics/Parametro di Target: `a.ltv.amount`
   * Caratteristica di Gestione dell&#39;audience: `c_a_ltv_amount`

* **Codice di tracciamento**

   Viene compilata dalla funzione Acquisizione da app mobile. Il codice viene generato automaticamente da Adobe Mobile Services.

   * Dati contestuali di Analytics/Parametro di Target: `a.referrer.campaign.trackingcode`
   * Caratteristica di Gestione dell&#39;audience: `c_a_referrer_campaign_trackingcode`

* **Campaign**

   Nome della campagna, memorizzato anche nella variabile della campagna. Viene compilata dalla funzione Acquisizione da app mobile.

   * Dati contestuali di Analytics/Parametro di Target: `a.referrer.campaign.name`
   * Caratteristica di Gestione dell&#39;audience: `c_a_referrer_campaign_name`

* **Contenuto campagna**

   Nome o ID del contenuto che ha visualizzato il collegamento. Viene compilata dalla funzione Acquisizione da app mobile.

   * Dati contestuali di Analytics/Parametro di Target: `a.referrer.campaign.content`
   * Caratteristica di Gestione dell&#39;audience: `c_a_referrer_campaign_content`

* **Canale campagna**

   Canale di marketing, ad esempio banner o e-mail. Viene compilata dalla funzione Acquisizione da app mobile.

   * Dati contestuali di Analytics/Parametro di Target: `a.referrer.campaign.medium`
   * Caratteristica di Gestione dell&#39;audience: `c_a_referrer_campaign_medium`

* **Origine campagna**

   Referente originale, ad esempio newsletter o Social media network. Viene compilata dalla funzione Acquisizione da app mobile.

   * Dati contestuali di Analytics/Parametro di Target: `a.referrer.campaign.source`
   * Caratteristica di Gestione dell&#39;audience: `c_a_referrer_campaign_source`

* **Termine campagna**

   Parole chiave a pagamento o altri termini di cui tenere traccia con questa acquisizione. Viene compilata dalla funzione Acquisizione da app mobile.

   * Dati contestuali di Analytics/Parametro di Target: `a.referrer.campaign.term`
   * Caratteristica di Gestione dell&#39;audience: `c_a_referrer_campaign_term`
