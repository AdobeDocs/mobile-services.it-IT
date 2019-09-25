---
description: La funzione di preacquisizione di Adobe Target utilizza gli SDK per dispositivi mobili iOS per recuperare il contenuto delle offerte il minor numero di volte possibile, memorizzando nella cache le risposte dal server.
seo-description: La funzione di preacquisizione di Adobe Target utilizza gli SDK per dispositivi mobili iOS per recuperare il contenuto delle offerte il minor numero di volte possibile, memorizzando nella cache le risposte dal server.
seo-title: Preacquisizione del contenuto delle offerte in iOS
title: Preacquisizione del contenuto delle offerte in iOS
uuid: fef58042-65e2-4579-b8f1-d21554d2af57
translation-type: tm+mt
source-git-commit: fa7375ac8a1345d81748bcf635791c46d3943fed

---


# Preacquisizione del contenuto delle offerte in iOS {#prefetch-offer-content-in-ios}

La funzione di preacquisizione di Adobe Target utilizza gli SDK per dispositivi mobili iOS per recuperare il contenuto delle offerte il minor numero di volte possibile, memorizzando nella cache le risposte dal server.

>[!IMPORTANT]
>
>La funzionalità di recupero preventivo negli SDK Mobile per iOS non è supportata per i tipi di attività di destinazione automatica, allocazione automatica e Automated Personalization (Personalizzazione automatica) in Adobe Target.

Questo processo consente di ridurre il tempo di caricamento, evita l'esecuzione di più chiamate di rete e permette di notificare ad Adobe Target quale elemento mbox è stato visitato dall'utente dell'app mobile. Tutto il contenuto viene recuperato e memorizzato nella cache durante la chiamata di preacquisizione, e da qual momento viene richiamato dalla cache per tutte le chiamate future che includono quel contenuto per il nome di mbox specificato.

Il contenuto di preacquisizione non rimane tra un avvio dell'app e quello successivo. The prefetch content is cached as long as the application lives or until the `clearPrefetchCache()` method is called.

