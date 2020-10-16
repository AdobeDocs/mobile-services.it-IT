---
description: Definizione ed esempi di codice sorgente per la funzione Postback.
seo-description: Definizione ed esempi di codice sorgente per la funzione Postback.
seo-title: Esempio di postback
solution: Experience Cloud,Analytics
title: Esempio di postback
topic: Developer and implementation
uuid: 809c5646-7a80-40df-984b-0af89d854259
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '124'
ht-degree: 100%

---


# Esempio di postback {#postback-example}

Definizione ed esempi di codice sorgente per la funzione Postback.

>[!CAUTION]
>
>Questo esempio è fornito unicamente a scopo informativo. Il file `ADBMobileConfig.json` deve essere configurato nell&#39;interfaccia utente di Adobe Mobile e non deve essere modificato manualmente. Un file di configurazione modificato manualmente rappresenta un rischio quando è attiva la configurazione di messaggi in remoto.

## Definizione di ADBMobileConfig.json {#section_0F6EC001AB6D488E815F50C7F5DA022E}

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

## Esempio di codice {#section_8169B88A2C634CB788DA574EE8C4B1DC}

```objective-c
NSDictionary *contextData = @{@"user.name":@"bob", @"user.zip":@"90210"}; 
[ADBMobile trackState:@"MainMenu" data:contextData];
```

Poiché il suo stato è `“MainMenu”`, questa chiamata di tracciamento attiva il messaggio di postback riportato sopra. L&#39;URL sostituisce tutte le variabili di modello con i valori dell&#39;hit. Presupponendo che la sessione precedente dell&#39;utente sia durata 132 secondi e che l&#39;utente disponga della versione SDK 4.6.0 per iOS, ecco un esempio dell&#39;URL risultante:

`https://my.server.com/?user=bob&zip=90210&c16=4.6.0-iOS&c27=cln,132`
