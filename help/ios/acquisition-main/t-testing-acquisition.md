---
description: Le informazioni seguenti sono utili per eseguire un ciclo di verifica completo per un collegamento di campagna di acquisizione legacy, basato sull'impronta digitale di un dispositivo.
seo-description: Le informazioni seguenti sono utili per eseguire un ciclo di verifica completo per un collegamento di campagna di acquisizione legacy, basato sull'impronta digitale di un dispositivo.
seo-title: Verifica dell'acquisizione legacy
solution: Marketing Cloud,Analytics
title: Verifica dell'acquisizione legacy
uuid: e0591f4a-e26b-4fe4-97c1-a6831a926fa5
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Testing legacy acquisition {#testing-legacy-acquisition}

Le informazioni seguenti sono utili per eseguire un ciclo di verifica completo per un collegamento di campagna di acquisizione legacy, basato sull'impronta digitale di un dispositivo.

Se l'app per dispositivi mobili non è ancora disponibile in Google Play, puoi selezionare una qualsiasi app mobile da usare come destinazione al momento di creare il collegamento della campagna. Questo incide solo sul server di acquisizione al quale l'app ti reindirizzerà quando fai clic sul collegamento di acquisizione, e non la capacità di verificare il funzionamento del collegamento di acquisizione.

1. Passa a **[!UICONTROL Utilizzare collegamenti di acquisizione legacy]in Adobe Mobile Services e genera un URL per una campagna di acquisizione.**

   Per ulteriori informazioni, consulta [Utilizzare collegamenti di acquisizione legacy](/help/using/acquisition-main/c-marketing-links-builder/t-create-edit-adobe-links/c-use-legacy-acquisition-links/c-use-legacy-acquisition-links.md).

1. Dal dispositivo mobile sul quale hai installato l'app, fai clic sul collegamento generato.

   I server di Adobe (`c00.adobe.com`) memorizzano l'impronta digitale e quindi eseguono il reindirizzamento all'App Store. Non è necessario scaricare l'app per eseguire la verifica.

1. Sullo stesso dispositivo mobile utilizzato al passaggio 2, avvia l'applicazione per la prima volta.

   Per essere certo che si tratti effettivamente del primo avvio, elimina e installa di nuovo l'app.

Considerazioni da ricordare:

* Il server di acquisizione fornisce una corrispondenza di attribuzione basata sull'indirizzo IP e sulle informazioni dell'agente utente registrate al momento del clic sul collegamento (passaggio 2) e all'avvio dell'app (passaggio 3).
* Utilizzando strumenti di monitoraggio HTTP, è possibile monitorare gli hit inviati dall'app per fornire elementi utili alla verifica dell'attribuzione dell'acquisizione.

>[!TIP]
>
>Eventuali varianti nell'agente utente inviato potrebbero provocare errori di attribuzione.
