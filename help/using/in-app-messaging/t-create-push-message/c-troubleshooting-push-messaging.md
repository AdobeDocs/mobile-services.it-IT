---
description: Queste informazioni possono essere utili per risolvere eventuali problemi dei messaggi push.
keywords: mobile
seo-description: Queste informazioni possono essere utili per risolvere eventuali problemi dei messaggi push.
seo-title: Risoluzione dei problemi dei messaggi push
solution: Experience Cloud,Analytics
title: Risoluzione dei problemi dei messaggi push
topic: Metrics
uuid: c7be4ab7-0cfe-4296-84a8-01412f4fd93f
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '735'
ht-degree: 100%

---


# Risoluzione dei problemi dei messaggi push {#troubleshooting-push-messaging}

Queste informazioni possono essere utili per risolvere eventuali problemi dei messaggi push.

## Perché a volte si verificano dei ritardi nell’invio dei messaggi push?

I seguenti tipi di ritardo possono essere associati ai messaggi push per Mobile Services:

* **Attesa degli hit di Analytics**

   Per ogni suite di rapporti, un’impostazione consente di determinare quando elaborare gli hit di Analytics in arrivo. L’impostazione predefinita è ogni ora.

   L’effettiva elaborazione degli hit di Analytics potrebbe richiedere fino a 30 minuti, ma in genere dura 15-20 minuti. Ad esempio, una suite di rapporti elabora gli hit ogni ora. Considerando il tempo massimo di elaborazione richiesto (30 minuti), potrebbero essere necessari fino a 90 minuti perché un hit in arrivo sia disponibile per un messaggio push. Se un utente ha avviato l’app alle 09:01, l’hit risulterebbe nell’interfaccia di Mobile Services come nuovo utente unico tra le 10:15 e le 10:30.

* **Attesa del servizio push**

   Il servizio push (APNS o GCM) potrebbe non inviare subito il messaggio. Anche se raramente, sono stati registrati casi con tempi di attesa di 5-10 minuti. Puoi controllare se il messaggio push è stato inviato al servizio push guardando la vista **[!UICONTROL Rapporto]** del messaggio push, individuando il messaggio nella tabella **[!UICONTROL Cronologia messaggio]** e visualizzando il dato **[!UICONTROL Pubblicato]**.

   >[!TIP]
   >
   >Questo dato corrisponde al numero di invii ai servizi push con esito positivo. I servizi push non garantiscono al 100% l’effettivo invio di un messaggio.

   Per maggiori informazioni sull’affidabilità del servizio, vedi:

   * [Qualità del servizio](https://developer.apple.com/library/content/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/APNSOverview.html#//apple_ref/doc/uid/TP40008194-CH8-SW5l)
   * [Ciclo di vita del messaggio](https://developers.google.com/cloud-messaging/concept-options#lifetime).

## Perché la mia chiave API GCM Android non è valida?

* **Chiave API non valida**

   La chiave API potrebbe non essere valida per i motivi seguenti:

   * La chiave API che hai fornito non è una chiave server con il valore chiave API GCM corretto.
   * La chiave server ha dato il consenso agli IP e sta impedendo l’invio di un messaggio push da parte dei server Adobe.

* **Determinare la validità di una chiave API**

   Per determinare la validità di una chiave API, esegui il comando seguente:

   **Android**

   ```java
   # api_key=YOUR_API_KEY
   #curl--header"Authorization:key=$api_key"\
       --headerContent-Type:"application/json"\ 
       https://gcm-http.googleapis.com/gcm/send\
       -d"{\"registration_ids\":[\"ABC\"]}"
   ```

   Se viene restituito un codice di stato HTTP 401 la chiave API non è valida. Altrimenti, il risultato visualizzato sarà simile al seguente:

   ```java
   {"multicast_id":6782339717028231855,"success":0,"failure":1,
   canonical_ids":0,"results":[{"error":"InvalidRegistration"}]}
   ```

   Per controllare la validità di un token di registrazione, sostituisci `"ABC"` con il token.

## Perché il mio certificato APNS non funziona?

Il certificato APNS potrebbe non essere valido per i motivi seguenti:

* Stai utilizzando un certificato sandbox invece del certificato di produzione.
* Stai utilizzando un nuovo certificato di produzione/sandbox non supportato.
* Stai usando un file `.p8` invece di un file `.p12`.

## Risoluzione degli errori dei messaggi push

**Un esempio**

L’esempio seguente illustra come risolvere un errore push quando usi una VRS.

Il cliente seguente ha due app iOS:

* Nome app: PhotoShop_app_iOS
   * RSID principale: AllAdobe PhotoShop_apps
   * VRSID: PhotoShop_iOS_app_SF
   * Segmento di definizione VRSID: `a.appid contains “PhotoShop_iOS_app_SF”`
* Nome app: PhotoShop_app_iOS
   * RSID principale: AllAdobe PhotoShop_apps
   * RSID: PhotoShop_iOS_app_LA
   * Segmento di definizione VRSID: `a.os contains “iOS”`

In questo esempio, se un dipendente Photoshop invia un messaggio push all’app *PhotoShop_iOS_app_SF*, tutti gli utenti dell’app *PhotoShop_iOS_app_SF* riceveranno normalmente il messaggio push. Tuttavia, se il dipendente invia un messaggio all’app *PhotoShop_iOS_app_LA*, poiché il relativo Segmento di definizione VRSID non è corretto (`iOS` anziché`a.os contains "PhotoShop_iOS_app_LA"`), il messaggio viene inviato a **tutti** gli utenti iOS in *AllAdobe PhotoShop_apps*. Nonostante venga inviato agli utenti di *PhotoShop_iOS_app_LA*, questo messaggio inserisce nella blocklist gli ID push per gli utenti di *PhotoShop_iOS_app_SF* poiché l’app *PhotoShop_iOS_app_SF* dispone di un certificato diverso. Se il segmento fosse stato definito come `a.os contains “PhotoShop_iOS_app_LA”`, il messaggio push sarebbe stato inviato solo agli utenti *PhotoShop_iOS_app_LA*.

Se passati con il certificato push *PhotoShop_IOS_app_LA*, gli identificatori push di *PhotoShop_iOS_app_SF* verrebbero restituiti come `invalid`.

>[!CAUTION]
>
>Quando crei un messaggio push per un’app che utilizza una VRS e fai clic su **[!UICONTROL Salva e invia]**, viene visualizzato un avviso che ti ricorda di verificare che ogni app indicata **deve** avere un certificato valido. Se ogni app **non** dispone di un certificato valido, i segmenti di pubblico potrebbero essere inseriti nella blocklist a tempo indefinito e in futuro non sarebbe possibile inviare messaggi push agli utenti in questione. Per ulteriori informazioni sui segmenti di pubblico, vedi [Pubblico: definire e configurare le opzioni relative al pubblico per i messaggi push](/help/using/in-app-messaging/t-create-push-message/c-audience-push-message.md).
