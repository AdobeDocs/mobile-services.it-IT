---
description: Queste informazioni sono utili per risolvere eventuali problemi dei messaggi push.
keywords: dispositivi mobili
solution: Experience Cloud Services,Analytics
title: Risoluzione dei problemi dei messaggi push
topic-fix: Metrics
uuid: 87d7dcb6-82a8-46e3-a6ed-7f895a22f2af
exl-id: dda84d30-2a7b-496c-b8f3-3bd6b97076aa
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 100%

---

# Risoluzione dei problemi dei messaggi push {#troubleshooting-push-messaging}

Queste informazioni sono utili per risolvere eventuali problemi dei messaggi push.

## Perché a volte si verificano dei ritardi nell’invio dei messaggi push?

I seguenti tipi di ritardo possono essere associati ai messaggi push per Mobile Services:

* **Attesa degli hit di Analytics**

   Per ogni suite di rapporti, un’impostazione consente di determinare quando elaborare gli hit di Analytics in arrivo. L&#39;impostazione predefinita è pari a 1 ora, allo scoccare dell&#39;ora. L&#39;effettiva elaborazione degli hit di Analytics potrebbe richiedere fino a 30 minuti, ma in genere dura 15-20 minuti.

   Ad esempio, una suite di rapporti elabora gli hit ogni ora. Considerando il tempo massimo di elaborazione richiesto (30 minuti), potrebbero essere necessari fino a 90 minuti perché un hit in arrivo sia disponibile per un messaggio push. Se un utente ha avviato l’app alle 09:01, l’hit risulterebbe nell’interfaccia di Mobile Services come nuovo utente univoco tra le 10:15 e le 10:30.

* **Attesa del servizio push**

   Il servizio push (APNS o GCM) potrebbe non inviare subito il messaggio. Anche se raramente, è possibile che si verifichi un ritardo di 5-10 minuti. Nella pagina Messaggi, fai clic sul collegamento Visualizza associato al messaggio per verificare che il messaggio push sia stato inviato al servizio push. Nel rapporto, il numero di invii con esito positivo è elencato nella colonna Pubblicato.

   >[!TIP]
   >
   >I servizi push non garantiscono al 100% l’effettivo invio di un messaggio. Per ulteriori informazioni sull’affidabilità dei servizi, consulta la documentazione appropriata:
   >
   >* **APNS**: [qualità del servizio](https://developer.apple.com/library/content/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/APNSOverview.html#//apple_ref/doc/uid/TP40008194-CH8-SW5)
   >* **FCM**: [ciclo di vita di un messaggio](https://firebase.google.com/docs/cloud-messaging/concept-options#lifetime)


## Come posso rinnovare il certificato Apple Push Service?

Per poter inviare messaggi push è necessario disporre di un certificato Push Service valido. Se il tuo certificato sta per scadere o è già scaduto, riceverai una notifica da Mobile Services. Per rinnovare il certificato, completa i passaggi seguenti:

1. Fai clic su **[!UICONTROL Gestione impostazioni app]**.
2. Per eliminare il certificato corrente, scorri fino a **[!UICONTROL Servizi push]** e fai clic su **[!UICONTROL Elimina]**.
3. Configura e verifica un nuovo certificato.

   Per ulteriori informazioni, consulta [Prerequisiti per abilitare i messaggi push.](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/prerequisites-push-messaging.md)

4. Fai clic su **[!UICONTROL Salva]**.

## Perché non posso visualizzare i miei messaggi push in un simulatore iOS?

I simulatori iOS non supportano i messaggi push.
