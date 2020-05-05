---
description: Per iniziare a utilizzare Experience Cloud Device Co-op, contatta il tuo rappresentante Adobe.
seo-description: Per iniziare a utilizzare Experience Cloud Device Co-op, contatta il tuo rappresentante Adobe.
seo-title: Experience Cloud Device Co-op
title: Experience Cloud Device Co-op
uuid: 7bb8a19c-4b80-4911-879d-f9941baa3b62
translation-type: tm+mt
source-git-commit: 82b3dc38a0325b3aa733b491ddad9b59dbe84eaa

---


# Experience Cloud Device Co-op {#experience-cloud-device-co-op}

Per iniziare a utilizzare Experience Cloud Device Co-op, contatta il tuo rappresentante Adobe.

Per abilitare Experience Cloud Device Co-op nelle tue app mobile, completa i seguenti passaggi per gli SDK Experience Cloud per Android:

>[!IMPORTANT]
>
>Questa funzionalità richiede la versione SDK 4.8.3 o successiva per Android.

A partire dalla versione SDK 4.16.1, i membri di Device Co-op possono scegliere i propri dati dei dispositivi mobili da Experience Cloud Device Co-op. Per ulteriori informazioni, vedi Configurazione [JSON](/help/android/configuration/json-config/json-config.md) ADBMobile e il `visitorAPI.js` metodo per [isCoopSafe](https://docs.adobe.com/content/help/en/id-service/using/id-service-api/configurations/coopsafe.html).

1. Implementa l&#39;SDK di Adobe Mobile.

   Per ulteriori informazioni, vedi [Implementazione e ciclo di vita di base](/help/android/getting-started/dev-qs.md).
1. Abilita il tuo servizio Experience Cloud ID.

   Per ulteriori informazioni, consulta [Configurazione Experience Cloud ID](/help/android/c-marketing-cloud/mcvid.md).
1. Passa le identità autenticate, come ad esempio gli ID CRM o indirizzi e-mail con hash, utilizzando uno dei metodi di sincronizzazione.

   Per ulteriori informazioni, vedi [Metodi di Adobe Experience Platform Identity](/help/android/c-marketing-cloud/mc-methods.md).

## Flag `coopUnsafe`

Ecco alcune informazioni aggiuntive sul flag `coopUnsafe`:

* Versione SDK minima: 4.16.1
* Proprietà booleana dell’oggetto `marketingCloud` che, se impostata su `true`, determina il rifiuto di partecipazione a Experience Cloud Device Co-op.
* Il valore predefinito è `false`.
* Questa impostazione è utilizzata **solo** per i clienti abilitati per Device Co-op.

I membri Device Co-op che necessitano tale valore impostato su `true` devono rivolgersi al team Co-op e richiedere un flag blacklist sul proprio account Device Co-op. Non esiste alcun percorso self-service per l&#39;attivazione di questi flag.

Considerazioni da ricordare:

* Quando `coopUnsafe` è impostato su `true`, agli hit di Audience Manager e del servizio ID visitatori verrà sempre aggiunto `coop_unsafe=1`.
* Se abiliti l’inoltro lato server da Analytics ad Audience Manager, troverai l’hit di Analytics `coop_unsafe=1`.