---
description: Per iniziare a utilizzare Experience Cloud Device Co-op, contatta il tuo rappresentante Adobe.
seo-description: Per iniziare a utilizzare Experience Cloud Device Co-op, contatta il tuo rappresentante Adobe.
seo-title: Experience Cloud Device Co-op
title: Experience Cloud Device Co-op
uuid: 7bb8a19c-4b80-4911-879d-f9941baa3b62
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Experience Cloud Device Co-op {#experience-cloud-device-co-op}

Per iniziare a utilizzare Experience Cloud Device Co-op, contatta il tuo rappresentante Adobe.

Per abilitare le app mobile per Experience Cloud Device Co-op, completa i seguenti passaggi per gli SDK di Experience Cloud per Android:

>[!IMPORTANT]
>
>Questa funzionalità richiede la versione 4.8.3 o successiva dell’SDK per Android.

A partire dalla versione 4.16.1 dell’SDK, i membri Device Co-op possono scegliere di escludere da Experience Cloud Device Co-op i propri dati relativi ai dispositivi mobili. Per ulteriori informazioni, vedi [File di configurazione ADBMobile JSON](/help/android/configuration/json-config/json-config.md) e il metodo `visitorAPI.js` per [isCoopSafe](https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid-coopsafe.html).

1. Implementa l'SDK di Adobe Mobile.

   For more information, see Core Implementation and Lifecycle.[](/help/android/getting-started/dev-qs.md)
1. Abilita il tuo servizio Experience Cloud ID.

   For more information, see [Experience Cloud ID Configuration](/help/android/c-marketing-cloud/mcvid.md).
1. Passa le identità autenticate, come ad esempio gli ID CRM o indirizzi e-mail con hash, utilizzando uno dei metodi di sincronizzazione.

   Per ulteriori informazioni, vedi Metodi [del servizio identità](/help/android/c-marketing-cloud/mc-methods.md)Adobe Experience Platform.

## `coopUnsafe` flag

Ecco alcune informazioni aggiuntive sul flag `coopUnsafe`:

* Versione SDK minima: 4.16.1
* The Boolean property of the `marketingCloud` object that, when set to `true`, causes the device to be opted-out of the Experience Cloud's Device Co-Op.
* Il valore predefinito è `false`.
* Questa impostazione è utilizzata **solo** per i clienti abilitati per Device Co-op.

I membri Device Co-op che necessitano tale valore impostato su `true` devono rivolgersi al team Co-op e richiedere un flag blacklist sul proprio account Device Co-op. Non esiste alcun percorso self-service per l'attivazione di questi flag.

Considerazioni da ricordare:

* When `coopUnsafe` is set to `true`, `coop_unsafe=1` will always be appended to Audience Manager and Visitor ID hits.
* If you enable Analytics server-side forwarding to Audience Manager, you will also see `coop_unsafe=1` Analytics hits.