---
description: Devi eseguire queste operazioni prima di configurare i messaggi push nelle applicazioni.
keywords: dispositivi mobili
seo-description: Devi eseguire queste operazioni prima di configurare i messaggi push nelle applicazioni.
seo-title: Prerequisiti per abilitare i messaggi push
solution: Marketing Cloud,Analytics
title: Prerequisiti per abilitare i messaggi push
topic: Metrics (Metriche)
uuid: 194e6e07-b794-4152-a838-a4125c3292d4
translation-type: tm+mt
source-git-commit: 92b1e430293fbded666e8af3f01393898c0e5811

---


# Prerequisites to enable push messaging {#prerequisites-to-enable-push-messaging}

You must complete these tasks before configuring push messaging in your applications.

## Abilita Experience Cloud per la tua società

La tua azienda Adobe Analytics deve essere abilitata per Experience Cloud. Potete verificare lo stato del vostro responsabile commerciale di Adobe.

## Installare e configurare l’SDK di Mobile

* **Installare l'SDK di Mobile**

   To configure push messaging, you must download and install at least version 4.6 or later of the Mobile SDK. For more information, see [Download the SDKs](/help/using/c-manage-app-settings/c-mob-confg-app/t-config-analytics/download-sdk.md).

* **Configurare i servizi push**

   Devi configurare i servizi push nell'SDK di Mobile.
Per ulteriori informazioni, consulta:

   * [Push Messaging in Android](/help/android/messaging-main/push-messaging/push-messaging.md)
   * [Push Messaging in iOS](/help/ios/messaging-main/push-messaging/push-messaging.md)

## Accedi al servizio core Mobile utilizzando il tuo Adobe ID

>[!IMPORTANT]
>
>Per utilizzare la funzionalità Servizi push, gli utenti devono accedere al servizio core Mobile utilizzando il proprio Adobe ID e il loro account Analytics deve essere collegato ai loro Adobe ID. La funzione Servizi push non è disponibile se gli utenti accedono utilizzando altri account Adobe Analytics.

Se gli utenti non dispongono di un Adobe ID, effettua i seguenti passaggi:

1. (**Experience Cloud Administrator**) Invite users to the Experience Cloud.

1. (**User**) Create a personal Adobe ID using the instructions that you received from the Experience Cloud administrator.

   A ogni utente viene inviato automaticamente un messaggio e-mail dopo che l'amministratore ha eseguito l'operazione precedente.

1. (**Users**) Log in to Mobile using their Adobe ID.

## Collegare gli account degli utenti in Experience Cloud

Ogni utente deve collegare l’account della soluzione Analytics dall’organizzazione Experience Cloud.

1. Per accedere a Experience Cloud con un Adobe ID, digita [https://marketing.adobe.com](https://marketing.adobe.com) in un browser.

1. Nell'angolo in alto a destra, seleziona il nome dell'azienda Analytics.

1. Fai clic su **[!UICONTROL Aggiungi organizzazione]**, quindi seleziona **Adobe SiteCatalyst/Adobe Social]dall'elenco a discesa.[!UICONTROL **

1. Inserisci il nome dell'azienda e le credenziali legacy dell'azienda in questione, quindi fai clic su **[!UICONTROL Collega account]**.

   Ora l'Adobe ID è collegato al tuo account Analytics, alla tua società e alle relative credenziali di accesso.

Per ulteriori informazioni, vedi [Risoluzione dei problemi di collegamento dell'account](https://marketing.adobe.com/resources/help/en_US/mcloud/organizations.html).

## Configurare i servizi push e il servizio ID SDK nell'interfaccia utente di Mobile

Finché non attivi il servizio ID per la tua app, la sezione **[!UICONTROL Servizi push]risulta disabilitata.** Tuttavia, dopo aver attivato il servizio ID, la sezione Servizi push viene abilitata. Per ulteriori informazioni sull'abilitazione dei servizi push, consulta [Configurare le opzioni](/help/using/c-manage-app-settings/c-mob-confg-app/t-config-visitor.md)del servizio ID SDK.

>[!IMPORTANT]: Fai clic su **[!UICONTROL Salva]** per salvare le modifiche e aggiornare i servizi push.
>
>Puoi configurare un'app per app store per Apple e una per Google in ogni suite di rapporti. Se ti servono altre app, ad esempio una per un ambiente di produzione e una per un ambiente di sviluppo, configura una nuova app per app store e una nuova suite di rapporti per ciascun ambiente.

* Per **Apple**, trascina e rilascia la tua chiave privata e/o il certificato. Se la chiave privata è protetta da una password, inserisci anche la password.

   * Per **Chiave privata**, trascina e rilascia il file della chiave privata nell'apposita casella.

      Puoi anche fare clic su **[!UICONTROL Sfoglia]per selezionare il file.** Il file contiene la chiave privata. The certificate might also be included in this file (`.p12`, `pkcs12`, `.pfx`, `.key`, `.pem`).

   * Per **Password chiave privata**, se il file della chiave privata è crittografato, digita la password.

      (Condizionale) Per **Certificato**, trascina e rilascia il file del certificato nella casella. Puoi anche fare clic su **[!UICONTROL Sfoglia]per selezionare il file.** This field is not required if the private-key file also contains the certificate ( `.cert`, `.cer`, `.crt`, `.pem`).

* Per **Google**, specifica la chiave API dell'app.

   Fai clic su **[!UICONTROL Prova]per verificare che l'app e Mobile Services siano configurati correttamente.** Questa opzione è utile per le attività di debug e la risoluzione dei problemi.

   Digita i token push del dispositivo al quale vuoi inviare il messaggio. Puoi inviare il messaggio a più dispositivi specificando i diversi token in un elenco separato da virgole.

   ![push test message](assets/push_test_list.png)
