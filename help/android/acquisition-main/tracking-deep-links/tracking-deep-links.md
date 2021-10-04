---
description: Queste informazioni sono utili per tenere traccia dei collegamenti profondi (deep link) e di quelli profondi differiti (deferred deep link) nelle app mobili, mediante l'SDK di Adobe Mobile per Android.
keywords: android,libreria,mobile,sdk
solution: Experience Cloud,Analytics
title: Tracciamento dei collegamenti profondi
topic-fix: Developer and implementation
uuid: ebb1c08c-a246-40b3-9ac6-4606a14b4c5a
exl-id: 4f59b77d-3cac-4853-bb6b-50a403036771
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 97%

---

# Tracciamento dei collegamenti profondi

Queste informazioni sono utili per tenere traccia dei collegamenti profondi (deep link) e di quelli profondi differiti (deferred deep link) nelle app mobili, mediante l’SDK di Adobe Mobile per Android.

## Tracciamento dei collegamenti profondi

1. Aggiungi l&#39;SDK al tuo progetto e implementa le metriche del ciclo di vita.

   Per ulteriori informazioni, consulta *Aggiungere l’SDK e il file di configurazione al progetto IntelliJ IDEA o Eclipse* in [Implementazione e ciclo di vita di base](/help/android/getting-started/dev-qs.md).

1. Registra l&#39;applicazione per gestire gli URL.

   Per ulteriori informazioni, consulta [URL](https://developer.android.com/training/basics/intents/filters.html).
1. Passa l&#39;attività con l&#39;intento dei collegamenti profondi ad Adobe SDK tramite `collectLifecycleData`.

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

L’SDK di Adobe Mobile può analizzare le coppie chiave-valore di dati che sono stati aggiunti alla fine di un collegamento diretto o universale, purché questo contenga una chiave con l’etichetta `a.deeplink.id` e un valore corrispondente non nullo e generato dall’utente. Tutte le coppie di dati chiave-valore aggiunte alla fine del collegamento vengono analizzate, allegate all’hit del ciclo di vita e inviate ad Adobe Analytics, purché il collegamento contenga la coppia chiave-valore `a.deeplink.id`.

Inoltre, puoi anche aggiungere al collegamento diretto o universale una o più delle seguenti chiavi riservate (con valori generati dall&#39;utente):

* `a.launch.campaign.trackingcode`
* `a.launch.campaign.source`
* `a.launch.campaign.medium`
* `a.launch.campaign.term`
* `a.launch.campaign.content`

Queste chiavi sono variabili premappate per il reporting in Adobe Analytics. Per maggiori informazioni sulle regole di mappatura ed elaborazione, vedi [Regole di elaborazione e dati contestuali](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/processing-rules/processing-rules.html).

## Tracciamento dei collegamenti profondi differiti (per l&#39;utilizzo con i collegamenti di marketing)

Nel caso di un collegamento profondo differito, Adobe SDK aprirà un nuovo Intent con il collegamento profondo come dati di intento. Questo processo viene gestito come collegamento profondo esterno utilizzando il codice indicato in precedenza.

## Informazioni pubbliche sui collegamenti diretti {#section_1815396353614DA8A63D8D92112217E7}

### Costanti

```java
/* 
 * Used for message deep link tracking
 * Key for deep link URL. 
 */
public static final String ADB_MESSAGE_DEEPLINK_KEY = "adb_deeplink";
```
