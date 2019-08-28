---
description: Puoi sfruttare Adobe Target nelle app TVML/TVJS effettuando sostituzioni dirette nei file .xml. Per designare le aree della pagina da sostituire con i contenuti Target, usa l'elemento XML personalizzato ADBTarget.
seo-description: Puoi sfruttare Adobe Target nelle app TVML/TVJS effettuando sostituzioni dirette nei file .xml. Per designare le aree della pagina da sostituire con i contenuti Target, usa l'elemento XML personalizzato ADBTarget.
seo-title: Adobe Target per TVML/TVJS
title: Adobe Target per TVML/TVJS
uuid: afd 5 a 583-5266-43 f 2-8 cb 0-0 ace 89 c 53 a 57
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Adobe Target per TVML/TVJS{#adobe-target-for-tvml-tvjs}

Puoi sfruttare Adobe Target nelle app TVML/TVJS effettuando sostituzioni dirette nei file .xml. Per designare le aree della pagina da sostituire con i contenuti Target, usa l'elemento XML personalizzato ADBTarget.

>[!IMPORTANT]
>
>Before using the `ADBTarget` element in your TVML pages, you must configure your TVML/TVJS app to use the tvOS SDK. Per ulteriori informazioni, consultate [Implementazione Apple TV con tvos](/help/ios/apple-tv-implementation-tvos/apple-tv-implementation-tvos.md).

## Getting started {#section_88445645FD67416EAF6FDC3E3D3F5C33}

1. Identify the `.xml` file in which you want to use your Target location.
1. Add an `ADBTarget` element to the file as a child of the `<document>` element.
1. If Target fails to find your Mbox location, or it times out, the value between your `<ADBTarget>` and `</ADBTarget>` tags is used as default content.

## Configure your mbox in Target {#section_F2DA140C34B0421D976046F825B23123}

The returned content from Target replaces all content between `<ADBTarget>` and `</ADBTarget>`, including both `ADBTarget` tags.

>[!TIP]
>
>Pianificate il contenuto da sostituire di conseguenza.

Potrebbe trattarsi della semplice sostituzione di un valore stringa in un'etichetta o della più complessa sostituzione di un'intera pagina.

## Configurare l'elemento adbtarget {#section_44A7AEC6FC0648ADAD0BACB57D493AFA}

Nell'elemento `ADBTarget`, devi fornire il nome nella proprietà `mbox`mbox. You can optionally add custom properties to your request in the `customParameterName="customParameterValue"` format.

* **`mbox`**

   Nome della posizione Mbox.

   * Tipo proprietà: Stringa
   * Questa proprietà è obbligatoria.

* **`id`**

   L'ID ordine.

   * Tipo proprietà: Stringa
   * Questa proprietà **non** è necessaria.

* **`total`**

   Totale ordine.

   * Tipo proprietà: Stringa
   * Questa proprietà **non** è necessaria.

* **`purchasedProductIds`**

   Elenco degli ID, separati da virgola, dei prodotti acquistati per questo ordine.

   * Ecco l'esempio di codice per questa proprietà:


      ```objective-c
      purchasedProductIds="product1,product2,product3" 
      ```

   * Tipo proprietà: Stringa
   * Questa proprietà **non** è necessaria.

* **`mboxParameters`**

   Elenco di coppie chiave-valore per `mboxParameters`. Ogni voce di questa stringa è separata da un punto e virgola e i valori chiave sono separati da due punti.

   * Ecco l'esempio di codice per questa proprietà:

      ```objective-c
      mboxParameters="mboxparameterKey:mboxParameterValue;mboxParameterKey1:mboxParameterValue1;mboxParameterKey2:mboxParameterValue2"
      ```

   * Tipo proprietà: Stringa
   * Questa proprietà **non** è necessaria.

* **`customParameterName`**

   Il valore di questa proprietà `customParameterValue`è.

   * Tipo proprietà: Stringa
   * Questa proprietà **non** è necessaria.


## Esempi {#section_6D6D6E8C7FE147168FC30D83CBC06985}

### Esempio 1

Nell'esempio seguente, un elemento `ADBTarget` nella pagina `LandingPage.xml.js` viene utilizzato per sostituire i contenuti di un avviso:

#### Configurare Target

Supponiamo di avere una posizione Mbox denominata `landingPage` e di dover impostare il contenuto dell'offerta come segue:

```objective-c
<title>My cool landing page</title> 
<description>Thanks for coming to my page</description> 
```

#### Configurare landingPage.xml.js

* Configurazione per landingPage.xml.js:

   ```js
   <alertTemplate> 
       <ADBTarget mbox="landingPage">  
           <title>TargetTestPage</title> 
           <description>Load fail or timeout (defaultContent)</description> 
       </ADBTarget>  
   </alertTemplate> 
   ```

* Se la richiesta inviata a Target ha esito positivo e viene restituito il contenuto dell'offerta, il codice della pagina risultante sarà:

   ```objective-c
   <alertTemplate> 
       <title>My cool landing page</title> 
       <description>Thanks for coming to my page</description> 
   </alertTemplate>
   ```

* Se non è possibile accedere al server Target o si verifica il timeout della richiesta, il codice della pagina risultante sarà:

   ```objective-c
   <alertTemplate> 
       <title>TargetTestPage</title> 
       <description>Load fail or timeout (defaultContent)</description> 
   </alertTemplate>
   ```

### Esempio 2

L'esempio seguente illustra come aggiungere dati personalizzati all'elemento `ADBTarget`. Questo metodo permette di creare esperienze condizionali e contenuti di offerte per questa posizione Mbox in Target:

```objective-c
<alertTemplate> 
    <ADBTarget mbox="landingPage" customData="custom data" moreCustomData="more custom data"> 
        <title>TargetTestPage</title> 
        <description>Load fail or timeout (defaultContent)</description> 
    </ADBTarget>  
</alertTemplate>
```
