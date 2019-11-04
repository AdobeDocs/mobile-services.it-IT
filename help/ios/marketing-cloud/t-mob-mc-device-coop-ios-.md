---
description: Per iniziare a utilizzare Experience Cloud Device Co-op, contatta il tuo rappresentante Adobe.
seo-description: Per iniziare a utilizzare Experience Cloud Device Co-op, contatta il tuo rappresentante Adobe.
seo-title: Experience Cloud Device Co-op
title: Experience Cloud Device Co-op
uuid: 434a6f8f-ec24-439d-95f0-a246b384b3b5
translation-type: ht
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Experience Cloud Device Co-op {#experience-cloud-device-co-op}

Per iniziare a utilizzare Experience Cloud Device Co-op, contatta il tuo rappresentante Adobe.

Per abilitare Experience Cloud Device Co-op nelle tue app per dispositivi mobili, effettua i passaggi seguenti per gli SDK iOS di Experience Cloud.

>[!IMPORTANT]
>
>Questa funzione richiede la versione SDK 4.8.5 o successiva per iOS.

A partire dalla versione 4.16.1 dell’SDK, i membri Device Co-op possono scegliere di escludere da Experience Cloud Device Co-op i propri dati relativi ai dispositivi mobili. Per ulteriori informazioni, vedi  [File di configurazione ADBMobile JSON](/help/ios/configuration/json-config/json-config.md) e il `visitorAPI.js` metodo per [isCoopSafe](https://marketing.adobe.com/resources/help/it_IT/mcvid/mcvid-coopsafe.html).

1. Implementa l'SDK di Adobe Mobile.

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

I membri Device Co-op che necessitano tale valore impostato su `true` devono rivolgersi al team Co-op e richiedere un flag blacklist sul proprio account Device Co-op. Non esiste alcun percorso self-service per l'attivazione di questi flag.

Considerazioni da ricordare:

* Quando `coopUnsafe` è impostato su `true`, agli hit di Audience Manager e del servizio ID visitatori verrà sempre aggiunto `coop_unsafe=1`.
* Se abiliti l’inoltro lato server da Analytics ad Audience Manager, negli hit di Analytics troverai `coop_unsafe=1`.


