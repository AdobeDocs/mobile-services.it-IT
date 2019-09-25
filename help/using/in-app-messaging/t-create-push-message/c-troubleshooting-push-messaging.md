---
description: Queste informazioni possono essere utili per risolvere eventuali problemi dei messaggi push.
keywords: dispositivi mobili
seo-description: Queste informazioni possono essere utili per risolvere eventuali problemi dei messaggi push.
seo-title: Risoluzione dei problemi dei messaggi push
solution: Marketing Cloud,Analytics
title: Risoluzione dei problemi dei messaggi push
topic: Metrics (Metriche)
uuid: c7be4ab7-0cfe-4296-84a8-01412f4fd93f
translation-type: tm+mt
source-git-commit: e9691f9cbeadd171948aa752b27a014c3ab254d6

---


# Troubleshooting push messaging{#troubleshooting-push-messaging}

Queste informazioni possono essere utili per risolvere eventuali problemi dei messaggi push.

## Perché a volte si verificano dei ritardi nell'invio dei messaggi push?

I seguenti tipi di ritardo possono essere associati ai messaggi push per Mobile Services:

* **Attesa degli hit di Analytics**

   Per ogni suite di rapporti, un'impostazione consente di determinare quando elaborare gli hit di Analytics in arrivo. L'impostazione predefinita è ogni ora.

   L'effettiva elaborazione degli hit di Analytics potrebbe richiedere fino a 30 minuti, ma in genere dura 15-20 minuti. Prendiamo ad esempio una suite di rapporti che elabora gli hit ogni ora. Considerando il tempo di elaborazione massimo di 30 minuti, prima che un hit in arrivo diventi disponibile per un messaggio push potrebbero quindi trascorrere 90 minuti. Se un utente ha avviato l'app alle 09:01, l'hit risulterebbe nell'interfaccia di Mobile Services come nuovo utente unico tra le 10:15 e le 10:30.

* **Attesa del servizio push**

   Il servizio push (APNS o GCM) potrebbe non essere in grado di inviare il messaggio immediatamente. Anche se raramente, sono stati registrati casi con tempi di attesa di 5-10 minuti. Puoi controllare se il messaggio push è stato inviato al servizio push guardando la vista **[!UICONTROL Rapporto]** del messaggio push, individuando il messaggio nella tabella **[!UICONTROL Cronologia messaggio]e visualizzando il dato** Pubblicato **.**

   >[!TIP]
   >
   >Questo numero corrisponde al numero di invii con esito positivo ai servizi push. I servizi push non garantiscono al 100% l'effettivo invio di un messaggio.

   Per maggiori informazioni sull'affidabilità del servizio, vedi:

   * [Qualità del servizio](https://developer.apple.com/library/content/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/APNSOverview.html#//apple_ref/doc/uid/TP40008194-CH8-SW5l)
   * [Durata di un messaggio](https://developers.google.com/cloud-messaging/concept-options#lifetime).

## Perché la mia chiave API GCM Android non è valida?

* **Chiave API non valida**

   La chiave API potrebbe risultare non valida per i motivi seguenti:

   * La chiave API che hai fornito non è una chiave server con il valore chiave API GCM corretto.
   * La chiave server ha inserito gli IP in una whitelist e sta impedendo ai server Adobe di inviare un messaggio push.

* **Stabilire la validità di una chiave API**

   Per determinare la validità della chiave API, esegui il comando seguente:

   **Android**

   ```java
   # api_key=YOUR_API_KEY
   #curl--header"Authorization:key=$api_key"\
       --headerContent-Type:"application/json"\ 
       https://gcm-http.googleapis.com/gcm/send\
       -d"{\"registration_ids\":[\"ABC\"]}"
   ```

   Se viene restituito un codice di stato HTTP 401, significa che la chiave API non è valida. Altrimenti, il risultato visualizzato sarà simile al seguente:

   ```java
   {"multicast_id":6782339717028231855,"success":0,"failure":1,
   canonical_ids":0,"results":[{"error":"InvalidRegistration"}]}
   ```

   You can also check the validity of a registration token by replacing `"ABC"` with the token.

## Perché il mio certificato APNS non funziona?

Il certificato APNS potrebbe risultare non valido per i motivi seguenti:

* È possibile che tu stia utilizzando un certificato sandbox invece del certificato di produzione.
* Stai usando un nuovo certificato di produzione/sandbox che non è supportato.
* You are using `.p8` file instead of a `.p12` file.

## Risoluzione degli errori dei messaggi push

**Un esempio**

L'esempio seguente illustra come risolvere un errore push quando usi una VRS.

Il cliente seguente ha due app iOS:

* Nome app: PhotoShop_app_iOS
   * RSID principale: AllAdobe PhotoShop_apps
   * VRSID: PhotoShop_iOS_app_SF
   * VRSID Definition Segment: `a.appid contains “PhotoShop_iOS_app_SF”`
* Nome app: PhotoShop_app_iOS
   * RSID principale: AllAdobe PhotoShop_apps
   * RSID: PhotoShop_iOS_app_LA
   * VRSID Definition Segment: `a.os contains “iOS”`

In this example, if a Photoshop employee sends a push to the *PhotoShop_iOS_app_SF* app, all *PhotoShop_iOS_app_SF app* users receive the push message as expected. But, if the employee sends a message to the *PhotoShop_iOS_app_LA* app, because its VRSID Definition Segment is incorrect (`iOS` instead of `a.os contains "PhotoShop_iOS_app_LA"`), the message is sent to **all** iOS users in *AllAdobe PhotoShop_apps*. Although the message still goes to *PhotoShop_iOS_app_LA* users, the message also blacklists the push IDs for *PhotoShop_iOS_app_SF* users because the *PhotoShop_iOS_app_SF* app has a different certificate. If the segment had been defined as `a.os contains “PhotoShop_iOS_app_LA”`, the push message would have been sent to only *PhotoShop_iOS_app_LA* users.

If passed with the *PhotoShop_IOS_app_LA* push certificate, the push identifiers for the *PhotoShop_iOS_app_SF* come back as `invalid`.

>[!CAUTION]
>
>After you create a push message for an app that is using a VRS and click **[!UICONTROL Save &amp; Send]**, an alert appears that reminds you ensure that each app that is listed **must** have a valid certificate. Se un'app **non** dispone di un certificato valido, i tuoi segmenti di pubblico potrebbero essere inseriti in blacklist a tempo indefinito e di conseguenza non saresti in grado di inviare messaggi push agli utenti interessati. Per ulteriori informazioni sui segmenti di pubblico, vedi [Pubblico: definire e configurare le opzioni relative al pubblico per i messaggi](/help/using/in-app-messaging/t-create-push-message/c-audience-push-message.md)push.
