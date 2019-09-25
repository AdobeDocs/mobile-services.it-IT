---
description: Queste informazioni sono utili per tenere traccia dei collegamenti profondi (deep link) e di quelli profondi differiti (deferred deep link) nelle app mobili, mediante l'SDK di Adobe Mobile per Android.
keywords: android;libreria;mobile;sdk
seo-description: Queste informazioni sono utili per tenere traccia dei collegamenti profondi (deep link) e di quelli profondi differiti (deferred deep link) nelle app mobili, mediante l'SDK di Adobe Mobile per Android.
seo-title: Tracciamento dei collegamenti profondi in Adobe Mobile Services
solution: Marketing Cloud,Analytics
title: Tracciamento dei collegamenti profondi (deep link)
topic: Sviluppatore e implementazione
uuid: ebb1c08c-a246-40b3-9ac6-4606a14b4c5a
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Tracking deep links {#tracking-deep-links}

Queste informazioni sono utili per tenere traccia dei collegamenti profondi (deep link) e di quelli profondi differiti (deferred deep link) nelle app mobili, mediante l'SDK di Adobe Mobile per Android.

## Tracciamento dei collegamenti profondi

1. Aggiungi l'SDK al tuo progetto e implementa le metriche del ciclo di vita.

   Per ulteriori informazioni, consulta *Aggiungere l’SDK e il file di configurazione al progetto* IntelliJ IDEA o Eclipse nell’implementazione e nel ciclo di vita [di](/help/android/getting-started/dev-qs.md)base.

1. Registra l'applicazione per gestire gli URL.

   For more information, see [URLs](https://developer.android.com/training/basics/intents/filters.html).
1. Passa l'attività con l'intento dei collegamenti profondi ad Adobe SDK tramite `collectLifecycleData`.

   Ecco un esempio di tracciamento di un collegamento profondo:

   ```java
   public class ParseDeepLinkActivity extends Activity { 
       @Override 
       protected void onCreate(Bundle savedInstanceState) { 
           super.onCreate(savedInstanceState); 
   
           Config.collectLifecycleData(this); 
           ... 
       } 
   }
   ```

The Adobe Mobile] SDK can parse key and value pairs of data that is appended to any Deep or Universal Link as long as the link contains a key with the `a.deeplink.id` label and a corresponding non-null and user-generated value. All key and value pairs of data that are appended to the link will be parsed, attached to a lifecycle hit, and sent to Adobe Analytics] as long as the link contains the `a.deeplink.id` key and value.

Inoltre, puoi aggiungere una o più delle seguenti chiavi riservate (con valori generati dall’utente) al collegamento profondo o universale:

* `a.launch.campaign.trackingcode`
* `a.launch.campaign.source`
* `a.launch.campaign.medium`
* `a.launch.campaign.term`
* `a.launch.campaign.content`

Queste chiavi sono variabili premappate per il reporting in Adobe Analytics. Per maggiori informazioni sulle regole di mappatura ed elaborazione, vedi [Regole di elaborazione e dati contestuali](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules.html).

## Tracciamento di collegamenti profondi differiti (per l’utilizzo con collegamenti di marketing)

Nel caso di un collegamento profondo differito, Adobe SDK aprirà un nuovo Intent con il collegamento profondo come dati di intento. Questo processo viene gestito come collegamento profondo esterno utilizzando il codice indicato in precedenza.

## Deep link public information {#section_1815396353614DA8A63D8D92112217E7}

### Costanti

```java
/* 
 * Used for message deep link tracking
 * Key for deep link URL. 
 */
public static final String ADB_MESSAGE_DEEPLINK_KEY = "adb_deeplink";
```

