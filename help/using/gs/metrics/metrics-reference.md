---
description: Seguono alcune informazioni di riferimento per le metriche e le dimensioni predefinite di Mobile.
keywords: dispositivi mobili
seo-description: Seguono alcune informazioni di riferimento per le metriche e le dimensioni predefinite di Mobile.
seo-title: Riferimento per le metriche e le dimensioni di Mobile
solution: Experience Cloud, Analytics
title: Riferimento per le metriche e le dimensioni di Mobile
topic: Metrics (Metriche)
uuid: 96170ae7-8553-4f3e-ae01-65e5b664adf4
translation-type: ht
source-git-commit: 056bb3edb94c2ceb2961bbe8e4851c20429e1ea2

---


# Riferimento per le metriche e le dimensioni di Mobile {#mobile-metrics-and-dimensions-reference}

Queste informazioni sono utili per comprendere meglio le metriche e le dimensioni predefinite di Mobile.

>[!TIP]
>
>Le autorizzazioni relative a metriche e dimensioni impostate in Adobe Analytics valgono anche per Mobile Services. Quando si tenta di eseguire un rapporto senza le autorizzazioni appropriate, si verifica un errore.

## Metriche {#section_6704C815147D44AF96151D626BEB813C}

Elenco delle metriche predefinite per dispositivi mobili:

* **Primi avvii**

   Attivazione alla prima esecuzione dopo un’installazione o reinstallazione.

* **Aggiornamenti**

   Attivazione alla prima esecuzione dopo un aggiornamento o quando cambia il numero di versione.

* **Utenti giornalieri coinvolti**

   Attivazione quando l’applicazione viene utilizzata in un giorno particolare.

   >[!TIP]
   >L’evento Utenti giornalieri coinvolti non viene memorizzato automaticamente in una metrica Analytics. Devi creare una regola di elaborazione che imposti un evento personalizzato per la cattura di questa metrica.

* **Utenti mensili coinvolti**

   Attivazione quando l’applicazione viene utilizzata durante un mese.

   >[!TIP]
   >L’evento Utenti mensili coinvolti non viene memorizzato automaticamente in una metrica Analytics. Devi creare una regola di elaborazione che imposti un evento personalizzato per la cattura di questa metrica.

* **Avvii**

   Attivazione a un’esecuzione che non è un’installazione o un aggiornamento. L’attivazione ha luogo anche quando l’applicazione viene portata in primo piano. Per impostazione predefinita, viene attivato un nuovo avvio dopo che l’applicazione sia rimasta in background per almeno cinque minuti. Il tempo di esecuzione in background trascorso il quale viene attivato un nuovo avvio può essere configurato nelle **[!UICONTROL Opzioni SDK Analytics]** nella pagina Gestione impostazioni app. Per ulteriori informazioni, vedi la riga *Timeout sessione (secondi)* in [Configurare le opzioni SDK Analytics](/help/using/c-manage-app-settings/c-mob-confg-app/t-config-analytics/t-config-analytics.md).

   >[!IMPORTANT]
   >A causa di come vengono calcolate le visite in [!UICONTROL Adobe Analytics] e gli avvii di app mobili in [!UICONTROL Adobe Mobile Services], è possibile che nei rapporti figurino risultati differenti. Per maggiori informazioni, consulta [Confrontare visite e avvii di app mobili](https://helpx.adobe.com/it/analytics/kb/compare-visits-and-mobile-app-launches.html).

* **Arresti anomali**

   Attivazione quando l’applicazione non si chiude correttamente. L’evento è inviato all’avvio dell’applicazione dopo un arresto anomalo.

   >[!TIP]
   >L’applicazione viene considerata in arresto se non viene chiamato il comando di uscita.

* **Lunghezza totale della sessione**

   Totale aggregato della lunghezza della sessione.

## Dimensioni {#section_1784C7E859F64CCEB95C5DD1DCF5C98D}

Elenco delle dimensioni predefinite per dispositivi mobili:

* **Data di installazione**

   Data del primo avvio dopo l’installazione. Il formato della data è *MM/GG/AAAA*.

* **ID app**

   Memorizza il nome e la versione dell’applicazione nel seguente formato: `[AppName] [BundleVersion]`. Ad esempio, `myapp 1.1`.

* **Numero di avvii**

   Numero di volte per cui l’applicazione è stata avviata o portata in primo piano.

* **Giorni dal primo utilizzo**

   Numero di giorni dalla prima esecuzione.

* **Giorni dall’ultimo utilizzo**

   Numero di giorni dall’ultimo utilizzo.

* **Ora del giorno**

   Misura l’ora in cui è stata avviata l’app (nel formato numerico a 24 ore). Questa dimensione viene utilizzata anche per la suddivisione del tempo per determinare le ore di utilizzo di picco.

* **Giorno della settimana**

   Numero del giorno della settimana in cui è stata avviata l’app.

* **Sistema operativo**

   Sistema operativo del dispositivo.

* **Versione sistema operativo**

   Versione del sistema operativo.

* **Giorni dall’ultimo aggiornamento**

   Numero di giorni dalla modifica del numero di versione dell’applicazione.

   >[!TIP]
   >
   >La metrica Giorni dall’ultimo aggiornamento non viene memorizzata automaticamente in una variabile di Analytics. È necessario creare una regola di elaborazione per copiare questo valore in una variabile di Analytics da usare nei rapporti.

* **Avvii dall’ultimo aggiornamento**

   Numero di avvii dalla modifica del numero di versione dell’applicazione.

   >[!TIP]
   >
   >La metrica Avvii dall’ultimo aggiornamento non viene memorizzata automaticamente in una variabile di Analytics. È necessario creare una regola di elaborazione per copiare questo valore in una variabile di Analytics da usare nei rapporti.

* **Nome del dispositivo**

   Memorizza il nome del dispositivo. In iOS, una stringa di due cifre separate da virgola identifica il dispositivo iOS. Il primo numero rappresenta la generazione del dispositivo e il secondo numero indica membri diversi della famiglia di dispositivi. Per un elenco completo dei nomi dei dispositivi più comuni, vedi [Versioni dei dispositivi iOS](/help/ios/reference/device-versions.md).

* **Nome gestore**

   Memorizza il nome del provider di servizi mobili.

* **Risoluzione**

   Larghezza e altezza in pixel reali.
