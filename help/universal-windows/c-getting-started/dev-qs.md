---
description: 'null'
seo-description: 'null'
seo-title: Guida rapida per sviluppatori
solution: Experience Cloud,Analytics
title: Guida rapida per sviluppatori
topic-fix: Developer and implementation
uuid: 11c06fcf-d5e4-4858-9a4e-3bf66cdd2a48
exl-id: 28fc2a96-907e-41fc-a798-3e8d43fc7616
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '842'
ht-degree: 4%

---

# Guida rapida per sviluppatori{#developer-quick-start}

Seguono alcune informazioni su come implementare la libreria della piattaforma UWP (Universal Windows Platform).

>[!IMPORTANT]
>
>Per implementare l&#39;SDK, è necessario Visual Studio 2013 o versione successiva.

## Scaricare l&#39;SDK  {#section_99FE1A17A36D4A2C943939023CF6265C}

Dopo aver decompresso il file [Download SDK](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases), avrai a disposizione una cartella separata per ogni architettura e combinazione di piattaforme supportate. Avrai anche un file `ADBMobileConfig.json` . Per ulteriori informazioni su questo file, consulta [File di configurazione ADBMobileConfig.json](/help/universal-windows/c-configuration/c.json.md).

## Seleziona la versione corretta {#section_E53C5AA7D5474824A89BB32C003865A1}

Per ogni architettura supportata vengono forniti file `.dll/.winmd` diversi (x86, x64, ARM).

