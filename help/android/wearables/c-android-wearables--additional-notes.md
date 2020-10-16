---
description: Informazioni utili per configurare l’estensione Android, che consente di raccogliere dati dall’app Android Wearable.
seo-description: Informazioni utili per configurare l’estensione Android, che consente di raccogliere dati dall’app Android Wearable.
seo-title: Wearable Android - Note aggiuntive
solution: Experience Cloud,Analytics
title: Wearable Android - Note aggiuntive
topic: Developer and implementation
uuid: 3bcf352b-4d46-4ab3-81ec-c27e86fe9be3
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '161'
ht-degree: 100%

---


# Wearable Android: note aggiuntive {#android-wearables-additional-notes}

Informazioni utili per configurare l’estensione Android, che consente di raccogliere dati dall’app Android Wearable.

* L’estensione Adobe Mobile per Android Wearable richiede la versione Android 4.4 (KitKat) o superiore.
* Esiste un valore contestuale aggiuntivo, `A.RunMode`, che è stato aggiunto per indicare se i dati provengono dall&#39;app contenente o dall&#39;o estensione.

   * `RunMode` = `Application`

      L’hit proviene dall’app Handheld.

   * `RunMode` = `Extension`

      L’hit proviene dall’app Wearable.

* L&#39;SDK sincronizza automaticamente lo stato `aid`/`vid`/`visitor`/`service id`/`privacy` dall&#39;app Handheld all&#39;app Wearable, pertanto non occorre chiamare `setPrivacyStatus`/`setUserIdentifier`/`idSync` dall&#39;app Wearable.
* [I messaggi in-app](/help/android/messaging-main/messaging/messaging.md), [Target](/help/android/target-main/target.md) e [Audience Manager](/help/android/audience-manager/audiencemgmt.md) sono disabilitati per l&#39;app Wearable.

