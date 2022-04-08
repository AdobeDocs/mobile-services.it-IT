---
description: La funzione di preacquisizione di Adobe Target utilizza gli SDK per dispositivi mobili iOS per recuperare il contenuto delle offerte il minor numero di volte possibile, memorizzando nella cache le risposte dal server.
title: Preacquisizione del contenuto delle offerte in iOS
uuid: fef58042-65e2-4579-b8f1-d21554d2af57
exl-id: 64d43be7-6bd1-4657-8154-5b2c1cbbf42b
source-git-commit: 5d44c09a18a557e934628533c4eefaa9e26aba42
workflow-type: tm+mt
source-wordcount: '707'
ht-degree: 85%

---

# Preacquisizione del contenuto delle offerte in iOS {#prefetch-offer-content-in-ios}

La funzione di preacquisizione di Adobe Target utilizza gli SDK per dispositivi mobili iOS per recuperare il contenuto delle offerte il minor numero di volte possibile, memorizzando nella cache le risposte dal server.

Questo processo riduce il tempo di caricamento, evita l’esecuzione di più chiamate di rete e consente ad Adobe Target di notificare quale elemento mbox è stato visitato dall’utente dell’app mobile. Tutto il contenuto verrà recuperato e memorizzato nella cache durante la chiamata di preacquisizione, e lo stesso verrà recuperato dalla cache per tutte le chiamate future che contengono contenuto nella cache per il nome mbox specificato.

Il contenuto di preacquisizione non rimane tra un avvio dell’app e quello successivo. Viene memorizzato nella cache per tutto il tempo in cui l’app rimane attiva oppure fino alla chiamata del metodo `clearPrefetchCache()`.

>[!IMPORTANT]
>
>Le API di pre-acquisizione di Target sono disponibili a partire dalla versione 4.14.0 dell&#39;SDK. Per maggiori informazioni sulle limitazioni relative ai parametri, vedi [Parametri batch di input](https://developers.adobetarget.com/api/#batch-input-parameters).

Nella versione 4.14 o successiva dell’SDK, se specificato, `environmentId` viene preso dal file `ADBMobileConfig.json` quando si avvia una chiamata TnT batch mbox v2. Se nel file non è specificato alcun `environmentId`, no viene inviato alcun parametro di ambiente in una chiamata TnT batch mbox, e l’offerta viene distribuita per l’ambiente predefinito.

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

         Viene richiamato quando la preacquisizione è completa. Restituisce `true` se la preacquisizione è avvenuta correttamente oppure `false` in caso contrario.

* **targetLoadRequests**

   Esegue una richiesta batch per più posizioni mbox specificate nell&#39;array requests. Ogni oggetto dell&#39;array contiene una funzione di callback che viene richiamata quando il contenuto è disponibile per la posizione mbox corrispondente.

   >[!IMPORTANT]
   >
   >Se il contenuto delle posizioni richieste è già presente nella cache, viene restituito immediatamente nel callback specificato. In caso contrario, l&#39;SDK invia una richiesta di rete ai server Target per recuperare il contenuto.

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

   Crea e restituisce un&#39;istanza di `TargetRequestObject` con i dati specificati.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      +(nullableADBTargetRequestObject*)targetRequestObjectWithName:(nonnullNSString*)name
      defaultContent:(nonnullNSString*)defaultContent
      mboxParameters:(nullableNSDictionary*)mboxParameters
      callback:(nullablevoid(^)(NSString*__nullablecontent))callback;
      ```

   * Nessun parametro per questo metodo.

* **createTargetPrefetchObject**

   Crea e restituisce un&#39;istanza di `TargetPrefetchObject` con i dati specificati.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      +(nullable ADBTargetPrefetchObject *) targetPrefetchObjectWithName:(nonnullNSString *)name
      mboxParameters:(nullableNSDictionary *)mboxParameters;
      ```

## Classi pubbliche {#section_A273E53F069E4327BBC8CE4910B37888}

Di seguito sono indicate le classi pubbliche che supportano la preacquisizione in iOS:

### Riferimento della classe: TargetPreFetchObject

Racchiude il nome mbox e tutti i parametri utilizzati per la preacquisizione mbox.

* **`name`**

   Nome della posizione/mbox da recuperare.

   * **Tipo**: NSString*

* **`mboxParameters`**

   Un dizionario opzionale che contiene le coppie chiave-valore dei parametri Mbox.

   * **Tipo**: NSDictionary*

* **`orderParameters`**

   Dizionario che contiene le coppie chiave-valore dei parametri dell&#39;ordine.

   * **Tipo**: NSDictionary*

* **`productParameters`**

   Dizionario che contiene le coppie chiave-valore dei parametri di prodotto.

   * **Tipo**: NSDictionary*

### Riferimento classe: TargetRequestObject

Questa classe racchiude il nome mbox, il contenuto predefinito, i parametri mbox e il callback di ritorno utilizzati per le richieste di posizioni Target.

* **`name`**

   Nome della posizione richiesta.

   * **Tipo**: NSString*

* **`mboxParameters`**

   Il valore NSString che rappresenta il nome della posizione/mbox che si desidera recuperare.

   * **Tipo**: NSString*

* **`defaultContent`**

   Contenuto predefinito che verrà restituito se i server di Target non sono raggiungibili.

   * **Tipo**: NSString*

* **`callback`**

   Quando la batch richiede le posizioni Target, la callback sarà invocata quando il contenuto è disponibile per questa posizione.

   * **Tipo**: Funzione

## Esempio di codice {#section_BF7F49763D254371B4656E17953D520C}

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
