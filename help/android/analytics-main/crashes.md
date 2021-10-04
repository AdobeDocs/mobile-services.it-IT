---
description: Queste informazioni sono utili per capire come vengono tracciati gli arresti anomali dell'app e quali best practice adottare per gestire i falsi arresti anomali.
solution: Experience Cloud,Analytics
title: Tracciare gli arresti anomali dell’app
topic-fix: Developer and implementation
uuid: 3ab98c14-ccdf-4060-ad88-ec07c1c6bf07
exl-id: d8d59b4e-0231-446d-9ba1-8a9809be9c61
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 100%

---

# Tracciare gli arresti anomali dell’app {#track-app-crashes}

Queste informazioni sono utili per capire come vengono tracciati gli arresti anomali dell&#39;app e quali best practice adottare per gestire i falsi arresti anomali.

>[!TIP]
>
>Gli arresti anomali dell&#39;app sono tracciati come parte delle metriche del ciclo di vita. Prima di poter tenere traccia degli arresti anomali, aggiungi la libreria al progetto e implementa il ciclo di vita (lifecycle). Per ulteriori informazioni, consulta *Aggiungere l’SDK e il file di configurazione al progetto IntelliJ IDEA o Eclipse* in [Implementazione e ciclo di vita di base](/help/android/getting-started/dev-qs.md).

Quando si implementano le metriche del ciclo di vita, viene effettuata una chiamata a `Config.collectLifecycleData` nel metodo `OnResume` di ciascuna attività. Nel metodo `onPause` viene effettuata una chiamata a `Config.pauseCollectingLifeCycleData`.

In `pauseCollectingLifeCycleData` viene impostato un flag per indicare una corretta uscita. Quando l&#39;app viene avviata di nuovo o ripresa, `collectLifecycleData` verifica questo flag. Se lo stato del flag determina che l&#39;uscita dall&#39;app non è avvenuta correttamente, i dati contestuali `a.CrashEvent` vengono inviati con la chiamata successiva e viene segnalato un evento di arresto anomalo.

Per ottenere una segnalazione accurata degli arresti anomali, devi chiamare `pauseCollectingLifeCycleData` nel metodo `onPause` di ciascuna attività. Per capire il motivo per il quale è essenziale, ecco un diagramma che illustra il ciclo di vita delle attività Android:

![](assets/android-lifecycle.png)

Per maggiori informazioni sul ciclo di vita delle attività Android, consulta [Attività](https://developer.android.com/guide/components/activities.html).

*Questa illustrazione sul ciclo di vita Android è stata creata e [condivisa da Android Open Source Project](https://source.android.com/) e viene utilizzata in base ai termini della [Creative Commons 2.5 Attribution License](https://creativecommons.org/licenses/by/2.5/).*

## Cosa causa la segnalazione di un arresto anomalo falso?

1. Se esegui il debugging utilizzando un IDE, come Android Studio, l&#39;avvio di un&#39;app nuovamente dall&#39;IDE quando l&#39;app è in primo piano causa un arresto anomalo.

   >[!TIP]
   >
   >Puoi evitare questo arresto anomalo mettendo l&#39;app in background prima di avviarla nuovamente dall&#39;IDE.

1. Se l&#39;ultima attività in primo piano dell&#39;app è messa in background e non chiama `Config.pauseCollectingLifecycleData();`, in `onPause`, e l&#39;app viene chiusa manualmente o dal sistema operativo, l&#39;avvio successivo termina in un arresto anomalo.

## Come vanno gestiti i fragmenti?

I frammenti presentano eventi del ciclo di vita dell’applicazione simili a quelli delle attività. Tuttavia, un frammento non può essere attivo senza essere associato a un’attività.

>[!IMPORTANT]
>
>Occorre fare affidamento sugli eventi del ciclo di vita rispetto ai quali le attività di contenimento possono eseguire il codice. L&#39;operazione viene gestita dalla vista principale del frammento.

## (Facoltativo) Implementa i callback del ciclo di vita dell&#39;attività

A partire dall&#39;API livello 14, Android consente callback del ciclo di vita globali per le attività. Per ulteriori informazioni, consulta [Applicazione](https://developer.android.com/reference/android/app/Application).

Puoi usare questi callback per far sì che tutte le attività chiamino correttamente `collectLifecycleData()` e `pauseCollectingLifecycleData()`. Occorre aggiungere questo codice solo nell&#39;attività principale e in qualsiasi altra attività in cui la tua app potrebbe essere avviata:

```js
import com.adobe.mobile.Config; 
  
public class MainActivity extends Activity { 
... 
    @Override 
    protected void onCreate(Bundle savedInstanceState) { 
        super.onCreate(savedInstanceState); 
        setContentView(R.layout.activity_main); 
  
        getApplication().registerActivityLifecycleCallbacks(new Application.ActivityLifecycleCallbacks() { 
            @Override 
            public void onActivityResumed(Activity activity) { 
                Config.setContext(activity.getApplicationContext()); 
                Config.collectLifecycleData(activity); 
            } 
  
            @Override 
            public void onActivityPaused(Activity activity) {     
                Config.pauseCollectingLifecycleData(); 
            } 
    
            // the following methods aren't needed for our lifecycle purposes, but are required to be implemented 
            // by the ActivityLifecycleCallbacks object 
            @Override 
            public void onActivityCreated(Activity activity, Bundle savedInstanceState) {} 
            @Override 
            public void onActivityStarted(Activity activity) {} 
            @Override 
            public void onActivityStopped(Activity activity) {} 
            @Override 
            public void onActivitySaveInstanceState(Activity activity, Bundle outState) {} 
            @Override 
            public void onActivityDestroyed(Activity activity) {} 
        }); 
    } 
... 
}
```

Per inviare dati contestuali aggiuntivi con la chiamata del ciclo di vita utilizzando `Config.collectLifecycleData(Activity activity`, `Map<String`, `Object> contextData)`, devi sovrascrivere l&#39;override del metodo `onResume` per tale attività e accertarti di chiamare `super.onResume()` dopo aver chiamato manualmente `collectLifecycleData`.

```js
@Override 
protected void onResume() { 
    HashMap<String, Object> cdata = new HashMap<>(); 
    cdata.put("someKey", "someValue"); 
    Config.collectLifecycleData(this, cdata); 
  
    super.onResume(); 
}
```
