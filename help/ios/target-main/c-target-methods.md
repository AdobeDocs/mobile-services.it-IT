---
description: Elenco dei metodi di Adobe Target forniti dalla libreria iOS.
seo-description: Elenco dei metodi di Adobe Target forniti dalla libreria iOS.
seo-title: Metodi di destinazione iOS per Adobe Mobile Services
solution: Marketing Cloud,Analytics
title: Metodi di destinazione per iOS
topic: Developer and implementation
uuid: 692bcda1-02ba-4902-bd65-15888adf1952
translation-type: tm+mt
source-git-commit: c198ae57b05f8965a8e27191443ee2cd552d6c50
workflow-type: tm+mt
source-wordcount: '656'
ht-degree: 100%

---


# Metodi di destinazione per iOS {#target-methods}

Elenco dei metodi di Adobe Target forniti dalla libreria iOS.

L&#39;SDK supporta attualmente più soluzioni Adobe Experience Cloud, tra cui Analytics, Target, Audience Manager e il servizio Adobe Experience Platform Identity. Ai metodi è applicato il prefisso della relativa soluzione. Ad esempio, i metodi di hanno il prefisso `target`target.

>[!TIP]
>
>Le metriche del ciclo di vita sono inviate come parametri a ciascun caricamento Mbox. Per ulteriori informazioni, vedi [Metriche del ciclo di vita](/help/ios/metrics.md). Se invii richieste Target all&#39;interno del metodo `didFinishLaunching` delegate, aggiungi un `[ADBMobile trackAction:data:]` o una chiamata `[ADBMobile trackState:data:]` prima del codice di implementazione di Target. In questo modo, le richieste Target conterranno tutti i dati del ciclo di vita.

## Guida di riferimento della classe ADBTargetLocationRequest

### Proprietà

```objective-c
NSString *name; 
NSString *defaultContent; 
NSMutableDictionary *parameters;
```

### Costanti di stringa

>[!TIP]
>
>Le seguenti costanti di stringa offrono facilità di utilizzo quando imposti le chiavi per i parametri personalizzati.

```iOS
NSString *const ADBTargetParameterOrderId; 
NSString *const ADBTargetParameterOrderTotal; 
NSString *const ADBTargetParameterProductPurchasedId; 
NSString *const ADBTargetParameterCategoryId; 
NSString *const ADBTargetParameterMbox3rdPartyId; 
NSString *const ADBTargetParameterMboxPageValue; 
NSString *const ADBTargetParameterMboxPc; 
NSString *const ADBTargetParameterMboxSessionId; 
NSString *const ADBTargetParameterMboxHost;
```

