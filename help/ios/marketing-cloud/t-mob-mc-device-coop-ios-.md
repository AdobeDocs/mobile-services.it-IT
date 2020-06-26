---
description: Per iniziare a utilizzare Experience Cloud Device Co-op, contatta il tuo rappresentante Adobe.
seo-description: Per iniziare a utilizzare Experience Cloud Device Co-op, contatta il tuo rappresentante Adobe.
seo-title: Experience Cloud Device Co-op
title: Experience Cloud Device Co-op
uuid: 434a6f8f-ec24-439d-95f0-a246b384b3b5
translation-type: ht
source-git-commit: 86ba045b44bf6553e80727c0d61ccdd9a552d16c
workflow-type: ht
source-wordcount: '292'
ht-degree: 100%

---


# Experience Cloud Device Co-op {#experience-cloud-device-co-op}

Per iniziare a utilizzare Experience Cloud Device Co-op, contatta il tuo rappresentante Adobe.

Per abilitare le app mobili per Experience Cloud Device Co-op, completa i seguenti passaggi per gli SDK di Experience Cloud per iOS.

>[!IMPORTANT]
>
>Questa funzione richiede la versione SDK 4.8.5 o successiva per iOS.

A partire dall’SDK versione 4.16.1, i membri di Device Co-op possono scegliere di rimuovere i dati dei propri dispositivi mobili da Experience Cloud Device Co-op. Per ulteriori informazioni, vedi [File di configurazione ADBMobile JSON](/help/ios/configuration/json-config/json-config.md) e il metodo `visitorAPI.js` per [isCoopSafe](https://docs.adobe.com/content/help/it-IT/id-service/using/id-service-api/configurations/coopsafe.html).

1. Implementa l&#39;SDK di Adobe Mobile.

   Per ulteriori informazioni, vedi [Implementazione e ciclo di vita di base](/help/ios/getting-started/dev-qs.md).
1. Abilita il tuo servizio Experience Cloud ID.

   Per ulteriori informazioni, consulta [Experience Cloud ID](/help/ios/marketing-cloud/mcvid.md).
1. Passa le identità autenticate, come ad esempio gli ID CRM o indirizzi e-mail con hash, utilizzando uno dei metodi di sincronizzazione qui descritti.

   Per ulteriori informazioni, vedi [Metodi di Adobe Experience Platform Identity](/help/ios/marketing-cloud/mc-methods.md).

## Flag `coopUnsafe`

Ecco alcune informazioni aggiuntive sul flag `coopUnsafe`:

* Versione SDK minima: 4.16.1
* Proprietà booleana dell’oggetto `marketingCloud` che, se impostata su `true`, determina il rifiuto di partecipazione a Experience Cloud Device Co-op.
* Il valore predefinito è `false`.
* Questa impostazione è utilizzata **solo** per i clienti abilitati per Device Co-op.

Per i membri Device Co-op che richiedono che questo valore sia impostato come `true`, è necessario collaborare con il team Co-op per richiedere un flag di blocklist per l’account Device Co-op. Non esiste alcun percorso self-service per l&#39;attivazione di questi flag.

Considerazioni da ricordare:

* Quando `coopUnsafe` è impostato su `true`, `coop_unsafe=1` agli hit di Audience Manager e del servizio ID visitatori verrà sempre aggiunto.
* Se abiliti l’inoltro lato server da Analytics ad Audience Manager, negli hit di Analytics troverai `coop_unsafe=1`.


