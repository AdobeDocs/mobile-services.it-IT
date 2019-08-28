---
description: Definizione ed esempi di codice sorgente per la funzione Postback.
seo-description: Definizione ed esempi di codice sorgente per la funzione Postback.
seo-title: Esempio di postback
solution: Marketing Cloud, Analytics
title: Esempio di postback
topic: Sviluppatore e implementazione
uuid: 809 c 5646-7 a 80-40 df -984 b -0 af 89 d 854259
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Postback example {#postback-example}

Definizione ed esempi di codice sorgente per la funzione Postback.

>[!CAUTION]
>
>Questo esempio viene fornito solo a scopo informativo. Il file `ADBMobileConfig.json` deve essere configurato nell'interfaccia utente di Adobe Mobile e non deve essere modificato manualmente. Un file di configurazione modificato manualmente rappresenta un rischio quando è attiva la configurazione di messaggi in remoto.

## ADBMobileConfig.json definition {#section_0F6EC001AB6D488E815F50C7F5DA022E}

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

## Code sample {#section_8169B88A2C634CB788DA574EE8C4B1DC}

```objective-c
NSDictionary *contextData = @{@"user.name":@"bob", @"user.zip":@"90210"}; 
[ADBMobile trackState:@"MainMenu" data:contextData];
```

Because its state is `“MainMenu”`, this tracking call triggers the above postback message. L'URL sostituisce tutte le variabili di modello con i valori dell'hit. Presupponendo che la sessione precedente dell'utente sia durata di 132 secondi e che l'utente sia sulla versione SDK 4.6.0 per iOS, ecco un esempio dell'URL risultante:

`https://my.server.com/?user=bob&zip=90210&c16=4.6.0-iOS&c27=cln,132`