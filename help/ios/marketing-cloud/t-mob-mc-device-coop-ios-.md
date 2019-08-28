---
description: Per iniziare a utilizzare Experience Cloud Device Co-op, contatta il tuo rappresentante Adobe.
seo-description: Per iniziare a utilizzare Experience Cloud Device Co-op, contatta il tuo rappresentante Adobe.
seo-title: Experience Cloud Device Co-op
title: Experience Cloud Device Co-op
uuid: 434 a 6 f 8 f-ec 24-439 d -95 f 0-a 246 b 384 b 3 b 5
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Experience Cloud Device Co-op {#experience-cloud-device-co-op}

Per iniziare a utilizzare Experience Cloud Device Co-op, contatta il tuo rappresentante Adobe.

Per abilitare Experience Cloud Device Co-op nelle tue app per dispositivi mobili, effettua i passaggi seguenti per gli SDK iOS di Experience Cloud.

>[!IMPORTANT]
>
>Questa funzionalità richiede la versione SDK 4.8.5 o successiva per iOS.

A partire dalla versione 4.16.1 dell’SDK, i membri Device Co-op possono scegliere di escludere da Experience Cloud Device Co-op i propri dati relativi ai dispositivi mobili. Per ulteriori informazioni, vedi [File di configurazione ADBMobile JSON](/help/ios/configuration/json-config/json-config.md) e il metodo `visitorAPI.js` per [isCoopSafe](https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid-coopsafe.html).

1. Implementa l'SDK di Adobe Mobile.

   Per ulteriori informazioni, vedi [Implementazione di base e ciclo di vita](/help/ios/getting-started/dev-qs.md).
1. Abilita il tuo servizio Experience Cloud ID.

   For more information, see [Experience Cloud ID](/help/ios/marketing-cloud/mcvid.md).
1. Passa le identità autenticate, come ad esempio gli ID CRM o indirizzi e-mail con hash, utilizzando uno dei metodi di sincronizzazione qui descritti.

   Per ulteriori informazioni, vedi [Metodi del servizio identità Adobe Experience Platform](/help/ios/marketing-cloud/mc-methods.md).

## `coopUnsafe` flag

Here is some additional information on the `coopUnsafe` flag:

* Versione SDK minima: 4.16.1
* The Boolean property of the `marketingCloud` object that, when set to `true`, causes the device to be opted-out of the Experience Cloud's Device Co-Op.
* Il valore predefinito è `false`.
* Questa impostazione è utilizzata **solo** per i clienti abilitati per Device Co-op.

I membri Device Co-op che necessitano tale valore impostato su `true` devono rivolgersi al team Co-op e richiedere un flag blacklist sul proprio account Device Co-op. Non esiste alcun percorso self-service per l'attivazione di questi flag.

Considerazioni da ricordare:

* When `coopUnsafe` is set to `true`, `coop_unsafe=1` will always be appended to Audience Manager and Visitor ID hits.
* Se abiliti l’inoltro lato server da Analytics ad Audience Manager, negli hit di Analytics troverai `coop_unsafe=1`.


