---
description: Dopo aver configurato l'URL di collegamento profondo (deep linking) nell'interfaccia utente di Adobe Mobile Services, tale URL si troverà nel payload push con la chiave adb_deeplink.
seo-description: Dopo aver configurato l'URL di collegamento profondo (deep linking) nell'interfaccia utente di Adobe Mobile Services, tale URL si troverà nel payload push con la chiave adb_deeplink.
seo-title: Implementare i messaggi push con collegamenti profondi
title: Implementare i messaggi push con collegamenti profondi
uuid: ee 9590 fc -8 bd 3-4111-9221-9011 d 9 edbd 84
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Implement push messaging with deep linking {#implement-push-messaging-with-deep-linking}

Dopo aver configurato l'URL di collegamento profondo (deep linking) nell'interfaccia utente di Adobe Mobile Services, tale URL si troverà nel payload push con la chiave `adb_deeplink`.

1. In AppDelegate, puoi recuperare l'URL di collegamento profondo e gestirlo autonomamente nelle seguenti posizioni:

   * In `application:didFinishLaunchingWithOptions`:

      Se l'app non è in esecuzione quando si verifica un click-through push, puoi ottenere il payload push da `launchOptions`; l'URL di collegamento profondo si trova nel dizionario di payload accanto alla chiave `adb_deeplink`.

   * I metodi delegate per le notifiche remote

      In the `didReceiveRemoteNotification:` application or in the `didReceiveRemoteNotification:fetchCompletionHandler:` application, you can get the URL by accessing the `userInfo` dictionary with the `adb_deeplink` key.

   * The delegate methods for `UNUserNotificationCenter`

      In the `userNotificationCenter:didReceiveNotificationResponse:withCompletionHandler:` method, you can get the push payload from the `userInfo` dictionary, in the `adb_deeplink` key.

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

