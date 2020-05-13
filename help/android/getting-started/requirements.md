---
description: 'Prima di configurare una suite di rapporti e raccogliere dati dell''app Android, completa le seguenti attività di prerequisito '
seo-description: 'Prima di configurare una suite di rapporti e raccogliere dati dell''app Android, completa le seguenti attività di prerequisito '
seo-title: Prima di iniziare
solution: Marketing Cloud,Analytics
title: Prima di iniziare
topic: Developer and implementation
uuid: 0ca9e937-8d40-4570-9dbf-9aecc6ecedf6
translation-type: ht
source-git-commit: 82b3dc38a0325b3aa733b491ddad9b59dbe84eaa
workflow-type: ht
source-wordcount: '760'
ht-degree: 100%

---


# Prima di iniziare {#before-you-start}

Prima di configurare una suite di rapporti e raccogliere dati dell&#39;app Android, completa le seguenti attività di prerequisito:

## Attività per specifici ruoli {#section_8B9EA1FA189F4C6DB7D829F0B5844FBC}

Gli amministratori di Analytics e gli sviluppatori di app devono completare le seguenti attività:

### Amministratori di Analytics

Per configurare una suite di rapporti e raccogliere i dati dalle app per dispositivi mobili:

1. Completa una delle sezioni in [Eseguire l’accesso all’interfaccia utente di Adobe Mobile Services](../getting-started/requirements.md#section_690A2EC4572E47869F183974E932A6A8).
1. Crea un account Analytics per ogni sviluppatore di app.

Gli sviluppatori di app ora hanno accesso alla visualizzazione delle suite di rapporti che hai creato.

>[!IMPORTANT]
>
>Per creare una nuova suite di rapporti e scaricare gli SDK, devi essere un amministratore di Analytics.

### Sviluppatori di app

1. Assicurati che il tuo amministratore di Analytics abbia completato i passaggi descritti in *Amministratori di Analytics* all’interno di [Attività per specifici ruoli](../getting-started/requirements.md#section_8B9EA1FA189F4C6DB7D829F0B5844FBC).
1. Verifica che il tuo amministratore di Analytics abbia eseguito una delle procedure descritte in [Eseguire l’accesso all’interfaccia utente di Adobe Mobile Services](../getting-started/requirements.md#section_690A2EC4572E47869F183974E932A6A8).
1. Dopo che la suite di rapporti è stata configurata, completa i passaggi descritti in [Scaricare l’SDK](../getting-started/requirements.md#section_044C17DF82BC4FD8A3E409C456CE9A46).

Per ulteriori informazioni su ruoli e autorizzazioni, vedi [Ruoli e autorizzazioni](/help/using/gs/c-mob-roles-and-permissions.md).

## Eseguire l&#39;accesso all&#39;interfaccia utente di Adobe Mobile Services {#section_690A2EC4572E47869F183974E932A6A8}

Adobe Mobile Services è l’interfaccia di reportistica principale per l’analisi e il targeting delle app per dispositivi mobili. Dopo aver completato questi passaggi, puoi scaricare un file di configurazione preconfigurato con il server di raccolta dati, la suite di rapporti e molte altre impostazioni.

Puoi accedere all’interfaccia utente di Adobe Mobile Services in uno dei seguenti modi:

### Experience Cloud

Accedi a [Experience Cloud](https://experiencecloud.adobe.com) con il tuo Adobe ID. Questo metodo presuppone che tua società abbia eseguito il provisioning della in Experience Cloud e che tu abbia effettuato il collegamento all&#39;account di Analytics. Per ulteriori informazioni, consulta [Gestione di utenti e prodotti Experience Cloud](https://docs.adobe.com/content/help/it-IT/core-services/interface/manage-users-and-products/admin-getting-started.html).

>[!TIP]
>
>Se non sei sicuro se per la tua società sia già stato eseguito il provisioning in Experience Cloud, usa il tuo account Adobe Analytics esistente.

### Adobe Analytics

Fai clic su **[!UICONTROL Accedi con l&#39;account Analytics]** e immetti il nome della tua società Analytics, il tuo nome utente e la tua password.

## Creare una suite di rapporti {#section_7BC602ED1ABA42C6AB722F506B5219F3}

Per impostare una nuova suite di rapporti per la raccolta dei dati dall&#39;app e definire un&#39;app:

1. Accedi all’interfaccia utente di Mobile Services e digita [https://mobilemarketing.adobe.com/](https://mobilemarketing.adobe.com/) in un browser.
1. Fai clic su **[!UICONTROL Crea un’app]**.

   Se non trovi questo pulsante, fai clic su **[!UICONTROL Gestione app]** > **[!UICONTROL Aggiungi]**.

1. Nel menu a discesa **[!UICONTROL Suite di rapporti]**, seleziona **[!UICONTROL Nuova suite di rapporti]**.

1. Immetti il nome dell&#39;app e seleziona un tipo di suite di rapporti.

   Ad esempio, l&#39;ID suite di rapporti potrebbe essere `mycomobileappdev`. Devi impostare suite di rapporti e app distinte per le versioni di sviluppo e di produzione. Ripeti quindi questi passaggi quando sarà il momento di impostare la versione di produzione.
1. In **[!UICONTROL ID suite di rapporti]**, verifica che sia visualizzato il nome della tua suite di rapporti.
1. In **[!UICONTROL Copia impostazioni da]**, verifica che sia selezionato **[!UICONTROL Modello per app mobile]**.

   Questo modello abilita le marche temporali per la raccolta dei dati offline e attiva le variabili della soluzione mobile per l&#39;acquisizione delle metriche sul ciclo di vita.

1. Seleziona il tuo fuso orario e la tua valuta, quindi fai clic su **[!UICONTROL Salva]**.

## Scaricare l&#39;SDK {#section_044C17DF82BC4FD8A3E409C456CE9A46}

Per scaricare l&#39;SDK di Mobile:

1. accedi all’interfaccia utente di Mobile Services e digita [https://mobilemarketing.adobe.com/](https://mobilemarketing.adobe.com/) in un browser.
1. Nel riquadro a sinistra, fai clic sull’elenco a discesa **[!UICONTROL Tutte le applicazioni]** e seleziona la tua app.
Puoi anche selezionare l’app nel riquadro a destra.

   >[!IMPORTANT]
   >
   >Per visualizzare l’app nel riquadro a destra, devi prima crearne una. Consulta [Aggiungi una nuova app](https://docs.adobe.com/content/help/it-IT/mobile-services/using/manage-apps-ug/t-new-app.html) per informazioni sulla creazione di app.

1. Nel riquadro a sinistra dell&#39;app, fai clic su **[!UICONTROL Gestione impostazioni app]**.

   >[!IMPORTANT]
   >
   >Se non trovi l’opzione **[!UICONTROL Gestione impostazioni app]**, accertati di aver effettuato l’accesso ad Adobe Mobile Services. Per verificare il funzionamento, fai clic sull’icona del ![commutatore della soluzione](assets/solution-switcher.png) in alto a destra della pagina e accertati che **[!UICONTROL Adobe Mobile Services]** sia visualizzato in alto a sinistra.

1. Nella parte inferiore della pagina Gestione impostazioni app, nella sezione **[!UICONTROL Scaricare l’SDK di app]**, scarica l’SDK e l’app di esempio per la tua piattaforma.

>[!TIP]
>
>Nel download dell&#39;SDK viene automaticamente incluso un file di configurazione per la tua app; non è quindi necessario scaricare manualmente tale file. Tuttavia, se hai scaricato l&#39;SDK in precedenza e ora desideri ottenere le impostazioni aggiornate, dovrai scaricare nuovamente il file di configurazione.

Se usi Android Studio, puoi anche aggiungere la riga seguente al file `build.gradle` dell&#39;app:

```java
compile 'com.adobe.mobile:adobeMobileLibrary:4.13.7'
```

Considerazioni da ricordare:

* Sostituisci il numero di versione nell’esempio di codice con la versione appropriata degli SDK per Android.
* Scarica il file di configurazione e inseriscilo nel progetto.