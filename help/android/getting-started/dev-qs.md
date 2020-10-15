---
description: Queste informazioni sono utili per implementare la libreria Android e raccogliere metriche sul ciclo di vita, come avvii, aggiornamenti, sessioni, utenti attivi e così via.
keywords: android;library;mobile;sdk
seo-description: Queste informazioni sono utili per implementare la libreria Android e raccogliere metriche sul ciclo di vita, come avvii, aggiornamenti, sessioni, utenti attivi e così via.
seo-title: Implementazione e ciclo di vita di base
solution: Experience Cloud,Analytics
title: Implementazione e ciclo di vita di base
topic: Developer and implementation
uuid: af4d11ac-8245-46a0-9b3a-4a0a29cfbbb2
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '560'
ht-degree: 100%

---


# Implementazione e ciclo di vita di base {#core-implementation-and-lifecycle}

Queste informazioni sono utili per implementare la libreria Android e raccogliere metriche sul ciclo di vita, come avvii, aggiornamenti, sessioni, utenti attivi e così via.

## Scaricare l&#39;SDK {#section_99FE1A17A36D4A2C943939023CF6265C}

>[!IMPORTANT]
>
>Per scaricare l&#39;SDK, devi usare Android 2.2 o successivo.

1. Completa i passaggi descritti nelle sezioni seguenti per configurare una suite di rapporti per la fase di sviluppo e scaricare una versione precompilata del file di configurazione:

   * [Creare una suite di rapporti](/help/android/getting-started/requirements.md)
   * [Scaricare l&#39;SDK](/help/android/getting-started/requirements.md)

1. Scarica e decomprimi il file `[Your_App_Name_]AdobeMobileLibrary-4.*-Android.zip` e verifica che siano presenti i seguenti componenti software:

   * `adobeMobileLibrary.jar`, che è la libreria che sarà utilizzata con dispositivi e simulatori Android.

   * `ADBMobileConfig.json`, file di configurazione dell’SDK personalizzato per la tua app.
   >[!IMPORTANT]
   >
   >Se scarichi l&#39;SDK all&#39;esterno dell&#39;interfaccia utente di Adobe Mobile Services, il file `ADBMobileConfig.json` dovrà essere configurato manualmente. Se hai poca esperienza con Analytics e l&#39;SDK Mobile e desideri impostare una suite di rapporti per la fase di sviluppo e scaricare una versione precompilata del file di configurazione, vedi [Prima di iniziare](/help/android/getting-started/requirements.md).

## Aggiungere l&#39;SDK e il file di configurazione al progetto IntelliJ IDEA o Eclipse {#section_B89510FBB4C646AEA73A185B966E54D3}

**Progetto IntelliJ IDEA**

Per aggiungere l&#39;SDK e il file di configurazione al tuo progetto:

1. Aggiungi il file `ADBMobileConfig.json` alla cartella `assets` del progetto.

1. Fai clic con il pulsante destro del mouse nel pannello di navigazione del progetto.
1. Seleziona **[!UICONTROL Impostazioni modulo aperto]**.
1. In **[!UICONTROL Impostazioni progetto]**, seleziona **[!UICONTROL Librerie]**.
1. Fai clic sull’icona **[!UICONTROL +]** per aggiungere una nuova libreria.
1. Seleziona **[!UICONTROL Java]** e naviga fino al file `adobeMobileLibrary.jar`.
1. Seleziona i moduli nei quali intendi usare la libreria mobile.
1. Fai clic su **[!UICONTROL Applica]** e su **[!UICONTROL OK]** per chiudere la finestra Impostazioni modulo.

**Progetto Eclipse**

Per aggiungere l&#39;SDK e il file di configurazione al tuo progetto:

1. Aggiungi il file `ADBMobileConfig.json` alla cartella `assets` del progetto.
1. In **[!UICONTROL Eclipse IDE]**, fai clic con il pulsante destro del mouse sul nome del progetto.
1. Fai clic su **[!UICONTROL Percorso build]** > **[!UICONTROL Aggiungi archivi esterni]**.
1. Seleziona `adobeMobileLibrary.jar`.
1. Fai clic su **[!UICONTROL Apri]**.
1. Fai di nuovo clic con il pulsante destro del mouse sul progetto e seleziona **[!UICONTROL Percorso build]** > **[!UICONTROL Configura percorso build]**.
1. Nella scheda **[!UICONTROL Ordine ed esportazione]**, accertati che sia selezionato **`adobeMobileLibrary.jar`**.

## Aggiungere le autorizzazioni dell&#39;app {#section_2EAF73ABF6424647B219A63B33B02CD5}

La libreria AppMeasurement richiede le seguenti autorizzazioni per inviare dati e registrare le chiamate di tracciamento offline:

* `INTERNET`
* `ACCESS_NETWORK_STATE`

Per aggiungere queste autorizzazioni, aggiungi le seguenti righe al file `AndroidManifest.xml`, che si trova nella directory di progetto dell&#39;applicazione:

```java
<uses-permission android:name="android.permission.INTERNET" /> 
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

## Impostare il contesto dell&#39;applicazione {#set-application-context}

Nel metodo `onCreate` dell&#39;attività principale deve essere aggiunto il seguente codice:

```java
   @Override
   public void onCreate(BundlesavedInstanceState){
     super.onCreate(savedInstanceState)
     setContentView(R.layout.main);
     Config.setContext(this.getApplicationContext());
   }
```

## Implementare le metriche del ciclo di vita {#section_BA686C09021F474AADDE8690BBB910F7}

Dopo che avrai abilitato la funzione &quot;lifecycle&quot; (ciclo di vita), ad ogni avvio dell&#39;app viene inviato un hit per la misurazione di avvii, aggiornamenti, sessioni, utenti coinvolti e molte altre metriche. Per ulteriori informazioni, vedi [Metriche del ciclo di vita](/help/android/metrics.md).

**Completa i seguenti passaggi in ogni attività dell’applicazione:**

1. Importa la libreria:

   ```java
   import com.adobe.mobile.*;
   ```

1. Nella funzione `onResume`, avvia la raccolta di dati del ciclo di vita:

   ```java
   @Override 
   public void onResume() { 
       Config.collectLifecycleData(this); 
       // -or- Config.collectLifecycleData(this, contextData); 
   }
   ```

1. Nella funzione `onPause`, sospendi la raccolta di dati del ciclo di vita:

   ```java
   @Override 
   public void onPause() { 
       Config.pauseCollectingLifecycleData(); 
   }
   ```

>[!IMPORTANT]
>
>Devi aggiungere queste chiamate a ogni attività per garantire una segnalazione accurata degli arresti anomali. Per ulteriori informazioni, vedi [Tracciare gli arresti anomali dell’app](/help/android/analytics-main/crashes.md).

## Includere dati aggiuntivi con le chiamate &quot;lifecycle&quot;

Per includere dati aggiuntivi con le chiamate delle metriche &quot;lifecycle&quot;, usa un parametro aggiuntivo a `collectLifecycleData` che contenga dati contestuali:

```java
@Override 
public void onResume() {
    HashMap<String, Object> contextData = new HashMap<String, Object>(); 
    contextData.put("myapp.category", "Game"); 
    Config.collectLifecycleData(this, contextData); 
}
```

Eventuali valori di dati di contesto aggiuntivi inviati con `collectLifecycleData` devono essere mappati su variabili personalizzate in Adobe Mobile Services:

![](assets/map-variable-lifecycle.png)

Altre metriche &quot;lifecycle&quot; vengono raccolte automaticamente. Per ulteriori informazioni, vedi [Metriche del ciclo di vita](/help/android/metrics.md).

## Passi successivi {#section_BF709684E1DD40EA9169BC1D0D4B37C2}

Completa le attività seguenti:

* [Tracciare gli stati dell’app](/help/android/analytics-main/states.md)
* [Tracciare le azioni eseguite nell’app](/help/android/analytics-main/actions.md)

