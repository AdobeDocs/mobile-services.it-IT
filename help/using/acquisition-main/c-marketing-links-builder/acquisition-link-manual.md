---
description: Puoi creare collegamenti di marketing per acquisire al volo nuovi utenti di app mobili configurando manualmente i parametri degli URL.
keywords: dispositivi mobili
seo-description: Puoi creare collegamenti di marketing per acquisire al volo nuovi utenti di app mobili configurando manualmente i parametri degli URL.
seo-title: Creare manualmente collegamenti di acquisizione
solution: Marketing Cloud, Analytics
title: Creare manualmente collegamenti di acquisizione
topic: Metrics (Metriche)
uuid: d 7709203-f 793-4982-adaa -9 c 3 c 914 aca 2 b
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Creare manualmente collegamenti di acquisizione {#create-acquisition-link-manually}

Puoi creare collegamenti di marketing per acquisire al volo nuovi utenti di app mobili configurando manualmente i parametri degli URL.

>[!IMPORTANT]
>
>Questa funzione richiede la versione SDK 4.6 o successiva. Per ulteriori informazioni, consulta [Prerequisiti sull'acquisizione](/help/using/acquisition-main/c-acquisition-prerequisites.md).

Il diagramma seguente illustra i componenti di un collegamento di tracciamento creato manualmente e visualizza i diversi parametri URL che devi configurare correttamente quando crei manualmente dei collegamenti di acquisizione.

![](assets/acquisition_url.png)

Questo collegamento è configurato per eseguire un reindirizzamento specifico della piattaforma a Google Play o a Apple App Store per un'app mobile. Se non è possibile determinare la destinazione, lo store predefinito è impostato su Apple App Store. Dopo che l'app è stata installata, la chiave contestuale personalizzata `my.custom.key:test` viene associata all'hit di installazione Analytics.

Per creare manualmente i collegamenti, usa il formato di URL seguente:

`http(s)://c00.adobe.com/v3/ {mobile-services-app-hash}/start? {parameters}`

>[!TIP]
>
>La versione di Android SDK che utilizzi non ha alcun impatto su questo processo.

Per iOS, assicurati di usare il protocollo corretto:

* Use **HTTP** if you are using the iOS SDKs before version 4.7.0, or if you are using iOS SDK 4.7.0 or later, and if **[!UICONTROL Use HTTPS]** is **not** selected on the Manage App Settings page.
* Use **HTTPS** if you are using iOS SDK 4.7.0 or later and **[!UICONTROL Use HTTPS]** **is** selected on the Manage App Settings page.

Se si verificano le seguenti condizioni:

* `{mobile-services-app-hash}` corrisponde all'identificatore dell'applicazione nel `acquisition:appid ` file di configurazione.

   You can locate `{mobile-services-app-has}` in the Manage App Settings page under Acquisition SDK Options in the Tracking ID field.

   ![](assets/tracking-id.png)

* `{parameters}` è un elenco di parametri di query URL standard con nomi specifici.

Segue l'elenco dei parametri:

* **`a_g_id`**

   Identificatore app in Google Play.

   * Valore di esempio: `com.adobe.beardcons`

* **`a_g_lo`**

   Override lingua di Google Play.

   * Valore di esempio: `ko`

* **`a_i_id`**

   Identificatore app in iTunes.

   * Valore di esempio: `835196493`

* **`a_i_lo`**

   Override lingua di iTunes.

   * Valore di esempio: `jp`

* **`a_dd`**

   Store predefinito per reindirizzamento automatico.

   * Valore di esempio: `i | g`

* **`a_cid`**

   Override ID personalizzato (generalmente IDFA per iOS o ADID per Android).

   * Valore di esempio: `Any String < 255 characters (UTF-8 encoded)`

* **`ctx*`**

   Keys prefixed with `ctx` will be in the context data of the resulting launch hit.

   * Valore di esempio: `ctxmy.custom.key=myValue`

* **`ctxa.referrer.campaign.name`**

   Nome campagna di acquisizione.

   Questo parametro è necessario per i rapporti se vuoi confrontare le prestazioni di diversi collegamenti di acquisizione.

   * Valore di esempio: 2015 Summit Conference

* **`ctxa.referrer.campaign.trackingcode`**

   Codice di tracciamento

   Questo parametro è necessario per i rapporti se vuoi confrontare le prestazioni di diversi collegamenti di acquisizione.

   * Valore di esempio: `lexsxouj`

* **`ctxa.referrer.campaign.source`**

   L'origine.

   * Valore di esempio: Rete annunci pubblicitari

* **`ctxa.referrer.campaign.medium`**

   Canale

   * Valore di esempio: E-mail

* **`ctxa.referrer.campaign.content`**

   Contenuto

   * Valore di esempio: Image # 325689

* **`ctxa.referrer.campaign.term`**

   Termine

   * Valore di esempio: hiking + boots


Quando crei manualmente i collegamenti di acquisizione, tieni presente quanto segue:

* Tutti i parametri che non corrispondono a quelli della tabella vengono passati come parte del reindirizzamento all'app store.
* Tutti i parametri sono tecnicamente opzionali, anche se il collegamento non funzionerà se non viene specificato almeno un ID store.

   An example of a store ID is `a_g_id`/ `a_i_id`.

* Se non è possibile determinare automaticamente lo store di destinazione e non ne è stato fornito uno predefinito, viene restituito un errore 404.

