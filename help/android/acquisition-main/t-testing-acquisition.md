---
description: Queste informazioni consentono di esplorare un collegamento di campagna di acquisizione legacy su un dispositivo Android.
keywords: android,libreria,mobile,sdk
solution: Experience Cloud,Analytics
title: Verifica di acquisizioni legacy
topic-fix: Developer and implementation
uuid: bb7ace96-68eb-4f43-b3cf-af80730b9cee
exl-id: 43e3b24e-e8bc-407c-b788-5ab85e459a90
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 100%

---

# Verifica di acquisizioni legacy {#testing-legacy-acquisition}

Informazioni utilI per esplorare un collegamento di campagna di acquisizione legacy su un dispositivo Android.

Se l’app per dispositivi mobili non è ancora disponibile in Google Play, puoi selezionare una qualsiasi app mobile da usare come destinazione al momento di creare il collegamento della campagna. Questo incide solo sull’app alla quale il server di acquisizione ti reindirizzerà quando fai clic sul collegamento di acquisizione, e non sulla capacità di verificare il funzionamento del collegamento. I parametri della stringa di query vengono passati a Google Play Store, e quindi passati all’app al momento dell’installazione come parte di una trasmissione della campagna. Il test del ciclo completo di acquisizione da app mobile richiede la simulazione di questo tipo di trasmissione.

L’app deve essere stata appena installata oppure i dati devono essere eliminati nelle **[!UICONTROL Impostazioni]** tutte le volte che si esegue un test. In questo modo le metriche del ciclo di vita iniziali associate ai parametri di stringa della query della campagna vengono inviate al primo avvio dell&#39;app.

1. Nell&#39;interfaccia utente di Mobile Services, genera un URL della campagna di acquisizione legacy.

   Per ulteriori informazioni, consulta [Utilizzare collegamenti di acquisizione legacy](/help/using/acquisition-main/c-marketing-links-builder/t-create-edit-adobe-links/c-use-legacy-acquisition-links/c-use-legacy-acquisition-links.md).
1. Connetti il dispositivo a un computer, avvia ADB Shell e avvia l&#39;applicazione sul dispositivo.
1. Invia una trasmissione utilizzando il formato seguente:

   ```
   am broadcast -a com.android.vending.INSTALL_REFERRER -n com.example.adobetesttapp/com.google.analytics.tracking.android.CampaignTrackingReceiver --es "referrer" "utm_source=testSource&utm_medium=testMedium&utm_term=testTerm&utm_content=testContent&utm_campaign=testCampaign&trackingcode=trackingvalue"
   ```

1. Completa i seguenti passaggi:
   1. Sostituisci `com.example.adobetesttapp.com` con la voce DNS inversa della tua applicazione.
   1. Aggiorna il riferimento del ricevitore con il riferimento della posizione del ricevitore di tracciamento della campagna nella tua app.
   1. Sostituisci i valori associati a `utm_source`, `utm_medium`, `utm_term`, `utm_content`, `utm_campaign` e così via con i valori appropriati.

Se la trasmissione ha esito positivo, viene visualizzata una risposta simile a quella riportata di seguito:

```
Broadcasting: Intent { act=com.android.vending.INSTALL_REFERRER cmp=com.example.analyticsecommtest/com.google.analytics.tracking.android.AnalyticsReceiver has extras) } Broadcast completed: result=0
```

Vedrai anche una richiesta di immagine inviata ai server di raccolta dati di Adobe. Se l’SDK attende l’intera durata del timeout referente (impostato nel passaggio 1) per una richiesta di immagine che non include parametri della campagna, la trasmissione non riesce.
