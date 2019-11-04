---
description: Domande frequenti e risposte relative ad Adobe Mobile Services e descrizione generale delle funzioni.
keywords: dispositivi mobili
seo-description: Domande frequenti e risposte relative ad Adobe Mobile Services e descrizione generale delle funzioni.
seo-title: Domande frequenti
solution: Experience Cloud, Analytics
title: Domande frequenti
topic: Metrics (Metriche)
uuid: 62a9241c-2ada-483a-a594-b023916cb0b6
translation-type: ht
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Domande frequenti {#frequently-asked-questions}

La tabella seguente contiene un elenco delle domande frequenti per Adobe Mobile Services:

## SDK di Adobe Mobile {#section_9C2181F7B39A4BEB8EE6BCEFCF14C72F}

### L’SDK viene aggiornato spesso?

Sì, introduciamo costantemente nuovi aggiornamenti per garantire massima funzionalità, conformità e sicurezza dei nostri SDK. In genere viene rilasciata una nuova versione ogni mese. Gli aggiornamenti SDK di questo tipo sono aggiornamenti sostitutivi di tipo "drop-in" (per la versione 4x) per facilitarne l’implementazione. Per maggiori informazioni sugli aggiornamenti, consulta le [Note sulla versione](https://docs.adobe.com/content/help/it-IT/release-notes/experience-cloud/current.html).

### Quale versione SDK devo utilizzare?

La versione corrente degli SDK è la 4.11. Per ulteriori informazioni, consulta le [Note sulla versione](https://docs.adobe.com/content/help/it-IT/release-notes/experience-cloud/current.html).

### Dove si scaricano gli SDK?

Gli SDK per le singole piattaforme mobili possono essere scaricati dalla sezione [Gestisci impostazioni app](/help/using/c-manage-app-settings/c-manage-app-settings.md).

### Come si configurano gli SDK?

Dopo aver creato una nuova suite di rapporti per l’app, vai a Gestisci impostazioni app e configura tutte le opzioni richieste nella pagina Informazioni app. Dopo aver salvato la configurazione, scarica gli SDK richiesti dalla parte inferiore della pagina Gestione impostazioni app. L’SDK è preconfigurato con le opzioni che hai salvato e si trova nel file `ADBMobileConfig.json` all’interno del pacchetto SDK. Se modifichi delle impostazioni SDK nella pagina Gestione impostazioni app, ricordati di scaricare di nuovo i file dell’SDK o di aggiornare il file `ADBMobileConfig.json` con le modifiche apportate.

### Gli SDK di Adobe Mobile supportano IPv6 per iOS?

Gli SDK di Adobe Mobile usano gli stack di rete standard di iOS e Android. Per iOS, l’SDK utilizza NSURLSession (iOS versioni 7+) e NSURLConnection (iOS versioni 7 e successive), completamente compatibili con IPv6. Per gli sviluppatori che hanno creato o che utilizzano uno stack di rete proprio potrebbe essere utile verificarne la compatibilità per stabilire se è necessario apportare delle modifiche. Seguono alcune informazioni aggiuntive fornite da Apple:

*Se scrivi un’app lato client utilizzando API di rete di alto livello come NSURLSession e i framework CFNetwork, e ti connetti per nome, non dovrebbe essere necessario apportare alcuna modifica per garantire il funzionamento dell’app con gli indirizzi IPv6.* Per ulteriori informazioni, consulta [Supporto delle reti DNS64/NAT64 IPv6](https://developer.apple.com/library/content/documentation/NetworkingInternetWeb/Conceptual/NetworkingOverview/UnderstandingandPreparingfortheIPv6Transition/UnderstandingandPreparingfortheIPv6Transition.html#__/apple_ref/doc/uid/TP40010220-CH213-SW1).


## Adobe Analytics {#section_78EC9D83791F477AAED678720CEBA9F6}

### Che cosa sono le Metriche del ciclo di vita?

Le Metriche del ciclo di vita sono metriche "pronte all’uso" che vengono raccolte automaticamente al momento della prima implementazione dell’SDK nell’app. Per ulteriori informazioni, vedi [Metriche del ciclo di vita (Android)](/help/android/metrics.md) e [Metriche del ciclo di vita (iOS)](/help/ios/metrics.md).

### Come posso risolvere i problemi relativi alle regole di elaborazione?

Per maggiori informazioni, vedi [Suggerimenti e trucchi per le regole di elaborazione.](https://docs.adobe.com/content/help/it-IT/analytics/admin/admin-tools/processing-rules/processing-rules-tips.html)

### Posso inviare i miei dati analitici a più suite di rapporti?

Sì. Gli SDK forniscono la possibilità di inviare dati a più suite di rapporti di Adobe Analytics. Per catturare i dati in più suite di rapporti utilizzando una richiesta di immagine, imposta gli ID suite di rapporti nel campo **[!UICONTROL rsids]** nella sezione **[!UICONTROL anayltics**] del file`ADBMobileConfig.json`, separandoli con virgole e senza usare spazi. Per ulteriori informazioni, vedi [Configurazione JSON ADBMobile](/help/ios/configuration/json-config/json-config.md).

### In che cosa si differenziano le visite di Mobile dagli avvii?

Un avvio viene misurato dall’SDK quando un utente apre l’app per la prima volta o ritorna nell’app dopo che è trascorso un tempo maggiore del valore di timeout specificato. Il valore di timeout tipico è di 5 minuti (300 secondi) nel campo **[!UICONTROL lifecycleTimeout]** del file `ADBMobileConfig.json`. Una visita è un calcolo lato server eseguito da Adobe Analytics in base al primo e all’ultimo hit di dati inviati dall’SDK senza superare il timeout previsto per una visita. In genere, i timeout di sessione sono impostati su un valore di 30 minuti per una suite di rapporti. Anche se le visite sono dati analitici web di tipo tradizionale, questi hit possono comunque fornire informazioni utili sui comportamenti degli utenti nell’entrare e uscire dall’app.

## Messaggistica {#section_5EFDD2B2EBA543C09902FF979C89F2EC}

### Sono previsti limiti di dimensioni o di altro tipo per le notifiche push?

I messaggi di notifica push hanno un limite di 140 caratteri. Non sono invece previsti limiti per il numero di notifiche che è possibile inviare o pianificare né per la frequenza di invio di tali notifiche.

### Sono supportati i payload personalizzati per le notifiche push?

Sì, è supportato un payload push personalizzato che può essere codificato in JSON. Per i payload Android e iOS sono previsti limiti rispettivamente di 4 KB e 2 KB. Questi payload vengono inviati all’app tramite una notifica push o locale. Per ulteriori informazioni, consulta [Esperienza: messaggio push](/help/using/in-app-messaging/t-create-push-message/c-experience-push-message.md).

### Sono previsti limiti di dimensioni per i messaggi in-app?

I messaggi in-app pubblicati e attivi creati in Adobe Mobile Services sono ospitati su un server con un limite di 15 MB per ogni suite di rapporti app. Questo limite vale solo per il contenuto dei messaggi e le risorse in hosting presso Adobe. Non sono invece previste restrizioni per le risorse alle quali il messaggio in-app può fare riferimento su altri host o per quelle all’interno dell’app.

### Posso usare il mio codice HTML per i messaggi in-app?

Sì, supportiamo il codice HTML personalizzato per i messaggi in-app. Per ulteriori informazioni, consulta [Esperienza: messaggio in-app](/help/using/in-app-messaging/t-in-app-message/c-experience-in-app-message.md).

### Quali attivatori posso usare per inviare notifiche push o messaggi in-app?

È possibile scegliere qualsiasi dato o evento di Analytics che venga inviato come attivatore per la visualizzazione dei messaggi in-app. I messaggi in-app usano attivatori che si verificano localmente sul dispositivo. Se selezioni più attivatori, per attivare la visualizzazione del messaggio questi devono verificarsi tutti sullo stesso hit. Per ulteriori informazioni, consulta [Esperienza: messaggio in-app](/help/using/in-app-messaging/t-in-app-message/c-experience-in-app-message.md).

I messaggi push vengono inviati utilizzando segmenti Adobe Analytics preesistenti o segmenti personalizzati che possono essere creati sulla base di dati Analytics storici già raccolti. Per ulteriori informazioni, consulta [Esperienza: messaggio push](/help/using/in-app-messaging/t-create-push-message/c-experience-push-message.md).

### Perché ricevo un errore nel nome del messaggio in-app, messaggio push o collegamento di marketing che ho digitato?

Non puoi usare lo stesso nome di messaggio in-app, messaggio push o collegamento di marketing in più app che utilizzano la stessa suite di rapporti principale o virtuale. Per risolvere il problema, immetti un nome diverso.

## Posizione {#section_01208FE3B7764E0DADDCB9AD9E1FCD87}

### È previsto un limite per il numero di punti di interesse (PDI)?

Non esiste un limite specifico, ma consigliamo di creare o caricare non più di 5000 punti di interesse per assicurare prestazioni ottimali e non superare eventuali limiti di memoria del dispositivo dell’utente.

## Acquisizione {#section_B37F1129CD5843E890D0E54179455357}

### Posso attribuire le campagne ad attività in-app?

Sì. Con Adobe Mobile Services puoi creare trucchi di marketing per promuovere e indirizzare il traffico verso le tue app e collegare le campagne di acquisizione alle analitiche in-app e alle conversioni. Per ulteriori informazioni, vedi [Acquisizione](/help/using/acquisition-main/acquisition-main.md).

### Come si impostano collegamenti per l’acquisizione e il tracciamento dei nuovi utenti dell’app?

Puoi creare collegamenti di marketing che invitano gli utenti a scaricare applicazioni da Apple App Store e Google Play. Questi collegamenti ti consentono di attribuire i tuoi eventi di successo ai download. Per ulteriori informazioni, consulta [Marketing Links Builder](/help/using/acquisition-main/c-marketing-links-builder/c-marketing-links-builder.md).