---
description: Dopo aver configurato l'URL di collegamento profondo (deep linking) nell'interfaccia utente di Adobe Mobile Services, tale URL si troverà nel payload push con la chiave adb_deeplink.
title: Implementare i messaggi push con collegamenti profondi
uuid: ee9590fc-8bd3-4111-9221-9011d9edbd84
exl-id: c9ca955c-506f-45fe-82d6-fad2f9a80130
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '160'
ht-degree: 96%

---

# Implementare i messaggi push con collegamenti profondi {#implement-push-messaging-with-deep-linking}

Dopo aver configurato l&#39;URL di collegamento profondo (deep linking) nell&#39;interfaccia utente di Adobe Mobile Services, tale URL si troverà nel payload push con la chiave `adb_deeplink`.

1. In AppDelegate, puoi recuperare l&#39;URL di collegamento profondo e gestirlo autonomamente nelle seguenti posizioni:

   * In `application:didFinishLaunchingWithOptions`:

      Se l&#39;app non è in esecuzione quando si verifica un click-through push, puoi ottenere il payload push da `launchOptions`; l&#39;URL di collegamento profondo si trova nel dizionario di payload accanto alla chiave `adb_deeplink`.

   * I metodi delegate per le notifiche remote

      Nell&#39;applicazione `didReceiveRemoteNotification:` o `didReceiveRemoteNotification:fetchCompletionHandler:`, puoi ottenere l&#39;URL mediante l&#39;accesso al dizionario `userInfo` con la chiave `adb_deeplink`.

   * I metodi delegate per `UNUserNotificationCenter`

      Nel metodo `userNotificationCenter:didReceiveNotificationResponse:withCompletionHandler:` puoi ottenere il payload push dal dizionario `userInfo` nella chiave `adb_deeplink`.

Ad esempio:

```objective-c
- (BOOL) application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
    NSDictionary *remoteNotification = launchOptions[UIApplicationLaunchOptionsRemoteNotificationKey]; 
    if (remoteNotification && [remoteNotification isKindOfClass:[NSDictionary class]]) { 
        NSString *deeplink = remoteNotification[@"adb_deeplink"]; 
        // handle deep link url 
    }
    return YES; 
} 
  
// app target < iOS 7 
- (void) application:(UIApplication *)application didReceiveRemoteNotification:(NSDictionary *)userInfo { 
    // only send the hit if the app is not active 
    if (application.applicationState == UIApplicationStateInactive) { 
        [ADBMobile trackPushMessageClickThrough:userInfo]; 
        NSString *deeplink = userInfo[@"adb_deeplink"]; 
        // handle deep link url 
    } 
} 
  
// app target >= iOS 7 
- (void)application:(UIApplication *)application didReceiveRemoteNotification:(NSDictionary *)userInfo fetchCompletionHandler:(void (^)(UIBackgroundFetchResult))completionHandler { 
    if (application.applicationState == UIApplicationStateInactive) { 
        [ADBMobile trackPushMessageClickThrough:userInfo]; 
        NSString *deeplink = userInfo[@"adb_deeplink"]; 
        // handle deep link url 
    } 
    ... 
} 
 
// if using UNUserNotificationCenterDelegate and device is running iOS 10 or newer 
- (void) userNotificationCenter:(UNUserNotificationCenter *)center didReceiveNotificationResponse:(UNNotificationResponse *)response withCompletionHandler:(void (^)(void))completionHandler { 
    if ([response.notification.request.trigger isKindOfClass:UNPushNotificationTrigger.class]) { 
        [ADBMobile trackPushMessageClickThrough:response.notification.request.content.userInfo]; 
        NSString *deeplink = response.notification.request.content.userInfo[@"adb_deeplink"]; 
        // handle deep link url  
    } 
    ... 
}
```
