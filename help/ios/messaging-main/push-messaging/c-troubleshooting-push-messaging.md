---
description: Queste informazioni sono utili per risolvere eventuali problemi dei messaggi push.
keywords: mobile
seo-description: Queste informazioni sono utili per risolvere eventuali problemi dei messaggi push.
seo-title: Risoluzione dei problemi dei messaggi push
solution: Experience Cloud,Analytics
title: Risoluzione dei problemi dei messaggi push
topic: Metrics
uuid: 87d7dcb6-82a8-46e3-a6ed-7f895a22f2af
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 68%

---


# Risoluzione dei problemi dei messaggi push{#troubleshooting-push-messaging}

Queste informazioni sono utili per risolvere eventuali problemi dei messaggi push.

## Perché a volte si verificano dei ritardi nell&#39;invio dei messaggi push?

I seguenti tipi di ritardo possono essere associati ai messaggi push per Mobile Services:

* **Attesa degli hit di Analytics**

   Per ogni suite di rapporti, un&#39;impostazione consente di determinare quando elaborare gli hit di Analytics in arrivo. L&#39;impostazione predefinita è pari a 1 ora, allo scoccare dell&#39;ora. L&#39;effettiva elaborazione degli hit di Analytics potrebbe richiedere fino a 30 minuti, ma in genere dura 15-20 minuti.

   Ad esempio, una suite di rapporti elabora gli hit ogni ora. Considerando il tempo di elaborazione massimo di 30 minuti, potrebbero essere necessari fino a 90 minuti perché un hit in arrivo sia disponibile per un messaggio push. Se un utente ha avviato l&#39;app alle 09:01, l&#39;hit risulterebbe nell&#39;interfaccia di Mobile Services come nuovo utente unico tra le 10:15 e le 10:30.

* **Attesa del servizio push**

   Il servizio push (APNS o GCM) potrebbe non essere in grado di inviare il messaggio immediatamente. Anche se raramente, è possibile che si verifichi un ritardo di 5-10 minuti. Nella pagina Messaggi, fai clic sul collegamento Visualizza associato al messaggio per verificare che il messaggio push sia stato inviato al servizio push. Nel report, il numero di invii con esito positivo è elencato nella colonna Pubblicato.

   >[!TIP]
   >
   >I servizi push non garantiscono al 100% l&#39;effettivo invio di un messaggio. Per ulteriori informazioni sull&#39;affidabilità dei servizi, consulta la documentazione appropriata:
   >
   >* **APNS**: [Qualità del servizio](https://developer.apple.com/documentation/usernotifications)
   >
   >* **GCM**: [Durata di un messaggio](https://developers.google.com/cloud-messaging/concept-options)


## Come posso rinnovare il mio certificato Apple Push Service?

L&#39;invio di messaggi push richiede un certificato di servizio push valido. Se il tuo certificato sta per scadere o è già scaduto, riceverai una notifica da Mobile Services. Per rinnovare il certificato, completa i passaggi seguenti:

1. Fai clic su **[!UICONTROL Gestione impostazioni app]**.
2. Per eliminare il certificato corrente, scorri fino a **[!UICONTROL Servizi push]** e fai clic su **[!UICONTROL Elimina]**.
3. Configura e verifica un nuovo certificato.

   Per ulteriori informazioni, consulta [Prerequisiti per abilitare i messaggi push.](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/prerequisites-push-messaging.md)

4. Fai clic su **[!UICONTROL Salva]**.

## Perché non posso visualizzare i miei messaggi push in un simulatore iOS?

I simulatori iOS non supportano i messaggi push.