>[!IMPORTANT]
>
>Target prefetch APIs have been available since SDK version 4.14.0. For more information about parameter limitations, see [Batch Input Parameters](https://developers.adobetarget.com/api/#batch-input-parameters).

Nella versione 4.14 o successiva dell’SDK, se specificato, `environmentId``ADBMobileConfig.json` viene preso dal file quando si avvia una chiamata TnT batch mbox v2. Se nel file non è specificato alcun `environmentId`, no viene inviato alcun parametro di ambiente in una chiamata TnT batch mbox, e l’offerta viene distribuita per l’ambiente predefinito.

Ad esempio:

```
if (MobileConfig.getInstance().mobileUsingTarget()){ 
            long environmentID = MobileConfig.getInstance().getEnvironmentID(); 
            if(environmentID != 0L){ 
                parametersJson.put(TargetJson.ENVIRONMENT_ID, environmentID); 
            } 
        }
```

## Metodi di preacquisizione {#section_05967F1F3A554B0FBC2C08A954554BDE}

Di seguito sono indicati i metodi che puoi utilizzare per la preacquisizione in iOS:

* **targetPrefetchContent**

   Invia una richiesta di preacquisizione con un array di posizioni al server di Target configurato e restituisce lo stato della richiesta nel callback specificato.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      (void) targetPrefetchContent:(nonnull NSArray*)targetPrefetchObjectArray 
                     withProfileParameters:(nullable NSDictionary*)profileParameters 
                            callback:(nullable void(^)(BOOL success))callback;
      ```

   * I parametri di questo metodo sono i seguenti:

      * **`targetPrefetchArray`**

         Array di `TargetPrefetchObjects` che contiene il nome e i mboxParameters per ogni posizione Target da preacquisire.

      * **`profileParameters`**

         Contiene le chiavi e i valori dei parametri di profilo da utilizzare per ogni preacquisizione di posizione di questa richiesta.

      * **`callback`**

         Viene richiamato quando la preacquisizione è completa. Returns `true` if the prefetch was successful and `false` if the prefetch was unsuccesful.

* **targetLoadRequests**

   Esegue una richiesta batch per più posizioni mbox specificate nell'array requests. Ogni oggetto dell'array contiene una funzione di callback che viene richiamata quando il contenuto è disponibile per la posizione mbox corrispondente.

   >[!IMPORTANT]
   >
   >Se il contenuto delle posizioni richieste è già presente nella cache, verrà restituito immediatamente nel callback fornito. In caso contrario, l'SDK invia una richiesta di rete ai server Target per recuperare il contenuto.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      (void)targetLoadRequests:(nonnullNSArray*)requests 
               withProfileParameters:(nullableNSDictionary*)profileParameters;
      ```

   * I parametri di questo metodo sono i seguenti:

      * **`requests`**

         Array di `TargetRequestObjects` che contiene il nome, il contenuto predefinito e la funzione di callback di ogni posizione da recuperare.

      * **`profileParameters`**

         Contiene le chiavi e i valori dei parametri di profilo da utilizzare per ogni preacquisizione di posizione di questa richiesta.

* **targetPrefetchClearCache**

   Cancella i dati memorizzati nella cache da Target Prefetch.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      (void) targetPrefetchClearCache; 
      ```

   * Nessun parametro per questo metodo.

* **targetRequestObjectWithName**

   Crea e restituisce un'istanza di `TargetRequestObject` con i dati specificati.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      +(nullableADBTargetRequestObject*)targetRequestObjectWithName:(nonnullNSString*)name
      defaultContent:(nonnullNSString*)defaultContent
      mboxParameters:(nullableNSDictionary*)mboxParameters
      callback:(nullablevoid(^)(NSString*__nullablecontent))callback;
      ```

   * Nessun parametro per questo metodo.

* **createTargetPrefetchObject**

   Crea e restituisce un'istanza di `TargetPrefetchObject` con i dati specificati.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      +(nullable ADBTargetPrefetchObject *) targetPrefetchObjectWithName:(nonnullNSString *)name
      mboxParameters:(nullableNSDictionary *)mboxParameters;
      ```

## Public classes {#section_A273E53F069E4327BBC8CE4910B37888}

Di seguito sono indicate le classi pubbliche che supportano la preacquisizione in iOS:

### Riferimento classe: TargetPreFetchObject

Racchiude il nome mbox e tutti i parametri utilizzati per la preacquisizione mbox.

* **`name`**

   Nome della posizione/mbox da recuperare.

   * **Tipo**: NSString*

* **`mboxParameters`**

   Un dizionario opzionale che contiene le coppie chiave-valore dei parametri Mbox.

   * **Tipo**: NSDictionary*

* **`orderParameters`**

   Dizionario che contiene le coppie chiave-valore dei parametri dell'ordine.

   * **Tipo**: NSDictionary*

* **`productParameters`**

   Dizionario che contiene le coppie chiave-valore dei parametri del prodotto.

   * **Tipo**: NSDictionary*

### Riferimento classe: TargetRequestObject

Questa classe racchiude il nome mbox, il contenuto predefinito, i parametri mbox e il callback di ritorno utilizzati per le richieste di posizioni Target.

* **`name`**

   Nome della posizione richiesta.

   * **Tipo**: NSString*

* **`mboxParameters`**

   Il valore NSString rappresenta il nome per la posizione/Mbox da recuperare.

   * **Tipo**: NSString*

* **`defaultContent`**

   Contenuto predefinito che sarà restituito se i server Target sono irraggiungibili.

   * **Tipo**: NSString*

* **`callback`**

   Quando la batch richiede le posizioni Target, la callback sarà invocata quando il contenuto è disponibile per questa posizione.

   * **Tipo**: Funzione

## Code sample {#section_BF7F49763D254371B4656E17953D520C}

Di seguito è presente un esempio di come eseguire la preacquisizione del contenuto utilizzando gli SDK iOS:

```objective-c
/** 
 * Prefetch Content 
 */ 
  
    NSDictionary *mboxParameters1 = @{@"status":@"platinum"}; 
    NSDictionary *productParameters1 = @{@"id":@"24D3412", 
                                        @"categoryId":@"Books"}; 
    NSDictionary *orderParameters1 = @{@"id":@"ADCKKIM", 
                                      @"total":@"344.30", 
                                      @"purchasedProductIds":@"34, 125, 99"};

    NSDictionary *mboxParameters2 = @{@"userType":@"Paid"}; 
    NSDictionary *productParameters2 = @{@"id":@"764334", 
                                         @"categoryId":@"Online"}; 
  
    NSArray *purchaseIDs = @[@"id1",@"id2"]; 
    NSDictionary *orderParameters2 = @{@"id":@"4t4uxksa", 
                                       @"total":@"54.90", 
                                       @"purchasedProductIds":purchaseIDs};

    // Creating Prefetch Objects 
    ADBTargetPrefetchObject *prefetch1 = [ADBMobile targetPrefetchObjectWithName:@"logo" mboxParameters:mboxParameters1]; 
    prefetch1.productParameters = productParameters1; 
    prefetch1.orderParameters = orderParameters1; 
  
    ADBTargetPrefetchObject *prefetch2 = [ADBMobile targetPrefetchObjectWithName:@"buttonColor" mboxParameters:mboxParameters2]; 
    prefetch2.productParameters = productParameters2; 
    prefetch2.orderParameters = orderParameters2; 

    // Creating prefetch Array 
    NSArray *prefetchArray = @[prefetch1,prefetch2]; 
  
    // Creating Profile parameters 
    NSDictionary *profileParmeters = @{@"age":@"20-32"};

    // Target API Call 
    [ADBMobile targetPrefetchContent:prefetchArray withProfileParameters:profileParmeters callback:^(BOOL isSuccess){ 
       // do something with the Boolean result 
    }];
```

Di seguito è presente un esempio della batch `loadRequest` utilizzando gli SDK iOS:

```objective-c
/** 
 * Batch loadRequest  
 */ 
  
   NSDictionary *mboxParameters1 = @{@"status":@"platinum"}; 
   NSDictionary *productParameters1 = @{@"id":@"24D3412", 
                                        @"categoryId":@"Books"}; 
   NSDictionary *orderParameters1 = @{@"id":@"ADCKKIM", 
                                      @"total":@"344.30", 
                                      @"purchasedProductIds":@"34, 125, 99"};

    NSDictionary *mboxParameters2 = @{@"userType":@"Paid"}; 
    NSDictionary *productParameters2 = @{@"id":@"764334", 
                                         @"categoryId":@"Online"}; 
    NSArray *purchaseIDs = @[@"id1",@"id2"]; 
    NSDictionary *orderParameters2 = @{@"id":@"4t4uxksa", 
                                       @"total":@"54.90", 
                                       @"purchasedProductIds":purchaseIDs};

    ADBTargetRequestObject *request1 = [ADBMobile targetRequestObjectWithName:@"logo" defaultContent:@"BlueWhale" mboxParameters:mboxParameters1 callback:^(NSString *content){ 
        // do something with the received content 
    }]; 
  
    request1.productParameters = productParameters1; 
    request1.orderParameters = orderParameters1;

    ADBTargetRequestObject *request2 = [ADBMobile targetRequestObjectWithName:@"buttonColor" defaultContent:@"red" mboxParameters:mboxParameters2 callback:^(NSString *content){ 
        // do something with the received content 
    }]; 
    request2.productParameters = productParameters1; 
    request2.orderParameters = orderParameters1;

    // create request object array 
    NSArray *requestArray = @[request1,request2]; 
  
    // Call the API 
    [ADBMobile targetLoadRequests:requestArray withProfileParameters:profileParmeters];
```

## Informazioni aggiuntive {#section_A454BAD1CD49423E86C71BAEE06125FD}

Seguono alcune informazioni aggiuntive su questi esempi:

* `ProductParameters` ammette solo le chiavi seguenti:

   * `id`
   * `categoryId`

* `OrderParameters` ammette solo le chiavi seguenti:

   * `id`
   * `total`
   * `purchasedProductIds`

* `purchasedProducts` accetta un array di stringhe.