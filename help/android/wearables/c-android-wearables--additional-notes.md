---
description: Ecco alcune informazioni che aiutano nella configurazione dell'estensione Android che consente di raccogliere dati dall'app Android Wearable.
seo-description: Ecco alcune informazioni che aiutano nella configurazione dell'estensione Android che consente di raccogliere dati dall'app Android Wearable.
seo-title: Note aggiuntive su Android Wearable
solution: Marketing Cloud,Analytics
title: Android Wearables  Additional Notes
topic: Sviluppatore e implementazione
uuid: 3bcf352b-4d46-4ab3-81ec-c27e86fe9be3
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Android Wearables: additional notes{#android-wearables-additional-notes}

Ecco alcune informazioni che aiutano nella configurazione dell'estensione Android che consente di raccogliere dati dall'app Android Wearable.

* L'estensione Adobe Mobile Android Wearable richiede la versione di Android 4.4 (KitKat) o superiore.
* Esiste un valore contestuale aggiuntivo, `A.RunMode`, che è stato aggiunto per indicare se i dati provengono dall'app contenente o dall'o estensione.

   * `RunMode` = `Application`

      L’hit viene dall’app handheld.

   * `RunMode` = `Extension`

      L’hit proviene dall’app wearable.

* The SDK automatically syncs the `aid`/`vid`/`visitor` `service id`/`privacy` status from the handheld app to the wearable app, so do not call `setPrivacyStatus`/`setUserIdentifier`/`idSync` from the wearable app.
* [I messaggi](/help/android/messaging-main/messaging/messaging.md)in-app, [Target](/help/android/target-main/target.md)e [Audience Manager](/help/android/audience-manager/audiencemgmt.md) sono disabilitati per l'app wearable.

