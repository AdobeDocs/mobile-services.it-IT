---
description: Queste informazioni sono utili per risolvere eventuali problemi dei messaggi push.
keywords: mobile
seo-description: Queste informazioni sono utili per risolvere eventuali problemi dei messaggi push.
seo-title: Risolvere i problemi dei messaggi push
solution: Experience Cloud,Analytics
title: Risolvere i problemi dei messaggi push
topic: Metrics
uuid: 9c4a9371-6691-4a2c-a6c1-b9f901a41599
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 85%

---


# Risoluzione dei problemi dei messaggi push {#troubleshooting-push-messaging}

Queste informazioni sono utili per risolvere eventuali problemi dei messaggi push.

## Perché a volte si verificano dei ritardi nell&#39;invio dei messaggi push?

I seguenti tipi di ritardo possono essere associati ai messaggi push per Mobile Services:

* Attesa degli hit di Analytics

   Per ogni suite di rapporti, un&#39;impostazione consente di determinare quando elaborare gli hit di Analytics in arrivo. L&#39;impostazione predefinita è pari a 1 ora, allo scoccare dell&#39;ora. L&#39;effettiva elaborazione degli hit di Analytics potrebbe richiedere fino a 30 minuti, ma in genere dura 15-20 minuti. Ad esempio, una suite di rapporti elabora gli hit ogni ora. Considerando il tempo di elaborazione massimo di 30 minuti, potrebbero essere necessari fino a 90 minuti perché un hit in arrivo sia disponibile per un messaggio push. Se un utente ha avviato l&#39;app alle 09:01, l&#39;hit risulterebbe nell&#39;interfaccia di Mobile Services come nuovo utente unico tra le 10:15 e le 10:30.

* Attesa del servizio push

   Il servizio push (APNS o FCM) potrebbe non essere in grado di inviare il messaggio immediatamente. Anche se raramente, è possibile che si verifichi un ritardo di 5-10 minuti. Nella pagina Messaggi, fai clic sul collegamento **[!UICONTROL Visualizza]** associato al messaggio per verificare che il messaggio push sia stato inviato al servizio push. Nel report, il numero di invii con esito positivo è elencato nella colonna **[!UICONTROL Pubblicato]**.

   >[!TIP]
   >
   >I servizi push non garantiscono al 100% l&#39;effettivo invio di un messaggio.

   Per ulteriori informazioni sull&#39;affidabilità dei servizi, consulta la documentazione appropriata:

   * **APNS**: [Qualità del servizio](https://developer.apple.com/library/content/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/APNSOverview.html#//apple_ref/doc/uid/TP40008194-CH8-SW5)
   * **FCM**: [ciclo di vita di un messaggio](https://firebase.google.com/docs/cloud-messaging/concept-options#lifetime)

## Perché i miei messaggi push vengono troncati o non si espandono?

Su alcuni dispositivi Android, può essere necessario `NotificationCompat.BigTextStyle` quando si visualizzano i messaggi.