>[!IMPORTANT]
>
>La versione di `ADBMobile.winmd` non riflette la versione della libreria. Il file `.winmd` contiene solo metadati e ha un numero di versione di `255.255.255.255`, che è accettato il comportamento secondo Microsoft. Per ulteriori informazioni, vedere [Come aggiungere informazioni sull&#39;assembly per una DLL di componenti WinRT C++ / CX?](https://social.msdn.microsoft.com/Forums/windowsapps/en-US/6bcccaee-aa53-4770-bd5b-1205977f1ca7/how-do-i-add-assembly-information-for-a-winrt-c-cx-component-dll?forum=winappswithnativecode). Per controllare la versione della libreria che stai utilizzando, controlla la versione del file `ADBMobile.dll` sottostante.

## Differenze di sintassi {#section_A02DE120B6D240F5AFFE7509755C4F14}

La libreria della piattaforma UWP (Universal Windows Platform) può essere utilizzata in diversi linguaggi di programmazione. Gli esempi contenuti in questa guida sono in WinJS (JavaScript). Se utilizzi un linguaggio diverso, potrebbe essere necessario modificarlo. Quando utilizzi metodi winmd da winJS, la prima lettera viene impostata automaticamente come minuscola per tutti i metodi.

La differenza principale tra le implementazioni è la struttura dati utilizzata per i dati contestuali. Inoltre, quando utilizzi l&#39;SDK in un progetto WinJS, utilizza una stringa vuota ( `""` o `''`) invece di `null` per valori stringa vuoti.

## Aggiungi la libreria e il file di configurazione al tuo progetto - C# {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. Avviare Visual Studio e aprire la soluzione.
1. In **[!UICONTROL Esplora soluzioni]**, fai clic con il pulsante destro del mouse su **[!UICONTROL Riferimenti]** e seleziona **[!UICONTROL Aggiungi riferimento]**.

1. Seleziona la versione corretta della libreria e individua il file ADBMobile.winmd associato.

   Per ulteriori informazioni, consulta la sezione *Selezionare la versione corretta* in questa pagina.

1. Fai clic su **Aggiungi**.

1. Verifica che il file ADBMobile.winmd sia selezionato nella finestra **[!UICONTROL Gestione riferimenti]** e fai clic su **[!UICONTROL OK]**.

1. In **[!UICONTROL Esplora soluzioni]**, fai clic con il pulsante destro del mouse su **[!UICONTROL Riferimenti]** e seleziona **[!UICONTROL Aggiungi riferimento]**.

   Se hai anche un progetto C++ nella tua soluzione, salta questo passaggio.

1. Nella scheda **[!UICONTROL Windows]** a sinistra, selezionare **[!UICONTROL Estensioni]**, selezionare e aggiungere **[!UICONTROL Visual C++ 2015 Runtime per le app della piattaforma UWP]**.

1. Aggiungi la riga seguente alla classe:

   ```csharp
   using ADBMobile;
   ```

1. Fai clic con il pulsante destro del mouse sul progetto e fai clic su **[!UICONTROL Aggiungi]** > **[!UICONTROL Elemento esistente]**.

1. Individua il file `ADBMobileConfig.json` e fai clic su **[!UICONTROL Aggiungi]**.

1. Fai clic con il pulsante destro del mouse sul file `ADBMobileConfig.json` nella soluzione e seleziona **[!UICONTROL Proprietà]**.

1. Cambia **[!UICONTROL Crea azione]** in **[!UICONTROL Contenuto]**.

## Aggiungi la libreria e il file di configurazione al tuo progetto - C++ {#section_A95C1D18F6144F37ADC8F51590F3983E}

1. Avviare Visual Studio e aprire la soluzione.
1. In **[!UICONTROL Esplora soluzioni]**, fai clic con il pulsante destro del mouse sul progetto e seleziona **[!UICONTROL Aggiungi]** > **[!UICONTROL Riferimenti]**.

1. Seleziona la versione corretta della libreria e aggiungi un riferimento al file ADBMobile.winmd associato.

   Per ulteriori informazioni, consulta la sezione *Selezionare la versione corretta* in questa pagina.

1. Fai clic su **[!UICONTROL Aggiungi]**.

1. Verifica che `ADBMobile.winmd` sia selezionato nella finestra **[!UICONTROL Gestione riferimenti]** e fai clic su **[!UICONTROL OK]**.

1. Aggiungi la riga seguente alla classe:

   ```c++
   using namespace ADBMobile;
   ```

1. Fai clic con il pulsante destro del mouse sul progetto e seleziona **[!UICONTROL Aggiungi]** > **[!UICONTROL Elemento esistente]**.

1. Individua il file `ADBMobileConfig.json` e fai clic su **[!UICONTROL Aggiungi]**.

1. Fai clic con il pulsante destro del mouse sul file `ADBMobileConfig.json` nella soluzione e seleziona **[!UICONTROL Proprietà]**.

1. Nella scheda **[!UICONTROL Generale]**, cambia **[!UICONTROL Contenuto]** in **[!UICONTROL Sì]** e fai clic su **[!UICONTROL OK]**.

## Aggiungi la libreria e il file di configurazione al tuo progetto - WinJS {#section_FF83113EBF4742AFA929F4AC28F92DB5}

1. Avviare Visual Studio e aprire la soluzione.

1. In **[!UICONTROL Esplora soluzioni]**, fai clic con il pulsante destro del mouse su **[!UICONTROL Riferimenti]** e seleziona **[!UICONTROL Aggiungi riferimento]**.

1. Seleziona la versione corretta della libreria e individua il file ADBMobile.winmd associato.

1. Fai clic su **[!UICONTROL Aggiungi]**.

1. Verifica che il file ADBMobile.winmd sia selezionato nella finestra **[!UICONTROL Gestione riferimenti]** e fai clic su **[!UICONTROL OK]**.

1. In **[!UICONTROL Esplora soluzioni]**, fai clic con il pulsante destro del mouse su **[!UICONTROL Riferimenti]** e seleziona **[!UICONTROL Aggiungi riferimento]**.

   Se hai anche un progetto C++ nella tua soluzione, salta questo passaggio.

1. Nella scheda **[!UICONTROL Windows]** a sinistra, selezionare **[!UICONTROL Estensioni]**, quindi selezionare e aggiungere **[!UICONTROL Visual C++ 2015 Runtime per le app della piattaforma UWP]**.

1. Fai clic con il pulsante destro del mouse sul progetto e seleziona **[!UICONTROL Aggiungi]** > **[!UICONTROL Elemento esistente]**.

1. Individua il file `ADBMobileConfig.json` e fai clic su **[!UICONTROL Aggiungi]**.

1. Fai clic con il pulsante destro del mouse sul file `ADBMobileConfig.json` nella soluzione e seleziona **[!UICONTROL Proprietà]**.

1. Con **[!UICONTROL Proprietà file]** selezionato, assicurati che **[!UICONTROL Azione pacchetto]** sia impostato su **[!UICONTROL Contenuto]**.

   Per i progetti JavaScript, il file è impostato su Contenuto per impostazione predefinita.

## Aggiorna il file di configurazione ADBMobileConfig.json {#section_0BC8CC0E4AAD4AC385FA0AEDC3C56AFE}

Il file `ADBMobileConfig.json` contiene impostazioni SDK globali e si trova nella directory principale del progetto dopo aver completato i passaggi descritti nella sezione *Aggiungi la libreria e il file di configurazione al progetto* . Se il file `ADBMobileConfig.json` non è stato preconfigurato da Adobe Mobile Services, è necessario aggiornare alcuni valori per iniziare.

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

Come minimo, aggiorna i seguenti valori per le soluzioni che stai utilizzando:

* **Adobe Analytics**:  `rsids` e  `server`

* **Adobe Target**: `clientCode`

* **Adobe Audience Manager**: `server`

Per ulteriori informazioni, consulta [Metodi SDK](/help/universal-windows/c-configuration/methods.md).

## Eseguire il debug di {#section_3A10376A60394A15BEE483323E0CD4AA}

Per abilitare il debug per l&#39;SDK, chiama `ADBMobile.Config.setDebugLogging(true);`.

Per le app C Sharp e JavaScript, è necessario abilitare il debug del codice nativo completando i seguenti passaggi (il debug del codice nativo è l&#39;impostazione predefinita per le app C++):

### C Sharp

1. Fai clic con il pulsante destro del mouse sul progetto, fai clic su **[!UICONTROL Proprietà]** > **[!UICONTROL Scheda Debug]**.

1. Cambia il menu a discesa del tipo di debugger in **Solo nativo**.

### JavaScript

1. Fai clic con il pulsante destro del mouse sul progetto, fai clic su **[!UICONTROL Proprietà]** > **[!UICONTROL Proprietà di configurazione]** > **[!UICONTROL Scheda Debug]**.

1. Cambia il menu a discesa del tipo di debugger in **[!UICONTROL Solo nativo]**.

Tutto qui. Ora sei pronto per implementare Analytics, Target e Gestione dell’audience nella tua app della piattaforma UWP (Universal Windows Platform).
