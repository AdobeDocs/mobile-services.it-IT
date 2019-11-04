---
description: Queste informazioni sono utili per risolvere eventuali problemi dei messaggi push.
keywords: dispositivi mobili
seo-description: Queste informazioni sono utili per risolvere eventuali problemi dei messaggi push.
seo-title: Risoluzione dei problemi dei messaggi push
solution: Experience Cloud,Analytics
title: Risoluzione dei problemi dei messaggi push
topic: Metrics (Metriche)
uuid: 87d7dcb6-82a8-46e3-a6ed-7f895a22f2af
translation-type: ht
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Risoluzione dei problemi dei messaggi push{#troubleshooting-push-messaging}

Queste informazioni sono utili per risolvere eventuali problemi dei messaggi push.

## Perché a volte si verificano dei ritardi nell'invio dei messaggi push?

I seguenti tipi di ritardo possono essere associati ai messaggi push per Mobile Services:

* **Attesa degli hit di Analytics**

   Per ogni suite di rapporti, un'impostazione consente di determinare quando elaborare gli hit di Analytics in arrivo. L'impostazione predefinita è pari a 1 ora, allo scoccare dell'ora. L'effettiva elaborazione degli hit di Analytics potrebbe richiedere fino a 30 minuti, ma in genere dura 15-20 minuti.

   Prendiamo ad esempio una suite di rapporti che elabora gli hit ogni ora. Considerando il tempo di elaborazione massimo di 30 minuti, prima che un hit in arrivo diventi disponibile per un messaggio push potrebbero quindi trascorrere 90 minuti. Se un utente ha avviato l'app alle 09:01, l'hit risulterebbe nell'interfaccia di Mobile Services come nuovo utente unico tra le 10:15 e le 10:30.

* **Attesa del servizio push**

   Il servizio push (APNS o GCM) potrebbe non essere in grado di inviare il messaggio immediatamente. Anche se raramente, è possibile che si verifichi un ritardo di 5-10 minuti. Nella pagina Messaggi, fai clic sul collegamento Visualizza associato al messaggio per verificare che il messaggio push sia stato inviato al servizio push. Nel report, il numero di invii con esito positivo è elencato nella colonna Pubblicato.

   >[!TIP]
   >
   >I servizi push non garantiscono al 100% l'effettivo invio di un messaggio. Per ulteriori informazioni sull'affidabilità dei servizi, consulta la relativa documentazione:
   >
   >* **APNS**: [Qualità del servizio](https://developer.apple.com/documentation/usernotifications)
      >
      >
   * **GCM**: [Ciclo di vita di un messaggio](https://developers.google.com/cloud-messaging/concept-options)


## Come posso rinnovare il mio certificato Apple Push Service?

Per poter inviare messaggi push è necessario disporre di un certificato Push Service valido. Se il tuo certificato sta per scadere o è già scaduto, riceverai una notifica da Mobile Services. Per rinnovare il certificato, completa i passaggi seguenti:

1. Fai clic su **[!UICONTROL Gestione impostazioni app]**.
2. Per eliminare il certificato corrente, scorri fino a **[!UICONTROL Servizi push]** e fai clic su **[!UICONTROL Elimina]**.
3. Configura e verifica un nuovo certificato.

   Per ulteriori informazioni, consulta [Prerequisiti per abilitare i messaggi push](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/prerequisites-push-messaging.md).

4. Fai clic su **[!UICONTROL Salva]**.

## Perché non riesco a vedere i messaggi push in un simulatore iOS?

I simulatori iOS non supportano i messaggi push.
