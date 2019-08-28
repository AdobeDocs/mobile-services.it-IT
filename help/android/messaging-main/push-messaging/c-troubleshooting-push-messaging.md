---
description: Queste informazioni sono utili per risolvere eventuali problemi dei messaggi push.
keywords: dispositivi mobili
seo-description: Queste informazioni sono utili per risolvere eventuali problemi dei messaggi push.
seo-title: Risoluzione dei problemi dei messaggi push
solution: Marketing Cloud, Analytics
title: Risoluzione dei problemi dei messaggi push
topic: Metrics (Metriche)
uuid: 9 c 4 a 9371-6691-4 a 2 c-a 6 c 1-b 9 f 901 a 41599
translation-type: tm+mt
source-git-commit: 12e01e112debffd877dd62f1fd2505724b2aae7d

---


# Risoluzione dei problemi dei messaggi push {#troubleshooting-push-messaging}

Queste informazioni sono utili per risolvere eventuali problemi dei messaggi push.

## Perché a volte si verificano dei ritardi nell'invio dei messaggi push?

I seguenti tipi di ritardo possono essere associati ai messaggi push per Mobile Services:

* Attesa degli hit di Analytics

   Per ogni suite di rapporti, un'impostazione consente di determinare quando elaborare gli hit di Analytics in arrivo. L'impostazione predefinita è pari a 1 ora, allo scoccare dell'ora. L'effettiva elaborazione degli hit di Analytics potrebbe richiedere fino a 30 minuti, ma in genere dura 15-20 minuti. Prendiamo ad esempio una suite di rapporti che elabora gli hit ogni ora. Considerando il tempo di elaborazione massimo di 30 minuti, prima che un hit in arrivo diventi disponibile per un messaggio push potrebbero quindi trascorrere 90 minuti. Se un utente ha avviato l'app alle 09:01, l'hit risulterebbe nell'interfaccia di Mobile Services come nuovo utente unico tra le 10:15 e le 10:30.

* Attesa del servizio push

   Il servizio push (APNS o FCM) potrebbe non essere in grado di inviare il messaggio immediatamente. Anche se raramente, è possibile che si verifichi un ritardo di 5-10 minuti. Nella pagina Messaggi, fai clic sul collegamento **Visualizza** associato al messaggio per verificare che il messaggio push sia stato inviato al servizio push. Nel report, il numero di invii con esito positivo è elencato nella colonna **[!UICONTROL Pubblicato].**

   >[!TIP]
   >
   >I servizi push non garantiscono l'invio di un messaggio.

   Per ulteriori informazioni sull'affidabilità dei servizi, consulta la relativa documentazione:

   * **APNS**: [Qualità del servizio](https://developer.apple.com/library/content/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/APNSOverview.html#//apple_ref/doc/uid/TP40008194-CH8-SW5)
   * **FCM**: [Durata di un messaggio](https://firebase.google.com/docs/cloud-messaging/concept-options#lifetime)

## Perché i miei messaggi push vengono troncati o non si espandono?

Su alcuni dispositivi Android, può essere necessario `NotificationCompat.BigTextStyle` quando si visualizzano i messaggi.
