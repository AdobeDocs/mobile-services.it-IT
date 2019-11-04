---
description: Per iniziare a utilizzare Experience Cloud Device Co-op, contatta il tuo rappresentante Adobe.
seo-description: Per iniziare a utilizzare Experience Cloud Device Co-op, contatta il tuo rappresentante Adobe.
seo-title: Experience Cloud Device Co-op
title: Experience Cloud Device Co-op
uuid: 7bb8a19c-4b80-4911-879d-f9941baa3b62
translation-type: ht
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Experience Cloud Device Co-op {#experience-cloud-device-co-op}

Per iniziare a utilizzare Experience Cloud Device Co-op, contatta il tuo rappresentante Adobe.

Per abilitare le app mobile per Experience Cloud Device Co-op, completa i seguenti passaggi per gli SDK di Experience Cloud per Android:

>[!IMPORTANT]
>
>Questa funzionalità richiede la versione SDK 4.8.3 o successiva per Android.

A partire dalla versione 4.16.1 dell’SDK, i membri Device Co-op possono scegliere di escludere da Experience Cloud Device Co-op i propri dati relativi ai dispositivi mobili. Per ulteriori informazioni, vedi  [File di configurazione ADBMobile JSON](/help/android/configuration/json-config/json-config.md) e il `visitorAPI.js` metodo per [isCoopSafe](https://marketing.adobe.com/resources/help/it_IT/mcvid/mcvid-coopsafe.html).

1. Implementa l'SDK di Adobe Mobile.

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

I membri Device Co-op che necessitano tale valore impostato su `true` devono rivolgersi al team Co-op e richiedere un flag blacklist sul proprio account Device Co-op. Non esiste alcun percorso self-service per l'attivazione di questi flag.

Considerazioni da ricordare:

* Quando `coopUnsafe` è impostato su `true`, agli hit di Audience Manager e del servizio ID visitatori verrà sempre aggiunto `coop_unsafe=1`.
* Se abiliti l’inoltro lato server da Analytics ad Audience Manager, troverai l’hit di Analytics `coop_unsafe=1`.