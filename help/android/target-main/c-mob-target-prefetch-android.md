---
description: La funzione di preacquisizione di Adobe Target utilizza gli SDK per dispositivi mobili Android per recuperare il contenuto delle offerte il minor numero di volte possibile, memorizzando nella cache le risposte dal server.
title: Preacquisizione del contenuto delle offerte in Android
uuid: 063451b8-e191-4d58-8ed8-1723e310ad1a
exl-id: 60fd9703-972b-4c2c-bf9c-86e1f59bfba5
source-git-commit: 5d44c09a18a557e934628533c4eefaa9e26aba42
workflow-type: tm+mt
source-wordcount: '738'
ht-degree: 92%

---

# Preacquisizione del contenuto delle offerte in Android {#prefetch-offer-content-in-android}

La funzione di preacquisizione di Adobe Target utilizza gli SDK per dispositivi mobili Android per recuperare il contenuto delle offerte il minor numero di volte possibile, memorizzando nella cache le risposte dal server.

Questo processo riduce il tempo di caricamento, evita l’esecuzione di più chiamate di rete e consente ad Adobe Target di notificare quale elemento mbox è stato visitato dall’utente dell’app mobile. Tutto il contenuto verrà recuperato e memorizzato nella cache durante la chiamata di preacquisizione, e lo stesso verrà recuperato dalla cache per tutte le chiamate future che contengono contenuto nella cache per il nome mbox specificato.

Il contenuto di preacquisizione non rimane tra un avvio dell’app e quello successivo. Viene memorizzato nella cache per tutto il tempo in cui l’app rimane attiva oppure fino alla chiamata del metodo `clearPrefetchCache()`.

>[!IMPORTANT]
>
>Le API di pre-acquisizione di Target sono disponibili a partire dalla versione 4.14.0 dell&#39;SDK. Per maggiori informazioni sulle limitazioni relative ai parametri, vedi [Parametri di input batch](https://developers.adobetarget.com/api/#batch-input-parameters).

Nella versione 4.14 o successiva dell’SDK, se specificato, `environmentId` viene preso dal file `ADBMobileConfig.json` quando si avvia una chiamata TnT batch mbox v2. Se nel file non è specificato alcun `environmentId`, no viene inviato alcun parametro di ambiente in una chiamata TnT batch mbox, e l’offerta viene distribuita per l’ambiente predefinito.

Ad esempio:

```java
if (MobileConfig.getInstance().mobileUsingTarget()){ 
            long environmentID = MobileConfig.getInstance().getEnvironmentID(); 
            if(environmentID != 0L){ 
                parametersJson.put(TargetJson.ENVIRONMENT_ID, environmentID); 
            } 
        }
```

## Metodi di preacquisizione {#section_05967F1F3A554B0FBC2C08A954554BDE}

Di seguito sono elencati i metodi utilizzabili per la preacquisizione in Android:

* **prefetchContent**

   Invia una richiesta di preacquisizione con un array di posizioni al server di Target configurato e restituisce lo stato della richiesta nel callback specificato.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void prefetchContent(
      final List<TargetPrefetchObject> targetPrefetchArray,
      final Map<String, Object> profileParameters,
      final TargetCallback<Boolean> callback)
      ```

   * I parametri di questo metodo sono i seguenti:

      * **targetPrefetchArray**

         Array di `TargetPrefetchObjects` che contiene il nome e i mboxParameters per ogni posizione Target da preacquisire.

      * **profileParameters**

         Contiene le chiavi e i valori dei parametri di profilo da utilizzare per ogni preacquisizione di posizione di questa richiesta.

      * **callback**

         Viene richiamato quando la preacquisizione è completa. Restituisce `true` se la preacquisizione è avvenuta correttamente oppure `false` in caso contrario.

* **loadRequests**

   Esegue una richiesta batch per più posizioni mbox specificate nell&#39;array requests.  Ogni oggetto dell&#39;array contiene una funzione di callback che viene richiamata quando il contenuto è disponibile per la posizione mbox corrispondente.

   >[!IMPORTANT]
   >
   >Se il contenuto delle posizioni richieste è già presente nella cache, viene restituito immediatamente nel callback specificato. In caso contrario, l&#39;SDK invia una richiesta di rete ai server Target per recuperare il contenuto.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void loadRequests( final List<TargetRequestObject> requestArray,  final Map<String, Object> profileParameters)
      ```

   * I parametri di questo metodo sono i seguenti:

      * **requestArray**

         Array di `TargetRequestObjects` che contiene il nome, il contenuto predefinito e la funzione di callback di ogni posizione da recuperare.

      * **profileParameters**

         Contiene le chiavi e i valori dei parametri di profilo da utilizzare per ogni preacquisizione di posizione di questa richiesta.

* **clearPrefetchCache**

   Cancella i dati memorizzati nella cache da Target Prefetch.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static void clearPrefetchCache();
      ```

   * Nessun parametro per questo metodo.

* **createTargetRequestObject**

   Crea e restituisce un&#39;istanza di `TargetRequestObject` con i dati specificati.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static TargetPrefetchObject createTargetRequestObject( 
      final String mboxName,
      final String defaultContent, 
      final Map<String, Object> mboxParams, 
      final Map<String, Object> orderParams, 
      final Map<String, Object> productParams, 
      final Target.TargetCallback<String> callback)
      ```

