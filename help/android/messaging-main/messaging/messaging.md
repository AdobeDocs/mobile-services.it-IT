---
description: Puoi inviare messaggi in-app che vengano attivati da qualsiasi dato o evento di analisi. Dopo l’implementazione, i messaggi vengono inviati in modo dinamico all’app e non richiedono alcun aggiornamento del codice.
solution: Experience Cloud Services,Analytics
title: Messaggistica in-app
topic-fix: Developer and implementation
uuid: 351ee3d2-80b9-4f2d-9696-21f274d89f5a
exl-id: ca9414d1-86e6-4bb2-a2d6-57df37df2403
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '770'
ht-degree: 100%

---

# Messaggistica in-app  {#in-app-messaging}

Puoi inviare messaggi in-app che vengano attivati da qualsiasi dato o evento di analisi. Dopo l’implementazione, i messaggi vengono inviati in modo dinamico all’app e non richiedono alcun aggiornamento del codice.

## Nuova versione SDK per Adobe Experience Cloud

Hai bisogno di informazioni e documentazione relative all’SDK per dispositivi mobili di Adobe Experience Platform? Fai clic [qui](https://aep-sdks.gitbook.io/docs/) per la documentazione più recente.

>[!IMPORTANT]
>
>A settembre 2018 è stata rilasciata una nuova versione principale dell&#39;SDK. Questi nuovi SDK per dispositivi mobili di Adobe Experience Platform sono configurabili tramite [Experience Platform Launch](https://www.adobe.com/it/experience-platform/launch.html).

* Per iniziare, passa a [Launch](https://launch.adobe.com/).
* Per visualizzare cosa è compreso negli archivi Experience Platform SDK, passa a [Github: SDK di Adobe Experience Platform](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

>[!IMPORTANT]
>
> Se utilizzi gli SDK per dispositivi mobili di Adobe Experience Platform con Adobe Launch, **devi** anche installare l&#39;estensione Adobe Analytics Mobile Services per utilizzare le funzioni di Adobe Mobile Services, ad esempio la messaggistica in-app e le notifiche push. Per ulteriori informazioni, consulta [Adobe Analytics - Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services). Per ulteriori informazioni sull&#39;uso dei messaggi push e in-app con gli SDK Experience Cloud, consulta [Configurare i messaggi push](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services#set-up-push-messaging) e [Configurare la messaggistica in-app](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services#set-up-in-app-messaging).

>[!IMPORTANT]
>
>Per usare la funzione per messaggi in-app, **è necessaria** la versione 4.2 o successiva dell’SDK.

In Adobe Mobile Services puoi creare i messaggi e le regole che definiscano quando dovranno essere visualizzati. Per ulteriori informazioni, consulta [Creare un messaggio in-app](/help/using/in-app-messaging/t-in-app-message/t-in-app-message.md). Per visualizzare i messaggi in-app, è necessario aggiornare l’SDK. Puoi completare questi passaggi anche se non hai ancora definito alcun messaggio. Una volta definiti, i messaggi verranno inviati in modo dinamico all’app e visualizzati senza che sia necessario un aggiornamento dell’app store.

## Abilitazione dei messaggi in-app {#section_380DF56C4EE4432A823940E4AE4C9E91}

1. Aggiungi la libreria al tuo progetto e implementa le funzioni di ciclo di vita (lifecycle).

   Per ulteriori informazioni, consulta *Aggiungere l’SDK e il file di configurazione al progetto IntelliJ IDEA o Eclipse* in [Implementazione e ciclo di vita di base](/help/android/getting-started/dev-qs.md).

1. Aggiorna il file `AndroidManifest.xml` per dichiarare l&#39;attività a schermo intero e abilita il gestore di notifica dei messaggi:

   ```java
   <activity  
   android:name="com.adobe.mobile.MessageFullScreenActivity"  
   android:theme="@android:style/Theme.Translucent.NoTitleBar" /> 
   <receiver android:name="com.adobe.mobile.MessageNotificationHandler" />
   ```

   Se hai selezionato un layout modale, seleziona uno dei seguenti temi per il messaggio:

   * `Theme.Translucent.NoTitleBar.Fullscreen`
   * `Theme.Translucent.NoTitleBar`
   * `Theme.Translucent`

   Ad esempio:

   ```java
   <activity 
   android:name="com.adobe.mobile.MessageFullScreenActivity" 
   android:theme="@android:style/Theme.Translucent.NoTitleBar.Fullscreen" 
   android:windowSoftInputMode="adjustUnspecified|stateHidden" /> 
   <receiver android:name="com.adobe.mobile.MessageNotificationHandler" />
   ```

1. Importa la libreria:

   ```java
   import com.adobe.mobile.*;
   ```

1. In ciascuna chiamata `collectLifecycleData`, passa `this` per fornire un riferimento all&#39;attività corrente:

   ```java
   @Override 
   public void onResume() { 
       Config.collectLifecycleData(this); 
   }
   ```

1. Verifica che il file `ADBMobileConfig.json` contenga le impostazioni richieste per la messaggistica in-app.

   >[!IMPORTANT]
   >
   >`messages` o `remotes` è obbligatorio.

   Affinché i messaggi in-app vengano aggiornati dinamicamente all&#39;avvio, l&#39;oggetto `remotes` deve essere presente e configurato correttamente:

   ```js
   "messages": [ 
       { 
           "messageId": "de45c43c-37bf-441f-8cbd-cc3ba3469ebe", 
           "template": "fullscreen", 
           "showOffline": false, 
           "showRule": "always", 
           "endDate": 2524730400, 
           "startDate": 0, 
           "audiences": [], 
           "triggers": [], 
           "payload": { // contents change depending on template 
               "html": "<html>html code goes here</html>" 
           }, 
       }, 
       … 
   ] 
   "remotes" : { 
       "analytics.poi": "https://assets.adobedtm.com/…/yourfile.json", 
       "messages": "https://assets.adobedtm.com/…/yourfile.json" 
   }
   ```

   Se questo oggetto non è configurato, scarica un file `ADBMobileConfig.json` aggiornato da Adobe Mobile Services. Per ulteriori informazioni, consulta [Prima di iniziare](/help/android/getting-started/requirements.md).

## Tracciamento dei messaggi in-app {#section_B85CDF6929564AAEA79338B55E5CB1E8}

Per i messaggi in-app, gli SDK di Android Mobile tengono traccia delle metriche seguenti:

* Per messaggi in-app a schermo intero e di tipo avviso:

   * **Impression**: quando l’utente attiva un messaggio in-app.
   * **Click-through**: quando l’utente preme il pulsante **[!UICONTROL Click-through]**.
   * **Annulla**: quando l’utente preme **[!UICONTROL Annulla]**.

* Per i messaggi in-app personalizzati a schermo intero, nel contenuto HTML del messaggio deve essere presente il codice corretto per trasmettere informazioni alla funzione di tracciamento dell&#39;SDK per i seguenti pulsanti:

   * Esempio di tracciamento **Click-through** (reindirizzamento):

      `adbinapp://confirm/?url=https://www.yoursite.com`
   * Esempio di tracciamento per **annullamento** (chiusura):

      `adbinapp://cancel`

## Immagine di fallback locale {#section_DEACC1CE549B4573B556A44A52409941}

Quando crei un messaggio a schermo intero, puoi facoltativamente specificare un’immagine di fallback. Se il messaggio non è in grado di recuperare dal web l’immagine prevista, l’SDK tenta di caricare l’immagine con lo stesso nome dalla cartelle delle risorse dell’applicazione. Questo consente di visualizzare il messaggio nella sua forma originale anche se l’utente è offline o se l’immagine prevista non è raggiungibile.

>[!IMPORTANT]
>
>Il nome della risorsa dell&#39;immagine di fallback è specificato quando configuri il messaggio in Adobe Mobile Services; assicurati che la risorsa specificata sia disponibile.

## Configurare le icone di notifica {#section_DDA28BDBCBB748BCBECF3AB50A177D48}

I seguenti metodi di consentono di configurare l&#39;icona piccola e l&#39;icona grande che appaiono nell&#39;area di notifica, nonché l&#39;icona grande visualizzata quando le notifiche appaiono nel riquadro delle notifiche.

* **Config.setSmallIconResourceId(int resourceId)**

   Imposta l’icona piccola che verrà utilizzata per le notifiche create dall’SDK. Questa icona apparirà sulla barra di stato e sarà l’immagine secondaria mostrata quando l’utente visualizza la notifica completa nel centro notifiche.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void setSmallIconResourceId(final int resourceId); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      Config.setSmallIconResourceId(R.drawable.appIcon);
      ```

* **Config.setLargeIconResourceId(int resourceId)**

   Imposta l&#39;icona grande che verrà utilizzata per le notifiche create dall&#39;SDK. Questa icona è l&#39;immagine principale visualizzata dall&#39;utente nella notifica completa all&#39;interno del Centro notifiche.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void setLargeIconResourceId(final int resourceId); 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```java
      Config.setLargeIconResourceId(R.drawable.appIcon); 
      ```
