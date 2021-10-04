---
description: Per iniziare a utilizzare Experience Cloud Device Co-op, contatta il tuo rappresentante Adobe.
title: Experience Cloud Device Co-op
uuid: 7bb8a19c-4b80-4911-879d-f9941baa3b62
exl-id: e34b8a7e-3b70-4725-94a5-9903987c34f8
source-git-commit: d1ebb2bbc4742f5288f90a90e977d252f3f30aa3
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 97%

---

# Experience Cloud Device Co-op {#experience-cloud-device-co-op}

Per iniziare a utilizzare Experience Cloud Device Co-op, contatta il tuo rappresentante Adobe.

Per abilitare le app mobili per Experience Cloud Device Co-op, completa i seguenti passaggi per gli SDK di Experience Cloud per Android:

>[!IMPORTANT]
>
>Questa funzionalità richiede la versione SDK 4.8.3 o successiva per Android.

A partire dall’SDK versione 4.16.1, i membri di Device Co-op possono scegliere di rimuovere i dati dei propri dispositivi mobili da Experience Cloud Device Co-op. Per ulteriori informazioni, vedi [File di configurazione ADBMobile JSON](/help/android/configuration/json-config/json-config.md) e il metodo `visitorAPI.js` per [isCoopSafe](https://experienceleague.adobe.com/docs/id-service/using/id-service-api/configurations/coopsafe.html).

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

Per i membri Device Co-op che richiedono che questo valore sia impostato come `true`, è necessario collaborare con il team Co-op per richiedere un flag di blocklist per l’account Device Co-op. Non esiste alcun percorso self-service per l&#39;attivazione di questi flag.

Considerazioni da ricordare:

* Quando `coopUnsafe` è impostato su `true`, `coop_unsafe=1` agli hit di Audience Manager e del servizio ID visitatori verrà sempre aggiunto.
* Se abiliti l’inoltro lato server da Analytics ad Audience Manager, troverai l’hit di Analytics `coop_unsafe=1`.