* **createTargetPrefetchObject**

   Crea e restituisce un&#39;istanza di TargetPrefetchObject con i dati specificati.

   * Di seguito è riportata la sintassi per questo metodo:

      ```java
      public static TargetPrefetchObject createTargetPrefetchObject( 
      final String mboxName, 
      final Map<String, Object> mboxParams) 
      final Map<String, Object> orderParams, 
      final Map<String, Object> productParams)
      ```

## Classi pubbliche {#section_A273E53F069E4327BBC8CE4910B37888}

Di seguito sono elencate le classi pubbliche che supportano la preacquisizione in Android:

### Riferimento della classe: TargetPrefetchObject

Racchiude il nome mbox e tutti i parametri utilizzati per la preacquisizione mbox.

* **`name`**

   Nome della posizione che sarà preacquisita.
   * **Tipo**: String

* `mboxParameters`

   Raccolta di coppie chiave-valore che verranno aggiunte come `mboxParameters` a questa richiesta `TargetPrefetchObject`.
   * **Tipo**: mappa`<String, Object>`

* **`orderParameters`**

   Raccolta di coppie chiave-valore che verranno aggiunte alla mbox corrente sotto il nodo order.
   * **Tipo**: mappa `<String, Object>`

* **`productParameters`**

   Raccolta di coppie chiave-valore che verranno aggiunte alla mbox corrente sotto il nodo product.

   * **Tipo**: mappa `<String, Object>`


### Riferimento classe: TargetRequestObject

Questa classe racchiude il nome mbox, il contenuto predefinito, i parametri mbox e il callback di ritorno utilizzati per le richieste di posizioni Target.

* **`mboxName`**

   Nome della posizione richiesta.

   * **Tipo**: String

* **`mboxParameters`**

   Raccolta di coppie chiave-valore che verranno aggiunte come `mboxParameters` a questa richiesta  `TargetRequestObject`.

   * **Tipo: mappa`<String, Object>`**

* **`orderParameters`**

   Raccolta di coppie chiave-valore che verranno aggiunte alla mbox corrente sotto il nodo order.

   * **Tipo**: mappa `<String, Object>`

* **`productParameters`**

   Raccolta di coppie chiave-valore che verranno aggiunte alla mbox corrente sotto il nodo product.

   * **Tipo**: mappa `<String, Object>`

* **`defaultContent`**

   Valore stringa che viene restituito nel callback se l&#39;SDK non è in grado di recuperare il contenuto dai server Target.

   * **Tipo**: String

* **`callback`**

   Puntatore di funzione che viene chiamato quando è disponibile il contenuto per la richiesta `TargetRequestObject` specificata.

   * **Tipo**: Target.TargetCallback`<String>`


## Esempio di codice {#section_BF7F49763D254371B4656E17953D520C}

Di seguito è riportato un esempio di preacquisizione del contenuto mediante gli SDK per Android:

```java
// When your app launches, prefetch the content for a list of locations. 
// Define the list of mboxes that you want to prefetch. 
List<TargetPrefetchObject> prefetchMboxesList = new ArrayList<>(); 
  
Map<String, Object> mboxParameters1 = new HashMap<>(); 
mboxParameters1.put("status", "platinum"); 
prefetchMboxesList.add(Target.createTargetPrefetchObject("mboxName1", mboxParameters1));

Map<String, Object> mboxParameters2 = new HashMap<>(); 
mboxParameters2.put("userType", "paid"); 
 
List<String> purchasedIds = new ArrayList<String>(); 
purchasedIds.add("34"); 
purchasedIds.add("125");  
Map<String, Object> orderParameters2 = new HashMap<>(); 
orderParameters2.put("id", "ADCKKIM"); 
orderParameters2.put("total", "344.30"); 
orderParameters2.put("purchasedProductIds",  purchasedIds); 
  
Map<String, Object> productParameters2 = new HashMap<>(); 
productParameters2.put("id", "24D3412"); 
productParameters2.put("categoryId","Books"); 
  
prefetchMboxesList.add(Target.createTargetPrefetchObject("mboxName2", mboxParameters2, orderParameters2, productParameters2));

// Define the profile parameters map. 
Map<String, Object> profileParameters = new HashMap<>(); 
profileParameters.put("ageGroup", "20-32");

// Define the target callback for the prefetch call status. 
Target.TargetCallback<Boolean> prefetchStatusCallback = new Target.TargetCallback<Boolean>() { 
    @Override 
    public void call(final Boolean status) { 
        // check the returned status for the prefetch call 
    }};

// Call the prefetchContent API. 
Target.prefetchContent(prefetchMboxesList, profileParameters, prefetchStatusCallback);

// When the content is required, you can initiate the locations request. 
// Define the list of target request objects. 
List<TargetRequestObject> locationRequests = new ArrayList<>(); 
  
Target.TargetCallback<String> callback1 = new Target.TargetCallback<String>() { 
    @Override 
    public void call(final String content) { 
        // check the returned content for mboxName1. 
    }}; 
  
locationRequests.add(Target.createTargetRequestObject("mboxName1", "defaultContent1", mboxParameters1, callback1));

Target.TargetCallback<String> callback2 = new Target.TargetCallback<String>() { 
    @Override 
    public void call(final String content) { 
        // check the returned content for mboxName2. 
    }}; 
  
locationRequests.add(Target.createTargetRequestObject("mboxName2", "defaultContent2", mboxParameters2, orderParameters2, productParameters2, callback2)); 
  
// Call the loadRequests API. 
Target.loadRequests(locationRequests, profileParameters); 
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

* `purchasedProducts` accetta un ArrayList di stringhe.
