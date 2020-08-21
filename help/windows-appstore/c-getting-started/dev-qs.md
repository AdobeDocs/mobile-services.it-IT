---
description: 'null'
seo-description: 'null'
seo-title: Guida rapida per sviluppatori
solution: Marketing Cloud,Analytics
title: Guida rapida per sviluppatori
topic: Developer and implementation
uuid: b368959b-d985-436e-8b3e-97e355a97951
translation-type: tm+mt
source-git-commit: 7ae626be4d71641c6efb127cf5b1d3e18fccb907
workflow-type: tm+mt
source-wordcount: '919'
ht-degree: 2%

---


# Guida rapida per sviluppatori {#developer-quick-start}

Per implementare l’SDK è necessario Visual Studio 2013 o successivo.

## Scaricare l&#39;SDK  {#section_99FE1A17A36D4A2C943939023CF6265C}

Dopo aver decompresso il download [dell&#39;](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases)SDK, avrai una cartella separata per ogni combinazione di architettura e piattaforma supportata. Avrete anche un `ADBMobileConfig.json` file che verrà illustrato più avanti in questa guida.

## Selezionate la versione corretta {#section_E53C5AA7D5474824A89BB32C003865A1}

Vengono forniti `.dll`/ `.winmd` file diversi per ciascuna piattaforma di destinazione (Windows 8.1, Windows Phone 8.1) e architetture supportate (x86, x64, ARM). I file sono separati in una struttura di cartelle come segue:

![](assets/folder-structure.png)

>[!IMPORTANT]
>
>La versione di `ADBMobile.winmd` non riflette la versione della libreria. Il `.winmd` file contiene solo i metadati, e come tale avrà un numero di versione di `255.255.255.255` cui è accettato il comportamento secondo Microsoft (vedere [Come si aggiungono le informazioni di assembly per una dll componente WinRT C++ / CX?](https://social.msdn.microsoft.com/Forums/windowsapps/en-US/6bcccaee-aa53-4770-bd5b-1205977f1ca7/how-do-i-add-assembly-information-for-a-winrt-c-cx-component-dll?forum=winappswithnativecode)). Per verificare la versione della libreria in uso, controllate la versione del `ADBMobile.dll` file sottostante.

## Differenze di sintassi {#section_A02DE120B6D240F5AFFE7509755C4F14}

La libreria Windows 8.1 Universal App Store può essere utilizzata in diversi linguaggi di programmazione. Gli esempi contenuti in questa guida sono in WinJS (JavaScript) e potrebbero dover essere modificati se si utilizza un linguaggio diverso. Tenere presente che quando si utilizzano metodi winmd da winJS (JavaScript), tutti i metodi hanno automaticamente la prima lettera minuscola.

La differenza principale tra le implementazioni è la struttura dati utilizzata per i dati contestuali.

Inoltre, quando utilizzi l’SDK in un progetto WinJS, usa una stringa vuota ( `""` o `''`) invece di `null` valori stringa vuoti.

## Aggiungere la libreria e il file di configurazione al progetto - C Sharp {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. Avviare Visual Studio e aprire la soluzione.
1. In Esplora **soluzioni**, fare clic con il pulsante destro del mouse su **[!UICONTROL Riferimenti]** e selezionare **[!UIUCONTROL Aggiungi riferimento]**.

1. Selezionate la versione corretta della libreria e individuate il `ADBMobile.winmd` file associato.

   Per ulteriori informazioni, consulta la sezione *Selezionare la versione* corretta riportata di seguito.

1. Fai clic su **[!UICONTROL Aggiungi]**.

1. Verificare che `ADBMobile.winmd` sia selezionato nella finestra Gestione **** riferimenti e fare clic su **[!UICONTROL OK]**.

   >[!NOTE]
   >
   >Quando aggiungete un riferimento a un&#39;app Windows Phone, per selezionare `ADBMobile.winmd`, modificate il filtro file predefinito da File **** componente a **Tutti i file**.

1. In Esplora **[!UICONTROL soluzioni]**, fare clic con il pulsante destro del mouse su **[!UICONTROL Riferimenti]** e selezionare **[!UICONTROL Aggiungi riferimento]**.

   Ignora questo passaggio se hai anche un progetto C++ nella soluzione.

1. Nella scheda **Windows** a sinistra, selezionate **[!UICONTROL Estensioni]**, quindi selezionate e aggiungete **[!UICONTROL Microsoft Visual C++ 2013 Runtime Package for Windows]**.

1. Aggiungete la riga seguente alla classe:

   ```
   using ADBMobile;
   ```

1. Fai clic con il pulsante destro del mouse sul progetto e seleziona **[!UICONTROL Aggiungi]** > Elemento **** esistente.

1. Individuate il `ADBMobileConfig.json` file e fate clic su **[!UICONTROL Aggiungi]**.

1. Fare clic con il pulsante destro del mouse sul `ADBMobileConfig.json` file nella soluzione e selezionare **[!UICONTROL Proprietà]**.

1. Cambia Azione **[!UICONTROL di]** compilazione in **[!UICONTROL Contenuto]**.

## Add the library and config file to your project - C++ {#section_A95C1D18F6144F37ADC8F51590F3983E}

1. Avviare Visual Studio e aprire la soluzione.
1. In Esplora **[!UICONTROL soluzioni]**, fai clic con il pulsante destro del mouse sul progetto e seleziona **[!UICONTROL Aggiungi]** > **[!UICONTROL Riferimenti]**.

1. Selezionate la versione corretta della libreria, quindi aggiungete un riferimento al `ADBMobile.winmd` file associato.

   Per ulteriori informazioni, consultate la sezione *Selezionare la versione* corretta riportata di seguito.

1. Fai clic su **[!UICONTROL Aggiungi]**.

1. Nella finestra Gestione **** riferimenti verificare che `ADBMobile.winmd` sia selezionato e fare clic su **[!UICONTROL OK]**.

   >[!TIP]
   >
   >Quando aggiungete un riferimento a un&#39;app Windows Phone, per selezionare `ADBMobile.winmd`, modificate il filtro file predefinito da File **** componente a **Tutti i file**.

1. Aggiungete la riga seguente alla classe:

   ```
   using namespace ADMS::Measurement;
   ```

1. Fai clic con il pulsante destro del mouse sul progetto e seleziona **[!UICONTROL Aggiungi]** > Elemento **** esistente.

1. Individuate il `ADBMobileConfig.json` file e fate clic su **[!UICONTROL Aggiungi]**.

1. Fare clic con il pulsante destro del mouse sul `ADBMobileConfig.json` file nella soluzione e selezionare **[!UICONTROL Proprietà]**.

1. Nella scheda **[!UICONTROL Generale]** , modificate **[!UICONTROL Contenuto]** in **[!UICONTROL Sì]** e fate clic su **[!UICONTROL OK]**.

## Add the library and config file to your project - WinJS {#section_FF83113EBF4742AFA929F4AC28F92DB5}

1. Avviare Visual Studio e aprire la soluzione.
1. In Esplora **soluzioni**, fare clic con il pulsante destro del mouse su **[!UICONTROL Riferimenti]** e selezionare **[!UICONTROL Aggiungi riferimento]**.

   Per ulteriori informazioni, consultate *Selezionare la sezione Versione* corretta di seguito.

1. Selezionate la versione corretta della libreria, quindi individuate il `ADBMobile.winmd` file associato.

1. Fai clic su **[!UICONTROL Aggiungi]**.

1. Verificare che `ADBMobile.winmd` sia selezionato nella finestra Gestione **** riferimenti e fare clic su **[!UICONTROL OK]**.

   >[!TIP]
   >
   >Quando aggiungete un riferimento a un&#39;app Windows Phone, per selezionare `ADBMobile.winmd`, modificate il filtro file predefinito da File **** componente a **Tutti i file**.

1. In Esplora **[!UICONTROL soluzioni]**, fare clic con il pulsante destro del mouse su **[!UICONTROL Riferimenti]** e selezionare **[!UICONTROL Aggiungi riferimento]**.

   Ignora questo passaggio se hai anche un progetto C++ nella soluzione.

1. Nella scheda **[!UICONTROL Windows]** a sinistra, selezionate **[!UICONTROL Estensioni]** , quindi selezionate e aggiungete **[!UICONTROL Microsoft Visual C++ 2013 Runtime Package for Windows]**.

1. Fai clic con il pulsante destro del mouse sul progetto e seleziona **[!UICONTROL Aggiungi]** > Elemento **** esistente.

1. Individuate il `ADBMobileConfig.json` file e fate clic su **[!UICONTROL Aggiungi]**.

1. Fare clic con il pulsante destro del mouse sul `ADBMobileConfig.json]` file nella soluzione e selezionare **[!UICONTROL Proprietà]**.

1. Con Proprietà **** file selezionato, accertati che Azione **** pacchetto sia impostata su **[!UICONTROL Contenuto]**.

   Per i progetti JavaScript, il file è impostato su **[!UICONTROL Content]** per impostazione predefinita.

## Aggiornare il file di configurazione ADBMobileConfig.json {#section_0BC8CC0E4AAD4AC385FA0AEDC3C56AFE}

Il `ADBMobileConfig.json` file contiene impostazioni SDK globali e si trova nella directory principale del progetto dopo aver completato i passaggi descritti nella sezione *Aggiungi la libreria e il file di configurazione al progetto* . Se il `ADBMobileConfig.json` file non è stato preconfigurato da  Adobe Mobile Services, devi aggiornare alcuni valori per iniziare.

The following is an example of an `ADBMobileConfig.json` file:

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

* **Analytics**: `rsids` e `server`
* **Target**: `clientCode`
* **Gestione dell&#39;audience**: `server`

Per ulteriori dettagli, vedi [ADBMobileConfig.json config](/help/windows-appstore/c-configuration/methods.md).

## Eseguire il debug {#section_3A10376A60394A15BEE483323E0CD4AA}

Per abilitare il debug per l’SDK, devi chiamare `ADBMobile.Config.setDebugLogging(true);`.

Per le app C Sharp e JS, è necessario abilitare il debug del codice nativo eseguendo i passaggi seguenti (il debug del codice nativo è l&#39;impostazione predefinita per le app C++):

### C Nitido

Fare clic con il pulsante destro del mouse sul progetto, selezionare **[!UICONTROL Proprietà]** > scheda **** Debug. Nel menu a discesa Debugger, selezionate Solo **** nativo.

### JS

Fate clic con il pulsante destro del mouse sul progetto, selezionate **[!UICONTROL Proprietà]** > Proprietà **** configurazione > scheda **[!UICONTROL Debug]**. Cambia il tipo di debugger a discesa in Solo **** nativo.

Tutto qui. Ora sei pronto per implementare Analytics, Target e Gestione dell&#39;audience nell&#39;app Windows 8.1 Universal App Store.
