---
description: Queste informazioni sono utili per l'utilizzo di App Transport Security (ATS), un nuovo set di requisiti di sicurezza per iOS 9.
solution: Experience Cloud,Analytics
title: App Transport Security
topic-fix: Developer and implementation
uuid: e9ee13cf-9802-492e-8b11-95f028e34e61
exl-id: 2fe94e76-06d6-4ad1-95ba-193ae3df4d58
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 100%

---

# App Transport Security {#app-transport-security}

Queste informazioni sono utili per l&#39;utilizzo di App Transport Security (ATS), un nuovo set di requisiti di sicurezza per iOS 9.

Con iOS 9, Apple ha introdotto App Transport Security, un set di requisiti conformi a best practice per connessioni sicure. Per ulteriori informazioni, consulta *NSAppTransportSecurity* in [Riferimento della chiave di elenco delle proprietà delle informazioni](https://developer.apple.com/library/prerelease/ios/technotes/App-Transport-Security-Technote/).

Affinché l&#39;SDK di Adobe Mobile versione 4.7 o successiva funzioni direttamente con ATS, utilizza l&#39;opzione di abilitazione SSL nella pagina Gestione impostazioni app. Per ulteriori informazioni, vedi [Gestire le impostazioni app](/help/using/c-manage-app-settings/c-manage-app-settings.md) o [File di configurazione ADBMobile JSON](/help/ios/configuration/json-config/json-config.md).

In Adobe Mobile Services, selezionando l’opzione **[!UICONTROL Usa HTTPS]** nella pagina Gestione impostazioni app, tutti gli hit da Analytics, Audience Manager, Target e Identity Service di Adobe Experience Platform vengono inviati tramite HTTPS.

In alternativa, è possibile inserire i server seguenti nell’elenco dei server consentiti:

| Prodotto | Istruzioni |
|--- |--- |
| Analytics | Per dare il consenso al server Analytics, aggiungi il dominio del server di tracciamento al file info.plist come dominio di eccezione per ATS.  Il dominio del server di tracciamento si trova nella sezione Analytics del file `ADBMobileConfig.json` oppure nella sezione Analytics della pagina Gestione impostazioni app. |
| Audience Manager | Il dominio Audience Manager si trova nella proprietà server dell&#39;oggetto audienceManager nel file `ADBMobileConfig.json`.  Se usi Audience Manager nell&#39;app e SSL non è abilitato, aggiungi questo server come eccezione di dominio per ATS nel file `Info.plist`. |
| Target | Puoi inserire l&#39;endpoint Target nel file info.plist come eccezione di dominio per ATS.  Per trovare l&#39;endpoint Target, individua la proprietà `clientCodeproperty` nell&#39;oggetto target nel file `ADBMobileConfig.json`. L&#39;endpoint sarà `https://{clientCode}.tt.omtrdc.net`.  Ad esempio, se `clientCodeproperty` è `"myCompany"`, l&#39;endpoint si presenterà come `https://myCompany.tt.omtrdc.net`. |
| Servizio Adobe Experience Platform Identity | Puoi anche aggiungere il server Experience Cloud come eccezione di dominio per ATS nel file `Info.plist`. Il dominio è `dpm.demdex.net`. |
| Mobile Services: Acquisizione da app mobile | Dai il consenso al server di acquisizione come eccezione di dominio per ATS nel file `Info.plist`. Il dominio è `c00.adobe.com`. |
| Mobile Services: messaggi in-app | Se utilizzi i messaggi in-app, potresti dover aggiungere voci nell’eccezione di dominio per ATS per ogni URL utilizzato che non sia HTTPS. Questo elenco include le immagini in hosting ed eventuali URL incorporati nel messaggio HTML personalizzato a schermo intero.  Per ulteriori informazioni sulla configurazione delle eccezioni di dominio in un file `info.plist`, vedi la riga *NSExceptionDomains* nella *Tabella 2: chiavi principali del dizionario App Transport Security*. Vedi anche *Tabella 3: chiavi del dizionario dei domini di eccezione* in [Riferimento della chiave di elenco delle proprietà delle informazioni](https://developer.apple.com/library/prerelease/ios/technotes/App-Transport-Security-Technote/). |

>[!TIP]
>
>Queste considerazioni interessano le connessioni effettuate dall&#39;SDK di Adobe Mobile e non hanno alcun impatto sulla visualizzazione web o su altre connessioni effettuate dall&#39;app.
