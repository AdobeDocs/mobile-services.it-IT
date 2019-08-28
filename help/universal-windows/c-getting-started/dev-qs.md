---
description: nulle
seo-description: nulle
seo-title: Avvio rapido per sviluppatori
solution: Marketing Cloud, Analytics
title: Avvio rapido per sviluppatori
topic: Sviluppatore e implementazione
uuid: 11 c 06 fcf-d 5 e 4-4858-9 a 4 e -3 bf 66 cdd 2 a 48
translation-type: tm+mt
source-git-commit: 19264af3f4a675add6f61c27f4cdaf20033b9bb7

---


# Developer quick start{#developer-quick-start}

Seguono alcune informazioni su come implementare la libreria della piattaforma UWP (Universal Windows Platform).

>[!IMPORTANT]
>
>Per implementare l'SDK, è necessario Visual Studio 2013 o versione successiva.

## Scaricare l'SDK {#section_99FE1A17A36D4A2C943939023CF6265C}

After you unzip the [SDK download](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases) file, you will have a separate folder for each supported architecture and platform combination. Avrai anche un `ADBMobileConfig.json` file. Per ulteriori informazioni su questo file, vedi [File di configurazione adbmobileconfig. json](/help/universal-windows/c-configuration/c.json.md).

## Select the correct version {#section_E53C5AA7D5474824A89BB32C003865A1}

Different `.dll/.winmd` files are provided for each supported architecture (x86, x64, ARM).

