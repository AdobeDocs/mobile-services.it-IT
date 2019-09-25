---
description: nulle
seo-description: nulle
seo-title: Developer quick start
solution: Marketing Cloud,Analytics
title: Developer quick start
topic: Sviluppatore e implementazione
uuid: b368959b-d985-436e-8b3e-97e355a97951
translation-type: tm+mt
source-git-commit: 19264af3f4a675add6f61c27f4cdaf20033b9bb7

---


# Developer quick start {#developer-quick-start}

Per implementare l’SDK è necessario Visual Studio 2013 o versione successiva.

## Ottenere l’SDK {#section_99FE1A17A36D4A2C943939023CF6265C}

Una volta estratto il [download dell’SDK](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases), disporrai di una cartella separata per ogni architettura e combinazione di piattaforme supportata. Disporrai anche del file `ADBMobileConfig.json` che viene spiegato più avanti in questa guida.

## Select the correct version {#section_E53C5AA7D5474824A89BB32C003865A1}

Different `.dll`/ `.winmd` files are provided for each target platform (Windows 8.1, Windows Phone 8.1), and supported architecture (x86, x64, ARM). I file sono separati in una struttura di cartelle come la seguente:

![](assets/folder-structure.png)

>[!IMPORTANT]
>
>The version of `ADBMobile.winmd` does not reflect the version of the library. The `.winmd` file contains metadata only, and as such will have a version number of `255.255.255.255` which is accepted behavior according to Microsoft (see [How do I add assembly information for a WinRT C++ / CX component dll?](https://social.msdn.microsoft.com/Forums/windowsapps/en-US/6bcccaee-aa53-4770-bd5b-1205977f1ca7/how-do-i-add-assembly-information-for-a-winrt-c-cx-component-dll?forum=winappswithnativecode)). To check the version of the library you are using, check the version of the underlying `ADBMobile.dll` file.

## Syntax differences {#section_A02DE120B6D240F5AFFE7509755C4F14}

La libreria Windows 8.1 Universal App Store può essere utilizzata in vari linguaggi di programmazione. Gli esempi riportati in questa guida sono in WinJS (JavaScript) e potrebbero richiedere delle modifiche se utilizzi un linguaggio diverso. Ricorda che quando utilizzi metodi winmd da WinJS (JavaScript), in tutti i metodi la prima lettera viene automaticamente impostata come minuscola.

La differenza principale tra le implementazioni è la struttura dei dati utilizzata per i dati contestuali.

Additionally, when using the SDK in a WinJS project, use an empty string ( `""` or `''`) instead of `null` for empty string values.

## Add the library and config file to your project - C Sharp {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. Avvia Visual Studio e apri la soluzione.
1. In **Esplora soluzioni**, fai clic con il pulsante destro del mouse su **[!UICONTROL Riferimenti]** e seleziona **[!UIUCONTROL Aggiungi riferimento]**.

1. Select the correct version of the library and browse to the associated `ADBMobile.winmd` file.

   Per ulteriori informazioni, consulta la sezione *Selezionare la versione* corretta riportata di seguito.

1. Fai clic su **[!UICONTROL Aggiungi]**.

1. Verify that `ADBMobile.winmd` is selected in the **[!UICONTROL Reference Manager]** window and click **[!UICONTROL OK]**.

   >[!NOTE]
   >
   >Quando aggiungete un riferimento a un'app Windows Phone, per selezionare `ADBMobile.winmd`, modificate il filtro file predefinito da File **** componente a **Tutti i file**.

1. In the **[!UICONTROL Solution Explorer]**, right-click **[!UICONTROL References]** and select **[!UICONTROL Add Reference]**.

   Ignora questo passaggio se hai anche un progetto C++ nella soluzione.

1. Nella scheda **Windows** a sinistra, selezionate **[!UICONTROL Estensioni]**, quindi selezionate e aggiungete **[!UICONTROL Microsoft Visual C++ 2013 Runtime Package for Windows]**.

1. Aggiungi la riga seguente alla classe:

   ```
   using ADBMobile;
   ```

1. Right-click you your project and select **[!UICONTROL Add]** &gt; **[!UICONTROL Existing Item]**.

1. Individuate il `ADBMobileConfig.json` file e fate clic su **[!UICONTROL Aggiungi]**.

1. Right-click the `ADBMobileConfig.json` file in your solution and select **[!UICONTROL Properties]**.

1. Cambia **[!UICONTROL Operazione di generazione]** in **[!UICONTROL Contenuto]**.

## Add the library and config file to your project - C++ {#section_A95C1D18F6144F37ADC8F51590F3983E}

1. Avvia Visual Studio e apri la soluzione.
1. In the **[!UICONTROL Solution Explorer]**, right-click your project and select **[!UICONTROL Add]** &gt; **[!UICONTROL References]**.

1. Select the correct version of the library and then add a reference to the associated `ADBMobile.winmd` file.

   Per ulteriori informazioni, consultate la sezione *Selezionare la versione* corretta riportata di seguito.

1. Fai clic su **[!UICONTROL Aggiungi]**.

1. Nella finestra Gestione **** riferimenti verificare che `ADBMobile.winmd` sia selezionato e fare clic su **[!UICONTROL OK]**.

   >[!TIP]
   >
   >Quando aggiungete un riferimento a un'app Windows Phone, per selezionare `ADBMobile.winmd`, modificate il filtro file predefinito da File **** componente a **Tutti i file**.

1. Aggiungi la riga seguente alla classe:

   ```
   using namespace ADMS::Measurement;
   ```

1. Right-click you your project and select **[!UICONTROL Add]** &gt; **[!UICONTROL Existing Item]**.

1. Individuate il `ADBMobileConfig.json` file e fate clic su **[!UICONTROL Aggiungi]**.

1. Right-click the `ADBMobileConfig.json` file in your solution and select **[!UICONTROL Properties]**.

1. On the **[!UICONTROL General]** tab, change **[!UICONTROL Content]** to **[!UICONTROL Yes]**, and click **[!UICONTROL OK]**.

## Add the library and config file to your project - WinJS {#section_FF83113EBF4742AFA929F4AC28F92DB5}

1. Avvia Visual Studio e apri la soluzione.
1. In the **Solution Explorer**, right-click **[!UICONTROL References]** and select **[!UICONTROL Add Reference**.

   For more information, see Select the Correct Version section below.**

1. Select the correct version of the library and then browse to the associated `ADBMobile.winmd` file.

1. Fai clic su **[!UICONTROL Aggiungi]**.

1. Verifica che `ADBMobile.winmd`**sia selezionato nella finestra[!UICONTROL Gestione riferimenti]** e fai clic su **[!UICONTROL OK]**.

   >[!TIP]
   >
   >Quando aggiungete un riferimento a un'app Windows Phone, per selezionare `ADBMobile.winmd`, modificate il filtro file predefinito da File **** componente a **Tutti i file**.

1. In the **[!UICONTROL Solution Explorer]**, right-click **[!UICONTROL References]** and select **[!UICONTROL Add Reference]**.

   Ignora questo passaggio se hai anche un progetto C++ nella soluzione.

1. Nella scheda **[!UICONTROL Windows]** a sinistra, selezionate **[!UICONTROL Estensioni]** , quindi selezionate e aggiungete **[!UICONTROL Microsoft Visual C++ 2013 Runtime Package for Windows]**.

1. Right-click your project and select **[!UICONTROL Add]** &gt; **[!UICONTROL Existing Item]**.

1. Individuate il `ADBMobileConfig.json` file e fate clic su **[!UICONTROL Aggiungi]**.

1. Right-click the `ADBMobileConfig.json]` file in your solution and select **[!UICONTROL Properties]**.

1. Con Proprietà **** file selezionato, accertati che Azione **** pacchetto sia impostata su **[!UICONTROL Contenuto]**.

   Per i progetti JavaScript, il file è impostato su **[!UICONTROL Content]** per impostazione predefinita.

## Update the ADBMobileConfig.json config file {#section_0BC8CC0E4AAD4AC385FA0AEDC3C56AFE}

The `ADBMobileConfig.json` file contains global SDK settings, and is located at your project root after you complete the steps in the *Add the Library and Config File to your Project* section. If your `ADBMobileConfig.json` file was not pre-configured by Adobe Mobile Services, you need to update a few values to get started.

Di seguito viene indicato un esempio del file `ADBMobileConfig.json`:

```js
{ 
    "version" : "1.0", 
    "analytics" : { 
        "rsids" : "coolApp", 
        "server" : "my.CoolApp.com", 
        "charset" : "UTF-8", 
        "ssl" : true, 
        "offlineEnabled" : true, 
        "lifecycleTimeout" : 300, 
        "privacyDefault" : "optedin", 
        "poi" : [ 
                    ["san francisco",37.757144,-122.44812,7000], 
                    ["santa cruz",36.972935,-122.01725,600] 
                ] 
    }, 
 "target" : { 
  "clientCode" : "myTargetClientCode", 
  "timeout" : 1 
 }, 
 "audienceManager" : { 
  "server" : "myServer.demdex.com" 
 } 
}
```

Come minimo, aggiorna i seguenti valori delle soluzioni che utilizzi:

* **Analytics**: `rsids` e `server`
* **Target**: `clientCode`
* **Gestione dell'audience**: `server`

For more details, see [ADBMobileConfig.json config](/help/windows-appstore/c-configuration/methods.md).

## Eseguire il debug {#section_3A10376A60394A15BEE483323E0CD4AA}

Per attivare il debug per SDK, è necessario invocare `ADBMobile.Config.setDebugLogging(true);`.

Per le app C Sharp e JS, devi abilitare il debug del codice nativo eseguendo i passaggi seguenti (il debug del codice nativo è l'impostazione predefinita per le app C++):

### C Sharp

Right-click the project, select **[!UICONTROL Properties]** &gt; **[!UICONTROL Debug tab]**. Nel menu a discesa Debugger, selezionate Solo **** nativo.

### JS

Right-click the project, select  **[!UICONTROL Properties]** &gt; **[!UICONTROL Configuration Properties]** &gt; **[!UICONTROL Debug tab]**. Cambia l’elenco a discesa del tipo di debug in **Native Only (Solo nativo)**.

Fatto! Ora è tutto pronto per l’implementazione di Analytics, Target, e Audience Manager nella tua app Windows 8.1 Universal App Store.
