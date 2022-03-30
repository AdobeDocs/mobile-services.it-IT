---
description: Queste informazioni sono utili per risolvere eventuali problemi dei messaggi push.
keywords: dispositivi mobili
solution: Experience Cloud Services,Analytics
title: Risolvere i problemi dei messaggi push
topic-fix: Metrics
uuid: 9c4a9371-6691-4a2c-a6c1-b9f901a41599
exl-id: 82b89f56-f43e-4b0d-80c5-5bff4013e5f7
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 100%

---

# Risolvere i problemi dei messaggi push {#troubleshooting-push-messaging}

Queste informazioni sono utili per risolvere eventuali problemi dei messaggi push.

## Perché a volte si verificano dei ritardi nell’invio dei messaggi push?

I seguenti tipi di ritardo possono essere associati ai messaggi push per Mobile Services:

* Attesa degli hit di Analytics

   Per ogni suite di rapporti, un’impostazione consente di determinare quando elaborare gli hit di Analytics in arrivo. L&#39;impostazione predefinita è pari a 1 ora, allo scoccare dell&#39;ora. L&#39;effettiva elaborazione degli hit di Analytics potrebbe richiedere fino a 30 minuti, ma in genere dura 15-20 minuti. Ad esempio, una suite di rapporti elabora gli hit ogni ora. Considerando il tempo massimo di elaborazione richiesto (30 minuti), potrebbero essere necessari fino a 90 minuti perché un hit in arrivo sia disponibile per un messaggio push. Se un utente ha avviato l’app alle 09:01, l’hit risulterebbe nell’interfaccia di Mobile Services come nuovo utente univoco tra le 10:15 e le 10:30.

* Attesa del servizio push

   Il servizio push (APNS o FCM) potrebbe non essere in grado di inviare il messaggio immediatamente. Anche se raramente, è possibile che si verifichi un ritardo di 5-10 minuti. Nella pagina Messaggi, fai clic sul collegamento **[!UICONTROL Visualizza]** associato al messaggio per verificare che il messaggio push sia stato inviato al servizio push. Nel rapporto, il numero di invii con esito positivo è elencato nella colonna **[!UICONTROL Pubblicato]**.

   >[!TIP]
   >
   >I servizi push non garantiscono al 100% l’effettivo invio di un messaggio. Per ulteriori informazioni sull’affidabilità dei servizi, consulta la documentazione appropriata:
   >
   >* **APNS**: [qualità del servizio](https://developer.apple.com/library/content/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/APNSOverview.html#//apple_ref/doc/uid/TP40008194-CH8-SW5)
   >* **FCM**: [ciclo di vita di un messaggio](https://firebase.google.com/docs/cloud-messaging/concept-options#lifetime)


## Perché i miei messaggi push vengono troncati o non si espandono?

Su alcuni dispositivi Android, può essere necessario `NotificationCompat.BigTextStyle` quando si visualizzano i messaggi.
