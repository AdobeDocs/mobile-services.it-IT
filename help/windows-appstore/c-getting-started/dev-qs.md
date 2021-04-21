---
description: Articolo di avvio rapido per sviluppatori
solution: Experience Cloud,Analytics
title: Guida rapida per sviluppatori
topic-fix: Developer and implementation
uuid: b368959b-d985-436e-8b3e-97e355a97951
exl-id: dd3262b1-e211-4758-9b4a-9dc7c4920c10
translation-type: tm+mt
source-git-commit: b9ee49ba26d4726b1f97ef36f5c2e9923361b1ee
workflow-type: tm+mt
source-wordcount: '918'
ht-degree: 2%

---

# Guida rapida per sviluppatori {#developer-quick-start}

Per implementare l’SDK è necessario Visual Studio 2013 o versione successiva.

## Scaricare l&#39;SDK  {#section_99FE1A17A36D4A2C943939023CF6265C}

Dopo aver decompresso il [download dell&#39;SDK](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases), avrai a disposizione una cartella separata per ogni architettura e combinazione di piattaforme supportate. Disporrai anche di un file `ADBMobileConfig.json` che viene spiegato più avanti in questa guida.

## Seleziona la versione corretta {#section_E53C5AA7D5474824A89BB32C003865A1}

Vengono forniti file `.dll`/ `.winmd` diversi per ciascuna piattaforma di destinazione (Windows 8.1, Windows Phone 8.1) e per l’architettura supportata (x86, x64, ARM). I file vengono separati in una struttura di cartelle come segue:

![](assets/folder-structure.png)

>[!IMPORTANT]
>
>La versione di `ADBMobile.winmd` non riflette la versione della libreria. Il file `.winmd` contiene solo metadati, e come tale avrà un numero di versione di `255.255.255.255` che è il comportamento accettato in base a Microsoft (vedere [Come posso aggiungere informazioni di assembly per una DLL di componenti WinRT C++ / CX?](https://social.msdn.microsoft.com/Forums/windowsapps/en-US/6bcccaee-aa53-4770-bd5b-1205977f1ca7/how-do-i-add-assembly-information-for-a-winrt-c-cx-component-dll?forum=winappswithnativecode)). Per controllare la versione della libreria che stai utilizzando, controlla la versione del file `ADBMobile.dll` sottostante.

## Differenze di sintassi {#section_A02DE120B6D240F5AFFE7509755C4F14}

La libreria Windows 8.1 Universal App Store può essere utilizzata in diversi linguaggi di programmazione. Gli esempi contenuti in questa guida si trovano in WinJS (JavaScript) e potrebbero dover essere modificati se si utilizza un linguaggio diverso. Tieni presente che quando utilizzi metodi winmd da winJS (JavaScript), tutti i metodi presentano automaticamente la prima lettera minuscola.

La differenza principale tra le implementazioni è la struttura dati utilizzata per i dati contestuali.

Inoltre, quando utilizzi l&#39;SDK in un progetto WinJS, utilizza una stringa vuota ( `""` o `''`) invece di `null` per valori stringa vuoti.

## Aggiungi la libreria e il file di configurazione al tuo progetto - C Sharp {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. Avviare Visual Studio e aprire la soluzione.
1. In **Esplora soluzioni**, fai clic con il pulsante destro del mouse su **[!UICONTROL Riferimenti]** e seleziona **[!UICONTROL Aggiungi riferimento]**.

1. Seleziona la versione corretta della libreria e individua il file `ADBMobile.winmd` associato.

   Per ulteriori informazioni, consulta la sezione *Selezionare la versione corretta* di seguito.

1. Fai clic su **[!UICONTROL Aggiungi]**.

1. Verifica che `ADBMobile.winmd` sia selezionato nella finestra **[!UICONTROL Gestione riferimenti]** e fai clic su **[!UICONTROL OK]**.

   >[!NOTE]
   >
   >Quando aggiungi un riferimento a un&#39;app Windows Phone, per selezionare `ADBMobile.winmd`, modifica il filtro file predefinito da **[!UICONTROL File componente]** a **Tutti i file**.

1. In **[!UICONTROL Esplora soluzioni]**, fai clic con il pulsante destro del mouse su **[!UICONTROL Riferimenti]** e seleziona **[!UICONTROL Aggiungi riferimento]**.

   Ignora questo passaggio se hai anche un progetto C++ nella tua soluzione.

1. Nella scheda **Windows** a sinistra, selezionare **[!UICONTROL Estensioni]**, quindi selezionare e aggiungere **[!UICONTROL Microsoft Visual C++ 2013 Runtime Package for Windows]**.

1. Aggiungi la riga seguente alla classe:

   ```
   using ADBMobile;
   ```

1. Fai clic con il pulsante destro del mouse sul progetto e seleziona **[!UICONTROL Aggiungi]** > **[!UICONTROL Elemento esistente]**.

1. Individua il file `ADBMobileConfig.json` e fai clic su **[!UICONTROL Aggiungi]**.

1. Fai clic con il pulsante destro del mouse sul file `ADBMobileConfig.json` nella soluzione e seleziona **[!UICONTROL Proprietà]**.

1. Cambia **[!UICONTROL Crea azione]** in **[!UICONTROL Contenuto]**.

## Aggiungi la libreria e il file di configurazione al tuo progetto - C++ {#section_A95C1D18F6144F37ADC8F51590F3983E}

1. Avviare Visual Studio e aprire la soluzione.
1. In **[!UICONTROL Esplora soluzioni]**, fai clic con il pulsante destro del mouse sul progetto e seleziona **[!UICONTROL Aggiungi]** > **[!UICONTROL Riferimenti]**.

1. Seleziona la versione corretta della libreria, quindi aggiungi un riferimento al file `ADBMobile.winmd` associato.

   Per ulteriori informazioni, consulta la sezione *Selezionare la versione corretta* di seguito.

1. Fai clic su **[!UICONTROL Aggiungi]**.

1. Nella finestra **[!UICONTROL Gestione riferimenti]**, verifica che sia selezionato `ADBMobile.winmd` e fai clic su **[!UICONTROL OK]**.

   >[!TIP]
   >
   >Quando aggiungi un riferimento a un&#39;app Windows Phone, per selezionare `ADBMobile.winmd`, modifica il filtro file predefinito da **[!UICONTROL File componente]** a **Tutti i file**.

1. Aggiungi la riga seguente alla classe:

   ```
   using namespace ADMS::Measurement;
   ```

1. Fai clic con il pulsante destro del mouse sul progetto e seleziona **[!UICONTROL Aggiungi]** > **[!UICONTROL Elemento esistente]**.

1. Individua il file `ADBMobileConfig.json` e fai clic su **[!UICONTROL Aggiungi]**.

1. Fai clic con il pulsante destro del mouse sul file `ADBMobileConfig.json` nella soluzione e seleziona **[!UICONTROL Proprietà]**.

1. Nella scheda **[!UICONTROL Generale]**, cambia **[!UICONTROL Contenuto]** in **[!UICONTROL Sì]** e fai clic su **[!UICONTROL OK]**.

## Aggiungi la libreria e il file di configurazione al tuo progetto - WinJS {#section_FF83113EBF4742AFA929F4AC28F92DB5}

1. Avviare Visual Studio e aprire la soluzione.
1. In **Esplora soluzioni**, fai clic con il pulsante destro del mouse su **[!UICONTROL Riferimenti]** e seleziona **[!UICONTROL Aggiungi riferimento]**.

   Per ulteriori informazioni, consulta la sezione *Selezionare la versione corretta* di seguito.

1. Seleziona la versione corretta della libreria, quindi individua il file `ADBMobile.winmd` associato.

1. Fai clic su **[!UICONTROL Aggiungi]**.

1. Verifica che `ADBMobile.winmd` sia selezionato nella finestra **[!UICONTROL Gestione riferimenti]** e fai clic su **[!UICONTROL OK]**.

   >[!TIP]
   >
   >Quando aggiungi un riferimento a un&#39;app Windows Phone, per selezionare `ADBMobile.winmd`, modifica il filtro file predefinito da **[!UICONTROL File componente]** a **Tutti i file**.

1. In **[!UICONTROL Esplora soluzioni]**, fai clic con il pulsante destro del mouse su **[!UICONTROL Riferimenti]** e seleziona **[!UICONTROL Aggiungi riferimento]**.

   Ignora questo passaggio se hai anche un progetto C++ nella tua soluzione.

1. Nella scheda **[!UICONTROL Windows]** a sinistra, selezionare **[!UICONTROL Estensioni]**, quindi selezionare e aggiungere **[!UICONTROL Microsoft Visual C++ 2013 Runtime Package for Windows]**.

1. Fai clic con il pulsante destro del mouse sul progetto e seleziona **[!UICONTROL Aggiungi]** > **[!UICONTROL Elemento esistente]**.

1. Individua il file `ADBMobileConfig.json` e fai clic su **[!UICONTROL Aggiungi]**.

1. Fai clic con il pulsante destro del mouse sul file `ADBMobileConfig.json]` nella soluzione e seleziona **[!UICONTROL Proprietà]**.

1. Con **[!UICONTROL Proprietà file]** selezionato, assicurati che **[!UICONTROL Azione pacchetto]** sia impostato su **[!UICONTROL Contenuto]**.

   Per i progetti JavaScript, il file è impostato su **[!UICONTROL Contenuto]** per impostazione predefinita.

## Aggiornare il file di configurazione ADBMobileConfig.json {#section_0BC8CC0E4AAD4AC385FA0AEDC3C56AFE}

Il file `ADBMobileConfig.json` contiene impostazioni SDK globali e si trova nella directory principale del progetto dopo aver completato i passaggi descritti nella sezione *Aggiungi la libreria e il file di configurazione al progetto* . Se il file `ADBMobileConfig.json` non è stato preconfigurato da Adobe Mobile Services, è necessario aggiornare alcuni valori per iniziare.

Di seguito è riportato un esempio di file `ADBMobileConfig.json` :

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

* **Analytics**:  `rsids` e  `server`
* **Target**: `clientCode`
* **Gestione dell&#39;audience**: `server`

Per ulteriori dettagli, consulta [Configurazione ADBMobileConfig.json](/help/windows-appstore/c-configuration/methods.md).

## Eseguire il debug di {#section_3A10376A60394A15BEE483323E0CD4AA}

Per abilitare il debug per l&#39;SDK, devi chiamare `ADBMobile.Config.setDebugLogging(true);`.

Per le app C Sharp e JS, devi abilitare il debug del codice nativo completando i seguenti passaggi (il debug del codice nativo è l&#39;impostazione predefinita per le app C++):

### C Sharp

Fai clic con il pulsante destro del mouse sul progetto, seleziona **[!UICONTROL Proprietà]** > **[!UICONTROL Scheda Debug]**. Nel menu a discesa Debugger, seleziona **[!UICONTROL Solo nativo]**.

### JS

Fai clic con il pulsante destro del mouse sul progetto, seleziona **[!UICONTROL Proprietà]** > **[!UICONTROL Proprietà di configurazione]** > **[!UICONTROL Scheda Debug]**. Cambia il menu a discesa del tipo di debugger in **Solo nativo**.

Tutto qui. Ora sei pronto per implementare Analytics, Target e Gestione dell&#39;audience nella tua app Windows 8.1 Universal App Store.
