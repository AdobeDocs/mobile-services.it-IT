---
description: 'null'
seo-description: 'null'
seo-title: Guida rapida per sviluppatori
solution: Experience Cloud,Analytics
title: Guida rapida per sviluppatori
topic: Developer and implementation
uuid: 11c06fcf-d5e4-4858-9a4e-3bf66cdd2a48
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '842'
ht-degree: 4%

---


# Guida rapida per sviluppatori{#developer-quick-start}

Seguono alcune informazioni su come implementare la libreria della piattaforma UWP (Universal Windows Platform).

>[!IMPORTANT]
>
>Per implementare l’SDK, è necessario Visual Studio 2013 o versione successiva.

## Scaricare l&#39;SDK  {#section_99FE1A17A36D4A2C943939023CF6265C}

Dopo aver decompresso il file di download [dell’](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases) SDK, avrai una cartella separata per ogni combinazione di architettura e piattaforma supportata. Avrete anche un `ADBMobileConfig.json` file. Per ulteriori informazioni su questo file, consulta il file [di configurazione](/help/universal-windows/c-configuration/c.json.md)ADBMobileConfig.json.

## Selezionate la versione corretta {#section_E53C5AA7D5474824A89BB32C003865A1}

Vengono forniti `.dll/.winmd` file diversi per ciascuna architettura supportata (x86, x64, ARM).

