---
description: Nell’interfaccia di Adobe Mobile Services puoi pianificare un messaggio push per l’invio immediato, successivo o come evento ricorrente. Questi eventi possono essere pianificati su base giornaliera, settimanale o mensile.
keywords: dispositivi mobili
solution: Experience Cloud Services,Analytics
title: Pianificazione - Messaggi push
topic-fix: Metrics
uuid: 6810e27a-016f-4286-8fe2-9972d85fa326
exl-id: 36f263a0-4aad-423e-bb78-9c532c98df19
source-git-commit: 7cfaa5f6d1318151e87698a45eb6006f7850aad4
workflow-type: tm+mt
source-wordcount: '684'
ht-degree: 100%

---

# Pianificazione: messaggi push {#schedule-push-message}

{#eol}

Nell’interfaccia di Adobe Mobile Services puoi pianificare un messaggio push per l’invio immediato, successivo o come evento ricorrente. Questi eventi possono essere pianificati su base giornaliera, settimanale o mensile.

>[!TIP]
>
>Gli utenti possono modificare le impostazioni di pianificazione di un messaggio push in qualsiasi momento. Se non esiste una data valida per l’invio di un messaggio ricorrente (ad esempio il 31 febbraio, per un lavoro ricorrente pianificato per il 31° giorno del mese, oppure il 5° martedì del mese), il messaggio non viene inviato.

Considerazioni da ricordare:

* Il formato di data e ora corretto è `hh:mm` e `mm/dd/yyyy`.

* Puoi modificare un messaggio pianificato nei modi seguenti:

   * Modificano una data con una data successiva.
   * Modificando l’intervallo di ripetizione.

      Ad esempio, se il messaggio originale era stato inviato ogni giorno, puoi impostare la ricorrenza settimanale.

## Prima di pianificare messaggi push ricorrenti

È **fondamentale** comprendere le informazioni seguenti prima di pianificare dei messaggi push ricorrenti:

* Le opzioni visualizzate nell’elenco a discesa **[!UICONTROL Ripeti]** dipendono dalla data che hai digitato o selezionato.

   Ad esempio, se hai digitato `Saturday, October 7`, vengono visualizzate le seguenti opzioni:

   * **[!UICONTROL Mai]**
   * **[!UICONTROL Ogni giorno]**
   * **[!UICONTROL Ogni sabato]**
   * **[!UICONTROL Giorno 7 di ogni mese]**
   * **[!UICONTROL 1° sabato di ogni mese]**

* I messaggi push vengono pianificati e inviati in base all’Ora di Greenwich (GMT).

   Ad esempio, se hai pianificato un messaggio ricorrente da inviare ogni sabato alle 12:00 (mezzogiorno) **PST** a partire dal 7 ottobre, il messaggio verrà effettivamente inviato sabato alle 19:00 **GMT**.
* I messaggi vengono inviati in modo diverso a seconda che vi troviate negli Stati Uniti, in Europa o in Asia.

   Ad esempio, se ti trovi a San Jose, California, e pianifichi un messaggio da inviare il ***31 ottobre*** alle 17:30 **PST**, l’invio avverrà effettivamente il ***1° novembre*** alle 00:30 **GMT**. Se sei a Tokyo e pianifichi un messaggio da inviare il ***1° gennaio*** alle 05:30, l’invio avverrà effettivamente il ***31 dicembre*** alle 20:30 **GMT**.
* I messaggi push vengono inviati un’ora prima o dopo a seconda che sia attiva o meno l’ora legale.
* Nel rapporto sui messaggi push, il messaggio riporta il fuso orario locale del sistema.

   Ad esempio, se l’orario di invio è 12:00 **PST**, anche se il messaggio sarà inviato effettivamente alle 19:00 **GMT**, nel rapporto risulterà inviato alle 12:00 **PST**.

## Pianificare un messaggio push ricorrente {#section_675BD754E5A04423A1751193698A978F}

1. Nella pagina Pianifica per un nuovo messaggio push, seleziona **[!UICONTROL Pianificato]** oppure **[!UICONTROL Ora]**.

   Per ulteriori informazioni, consulta [Creare un messaggio push](/help/using/in-app-messaging/t-create-push-message/t-create-push-message.md).

   Se hai selezionato **[!UICONTROL Ora]**, il messaggio push viene inviato immediatamente. Per evitare che il messaggio venga pianificato subito, fai clic su **[!UICONTROL Salva come bozza]**.

   ![](assets/schedule-push-message.png)

1. Se hai selezionato **[!UICONTROL Pianificato]**, fai clic sull’icona del calendario e seleziona o digita una data di inizio.
1. Digita un’ora. 
1. In **[!UICONTROL Ripeti]**, seleziona una delle opzioni seguenti:

   * **[!UICONTROL Mai]**
   * **[!UICONTROL Ogni giorno]**
   * **[!UICONTROL Ogni martedì]**
   * **`<Day x>`del mese**

      Le opzioni visualizzate variano a seconda del giorno selezionato come giorno iniziale.
   * **`<nth day>`di ogni mese**

      Il valore visualizzato cambia a seconda della data che hai selezionato o digitato come data iniziale.

1. In **[!UICONTROL Fine ripetizione]**, digita una data e un’ora di fine.
1. Fai clic su una delle opzioni seguenti:

   * **[!UICONTROL Salva come bozza]**

      Il messaggio viene inviato in formato bozza. Puoi scegliere questa opzione per salvare un messaggio non ancora completato oppure per salvarne una versione provvisoria che dovrà essere modificata e approvata prima dell’attivazione.

      Se hai selezionato **[!UICONTROL Ora]** nel passaggio precedente, la bozza del messaggio viene inviata subito dopo l’attivazione. Se hai selezionato una data e un’ora per l’invio del messaggio push, questo viene inviato di conseguenza.

   * **[!UICONTROL Salva e pianifica]**

      Il messaggio viene inviato nel giorno e all’ora pianificati.

Per inviare la bozza del messaggio in un secondo momento, effettua una delle operazioni seguenti:

* Fai clic su **[!UICONTROL Gestione messaggi]**, seleziona la casella di controllo accanto al messaggio e fai clic su **[!UICONTROL Attiva selezionati]**.
* Fai clic su **[!UICONTROL Salva e invia]** per salvare il messaggio e inviarlo.
