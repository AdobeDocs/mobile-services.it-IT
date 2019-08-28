---
description: Puoi utilizzare queste informazioni per configurare le opzioni Servizi push nella pagina Gestione impostazioni app quando crei una nuova app o ne modifichi una già esistente.
keywords: dispositivi mobili
seo-description: Puoi utilizzare queste informazioni per configurare le opzioni Servizi push nella pagina Gestione impostazioni app quando crei una nuova app o ne modifichi una già esistente.
seo-title: Configurare i messaggi push
solution: Marketing Cloud, Analytics
title: Configurare i messaggi push
topic: Metrics (Metriche)
uuid: 6763858 d -6046-4 d 36-87 c 0-cf 3600 a 44 fb 1
translation-type: tm+mt
source-git-commit: 2c85c31d2fa54de26771553a6d349d3101e0048c

---


# Configure push messaging{#configure-push-messaging}

Puoi utilizzare queste informazioni per configurare le opzioni Servizi push nella pagina Gestione impostazioni app quando crei una nuova app o ne modifichi una esistente.

Prima di configurare i messaggi push, completa le attività preliminari nei [prerequisiti per abilitare i messaggi push](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/prerequisites-push-messaging.md).

* **Considerazioni sulle suite di rapporti**

   Puoi configurare un'app per app store per Apple e una per Google in ogni suite di rapporti. Se ti servono altre app, ad esempio una per un ambiente di produzione e una per un ambiente di sviluppo, configura una nuova app per app store e una nuova suite di rapporti per ciascun ambiente.

>[!IMPORTANT]
>
>Lo spostamento dell'app in una nuova suite di rapporti non è supportato. Se si effettua la migrazione a una nuova suite di rapporti, la configurazione push può interrompersi e i messaggi potrebbero non essere inviati.

1. Compila i seguenti campi nella sezione **[!UICONTROL Servizi push]**:

   * Apple

      **[!UICONTROL Chiave privata]**

      Browse to and select your valid private key `.p12`, `.key`, or `.pen`.

      >[!IMPORTANT]
      >If the file that you select for the **[!UICONTROL Private Key]** input also contains a certificate, you do not need to specify the certificate.

   * **[!UICONTROL Certificato]**

      Specifica un certificato valido. Questa opzione è necessaria solo se la **[!UICONTROL chiave privata]** che hai specificato **non** contiene già un certificato. Per ulteriori informazioni su come ottenere il certificato SSL e la chiave privata, consulta [Configurare app per l'uso di APNS o FCM](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/configure-app-apns-gcm.md).

   * Google

      **[!UICONTROL Chiave API]**

      Specifica una chiave API valida. Per ulteriori informazioni su come ottenere la chiave API, consulta [Configurare app per l'uso di APNS o FCM](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/configure-app-apns-gcm.md).

      Per maggiori informazioni, vedi i seguenti argomenti:

      * [Messaggi push in Android](/help/android/messaging-main/push-messaging/push-messaging.md)
      * [Messaggi push in iOS](/help/ios/messaging-main/push-messaging/push-messaging.md)

1. Fai clic su **[!UICONTROL Salva]**.
