---
description: Elenco dei metodi di Audience Manager forniti dalla libreria iOS.
seo-description: Elenco dei metodi di Audience Manager forniti dalla libreria iOS.
seo-title: Metodi di Audience Manager
solution: Experience Cloud,Analytics
title: Metodi di Audience Manager
topic: Developer and implementation
uuid: 97658bd6-4c4f-4875-abe9-36dad4ec8bae
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 80%

---


# Metodi di Audience Manager {#audience-manager-methods}

Elenco dei metodi di Audience Manager forniti dalla libreria iOS.

L&#39;SDK supporta attualmente più soluzioni Adobe Experience Cloud, tra cui Analytics, Target, Audience Manager e il servizio Adobe Experience Platform Identity. I metodi iniziano con un prefisso a seconda della soluzione; i metodi di Audience Manager hanno il prefisso &quot;`audience`&quot;.

Se Audience Manager è configurato nel file JSON, viene inviato un segnale contenente le metriche sul ciclo di vita con `application:didFinishLaunchingWithOptions:`.

* **audienceVisitorProfile**

   Restituisce il profilo del visitatore ottenuto più di recente e, se non è stato inviato un segnale, restituisce `null`. Il profilo del visitatore viene salvato in `NSUserDefaults` in modo da essere facilmente accessibile per diversi avvii dell&#39;applicazione.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      + (NSDictionary *) audienceVisitorProfile;
      ```

   * Di seguito è riportato un esempio di codice per questo menu:

      ```objective-c
      NSDictionary *profile = [ADBMobile audienceVisitorProfile]; 
      ```

* **audienceDpid**

   Restituisce il DPID corrente.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      +(NSString *) audience Dpid;
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      NSString *currentDpid = [ADBMobileaudience Dpid]; 
      ```

* **audienceDpuuid**

   Restituisce il DPUUID corrente.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      +(NSString *) audienceDpuuid;
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      NSString *currentDpuuid = [ADBMobileaudience Dpuuid]; 
      ```

* **audienceSetDpid:&#x200B;dpuuid:**

   Imposta gli identificatori DPID e DPUUID. Una volta impostati, entrambi saranno aggiunti a ciascun segnale.

   * L&#39;ID provider di **dati (DPID)** è l&#39;ID del partner di dati assegnato da  Audience Manager.
   * L&#39;ID utente univoco del fornitore di **dati (DPUUID)** è l&#39;ID univoco del fornitore di dati per l&#39;utente.

      >[!IMPORTANT]
      >
      >Prima della versione 4.13.x, DPUUID non era codificato automaticamente. A partire dalla versione 4.13.x, l’SDK prima annulla la codifica del valore passato, quindi codifica di nuovo il valore. Questo processo assicura che l’SDK non interrompa la compatibilità con le versioni precedenti.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      + (void) audienceSetDpid: (NSString*)   
                      dpiddpuuid:(NSString*)dpuuid;
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-
      [ADBMobile audienceSetDpid:@"290"
                        dpuuid:@"99301393920493"];
      ```

* **audienceReset**

   Ripristina l&#39;identificatore UUID di Audience Manager e svuota il profilo visitatore corrente.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      +(void) audienceReset;
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      [ADBMobile audienceReset]; 
      ```

* **audienceSignalWithData::&#x200B;callback:**

   Invia a gestione dell&#39;audience un segnale con le caratteristiche e riceve i segmenti corrispondenti restituiti nella funzione callback di un blocco.

   * Di seguito è riportata la sintassi per questo metodo:

      ```objective-c
      + (void) audienceSignalWithData:(NSDictionary*)data
                            callback:(void(^)(NSDictionary
      *response))callback; 
      ```

   * Di seguito è riportato un esempio di codice per questo metodo:

      ```objective-c
      [ADBMobile audienceSignalWithData:traits
                               callback:^(NSDictionary*response){
                                 //do something with returned segments
                               }];
      ```

## Esempio

```objective-c
// setup your traits dictionary 
NSDictionary *traits = @{@"trait":@"b"}; 
// submit your signal and take action on results 
[ADBMobile audienceSignalWithData:traits  
                         callback:^(NSDictionary *response) { 
                             // do something with visitor segments here 
                             if ([response[@"gender"] isEqualToString:@"male"]) { 
                             // do something with gender  
                             } 
                         }];
```
