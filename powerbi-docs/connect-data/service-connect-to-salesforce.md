---
title: Opret forbindelse til Salesforce med Power BI
description: Salesforce til Power BI
author: paulinbar
ms.author: painbar
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: how-to
ms.date: 05/30/2019
LocalizationGroup: Connect to services
ms.openlocfilehash: f43d60a22d436cc0be5aa57bc9b383d535dbfc0d
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96392881"
---
# <a name="connect-to-salesforce-with-power-bi"></a>Opret forbindelse til Salesforce med Power BI
Med Power BI kan du kan nemt oprette forbindelse til din konto på Salesforce.com. Med denne forbindelse kan du hente dine Salesforce-data og få et dashboard og rapporter automatisk.

Læs mere om [integrering af Salesforce](https://powerbi.microsoft.com/integrations/salesforce) med Power BI.

## <a name="how-to-connect"></a>Sådan opretter du forbindelse
1. Vælg **Hent data** nederst i navigationsruden i Power BI.
   
   ![Skærmbillede af knappen Hent data i navigationsruden.](media/service-connect-to-salesforce/pbi_getdata.png) 
2. Markér **Hent** i feltet **Tjenester**.
   
   ![Skærmbillede af dialogboksen Tjenester, der viser knappen Hent.](media/service-connect-to-salesforce/pbi_getservices.png) 
3. Vælg **Analyser til Salesforce**, og vælg **Hent**.  
   
   ![Skærmbillede af dialogboksen Analyser til Salesforce, hvor linket Hent den nu vises.](media/service-connect-to-salesforce/salesforce.png)
4. Vælg **Log på** for at starte logonflowet.
   
    ![Skærmbillede af dialogboksen Opret forbindelse til Salesforce, hvor knappen Log på vises.](media/service-connect-to-salesforce/dialog.png)
5. Angiv dine Salesforce-legitimationsoplysninger, når du bliver bedt om det. Vælg **Tillad**, og giv Power BI adgang til dine grundlæggende Salesforce-oplysninger og -data.
   
   ![Skærmbillede af Salesforce-legitimationsoplysningerne, der viser, at Power BI anmoder om tilladelse til at få adgang til dine oplysninger.](media/service-connect-to-salesforce/sf_authorize.png)
6. Konfigurer det, du gerne vil importere til Power BI, ved hjælp af rullemenuen:
   
   * **Dashboard**
     
     Vælg et foruddefineret dashboard, der er baseret på en karakter (f.eks. **Salgschef**). Disse dashboards henter et bestemt sæt af standarddata fra Salesforce, hvilket ikke omfatter brugerdefinerede felter.
     
     ![Skærmbillede af dashboardet Salesforce, der viser muligheden for at vælge et foruddefineret dashboard, som er baseret på en karakter.](media/service-connect-to-salesforce/pbi_salesforcechooserole.png)
   * **Rapporter**
     
     Vælg en eller flere brugerdefinerede rapporter fra din Salesforce-konto. Disse rapporter stemmer overens med dine visninger i Salesforce og kan indeholde data fra brugerdefinerede felter eller objekter.
     
     ![Skærmbillede af Salesforce-rapporterne, der viser en liste over brugerdefinerede rapporter.](media/service-connect-to-salesforce/pbi_salesforcereports.png)
     
     Hvis du ikke kan se nogen rapporter, kan du tilføje eller oprette dem i din Salesforce-konto og prøve at oprette forbindelse igen.

7. Vælg **Opret forbindelse** for at starte importprocessen. Under importen får du vist en meddelelse om, at importen er i gang. Når importen er fuldført, får du vist et dashboard, en rapport og et datasæt for dine Salesforce-data, som er angivet i navigationsruden.
   
   ![Skærmbillede af dashboardet Salgschef, som viser dashboardet, rapporten og datasættene.](media/service-connect-to-salesforce/pbi_getdatasalesforcedash.png)

Du kan ændre dette dashboard for at få vist dine data, som du vil. Du kan stille spørgsmål med Spørgsmål og svar eller [vælge et felt](../consumer/end-user-tiles.md) for at åbne den underliggende rapport og [redigere eller fjerne felterne på dashboardet](../create-reports/service-dashboard-edit-tile.md).

**Hvad nu?**

* Prøv [at stille et spørgsmål i feltet Spørgsmål og svar](../consumer/end-user-q-and-a.md) øverst i dashboard'et
* [Rediger eller fjern et felt](../create-reports/service-dashboard-edit-tile.md) på dashboardet
* [Vælg et felt](../create-reports/service-dashboard-tiles.md) for at åbne den underliggende rapport
* Selvom dit datasæt opdateres dagligt, kan du ændre tidsplanen for opdateringen eller prøve at opdatere det on-demand ved hjælp af **Opdater nu**

## <a name="system-requirements-and-considerations"></a>Systemkrav og overvejelser

- Forbindelse til en Salesforce-produktionskonto, der har adgang til API aktiveret

- Tilladelse er tildelt til Power BI-appen under logon

- Kontoen har tilstrækkelige API-kald til at trække og opdatere dataene

- Der kræves et gyldigt godkendelsestoken for at opdatere. Der er en grænse på fem godkendelsestokens pr. program i Salesforce, så sørg for, at du har importeret fem eller færre Salesforce-datasæt.

- Salesforce Reports-API'en har en begrænsning, der understøtter op til 2.000 rækker med data.


## <a name="troubleshooting"></a>Fejlfinding

Hvis der opstår fejl, skal du gennemse ovenstående krav. 

I øjeblikket understøttes det ikke at logge på et brugerdefineret domæne eller et sandkassedomæne.

### <a name="unable-to-connect-to-the-remote-server-message"></a>Meddelelsen "Der kan ikke oprettes forbindelse til fjernserveren"

Hvis du får vist meddelelsen "Der kan ikke oprettes forbindelse til fjernserveren", når du forsøger at oprette forbindelse til din Salesforce-konto, skal du se denne løsning på følgende forum: [Salesforce Connector sign in Error Message: Unable to connect to the remote server](https://www.outsystems.com/forums/Forum_TopicView.aspx?TopicId=17674&TopicName=log-in-error-message-unable-to-connect-to-the-remote-server&)


## <a name="next-steps"></a>Næste trin
[Hvad er Power BI?](../fundamentals/power-bi-overview.md)

[Datakilder til Power BI-tjenesten](service-get-data.md)