>[!IMPORTANT]
>
>La versione di `ADBMobile.winmd` non riflette la versione della libreria. Il `.winmd` file contiene solo i metadati e ha un numero di versione `255.255.255.255`, il che è un comportamento accettato secondo Microsoft. Per ulteriori informazioni, vedere [Come si aggiungono le informazioni sull&#39;assembly per una dll componente WinRT C++ / CX?](https://social.msdn.microsoft.com/Forums/windowsapps/en-US/6bcccaee-aa53-4770-bd5b-1205977f1ca7/how-do-i-add-assembly-information-for-a-winrt-c-cx-component-dll?forum=winappswithnativecode). Per verificare la versione della libreria in uso, controllate la versione del `ADBMobile.dll` file sottostante.

## Differenze di sintassi {#section_A02DE120B6D240F5AFFE7509755C4F14}

La libreria della piattaforma UWP (Universal Windows Platform) può essere utilizzata in diversi linguaggi di programmazione. Gli esempi contenuti in questa guida sono in WinJS (JavaScript), se utilizzi un linguaggio diverso, potrebbero dover essere modificati. Quando utilizzi metodi winmd da winJS, tutti i metodi hanno automaticamente la prima lettera minuscola.

La differenza principale tra le implementazioni è la struttura dati utilizzata per i dati contestuali. Inoltre, quando utilizzi l’SDK in un progetto WinJS, usa una stringa vuota ( `""` o `''`) invece di `null` valori stringa vuoti.

## Add the library and config File to your project - C# {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. Avviare Visual Studio e aprire la soluzione.
1. In Esplora **[!UICONTROL soluzioni]**, fare clic con il pulsante destro del mouse su **[!UICONTROL Riferimenti]** e selezionare **[!UICONTROL Aggiungi riferimento]**.

1. Seleziona la versione corretta della libreria e individua il file ADBMobile.winmd associato.

   Per ulteriori informazioni, consultate *Selezionare la sezione relativa alla versione* corretta in questa pagina.

1. Fai clic su **Aggiungi**.

1. Verifica che il file ADBMobile.winmd sia selezionato nella finestra Gestione **** riferimenti e fai clic su **[!UICONTROL OK]**.

1. In Esplora **[!UICONTROL soluzioni]**, fare clic con il pulsante destro del mouse su **[!UICONTROL Riferimenti]** e selezionare **[!UICONTROL Aggiungi riferimento]**.

   Se hai anche un progetto C++ nella soluzione, salta questo passaggio.

1. Nella scheda **[!UICONTROL Windows]** a sinistra, selezionare **[!UICONTROL Estensioni]**, selezionare e aggiungere Runtime **[!UICONTROL Visual C++ 2015 per le app]** della piattaforma UWP (Universal Windows Platform).

1. Aggiungete la riga seguente alla classe:

   ```csharp
   using ADBMobile;
   ```

1. Fai clic con il pulsante destro del mouse sul progetto e fai clic su **[!UICONTROL Aggiungi]** > Elemento **** esistente.

1. Individuate il `ADBMobileConfig.json` file e fate clic su **[!UICONTROL Aggiungi]**.

1. Fare clic con il pulsante destro del mouse sul `ADBMobileConfig.json` file nella soluzione e selezionare **[!UICONTROL Proprietà]**.

1. Cambia Azione **[!UICONTROL di]** compilazione in **[!UICONTROL Contenuto]**.

## Add the library and config file to your project - C++ {#section_A95C1D18F6144F37ADC8F51590F3983E}

1. Avviare Visual Studio e aprire la soluzione.
1. In Esplora **[!UICONTROL soluzioni]**, fai clic con il pulsante destro del mouse sul progetto e seleziona **[!UICONTROL Aggiungi]** > **[!UICONTROL Riferimenti]**.

1. Seleziona la versione corretta della libreria e aggiungi un riferimento al file ADBMobile.winmd associato.

   Per ulteriori informazioni, consultate *Selezionare la sezione relativa alla versione* corretta in questa pagina.

1. Fai clic su **[!UICONTROL Aggiungi]**.

1. Verificare che `ADBMobile.winmd` sia selezionato nella finestra Gestione **** riferimenti e fare clic su **[!UICONTROL OK]**.

1. Aggiungete la riga seguente alla classe:

   ```c++
   using namespace ADBMobile;
   ```

1. Fai clic con il pulsante destro del mouse sul progetto e seleziona **[!UICONTROL Aggiungi]** > Elemento **** esistente.

1. Individuate il `ADBMobileConfig.json` file e fate clic su **[!UICONTROL Aggiungi]**.

1. Fare clic con il pulsante destro del mouse sul `ADBMobileConfig.json` file nella soluzione e selezionare **[!UICONTROL Proprietà]**.

1. Nella scheda **[!UICONTROL Generale]** , cambiate **[!UICONTROL Contenuto]** in **[!UICONTROL Sì]** e fate clic su **[!UICONTROL OK]**.

## Add the library and config file to your project - WinJS {#section_FF83113EBF4742AFA929F4AC28F92DB5}

1. Avviare Visual Studio e aprire la soluzione.

1. In Esplora **[!UICONTROL soluzioni]**, fare clic con il pulsante destro del mouse su **[!UICONTROL Riferimenti]** e selezionare **[!UICONTROL Aggiungi riferimento]**.

1. Seleziona la versione corretta della libreria e individua il file ADBMobile.winmd associato.

1. Fai clic su **[!UICONTROL Aggiungi]**.

1. Verifica che il file ADBMobile.winmd sia selezionato nella finestra Gestione **** riferimenti e fai clic su **[!UICONTROL OK]**.

1. In Esplora **[!UICONTROL soluzioni]**, fare clic con il pulsante destro del mouse su **[!UICONTROL Riferimenti]** e selezionare **[!UICONTROL Aggiungi riferimento]**.

   Se hai anche un progetto C++ nella soluzione, salta questo passaggio.

1. Nella scheda **[!UICONTROL Windows]** a sinistra, selezionare **[!UICONTROL Estensioni]** , quindi selezionare e aggiungere Runtime **[!UICONTROL Visual C++ 2015 per le app]** della piattaforma UWP (Universal Windows Platform).

1. Fai clic con il pulsante destro del mouse sul progetto e seleziona **[!UICONTROL Aggiungi]** > Elemento **** esistente.

1. Individuate il `ADBMobileConfig.json` file e fate clic su **[!UICONTROL Aggiungi]**.

1. Fare clic con il pulsante destro del mouse sul `ADBMobileConfig.json` file nella soluzione e selezionare **[!UICONTROL Proprietà]**.

1. Con Proprietà **** file selezionato, accertati che Azione **** pacchetto sia impostata su **[!UICONTROL Contenuto]**.

   Per i progetti JavaScript, il file è impostato su Contenuto per impostazione predefinita.

## Aggiornare il file di configurazione ADBMobileConfig.json {#section_0BC8CC0E4AAD4AC385FA0AEDC3C56AFE}

Il `ADBMobileConfig.json` file contiene impostazioni SDK globali e si trova nella directory principale del progetto dopo aver completato i passaggi descritti nella sezione *Aggiungere la libreria e il file di configurazione alla sezione del progetto* . Se il `ADBMobileConfig.json` file non è stato preconfigurato da  Adobe Mobile Services, devi aggiornare alcuni valori per iniziare.

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

Come minimo, aggiornate i seguenti valori per le soluzioni in uso:

* **Adobe Analytics**: `rsids` e `server`

* **Adobe Target**: `clientCode`

* **Adobe Audience Manager**: `server`

For more information, see [SDK methods](/help/universal-windows/c-configuration/methods.md).

## Eseguire il debug di {#section_3A10376A60394A15BEE483323E0CD4AA}

Per abilitare il debug per l’SDK, chiama `ADBMobile.Config.setDebugLogging(true);`.

Per le app C Sharp e JavaScript, è necessario abilitare il debug del codice nativo eseguendo i passaggi seguenti (il debug del codice nativo è l&#39;impostazione predefinita per le app C++):

### C Nitido

1. Fare clic con il pulsante destro del mouse sul progetto, quindi scegliere **[!UICONTROL Proprietà]** > scheda **** Debug.

1. Cambia il tipo di debugger a discesa in Solo **** nativo.

### JavaScript

1. Fate clic con il pulsante destro del mouse sul progetto, fate clic su **[!UICONTROL Proprietà]** > Proprietà **** configurazione > scheda **** Debug.

1. Cambia il tipo di debugger a discesa in Solo **** nativo.

Tutto qui. Ora sei pronto per implementare Analytics, Target e Gestione dell&#39;audience nella tua app della piattaforma UWP (Universal Windows Platform).

