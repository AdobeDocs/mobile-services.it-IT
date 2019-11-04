---
description: Ecco alcune informazioni che aiutano nella configurazione dell'estensione Android che consente di raccogliere dati dall'app Android Wearable.
seo-description: Ecco alcune informazioni che aiutano nella configurazione dell'estensione Android che consente di raccogliere dati dall'app Android Wearable.
seo-title: 'Wearable Android: note aggiuntive'
solution: Experience Cloud,Analytics
title: 'Wearable Android: note aggiuntive'
topic: Sviluppatore e implementazione
uuid: 3bcf352b-4d46-4ab3-81ec-c27e86fe9be3
translation-type: ht
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Wearable Android: note aggiuntive{#android-wearables-additional-notes}

Ecco alcune informazioni che aiutano nella configurazione dell'estensione Android che consente di raccogliere dati dall'app Android Wearable.

* L'estensione Adobe Mobile Android Wearable richiede la versione di Android 4.4 (KitKat) o superiore.
* Esiste un valore contestuale aggiuntivo, `A.RunMode`, che è stato aggiunto per indicare se i dati provengono dall'app contenente o dall'o estensione.

   * `RunMode` = `Application`

      L’hit proviene dall’app Handheld.

   * `RunMode` = `Extension`

      L’hit proviene dall’app Wearable.

* L'SDK sincronizza automaticamente lo stato `aid`/`vid`/`visitor`/`service id`/`privacy` dall'app Handheld all'app Wearable, pertanto non occorre chiamare `setPrivacyStatus`/`setUserIdentifier`/`idSync` dall'app Wearable.
* [I messaggi in-app](/help/android/messaging-main/messaging/messaging.md), [Target](/help/android/target-main/target.md) e [Audience Manager](/help/android/audience-manager/audiencemgmt.md) sono disabilitati per l'app Wearable.

