---
description: Queste informazioni sono utili per l'utilizzo di App Transport Security (ATS), un nuovo set di requisiti di sicurezza per iOS 9.
seo-description: Queste informazioni sono utili per l'utilizzo di App Transport Security (ATS), un nuovo set di requisiti di sicurezza per iOS 9.
seo-title: App Transport Security
solution: Marketing Cloud, Analytics
title: App Transport Security
topic: Sviluppatore e implementazione
uuid: e 9 ee 13 cf -9802-492 e -8 b 11-95 f 028 e 34 e 61
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# App Transport Security {#app-transport-security}

Queste informazioni sono utili per l'utilizzo di App Transport Security (ATS), un nuovo set di requisiti di sicurezza per iOS 9.

Con iOS 9, Apple ha introdotto App Transport Security, un set di requisiti conformi a best practice per connessioni sicure. Per ulteriori informazioni, vedi *nsapptransportsecurity* in [Information Property List Key Reference](https://developer.apple.com/library/prerelease/ios/technotes/App-Transport-Security-Technote/).

Affinché l'SDK di Adobe Mobile versione 4.7 o successiva funzioni direttamente con ATS, utilizza l'opzione di abilitazione SSL nella pagina Gestione impostazioni app. Per ulteriori informazioni, vedi [Gestione impostazioni app](/help/using/c-manage-app-settings/c-manage-app-settings.md) o [Configurazione adbmobile JSON](/help/ios/configuration/json-config/json-config.md).

In Adobe Mobile Services, by selecting the **[!UICONTROL Use HTTPS]** option in the Manage App Settings page, all hits from Analytics, Audience Manager, Target, and Adobe Experience Platform Identity Services are sent via HTTPS.

In alternativa, puoi inserire in una whitelist i server seguenti:

| Prodotto | Istruzioni |
|--- |--- |
| Analytics | Per inserire il server Analytics in una whitelist, aggiungi il dominio del server di tracciamento al file info.plist come eccezione di dominio per ATS.  Il dominio del server di tracciamento si trova nella sezione Analytics del file `ADBMobileConfig.json` oppure nella sezione Analytics della pagina Gestione impostazioni app. |
| Audience Manager | Il dominio Audience Manager si trova nella proprietà server dell'oggetto audienceManager nel file `ADBMobileConfig.json`.  Se usi Audience Manager nell'app e SSL non è abilitato, aggiungi questo server come eccezione di dominio per ATS nel file `Info.plist`. |
| Target | Puoi inserire l'endpoint Target nel file info.plist come eccezione di dominio per ATS.  Per trovare l'endpoint Target, individua la proprietà `clientCodeproperty` nell'oggetto target nel file `ADBMobileConfig.json`. Your endpoint will be `https://{clientCode}.tt.omtrdc.net`.  For example, if your `clientCodeproperty` is `“myCompany”`, your endpoint will be `https://myCompany.tt.omtrdc.net`. |
| Servizio identità Adobe Experience Platform | Puoi anche aggiungere il server Experience Cloud come eccezione di dominio per ATS nel file `Info.plist`. This domain is `dpm.demdex.net`. |
| Mobile Services: Acquisizione da app mobile | Inserisci nella whitelist il server di acquisizione come eccezione di dominio per ATS nel file `Info.plist`. This domain is `c00.adobe.com`. |
| Mobile Services: Messaggi in-app | Se usi i messaggi in-app, potresti dover aggiungere delle voci nell'eccezione di dominio per ATS per ciascun URL non HTTPS che utilizzi. Questo elenco include le immagini in hosting ed eventuali URL incorporati nel messaggio HTML personalizzato a schermo intero.  Per maggiori dettagli sull'impostazione del dominio exceptions in un `info.plist` file, vedi la *riga nsexceptiondomains* nella *Tabella 2: Chiavi principali dizionario di App Transport Security*. Consultate *anche le chiavi* dizionario dei domini delle eccezioni 3 di Exception in [Information Property List Key Reference](https://developer.apple.com/library/prerelease/ios/technotes/App-Transport-Security-Technote/). |

>[!TIP]
>
>Queste considerazioni interessano le connessioni effettuate dall'SDK di Adobe Mobile e non hanno alcun impatto sulla visualizzazione Web o su altre connessioni effettuate dall'app.