>[!IMPORTANT]
>
>* Se utilizzi gli SDK **precedenti** alla versione 4.14.0, consulta [Parametri di input](https://developers.adobetarget.com/api/#input-parameters) per conoscere le limitazioni relative ai parametri.
   >
   >
* Se utilizzi gli SDK versione 4.14.0 **o successiva**, consulta [Parametri batch di input](https://developers.adobetarget.com/api/#batch-input-parameters) per conoscere le limitazioni relative ai parametri.


### Metodi

* **targetLoadRequest:&#x200B;callback**

   Invia la richiesta al server di Target configurato e restituisce il valore della stringa dell&#39;offerta generato in un blocco `callback`.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      + (void) targetLoadRequest:(ADBTargetLocationRequest *)request
                        callback:(void (^)(NSString *content))callback;
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      [ADBMobile targetLoadRequest:myRequest
                          callback:^(NSString *content) {
                            // do something with content
                          }];
      ```

* **targetLoadRequestWithName:defaultContent:profileParameters:orderParameters:mboxParameters:requestLocationParameters:callback:**

   Invia una richiesta al server di Target configurato e restituisce il valore stringa dell&#39;offerta generata in una funzione callback di un blocco.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      + (void) targetLoadRequestWithName:(nullable NSString *)name
                          defaultContent:(nullable NSString *)defaultContent
                      profileParameters:(nullable NSDictionary *)profileParameters
                        orderParameters:(nullable NSDictionary *)orderParameters
                         mboxParameters:(nullable NSDictionary *)mboxParameters
                requestLocationParameters:(nullable NSDictionary *)requestLocationParameters
                                 callback:(nullable void (^)(NSString
                                 * __nullable content))callback;
      ```

   * Restituisce: N/D

   * I parametri di questo metodo sono i seguenti:

      * **`name`**

         Nome dell&#39;Mbox/posizione Target che desideri recuperare.

         * **Tipo**: NSString*
      * **`defaultContent`**

         Valore restituito nella callback se il server di Target non è raggiungibile, oppure se l&#39;utente non è qualificato per la campagna.

         * **Tipo**: NSString*
      * **`profileParameters`**

         I valori in questo dizionario entrano nell&#39;oggetto &quot;profileParameters&quot; nella richiesta a Target.

         * **Tipo**: NSDictionary*
      * **`orderParameters`**

         I valori in questo dizionario entrano nell&#39;oggetto &quot;order&quot; nella richiesta a Target.

         * **Tipo**: NSDictionary
      * **`mboxParameters`**

         I valori in questo dizionario entrano nell&#39;oggetto &quot;mboxParameters&quot; nella richiesta a Target.

         * **Tipo**: NSDictionary*
      * **`requestLocationParameters`**

         I valori in questo dizionario entrano nell&#39;oggetto &quot;requestLocation&quot; nella richiesta a Target.

         **Tipo**: NSDictionary*

      * **`callback`**

         Questo metodo sarà chiamato con il contenuto dell&#39;offerta dal server di Target. Se non è possibile accedere al server di Target o se l&#39;utente non è idoneo per la campagna, viene restituito defaultContent.
      **Tipo**: Funzione

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      [ADBMobile targetLoadRequestWithName:@"myHeroBanner"
                            defaultContent:@"defaultHeroBanner.png"
                        profileParameters:@{@"age":@"20-29"}
                          orderParameters:nil
                           mboxParameters:@{@"customParam":@"customValue"}
                requestLocationParameters:@{@"host":@"my.hostname.com"}
                                 callback:^(NSString *content){
                                   // do something with content
                                   myImageView.image = [UIImage imageNamed:content];
                                 }];
      ```

      Per ulteriori informazioni sull&#39;API Target sottostante, consulta [Sviluppatori Adobe Target](https://docs.adobe.com/dev/products/target/reference/delivery.html).







* **targetLoadRequestWithName:defaultContent:profileParameters:orderParameters:mboxParameters:callback**

   Invia una richiesta al server di Target configurato e restituisce il valore stringa dell&#39;offerta generata in un callback di un blocco.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      + (void) targetLoadRequestWithName:(nullable NSString *)name
                          defaultContent:(nullable NSString *)defaultContent
                      profileParameters:(nullable NSDictionary *)profileParameters
                        orderParameters:(nullable NSDictionary *)orderParameters
                         mboxParameters:(nullable NSDictionary *)mboxParameters
                               callback:(nullable void (^)(NSString * __nullable content))callback;
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      [ADBMobile targetLoadRequestWithName:@"mboxName"
                            defaultContent:@"defaultContent"
                         profileParameters:{@"profile-parameter-key": @"profile-parameter-value"}
                           orderParameters:@{@"order-parameter-key": @"order-parameter-value"}
                            mboxParameters:@{@"mbox-parameter-key": @"mbox-parameter-value"}
                                   callback:^(NSString * content) {
                                           //do something with content 
                                 }
                               }];
      ```

* **targetCreateOrder&#x200B;ConfirmRequestWithName:&#x200B;orderId:&#x200B;orderTotal:&#x200B;productPurchasedId:&#x200B;parameters**

   Crea una `ADBTargetLocationRequest`.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      + (ADBTargetLocationRequest *)
      targetCreateOrderConfirmRequestWithName:(NSString *)name
                                      orderId:(NSString *)orderId
                                  orderTotal:(NSString *)orderTotal
                          productPurchasedId:(NSString *)productPurchasedId
                              parameters:(NSDictionary *)parameters;
      ```

* **targetCreateRequestWithName:&#x200B;&#x200B;defaultContent:&#x200B;parameters**

   Costruttore di convenienza per creare un oggetto ADBTargetLocationRequest con i parametri indicati.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      + (ADBTargetLocationRequest *)
      targetCreateRequestWithName:(NSString *)name
                           defaultContent:(NSString *)defaultContent
                               parameters:(NSDictionary *)parameters;
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      ADBTargetLocationRequest *myRequest =  
      [ADBMobile targetCreateRequestWithName:@"heroBanner"
                              defaultContent:@"default.png"
                                  parameters:nil];
      ```

* **targetThirdPartyID**

   Restituisce l&#39;ID di terze parti.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      + (nullable NSString *) targetThirdPartyID;
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      NSString *thirdPartyId = [ADBMobile targetThirdPartyID];
      ```

* **targetSetThirdPartyID**

   Imposta l&#39;ID di terze parti.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      + (void) targetSetThirdPartyID:(nullable NSString *)thirdPartyID;
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      [ADBMobile targetSetThirdPartyID:@"thirdPartyID"];
      ```

* **targetClearCookies**

   Elimina tutti i cookie di Target dall&#39;applicazione.

   >[!TIP]
   >
   >A partire dalla versione 4.10.0 dell&#39;SDK, Target non usa più i cookie. Questo metodo reimposta gli ID thirdPartyID e sessionID.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      + (void) targetClearCookies;
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      [ADBMobile targetClearCookies];
      ```

* **targetPcID**

   Restituisce il PcID.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      + (nullable NSString *) targetPcID;
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      NSString *myTargetPcID = [ADBMobile targetPcID];
      ```

* **targetSessionID**

   Restituisce l&#39;ID SessionID.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      + (nullable NSString *) targetPcID;
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      NSString *myTargetSessionID = [ADBMobile targetSessionID];
      ```

### Esempio

```objective-c
// make your request 
ADBTargetLocationRequest *myRequest =  
 [ADBMobile targetCreateRequestWithName:@"heroBanner"  
                         defaultContent:@"default.png"  
                          parameters:nil]; 
// load your request 
[ADBMobile targetLoadRequest:myRequest  
                    callback:^(NSString *content) { 
                        // do something with content 
                        heroImage.image = [UIImage imageNamed:content];
                    }];
```
