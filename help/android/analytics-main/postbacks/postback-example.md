---
description: Puoi usare queste informazioni per comprendere cosa sono i postback e come funzionano.
keywords: android,libreria,mobile,sdk
solution: Experience Cloud Services,Analytics
title: Esempi di postback
topic-fix: Developer and implementation
uuid: 8010cd00-d42b-4e16-8403-692fab2550f1
exl-id: 2ff41066-e2ee-425f-8aff-e5e3f3e5f0f5
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '128'
ht-degree: 100%

---

# Esempi di postback {#postbacks-example}

Puoi usare queste informazioni per comprendere cosa sono i postback e come funzionano.

>[!CAUTION]
>
>Questo esempio è fornito unicamente a scopo informativo. Il file `ADBMobileConfig.json` deve essere configurato nell&#39;interfaccia utente di Adobe Mobile e non deve essere modificato manualmente. Un file di configurazione modificato manualmente rappresenta un rischio quando è attiva la configurazione di messaggi in remoto.

## `ADBMobileConfig.json` definizione {#section_8751E8176F3546C09420341A39758AFF}

```js
"messages": [ 
    { 
        "messageId": "79ae37c9-89b9-465e-af7f-d3351771f1dc", 
        "template": "callback", 
        "payload": {  
            "templateurl": "https://my.server.com/?user={user.name}&zip={user.zip}&c16={%sdkver%}&c27=cln,{a.PrevSessionLength}", 
            "templatebody": "c2RrdmVyPXslc2RrdmVyJX0mY2I9eyVjYWNoZWJ1c3QlfSZjbGllbnRJZD17bi5jbGllbnQuaWR9JnRzPXsldGltZXN0YW1wVSV9JnRzej17JXRpbWVzdGFtcFolfQ==", 
            "contenttype": "application/x-www-form-urlencoded",  
            "timeout": 4 
        }, 
        "showOffline": true, 
        "showRule": "always", 
        "endDate": 2524730400, 
        "startDate": 0, 
        "audiences": [], 
        "triggers": [ 
            { 
                "key": "pageName", 
                "matches": "eq", 
                "values": [ 
                    "MainMenu" 
                ] 
            } 
        ] 
    } 
] 
```

## Esempio di codice {#section_D063DE82976D4EDEA97E804BD1C4718F}

```js
HashMap<String, Object> contextData = new HashMap<String, Object>(); 
contextData.put("user.name", "bob"); 
contextData.put("user.zip", "90210"); 
Analytics.trackState("MainMenu", contextData);
```

Poiché il suo stato è `"MainMenu"`, questa chiamata di tracciamento attiva il messaggio di postback riportato sopra. L&#39;URL sostituirà tutte le variabili di modello con i valori dell&#39;hit. Presupponendo che la sessione precedente dell&#39;utente sia durata 132 secondi e che l&#39;utente esegua la versione 4.6.0 dell&#39;SDK per Android, l&#39;URL risultante dovrebbe essere simile al seguente:

`https://my.server.com/?user=bob&zip=90210&c16=4.6.0-AN&c27=cln,132`
