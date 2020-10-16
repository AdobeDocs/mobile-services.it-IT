---
description: Le informazioni seguenti sono utili per eseguire un ciclo di verifica completo per un collegamento di campagna di acquisizione legacy, basato sull'impronta digitale di un dispositivo.
seo-description: Le informazioni seguenti sono utili per eseguire un ciclo di verifica completo per un collegamento di campagna di acquisizione legacy, basato sull'impronta digitale di un dispositivo.
seo-title: Verifica di acquisizioni legacy
solution: Experience Cloud,Analytics
title: Verifica di acquisizioni legacy
uuid: e0591f4a-e26b-4fe4-97c1-a6831a926fa5
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '272'
ht-degree: 100%

---


# Verifica di acquisizioni legacy {#testing-legacy-acquisition}

Le informazioni seguenti sono utili per eseguire un ciclo di verifica completo per un collegamento di campagna di acquisizione legacy, basato sull&#39;impronta digitale di un dispositivo.

Se l’app per dispositivi mobili non è ancora disponibile in Google Play, puoi selezionare una qualsiasi app mobile da usare come destinazione al momento di creare il collegamento della campagna. Questo incide solo sul server di acquisizione al quale l&#39;app ti reindirizzerà quando fai clic sul collegamento di acquisizione, e non la capacità di verificare il funzionamento del collegamento di acquisizione.

1. Passa a **[!UICONTROL Utilizzare collegamenti di acquisizione legacy]** in Adobe Mobile Services e genera un URL per una campagna di acquisizione.

   Per ulteriori informazioni, consulta [Utilizzare collegamenti di acquisizione legacy](/help/using/acquisition-main/c-marketing-links-builder/t-create-edit-adobe-links/c-use-legacy-acquisition-links/c-use-legacy-acquisition-links.md).

1. Dal dispositivo mobile sul quale hai installato l&#39;app, fai clic sul collegamento generato.

   I server di Adobe (`c00.adobe.com`) memorizzano l&#39;impronta digitale e quindi eseguono il reindirizzamento all&#39;App Store. Non è necessario scaricare l&#39;app per eseguire la verifica.

1. Sullo stesso dispositivo mobile utilizzato al passaggio 2, avvia l&#39;applicazione per la prima volta.

   Per essere certo che si tratti effettivamente del primo avvio, elimina e installa di nuovo l&#39;app.

Considerazioni da ricordare:

* Il server di acquisizione fornisce una corrispondenza di attribuzione basata sull&#39;indirizzo IP e sulle informazioni dell&#39;agente utente registrate al momento del clic sul collegamento (passaggio 2) e all&#39;avvio dell&#39;app (passaggio 3).
* Utilizzando strumenti di monitoraggio HTTP, è possibile monitorare gli hit inviati dall&#39;app per fornire elementi utili alla verifica dell&#39;attribuzione dell&#39;acquisizione.

>[!TIP]
>
>Eventuali varianti nell&#39;agente utente inviato potrebbero provocare errori di attribuzione.
