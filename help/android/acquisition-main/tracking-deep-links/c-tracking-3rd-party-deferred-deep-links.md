---
description: Usa l'SDK per Android per implementare il tracciamento dei collegamenti profondi differiti (deferred deep link) di terze parti.
title: Tracciamento dei collegamenti profondi differiti (deferred deep link) di terze parti
uuid: 4c798e47-7988-4a06-a191-6c4d05f6ee61
exl-id: d8cbc679-a512-44db-8c30-6a029ff738ae
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '495'
ht-degree: 84%

---

# Tracciamento dei collegamenti profondi differiti (deferred deep link) di terze parti {#tracking-third-party-deferred-deep-links}

Usa l&#39;SDK per Android per implementare il tracciamento dei collegamenti profondi differiti (deferred deep link) di terze parti.

## Collegamenti diretti classici dell&#39;SDK di Adobe Mobile {#section_D114FA1EB9664EAA82E036A990694B26}

L&#39;SDK di Adobe Mobile supporta attualmente i collegamenti profondi laddove gli sviluppatori di app devono usare l&#39;API SDK `collectLifecycleData` dall&#39;attività con collegamenti profondi. L&#39;SDK collega i dati dei collegamenti profondi dai parametri dell&#39;URL del collegamento profondo. Per maggiori informazioni sulle modalità di funzionamento dei collegamenti profondi nell&#39;SDK di Adobe Mobile, vedi  [Tracciamento dei collegamenti profondi](/help/android/acquisition-main/tracking-deep-links/tracking-deep-links.md).

## Collegamenti diretti di Facebook {#section_6A9DACB54A2F4CDEBE9C744DEFADFDED}

Il creatore di un&#39;inserzione può creare un&#39;inserzione su Facebook come collegamento profondo. Quando l&#39;utente fa clic sull&#39;inserzione, passa direttamente alle informazioni di interesse nell&#39;app. Il collegamento profondo **non** è un URL di generazione di impronta digitale. Tuttavia, durante la configurazione dell&#39;annuncio, è disponibile l&#39;opzione per fornire un URL di collegamento profondo di terze parti. Lo sviluppatore di app che utilizza l&#39;SDK di Adobe Mobile e Adobe Mobile Services deve immettere in questo campo l&#39;URL di generazione di impronte digitali configurato da Adobe Mobile Services. Se è tutto impostato correttamente, l&#39;SDK di Facebook passa questo URL all&#39;applicazione quando l&#39;app viene installata o avviata.

## Configurare gli SDK  {#section_834CD3109175432B8173ECB6EA7DE315}

Per prepararsi ad aggiungere il supporto per i collegamenti profondi di Facebook con l&#39;SDK di Adobe Mobile, lo sviluppatore di app esegue le seguenti attività:

* Introduzione all’SDK per Android

   Per ulteriori informazioni, consulta [Guida introduttiva all&#39;SDK per Android](https://developers.facebook.com/docs/android/getting-started).

* Impostazione di collegamenti diretti

   Per ulteriori informazioni, consulta [Configurazione collegamenti diretti](https://developers.facebook.com/docs/app-ads/deep-linking#os).

Se l&#39;applicazione è configurata correttamente, l&#39;API `trackAdobeDeepLink()` dovrebbe abilitare la raccolta delle informazioni sui collegamenti diretti dalla campagna di acquisizione di Facebook e inviarli ad Adobe Mobile Services. Se l&#39;hit di installazione non è stato inviato ad Adobe Mobile Services al primo avvio, queste informazioni saranno aggiunte all&#39;hit del ciclo di vita. In caso contrario, verrà inviato come hit di collegamento profondo di Adobe.

>[!TIP]
>
>Accertati che l&#39;URL del collegamento diretto disponga di una chiave denominata `a.deeplink.id`. Se nell&#39;URL manca il parametro ID del collegamento profondo, i parametri dell&#39;URL non saranno collegati ai dati contestuali.

Se il collegamento può essere attribuito a un&#39;acquisizione, l&#39;SDK Adobe Mobile memorizzerà i dati di acquisizione dai collegamenti profondi di Facebook utilizzati per chiamare `trackAdobeDeepLink()`. Questi dati saranno disponibili per Adobe Mobile SDK nei prossimi avvii. Se è stato registrato un callback, il callback Adobe verrà utilizzato anche per inviare i dati al client.

## Abilitare i collegamenti diretti in un&#39;applicazione Android {#section_64C15E269E89424B8E3D029F88094620}

1. Registra l&#39;applicazione per gestire i collegamenti profondi.

   Per ulteriori informazioni, consulta [Consentire ad altre app di avviare la tua attività](https://developer.android.com/training/basics/intents/filters.html).

1. Collegare gli SDK di Facebook.

   Per aggiungere la dipendenza gradle di Facebook nell&#39;app, completa i passaggi in [Guida introduttiva all&#39;SDK per Android](https://developers.facebook.com/docs/android/getting-started).

1. Per inizializzare il Facebook SDK, seguire le istruzioni contenute nella sezione *Configurazione di Android Studio*.
1. Chiama `trackAdobeDeepLink()` dall&#39;attività principale.

   ```java
   @Override 
   protected void onResume() { 
      super.onResume(); 
      AppEventsLogger.activateApp(this); 
      /* 
       * Adobe Tracking - Config 
       * 
       * call collectLifecycleData() to begin collecting lifecycle data 
       * must be in the onResume() of every activity in your app 
       */ 
      Config.collectLifecycleData(this);
   
      AppLinkData.fetchDeferredAppLinkData(this, 
            new AppLinkData.CompletionHandler() { 
               @Override 
               public void onDeferredAppLinkDataFetched(AppLinkData appLinkData) { 
                  // Process app link data 
                  if (appLinkData != null) { 
                     Config.trackAdobeDeepLink(appLinkData.getTargetUri()); 
                  } 
               } 
            } 
      ); 
   }
   ```
