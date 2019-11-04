---
description: Queste informazioni sono utili per l'utilizzo di App Transport Security (ATS), un nuovo set di requisiti di sicurezza per iOS 9.
seo-description: Queste informazioni sono utili per l'utilizzo di App Transport Security (ATS), un nuovo set di requisiti di sicurezza per iOS 9.
seo-title: App Transport Security
solution: Experience Cloud,Analytics
title: App Transport Security
topic: Sviluppatore e implementazione
uuid: e9ee13cf-9802-492e-8b11-95f028e34e61
translation-type: ht
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# App Transport Security {#app-transport-security}

Queste informazioni sono utili per l'utilizzo di App Transport Security (ATS), un nuovo set di requisiti di sicurezza per iOS 9.

Con iOS 9, Apple ha introdotto App Transport Security, un set di requisiti conformi a best practice per connessioni sicure. Per ulteriori informazioni, consulta *NSAppTransportSecurity* in [Riferimento della chiave di elenco delle proprietà delle informazioni](https://developer.apple.com/library/prerelease/ios/technotes/App-Transport-Security-Technote/).

Affinché l'SDK di Adobe Mobile versione 4.7 o successiva funzioni direttamente con ATS, utilizza l'opzione di abilitazione SSL nella pagina Gestione impostazioni app. Per ulteriori informazioni, vedi [Gestire le impostazioni app](/help/using/c-manage-app-settings/c-manage-app-settings.md) o [file di configurazione ADBMobile JSON](/help/ios/configuration/json-config/json-config.md).

In Adobe Mobile Services, selezionando l'opzione **[!UICONTROL Usa HTTPS]** nella pagina Gestisci impostazioni app, tutti gli hit da Analytics, Audience Manager, Target e dai servizi Adobe Experience Platform vengono inviati tramite HTTPS.

In alternativa, puoi inserire in una whitelist i server seguenti:

| Prodotto | Istruzioni |
|--- |--- |
| Analytics | Per inserire il server Analytics in una whitelist, aggiungi il dominio del server di tracciamento al file info.plist come eccezione di dominio per ATS.  Il dominio del server di tracciamento si trova nella sezione Analytics del file `ADBMobileConfig.json` oppure nella sezione Analytics della pagina Gestione impostazioni app. |
| Audience Manager | Il dominio Audience Manager si trova nella proprietà server dell'oggetto audienceManager nel file `ADBMobileConfig.json`.  Se usi Audience Manager nell'app e SSL non è abilitato, aggiungi questo server come eccezione di dominio per ATS nel file `Info.plist`. |
| Target | Puoi inserire l'endpoint Target nel file info.plist come eccezione di dominio per ATS.  Per trovare l'endpoint Target, individua la proprietà `clientCodeproperty` nell'oggetto target nel file `ADBMobileConfig.json`. L'endpoint sarà `https://{clientCode}.tt.omtrdc.net`.  Ad esempio, se `clientCodeproperty` è `“myCompany”`, l'endpoint si presenterà come `https://myCompany.tt.omtrdc.net`. |
| Servizio Adobe Experience Platform Identity | Puoi anche aggiungere il server Experience Cloud come eccezione di dominio per ATS nel file `Info.plist`. Il dominio è `dpm.demdex.net`. |
| Mobile Services: Acquisizione da app mobile | Inserisci nella whitelist il server di acquisizione come eccezione di dominio per ATS nel file `Info.plist`. Il dominio è `c00.adobe.com`. |
| Mobile Services: Messaggi in-app | Se usi i messaggi in-app, potresti dover aggiungere delle voci nell'eccezione di dominio per ATS per ciascun URL non HTTPS che utilizzi. Questo elenco include le immagini in hosting ed eventuali URL incorporati nel messaggio HTML personalizzato a schermo intero.  Per ulteriori informazioni sulla configurazione delle eccezioni di dominio in un file `info.plist`, vedi la riga *NSExceptionDomains* nella *Tabella 2: chiavi principali del dizionario App Transport Security*. Vedi anche *Tabella 3: chiavi del dizionario dei domini di eccezione* in [Riferimento della chiave di elenco delle proprietà delle informazioni](https://developer.apple.com/library/prerelease/ios/technotes/App-Transport-Security-Technote/). |

>[!TIP]
>
>Queste considerazioni interessano le connessioni effettuate dall'SDK di Adobe Mobile e non hanno alcun impatto sulla visualizzazione web o su altre connessioni effettuate dall'app.

