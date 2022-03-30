---
description: Articolo di avvio rapido per sviluppatori
solution: Experience Cloud Services,Analytics
title: Guida rapida per sviluppatori
topic-fix: Developer and implementation
uuid: b368959b-d985-436e-8b3e-97e355a97951
exl-id: dd3262b1-e211-4758-9b4a-9dc7c4920c10
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '918'
ht-degree: 2%

---

# Guida rapida per sviluppatori {#developer-quick-start}

Per implementare l’SDK è necessario Visual Studio 2013 o versione successiva.

## Scaricare l&#39;SDK  {#section_99FE1A17A36D4A2C943939023CF6265C}

Dopo aver decompresso il [Download SDK](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases), avrai a disposizione una cartella separata per ogni architettura e combinazione di piattaforme supportate. Avrà anche un `ADBMobileConfig.json` file illustrato più avanti in questa guida.

## Seleziona la versione corretta {#section_E53C5AA7D5474824A89BB32C003865A1}

Diverso `.dll`/ `.winmd` vengono forniti file per ogni piattaforma di destinazione (Windows 8.1, Windows Phone 8.1) e architettura supportata (x86, x64, ARM). I file vengono separati in una struttura di cartelle come segue:

![](assets/folder-structure.png)

>[!IMPORTANT]
>
>Versione di `ADBMobile.winmd` non riflette la versione della libreria. La `.winmd` il file contiene solo metadati e come tale avrà un numero di versione `255.255.255.255` che è un comportamento accettato in base a Microsoft (vedi [Come si aggiungono informazioni di assembly per una DLL di componenti WinRT C++ / CX?](https://social.msdn.microsoft.com/Forums/windowsapps/en-US/6bcccaee-aa53-4770-bd5b-1205977f1ca7/how-do-i-add-assembly-information-for-a-winrt-c-cx-component-dll?forum=winappswithnativecode)). Per controllare la versione della libreria che stai utilizzando, controlla la versione del sottostante `ADBMobile.dll` file.

## Differenze di sintassi {#section_A02DE120B6D240F5AFFE7509755C4F14}

La libreria Windows 8.1 Universal App Store può essere utilizzata in diversi linguaggi di programmazione. Gli esempi contenuti in questa guida si trovano in WinJS (JavaScript) e potrebbero dover essere modificati se si utilizza un linguaggio diverso. Tieni presente che quando utilizzi metodi winmd da winJS (JavaScript), tutti i metodi presentano automaticamente la prima lettera minuscola.

La differenza principale tra le implementazioni è la struttura dati utilizzata per i dati contestuali.

Inoltre, quando utilizzi l&#39;SDK in un progetto WinJS, utilizza una stringa vuota ( `""` o `''`) anziché `null` per valori stringa vuoti.

## Aggiungi la libreria e il file di configurazione al tuo progetto - C Sharp {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. Avviare Visual Studio e aprire la soluzione.
1. In **Esplora soluzioni**, fai clic con il pulsante destro del mouse **[!UICONTROL Riferimenti]** e seleziona **[!UICONTROL Aggiungi riferimento]**.

1. Seleziona la versione corretta della libreria e individua il `ADBMobile.winmd` file.

   Per ulteriori informazioni, consulta la sezione *Seleziona la versione corretta* di seguito.

1. Fai clic su **[!UICONTROL Aggiungi]**.

1. Verifica che `ADBMobile.winmd` è selezionato in **[!UICONTROL Gestione riferimenti]** finestra e fai clic su **[!UICONTROL OK]**.

   >[!NOTE]
   >
   >Quando aggiungi un riferimento a un&#39;app Windows Phone, per selezionare `ADBMobile.winmd`, modifica il filtro file predefinito da **[!UICONTROL File componenti]** a **Tutti i file**.

1. In **[!UICONTROL Esplora soluzioni]**, fai clic con il pulsante destro del mouse **[!UICONTROL Riferimenti]** e seleziona **[!UICONTROL Aggiungi riferimento]**.

   Ignora questo passaggio se hai anche un progetto C++ nella tua soluzione.

1. In **Windows** a sinistra, seleziona **[!UICONTROL Estensioni]**, quindi seleziona e aggiungi **[!UICONTROL Pacchetto runtime di Microsoft Visual C++ 2013 per Windows]**.

1. Aggiungi la riga seguente alla classe:

   ```
   using ADBMobile;
   ```

1. Fai clic con il pulsante destro del mouse sul progetto e seleziona **[!UICONTROL Aggiungi]** > **[!UICONTROL Elemento esistente]**.

1. Sfoglia il tuo `ADBMobileConfig.json` e fai clic su **[!UICONTROL Aggiungi]**.

1. Fai clic con il pulsante destro del mouse sul pulsante `ADBMobileConfig.json` nella soluzione e seleziona **[!UICONTROL Proprietà]**.

1. Modifica **[!UICONTROL Azione di creazione]** a **[!UICONTROL Contenuto]**.

## Aggiungi la libreria e il file di configurazione al tuo progetto - C++ {#section_A95C1D18F6144F37ADC8F51590F3983E}

1. Avviare Visual Studio e aprire la soluzione.
1. In **[!UICONTROL Esplora soluzioni]**, fai clic con il pulsante destro del mouse sul progetto e seleziona **[!UICONTROL Aggiungi]** > **[!UICONTROL Riferimenti]**.

1. Seleziona la versione corretta della libreria e aggiungi un riferimento al `ADBMobile.winmd` file.

   Per ulteriori informazioni, consulta la sezione *Selezionare la versione corretta* di seguito.

1. Fai clic su **[!UICONTROL Aggiungi]**.

1. In **[!UICONTROL Gestione riferimenti]** finestra, verificare che `ADBMobile.winmd` è selezionato e fai clic su **[!UICONTROL OK]**.

   >[!TIP]
   >
   >Quando aggiungi un riferimento a un&#39;app Windows Phone, per selezionare `ADBMobile.winmd`, modifica il filtro file predefinito da **[!UICONTROL File componenti]** a **Tutti i file**.

1. Aggiungi la riga seguente alla classe:

   ```
   using namespace ADMS::Measurement;
   ```

1. Fai clic con il pulsante destro del mouse sul progetto e seleziona **[!UICONTROL Aggiungi]** > **[!UICONTROL Elemento esistente]**.

1. Sfoglia il `ADBMobileConfig.json` e fai clic su **[!UICONTROL Aggiungi]**.

1. Fai clic con il pulsante destro del mouse sul pulsante `ADBMobileConfig.json` nella soluzione e seleziona **[!UICONTROL Proprietà]**.

1. Sulla **[!UICONTROL Generale]** scheda, modifica **[!UICONTROL Contenuto]** a **[!UICONTROL Sì]** e fai clic su **[!UICONTROL OK]**.

## Aggiungi la libreria e il file di configurazione al tuo progetto - WinJS {#section_FF83113EBF4742AFA929F4AC28F92DB5}

1. Avviare Visual Studio e aprire la soluzione.
1. In **Esplora soluzioni**, fai clic con il pulsante destro del mouse **[!UICONTROL Riferimenti]** e seleziona **[!UICONTROL Aggiungi riferimento]**.

   Per ulteriori informazioni, consulta *Selezionare la versione corretta* di seguito.

1. Seleziona la versione corretta della libreria, quindi individua il `ADBMobile.winmd` file.

1. Fai clic su **[!UICONTROL Aggiungi]**.

1. Verifica che `ADBMobile.winmd` è selezionato nella **[!UICONTROL Gestione riferimenti]** finestra e fai clic su **[!UICONTROL OK]**.

   >[!TIP]
   >
   >Quando aggiungi un riferimento a un&#39;app Windows Phone, per selezionare `ADBMobile.winmd`, modifica il filtro file predefinito da **[!UICONTROL File componenti]** a **Tutti i file**.

1. In **[!UICONTROL Esplora soluzioni]**, fai clic con il pulsante destro del mouse **[!UICONTROL Riferimenti]** e seleziona **[!UICONTROL Aggiungi riferimento]**.

   Ignora questo passaggio se hai anche un progetto C++ nella tua soluzione.

1. In **[!UICONTROL Windows]** a sinistra, seleziona **[!UICONTROL Estensioni]** e seleziona e aggiungi **[!UICONTROL Pacchetto runtime di Microsoft Visual C++ 2013 per Windows]**.

1. Fai clic con il pulsante destro del mouse sul progetto e seleziona **[!UICONTROL Aggiungi]** > **[!UICONTROL Elemento esistente]**.

1. Sfoglia il `ADBMobileConfig.json` e fai clic su **[!UICONTROL Aggiungi]**.

1. Fai clic con il pulsante destro del mouse sul pulsante `ADBMobileConfig.json]` nella soluzione e seleziona **[!UICONTROL Proprietà]**.

1. Con **[!UICONTROL Proprietà file]** selezionato, assicurati **[!UICONTROL Azione pacchetto]** è impostato su **[!UICONTROL Contenuto]**.

   Per i progetti JavaScript, il file è impostato su **[!UICONTROL Contenuto]** per impostazione predefinita.

## Aggiornare il file di configurazione ADBMobileConfig.json {#section_0BC8CC0E4AAD4AC385FA0AEDC3C56AFE}

La `ADBMobileConfig.json` Il file contiene le impostazioni SDK globali e si trova nella directory principale del progetto dopo aver completato i passaggi descritti in *Aggiungere la libreria e il file di configurazione al progetto* sezione . Se `ADBMobileConfig.json` file non preconfigurato da Adobe Mobile Services. Per iniziare, devi aggiornare alcuni valori.

Di seguito è riportato un esempio di `ADBMobileConfig.json` file:

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

* **Analytics**: `rsids` e `server`
* **Target**: `clientCode`
* **Gestione dell&#39;audience**: `server`

Per ulteriori dettagli, consulta [Configurazione di ADBMobileConfig.json](/help/windows-appstore/c-configuration/methods.md).

## Eseguire il debug di {#section_3A10376A60394A15BEE483323E0CD4AA}

Per abilitare il debug per l&#39;SDK, devi invocare `ADBMobile.Config.setDebugLogging(true);`.

Per le app C Sharp e JS, devi abilitare il debug del codice nativo completando i seguenti passaggi (il debug del codice nativo è l&#39;impostazione predefinita per le app C++):

### C Sharp

Fai clic con il pulsante destro del mouse sul progetto e seleziona **[!UICONTROL Proprietà]** > **[!UICONTROL Scheda Debug]**. Nel menu a discesa Debugger, seleziona **[!UICONTROL Solo nativo]**.

### JS

Fai clic con il pulsante destro del mouse sul progetto e seleziona  **[!UICONTROL Proprietà]** > **[!UICONTROL Proprietà di configurazione]** > **[!UICONTROL Scheda Debug]**. Cambia l’elenco a discesa del tipo di debugger in **Solo nativo**.

Tutto qui. Ora puoi implementare Analytics, Target e Gestione dell&#39;audience nella tua app Windows 8.1 Universal App Store.
