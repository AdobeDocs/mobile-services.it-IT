---
description: Puoi utilizzare queste informazioni per configurare le opzioni Servizi push nella pagina Gestione impostazioni app quando crei una nuova app o ne modifichi una già esistente.
keywords: dispositivi mobili
solution: Experience Cloud,Analytics
title: Configurare i messaggi push
topic-fix: Metrics
uuid: 6763858d-6046-4d36-87c0-cf3600a44fb1
exl-id: d4989c31-2692-4062-8fae-d41c3e3c179b
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 100%

---

# Configurare i messaggi push {#configure-push-messaging}

Puoi utilizzare queste informazioni per configurare le opzioni Servizi push nella pagina Gestione impostazioni app quando crei una nuova app o ne modifichi una già esistente.

Prima di configurare i messaggi push, completa i prerequisiti in [Prerequisiti per abilitare i messaggi push](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/prerequisites-push-messaging.md).

* **Considerazioni sulle suite di rapporti**

   Puoi configurare un’app per app store per Apple e una per Google in ogni suite di rapporti. Se hai bisogno di altre app, ad esempio una per un ambiente di produzione e una per un ambiente di sviluppo, configura una nuova app per app store e una nuova suite di rapporti per ciascun ambiente.

>[!IMPORTANT]
>
>Lo spostamento dell’app a una nuova suite di rapporti non è supportato. Se si effettua la migrazione a una nuova suite di rapporti, la configurazione push può interrompersi e i messaggi potrebbero non essere inviati.

1. Compila i seguenti campi nella sezione **[!UICONTROL Servizi push]**:

   * Apple

      **[!UICONTROL Chiave privata]**

      Cerca e seleziona la tua chiave privata valida `.p12`, `.key` o `.pen`.

      >[!IMPORTANT]
      >Se il file che selezioni per l’immissione della **[!UICONTROL Chiave privata]** contiene anche un certificato, non devi specificare il certificato.

   * **[!UICONTROL Certificato]**

      Specifica un certificato valido. Questa opzione è necessaria solo se la **[!UICONTROL chiave privata]** che hai specificato **non** contiene già un certificato. Per ulteriori informazioni su come ottenere il certificato SSL e la chiave privata, consulta [Configurare l’app per l’uso di APNS o FCM](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/configure-app-apns-gcm.md).

   * Google

      **[!UICONTROL Chiave API]**

      Specifica una chiave API valida. Per ulteriori informazioni su come ottenere la chiave API, consulta [Configurare l’app per l’uso di APNS o FCM](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/configure-app-apns-gcm.md).

      Per maggiori informazioni, vedi i seguenti argomenti:

      * [Messaggi push in Android](/help/android/messaging-main/push-messaging/push-messaging.md)
      * [Messaggi push in iOS](/help/ios/messaging-main/push-messaging/push-messaging.md)

1. Fai clic su **[!UICONTROL Salva]**.
