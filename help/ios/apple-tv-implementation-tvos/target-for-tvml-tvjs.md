---
description: Puoi sfruttare Adobe Target nelle app TVML/TVJS effettuando sostituzioni dirette nei file .xml. Per designare le aree della pagina da sostituire con il contenuto Target, utilizza l’elemento XML personalizzato ADBTarget .
title: Adobe Target per TVML/TVJS
uuid: afd5a583-5266-43f2-8cb0-0ace89c53a57
exl-id: 9348d49c-2a5a-4ea0-b90d-99d446bd336a
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 75%

---

# Adobe Target per TVML/TVJS{#adobe-target-for-tvml-tvjs}

Puoi sfruttare Adobe Target nelle app TVML/TVJS effettuando sostituzioni dirette nei file .xml. Per designare le aree della pagina da sostituire con il contenuto Target, utilizza l’elemento XML personalizzato ADBTarget .

>[!IMPORTANT]
>
>Prima di usare l&#39;elemento `ADBTarget` nelle pagine TVML, devi configurare l&#39;app TVML/TVJS per l&#39;utilizzo dell&#39;SDK per tvOS. Per ulteriori informazioni, consulta [Implementazione Apple TV con tvOS](/help/ios/apple-tv-implementation-tvos/apple-tv-implementation-tvos.md).

## Introduzione {#section_88445645FD67416EAF6FDC3E3D3F5C33}

1. Individua il file `.xml` nel quale desideri usare la posizione Target.
1. Aggiungi un elemento `ADBTarget` al file come elemento secondario di `<document>`.
1. Se Target non è in grado di trovare la posizione Mbox, o se si verifica un timeout, il valore tra i tag `<ADBTarget>` e `</ADBTarget>` viene utilizzato come contenuto predefinito.

## Configurare mbox in Target {#section_F2DA140C34B0421D976046F825B23123}

Il contenuto restituito da Target sostituisce tutto il contenuto tra i tag `<ADBTarget>` e `</ADBTarget>`, compresi entrambi i tag `ADBTarget`.

>[!TIP]
>
>Pianifica attentamente ciò che desideri sostituire.

Potrebbe trattarsi della semplice sostituzione di un valore stringa in un&#39;etichetta o della più complessa sostituzione di un&#39;intera pagina.

## Configura l’elemento ADBTarget {#section_44A7AEC6FC0648ADAD0BACB57D493AFA}

Nell&#39;elemento `ADBTarget`, devi fornire il nome nella proprietà `mbox`mbox. Facoltativamente, puoi aggiungere proprietà personalizzate alla richiesta nel formato `customParameterName="customParameterValue"`.

* **`mbox`**

   Nome della posizione Mbox.

   * Tipo di proprietà: String
   * Questa proprietà è obbligatoria.

* **`id`**

   ID ordine.

   * Tipo di proprietà: String
   * Questa proprietà **non** è obbligatoria.

* **`total`**

   Totale ordine.

   * Tipo di proprietà: String
   * Questa proprietà **non** è obbligatoria.

* **`purchasedProductIds`**

   Elenco degli ID, separati da virgola, dei prodotti acquistati per questo ordine.

   * Di seguito è riportato un esempio di codice per questa proprietà:


      ```objective-c
      purchasedProductIds="product1,product2,product3" 
      ```

   * Tipo di proprietà: String
   * Questa proprietà **non** è obbligatoria.

* **`mboxParameters`**

   Elenco di coppie chiave-valore per `mboxParameters`. Le voci di questa stringa sono separate da punto e virgola e le coppie chiave-valori sono separate da due punti.

   * Di seguito è riportato un esempio di codice per questa proprietà:

      ```objective-c
      mboxParameters="mboxparameterKey:mboxParameterValue;mboxParameterKey1:mboxParameterValue1;mboxParameterKey2:mboxParameterValue2"
      ```

   * Tipo di proprietà: String
   * Questa proprietà **non** è obbligatoria.

* **`customParameterName`**

   Il valore di questa proprietà è `customParameterValue`.

   * Tipo di proprietà: String
   * Questa proprietà **non** è obbligatoria.


## Esempi {#section_6D6D6E8C7FE147168FC30D83CBC06985}

### Esempio 1

Nell&#39;esempio seguente, un elemento `ADBTarget` nella pagina `LandingPage.xml.js` viene utilizzato per sostituire i contenuti di un avviso:

#### Configurare Target

Supponiamo di avere una posizione Mbox denominata `landingPage` e di dover impostare il contenuto dell&#39;offerta come segue:

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

* Se la richiesta a Target ha esito positivo e viene restituito il contenuto dell’offerta, la pagina risultante sarà:

   ```objective-c
   <alertTemplate> 
       <title>My cool landing page</title> 
       <description>Thanks for coming to my page</description> 
   </alertTemplate>
   ```

* Se non è possibile raggiungere il server Target o si verifica un timeout della richiesta, la pagina risultante sarà:

   ```objective-c
   <alertTemplate> 
       <title>TargetTestPage</title> 
       <description>Load fail or timeout (defaultContent)</description> 
   </alertTemplate>
   ```

### Esempio 2

L&#39;esempio seguente illustra come aggiungere dati personalizzati all&#39;elemento `ADBTarget`. Questo metodo permette di creare esperienze condizionali e contenuti di offerte per questa posizione Mbox in Target:

```objective-c
<alertTemplate> 
    <ADBTarget mbox="landingPage" customData="custom data" moreCustomData="more custom data"> 
        <title>TargetTestPage</title> 
        <description>Load fail or timeout (defaultContent)</description> 
    </ADBTarget>  
</alertTemplate>
```
