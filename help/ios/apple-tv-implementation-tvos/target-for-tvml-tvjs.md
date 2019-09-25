---
description: Puoi sfruttare Adobe Target nelle app TVML/TVJS effettuando sostituzioni dirette nei file .xml. Per designare le aree della pagina da sostituire con i contenuti Target, usa l'elemento XML personalizzato ADBTarget.
seo-description: Puoi sfruttare Adobe Target nelle app TVML/TVJS effettuando sostituzioni dirette nei file .xml. Per designare le aree della pagina da sostituire con i contenuti Target, usa l'elemento XML personalizzato ADBTarget.
seo-title: Adobe Target per TVML/TVJS
title: Adobe Target per TVML/TVJS
uuid: afd5a583-5266-43f2-8cb0-0ace89c53a57
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Adobe Target per TVML/TVJS{#adobe-target-for-tvml-tvjs}

Puoi sfruttare Adobe Target nelle app TVML/TVJS effettuando sostituzioni dirette nei file .xml. Per designare le aree della pagina da sostituire con i contenuti Target, usa l'elemento XML personalizzato ADBTarget.

>[!IMPORTANT]
>
>Before using the `ADBTarget` element in your TVML pages, you must configure your TVML/TVJS app to use the tvOS SDK. For more information, see Apple TV Implementation with tvOS.[](/help/ios/apple-tv-implementation-tvos/apple-tv-implementation-tvos.md)

## Getting started {#section_88445645FD67416EAF6FDC3E3D3F5C33}

1. Identify the `.xml` file in which you want to use your Target location.
1. Add an `ADBTarget` element to the file as a child of the `<document>` element.
1. If Target fails to find your Mbox location, or it times out, the value between your `<ADBTarget>` and `</ADBTarget>` tags is used as default content.

## Configure your mbox in Target {#section_F2DA140C34B0421D976046F825B23123}

The returned content from Target replaces all content between `<ADBTarget>` and `</ADBTarget>`, including both `ADBTarget` tags.

>[!TIP]
>
>Pianificare di conseguenza ciò che si desidera sostituire.

Potrebbe trattarsi della semplice sostituzione di un valore stringa in un'etichetta o della più complessa sostituzione di un'intera pagina.

## Configure your ADBTarget element {#section_44A7AEC6FC0648ADAD0BACB57D493AFA}

Nell'elemento `ADBTarget`, devi fornire il nome nella proprietà `mbox`mbox. You can optionally add custom properties to your request in the `customParameterName="customParameterValue"` format.

* **`mbox`**

   Nome della posizione Mbox.

   * Property type: String
   * Questa proprietà è obbligatoria.

* **`id`**

   The Order ID.

   * Property type: String
   * Questa proprietà **non** è obbligatoria.

* **`total`**

   Totale ordine.

   * Tipo di proprietà: Stringa
   * Questa proprietà **non** è obbligatoria.

* **`purchasedProductIds`**

   Elenco degli ID, separati da virgola, dei prodotti acquistati per questo ordine.

   * Esempio di codice per questa proprietà:


      ```objective-c
      purchasedProductIds="product1,product2,product3" 
      ```

   * Tipo di proprietà: Stringa
   * Questa proprietà **non** è obbligatoria.

* **`mboxParameters`**

   Elenco di coppie chiave-valore per `mboxParameters`. Ogni voce di questa stringa è separata da un punto e virgola e i valori chiave sono separati da due punti.

   * Esempio di codice per questa proprietà:

      ```objective-c
      mboxParameters="mboxparameterKey:mboxParameterValue;mboxParameterKey1:mboxParameterValue1;mboxParameterKey2:mboxParameterValue2"
      ```

   * Tipo di proprietà: Stringa
   * Questa proprietà **non** è obbligatoria.

* **`customParameterName`**

   Il valore di questa proprietà è `customParameterValue`.

   * Tipo di proprietà: Stringa
   * Questa proprietà **non** è obbligatoria.


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
