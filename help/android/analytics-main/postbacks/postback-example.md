---
description: Puoi usare queste informazioni per comprendere cosa sono i postback e come funzionano.
keywords: android; libreria; mobile; sdk
seo-description: Puoi usare queste informazioni per comprendere cosa sono i postback e come funzionano.
seo-title: Esempi di postback
solution: Marketing Cloud, Analytics
title: Esempi di postback
topic: Sviluppatore e implementazione
uuid: 8010 cd 00-d 42 b -4 e 16-8403-692 fab 2550 f 1
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Postbacks example {#postbacks-example}

Puoi utilizzare queste informazioni per comprendere quali postback sono e come funzionano.

>[!CAUTION]
>
>Questo esempio viene fornito solo a scopo informativo. Il file `ADBMobileConfig.json` deve essere configurato nell'interfaccia utente di Adobe Mobile e non deve essere modificato manualmente. Un file di configurazione modificato manualmente rappresenta un rischio quando è attiva la configurazione di messaggi in remoto.

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

## Code sample {#section_D063DE82976D4EDEA97E804BD1C4718F}

```js
HashMap<String, Object> contextData = new HashMap<String, Object>(); 
contextData.put("user.name", "bob"); 
contextData.put("user.zip", "90210"); 
Analytics.trackState("MainMenu", contextData);
```

Because its state is `“MainMenu”`, this tracking call triggers the above postback message. L'URL sostituirà tutte le variabili di modello con i valori dell'hit. Presupponendo che la sessione precedente dell'utente abbia avuto una durata di 132 secondi e che l'utente sia nella versione 4.6.0 di Android SDK, l'URL risultante si presenta così:

`https://my.server.com/?user=bob&zip=90210&c16=4.6.0-AN&c27=cln,132`