>[!IMPORTANT]
>
>The version of `ADBMobile.winmd` does not reflect the version of the library. `.winmd` Il file contiene solo metadati e ha un numero di versione, `255.255.255.255`che viene accettato in base a Microsoft. Per ulteriori informazioni, [vedi Come posso aggiungere informazioni sull'assemblaggio per un componente winrt C + +/CX?](https://social.msdn.microsoft.com/Forums/windowsapps/en-US/6bcccaee-aa53-4770-bd5b-1205977f1ca7/how-do-i-add-assembly-information-for-a-winrt-c-cx-component-dll?forum=winappswithnativecode). To check the version of the library you are using, check the version of the underlying `ADBMobile.dll` file.

## Differenze di sintassi {#section_A02DE120B6D240F5AFFE7509755C4F14}

La libreria della piattaforma UWP (Universal Windows Platform) può essere utilizzata in vari linguaggi di programmazione. Gli esempi di questa guida si trovano in winjs (javascript), se utilizzi un linguaggio diverso, potrebbe dover essere modificato. Quando utilizzi metodi winmd da winjs, tutti i metodi hanno automaticamente la prima lettera minuscola.

La differenza principale tra le implementazioni è la struttura dei dati utilizzata per i dati contestuali. Additionally, when using the SDK in a WinJS project, use an empty string ( `""` or `''`) instead of `null` for empty string values.

## Add the library and config File to your project - C# {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. Avvia Visual Studio e apri la soluzione.
1. In the **[!UICONTROL Solution Explorer]**, right-click **[!UICONTROL References]** and select **[!UICONTROL Add Reference]**.

1. Seleziona la versione corretta della libreria e individua il file adbmobile. winmd associato.

   Per ulteriori informazioni, consultate *Selezionare la sezione corretta della versione* in questa pagina.

1. Fai clic su **Aggiungi**.

1. Verify that the ADBMobile.winmd file is checked in the **[!UICONTROL Reference Manager]** window and click **[!UICONTROL OK]**.

1. In the **[!UICONTROL Solution Explorer]**, right-click **[!UICONTROL References]** and select **[!UICONTROL Add Reference]**.

   Se hai anche un progetto C + + nella soluzione, salta questo passaggio.

1. Nella scheda **[!UICONTROL Windows]** a sinistra, selezionate **[!UICONTROL Estensioni]**, selezionate e aggiungete **[!UICONTROL Runtime di Visual C + + 2015 per le app della piattaforma UWP (Universal Windows Platform)]**.

1. Aggiungi la riga seguente alla classe:

   ```csharp
   using ADBMobile;
   ```

1. Right-click your project and click **[!UICONTROL Add]** &gt; **[!UICONTROL Existing Item]**.

1. Individuate `ADBMobileConfig.json` il file e fate clic **[!UICONTROL su Aggiungi]**.

1. Fai clic con il pulsante destro del mouse `ADBMobileConfig.json` sul file nella tua soluzione e seleziona **[!UICONTROL Proprietà]**.

1. Cambia **[!UICONTROL Operazione di generazione]** in **[!UICONTROL Contenuto]**.

## Add the library and config file to your project - C++ {#section_A95C1D18F6144F37ADC8F51590F3983E}

1. Avvia Visual Studio e apri la soluzione.
1. In the **[!UICONTROL Solution Explorer]**, right-click your project and select **[!UICONTROL Add]** &gt; **[!UICONTROL References]**.

1. Seleziona la versione corretta della libreria e aggiungi un riferimento al file adbmobile. winmd associato.

   Per ulteriori informazioni, consultate *Selezionare la sezione corretta della versione* in questa pagina.

1. Fai clic su **[!UICONTROL Aggiungi]**.

1. Verifica che `ADBMobile.winmd`**sia selezionato nella finestra[!UICONTROL Gestione riferimenti]** e fai clic su **[!UICONTROL OK]**.

1. Aggiungi la riga seguente alla classe:

   ```c++
   using namespace ADBMobile;
   ```

1. Right-click your project and select **[!UICONTROL Add]** &gt; **[!UICONTROL Existing Item]**.

1. Browse to `ADBMobileConfig.json` file and click **[!UICONTROL Add]**.

1. Right-click the `ADBMobileConfig.json` file in your solution and select **[!UICONTROL Properties]**.

1. On the **[!UICONTROL General]** tab, change **[!UICONTROL Content]** to **[!UICONTROL Yes]** and click **[!UICONTROL OK]**.

## Add the library and config file to your project - WinJS {#section_FF83113EBF4742AFA929F4AC28F92DB5}

1. Avvia Visual Studio e apri la soluzione.

1. In the **[!UICONTROL Solution Explorer]**, right-click **[!UICONTROL References]** and select **[!UICONTROL Add Reference]**.

1. Seleziona la versione corretta della libreria e individua il file adbmobile. winmd associato.

1. Fai clic su **[!UICONTROL Aggiungi]**.

1. Verify that the ADBMobile.winmd file is checked in the **[!UICONTROL Reference Manager]** window and click **[!UICONTROL OK]**.

1. In the **[!UICONTROL Solution Explorer]**, right-click **[!UICONTROL References]** and select **[!UICONTROL Add Reference]**.

   Se hai anche un progetto C + + nella soluzione, salta questo passaggio.

1. Nella scheda **[!UICONTROL Windows]** a sinistra, selezionate **[!UICONTROL Estensioni]** , quindi selezionate e aggiungete **[!UICONTROL Runtime di Visual C + + 2015 per le app della piattaforma UWP (Universal Windows Platform]**).

1. Right-click your project and select **[!UICONTROL Add]** &gt; **[!UICONTROL Existing Item]**.

1. Individuate `ADBMobileConfig.json` il file e fate clic **[!UICONTROL su Aggiungi]**.

1. Right-click the `ADBMobileConfig.json` file in your solution and select **[!UICONTROL Properties]**.

1. Con **[!UICONTROL Proprietà file]** selezionata, assicurarsi che **[!UICONTROL Azione pacchetto]** sia impostata su **[!UICONTROL Contenuto]**.

   Per i progetti javascript, il file è impostato su Contenuto per impostazione predefinita.

## Update The ADBMobileConfig.json config file {#section_0BC8CC0E4AAD4AC385FA0AEDC3C56AFE}

The `ADBMobileConfig.json` file contains global SDK settings and is located at your project root after you complete the steps in the *Add the library and config file to your project* section. If your `ADBMobileConfig.json` file was not pre-configured by Adobe Mobile Services, you need to update a few values to get started.

Ecco un esempio di file `ADBMobileConfig.json`:

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

Come minimo, aggiorna i seguenti valori per le soluzioni che utilizzi:

* **Adobe Analytics**: `rsids` e `server`

* **Adobe Target**: `clientCode`

* **Adobe Audience Manager**: `server`

Per ulteriori informazioni, consulta [Metodi SDK](/help/universal-windows/c-configuration/methods.md).

## Eseguire il debug {#section_3A10376A60394A15BEE483323E0CD4AA}

Per abilitare il debug dell'SDK, `ADBMobile.Config.setDebugLogging(true);`invoca.

Per le app Sharp Sharp e javascript, devi abilitare il debug del codice nativo completando i passaggi seguenti (il debug del codice nativo è l'impostazione predefinita per le app C + +):

### C Sharp

1. Fai clic con il pulsante destro del mouse sul progetto, quindi fai clic su **[!UICONTROL Proprietà]** &gt; **[!UICONTROL scheda Debug]**.

1. Cambia l’elenco a discesa del tipo di debug in **Native Only (Solo nativo)**.

### JavaScript

1. Right-click the project, click **[!UICONTROL Properties]** &gt; **[!UICONTROL Configuration Properties]** &gt; **[!UICONTROL Debug tab]**.

1. Nell’elenco a discesa, cambia il tipo di debugger in **[!UICONTROL Solo nativo]**.

Tutto qui. A questo punto sei pronto per implementare Analytics, Target e Gestione dell'audience nell’app della piattaforma UWP (Universal Windows Platform).

