---
description: Queste informazioni consentono di esplorare un collegamento di campagna di acquisizione legacy su un dispositivo Android.
keywords: android,libreria,mobile,sdk
seo-description: Queste informazioni consentono di esplorare un collegamento di campagna di acquisizione legacy su un dispositivo Android.
seo-title: Verifica dell'acquisizione legacy
solution: Experience Cloud,Analytics
title: Verifica dell'acquisizione legacy
topic: Sviluppatore e implementazione
uuid: bb7ace96-68eb-4f43-b3cf-af80730b9cee
translation-type: ht
source-git-commit: bf076aa8e59d5c3e634fc4ae21f0de0d4541a83f

---


# Verifica dell'acquisizione legacy {#testing-legacy-acquisition}

Queste informazioni consentono di esplorare un collegamento di campagna di acquisizione legacy su un dispositivo Android.

Se l'app per dispositivi mobili non è ancora disponibile in Google Play, puoi selezionare una qualsiasi app mobile da usare come destinazione al momento di creare il collegamento della campagna. Questo incide solo sull'app alla quale il server di acquisizione ti reindirizzerà quando fai clic sul collegamento di acquisizione, e non sulla capacità di verificare il funzionamento del collegamento di acquisizione. I parametri della stringa di query vengono passati a Google Play Store e quindi all'app al momento dell'installazione, nell'ambito della trasmissione della campagna. Il test dell'acquisizione da app mobile richiede la simulazione di questo tipo di trasmissione.

L'app deve essere stata appena installata oppure i dati devono essere eliminati nelle **[!UICONTROL Impostazioni]** tutte le volte che si esegue un test. In questo modo le metriche del ciclo di vita iniziali associate ai parametri di stringa della query della campagna vengono inviate al primo avvio dell'app.

1. Nell'interfaccia utente di Mobile Services, genera un URL della campagna di acquisizione legacy.

   Per ulteriori informazioni, consulta [Utilizzare collegamenti di acquisizione legacy](/help/using/acquisition-main/c-marketing-links-builder/t-create-edit-adobe-links/c-use-legacy-acquisition-links/c-use-legacy-acquisition-links.md).
1. Connetti il dispositivo a un computer, avvia ADB Shell e avvia l'applicazione sul dispositivo.
1. Invia una trasmissione utilizzando il formato seguente:

   ```
   am broadcast -a com.android.vending.INSTALL_REFERRER -n com.example.adobetesttapp/com.google.analytics.tracking.android.CampaignTrackingReceiver --es "referrer" "utm_source=testSource&utm_medium=testMedium&utm_term=testTerm&utm_content=testContent&utm_campaign=testCampaign&trackingcode=trackingvalue"
   ```

1. Completa i seguenti passaggi:
   1. Sostituisci `com.example.adobetesttapp.com` con la voce DNS inversa della tua applicazione.
   1. Aggiorna il riferimento del ricevitore con il riferimento della posizione del ricevitore di tracciamento della campagna nella tua app.
   1. Sostituisci i valori associati a `utm_source`, `utm_medium`, `utm_term`, `utm_content`, `utm_campaign` e così via con i valori appropriati.

Se la trasmissione riesce, viene visualizzata una risposta simile alla seguente:

```
Broadcasting: Intent { act=com.android.vending.INSTALL_REFERRER cmp=com.example.analyticsecommtest/com.google.analytics.tracking.android.AnalyticsReceiver has extras) } Broadcast completed: result=0
```

Vedrai anche una richiesta di immagine inviata ai server di raccolta dati di Adobe. Se l'SDK attende la durata di completamento del timeout di riferimento impostata nel passaggio 1, con una richiesta di immagine che non include i parametri della campagna, la trasmissione non sarà riuscita.
