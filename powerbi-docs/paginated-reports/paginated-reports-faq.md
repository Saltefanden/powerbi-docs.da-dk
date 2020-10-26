---
title: 'Sideinddelte rapporter i Power BI: Ofte stillede spørgsmål'
description: I denne artikel finder du svar på ofte stillede spørgsmål om sideinddelte rapporter. Disse rapporter indeholder megen formatering og er perfekt pixeleret output, der er optimeret til udskrivning eller generering af PDF.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 10/19/2020
ms.openlocfilehash: 2a0490106d5954a57abea1dd5de61f26f2fe2377
ms.sourcegitcommit: eab5a02520c421a57019595c03e9ecfdb41d52ad
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 10/20/2020
ms.locfileid: "92257006"
---
# <a name="paginated-reports-in-power-bi-faq"></a>Sideinddelte rapporter i Power BI: Ofte stillede spørgsmål 

I denne artikel finder du svar på ofte stillede spørgsmål om sideinddelte rapporter. Disse rapporter indeholder megen formatering og er perfekt pixeleret output, der er optimeret til udskrivning eller generering af PDF. De kaldes "sideinddelte", fordi de er formateret til at passe godt på flere sider. Sideinddelte rapporter er baseret på RDL-rapportteknologien i SQL Server Reporting Services. 

I denne artikel finde du svar på mange almindelige spørgsmål, som folk har om sideinddelte rapporter i Power BI Premium, og om Report Builder, som er et separat værktøj til oprettelse af sideinddelte rapporter. Du skal bruge en Power BI Pro-licens for at publicere en rapport i tjenesten. Du kan publicere og dele sideinddelte rapporter i Mit arbejdsområde eller i arbejdsområder, så længe arbejdsområdet er placeret i en Power BI Premium-kapacitet. 

## <a name="administration"></a>Administration

### <a name="what-size-premium-capacity-do-i-need-for-paginated-reports"></a>Hvilken størrelse Premium-kapacitet for sideinddelte rapporter skal jeg bruge?

Arbejdsbelastningen for sideinddelte rapporter er tilgængelig på P1-P3 SKU'er.  Du kan også bruge den med A4 – A6 SKU'er til integrerings- eller test/dev-scenarier.

### <a name="what-is-the-maximum-memory-threshold-i-can-put-for-paginated-reports-in-my-capacity"></a>Hvad er den maksimale hukommelsestærskel, jeg kan angive, for sideinddelte rapporter i min kapacitet?

Du må bruge op til 100 % af hukommelsen til denne arbejdsbelastning.

### <a name="how-does-user-access-work-for-paginated-reports"></a>Hvordan fungerer brugeradgang til sideinddelte rapporter?

Brugeradgang til sideinddelte rapporter er det samme som brugeradgang til alt andet indhold i Power BI-tjenesten 

### <a name="how-do-i-turn-onoff-my-paginated-reports-workload"></a>Hvordan slår jeg arbejdsbelastningen for mine sideinddelte rapporter til/fra?

Administratoren af kapacitet kan aktivere eller deaktivere arbejdsbelastningen for sideinddelte rapporter på siden med administratorportalen for kapacitet.  Arbejdsbelastningen er som standard aktiveret for alle nye kapaciteter, du opretter, men bruger ikke hukommelse, før du uploader din første sideinddelte rapport.  

### <a name="how-can-i-monitor-usage-of-paginated-reports-in-my-tenant"></a>Hvordan overvåger jeg forbrug af sideinddelte rapporter i min lejer?

Overvågningsloggene indeholder detaljerede oplysninger om forbrug af denne rapporttype i forbindelse med følgende hændelser:

- Vis Power BI-rapport
- Slet Power BI-rapport
- Opret Power BI-rapport
- Downloadet Power BI-rapport

Feltet ReportType har værdien "PaginatedReport" for at identificere sideinddelte rapporter i modsætning til Power BI-rapporter.

Desuden indeholder overvågningsloggene følgende hændelser for sideinddelte rapporter:

- Bundne Power BI-datasæt til gateway
- Udforsk Power BI-datakilde
- TakeOverDatasource

### <a name="can-i-monitor-this-workload-through-the-premium-capacity-monitoring-app"></a>Kan jeg overvåge denne arbejdsbelastning via appen til overvågning af Premium-kapacitet?

Ja, overvågning er tilgængelig som en ny fane med de samme relevante oplysninger, som du har til dine Power BI-datasæt.

### <a name="do-i-need-a-pro-license-to-create-and-publish-paginated-reports"></a>Skal jeg have en Pro-licens for at oprette og publicere sideinddelte rapporter?

Du kan uploade sideinddelte rapporter til Mit arbejdsområde uden en Pro-licens, hvis den er i en Premium-kapacitet.  For andre arbejdsområder skal du have en Pro-licens for at oprette og publicere indhold til dem. Vi anbefaler, at du henter og bruger Power BI Report Builder selv uden en Pro-licens, men du kan ikke publicere de sideinddelte rapporter, du opretter, uden den. 

### <a name="what-if-i-have-a-paginated-report-in-a-workspace-and-the-paginated-report-workload-is-turned-off"></a>Hvad nu hvis jeg har en sideinddelt rapport i et arbejdsområde, og arbejdsbelastningen for sideinddelte rapporter er slået fra?

Du får vist en fejlmeddelelse, og du kan ikke få vist rapporten, før arbejdsbelastningen er slået til igen. Du kan stadig slette rapporten fra arbejdsområdet.

### <a name="what-is-the-default-memory-for-each-of-the-premium-skus-that-support-paginated-reports"></a>Hvad er standardhukommelsen for hver af de Premium SKU'er, der understøtter sideinddelte rapporter?

Standardhukommelsen for hver Premium SKU for sideinddelte rapporter er:

- **P1/A4**: 20 % som standard, minimum 10 %
- **P2/A5**: 20 % som standard, minimum 5 %
- **P3/A6**: 20 % som standard, minimum 2,5 %

Power BI-administratorer kan ændre standardprocenten for maksimal hukommelse i administrationsportalen. Se arbejdsbelastningsafsnittet **Sideinddelte rapporter** under **Power BI Premium** under fanen **Kapacitetsindstillinger**.

:::image type="content" source="media/paginated-reports-faq/paginated-reports-capacity-settings.png" alt-text="Sideinddelte rapporter under fanen Kapacitetsindstillinger":::

## <a name="general"></a>Generelt

### <a name="when-should-i-use-a-paginated-report-vs-a-power-bi-report"></a>Hvornår skal jeg bruge en sideinddelt rapport i forhold til en Power BI-rapport?

Sideinddelte rapporter er bedst til scenarier, hvor der kræves megen formatering og perfekt pixeleret output, der er optimeret til udskrivning eller generering af PDF.  Et driftsregnskab er et godt eksempel på den type rapport, du sandsynligvis ville oprette som en sideinddelt rapport.  

Power BI-rapporter er optimeret til udforskning og interaktivitet.  En salgsrapport, hvor forskellige sælgere vil opdele dataene i den samme rapport for deres specifikke område/branche/kunde og se, hvordan tallene ændres, vil fungere bedst som en Power BI-rapport.

Du kan få flere oplysninger i [Her skal du bruge sideinddelte rapporter i Power BI](../guidance/report-paginated-or-power-bi.md).

### <a name="the-documentation-says-power-bi-report-builder-is-the-preferred-authoring-tool-can-i-create-paginated-reports-in-sql-server-data-tools-for-power-bi"></a>Ifølge dokumentationen er Power BI Report Builder det foretrukne værktøj til oprettelse. Kan jeg oprette sideinddelte rapporter i SQL Server Data Tools til Power BI?

Ja, men Power BI-tjenesten giver dig kun mulighed for at uploade et enkelt element ad gangen, så mange af de scenarier, forfattere bruger med SQL Server Data Tools (SSDT), understøttes endnu ikke. Du kan se en komplet [liste over ikke-understøttede funktioner](#what-paginated-report-features-in-ssrs-arent-yet-supported-in-power-bi) senere i disse Ofte stillede spørgsmål.  

### <a name="what-versions-of-report-builder-do-you-support"></a>Hvilke versioner af Report Builder understøttes?

Vi har udgivet Power BI Report Builder som det primære værktøj til oprettelse af sideinddelte rapporter i Power BI-tjenesten. Installér [Power BI Report Builder fra Microsoft Download Center](https://aka.ms/pbireportbuilder).

### <a name="how-do-i-move-existing-reports-i-have-saved-in-sql-server-reporting-services-to-power-bi"></a>Hvordan flytter jeg eksisterende rapporter, som jeg har gemt i SQL Server Reporting Services, til Power BI?

Et projekt i GitHub understøtter nu migrering af indhold fra SQL Server Reporting Services til Power BI.  Få vist detaljer, og download værktøjet her: [https://github.com/microsoft/RdlMigration](https://github.com/microsoft/RdlMigration)

### <a name="can-i-open-reports-and-publish-directly-to-the-service"></a>Kan jeg åbne rapporter og publicere direkte i tjenesten?

Ja. Vi har tilføjet understøttelse af åbning af rapporter og publicering af dem direkte i tjenesten fra Power BI Report Builder.

### <a name="what-paginated-report-features-in-ssrs-arent-yet-supported-in-power-bi"></a>Hvilke funktioner for sideinddelte rapporter i SSRS understøttes endnu ikke i Power BI?

Sideinddelte rapporter understøtter i øjeblikket ikke følgende elementer:

- Delte datakilder
- Delte datasæt
- Detaljeadgang og klikfrekvens til andre rapporter
- Linkede rapporter
- Brugerdefinerede skrifttyper

Du får vist en fejlmeddelelse, hvis du forsøger at uploade en fil, som indeholder en ikke-understøttet funktion i Power BI-tjenesten – med undtagelse af slå til/fra og sortering.

### <a name="what-data-sources-do-you-support-currently-for-paginated-reports"></a>Hvilke datakilder understøttes i øjeblikket for sideinddelte rapporter?

Se artiklen [Understøttede datakilder for sideinddelte rapporter i Power BI](paginated-reports-data-sources.md) for at få vist en liste over datakilder. 

### <a name="what-authentication-methods-do-you-support"></a>Hvilke godkendelsesmetoder understøttes?

Vi understøtter SSO til Azure Analysis Services, Azure SQL Database og Power BI-datakilder.  Vi understøtter også OAuth til Azure SQL Database og Azure Analysis Services.  For alle andre datakilder skal du i øjeblikket gemme et brugernavn og en adgangskode sammen med datakilden på portalen eller i gatewayen.  

### <a name="can-i-use-a-power-bi-dataset-as-a-data-source-for-my-paginated-report"></a>Kan jeg bruge et Power BI-datasæt som en datakilde til min sideinddelte rapport?

Ja, vi understøtter Power BI-datasæt som datakilder for dine sideinddelte rapporter.

### <a name="can-i-use-stored-procedures-through-the-gateway"></a>Kan jeg bruge gemte procedurer via denne gateway?

Ja, gemte procedurer via gatewayen understøttes til SQL Server-datakilder, herunder dem der bruger parametre.

### <a name="what-export-formats-are-available-for-my-report-in-the-power-bi-service"></a>Hvilke eksportformater er tilgængelige for min rapport i Power BI-tjenesten?

Du kan eksportere til Microsoft Excel, Microsoft Word, Microsoft PowerPoint, PDF, .CSV, XML og MHTML.

### <a name="can-i-print-paginated-reports"></a>Kan jeg udskrive sideinddelte rapporter?

Ja, udskrivning er tilgængelig for sideinddelte rapporter, herunder en ny og forbedret oplevelse af Vis udskrift. 

### <a name="are-e-mail-subscriptions-available-for-paginated-reports"></a>Er mailabonnementer tilgængelige for sideinddelte rapporter?

Ja, mailabonnementer understøttes fuldt ud for sideinddelte rapporter og omfatter understøttelse af seks forskellige filformater og parameterværdier.

### <a name="can-i-run-custom-code-in-my-report"></a>Kan jeg køre brugerdefineret kode i min rapport?

Ja, vi understøtter muligheden for at køre kode i dine rapporter, ligesom du kan i SSRS.

### <a name="can-i-use-power-bi-embedded-to-embed-my-paginated-reports-into-an-app-im-hosting"></a>Kan jeg bruge Power BI Embedded til at integrere mine sideinddelte rapporter i en app, jeg er vært for?

SaaS-integration, herunder understøttelse af sikker integration, er allerede tilgængelig. For PaaS-integration skal du se selvstudiet [Integrer sideinddelte Power BI-rapporter i et program til dine kunder](../developer/embedded/embed-paginated-reports-customers.md).

### <a name="can-i-drill-through-from-a-power-bi-report-to-a-paginated-report"></a>Kan jeg få detaljeadgang fra en Power BI-rapport til en sideinddelt rapport?

Ja, dette kan gøres ved at bruge URL-parametre sammen med sideinddelte rapporter.

### <a name="can-i-share-my-paginated-report-content-through-a-power-bi-app"></a>Kan jeg dele indhold i min sideinddelte rapport via en Power BI-app?

Ja, sideinddelte rapporter understøttes og kan implementeres med apps fra både v1- og v2-arbejdsområder. 

### <a name="will-other-report-specific-features-in-power-bi-like-pinning-report-tiles-to-dashboards-work-with-paginated-reports"></a>Kan andre rapportspecifikke funktioner i Power BI, f.eks. fastgørelse af rapportfelter til dashboards, fungere sammen med sideinddelte rapporter?

Vi har planer om, at rapporterne skal understøtte de samme overordnede scenarier i tjenesten så meget som muligt.  Selvom værktøjet til at oprette dem er forskelligt, er det, set fra en brugers synspunkt, ideelt set blot endnu en rapport på deres liste på portalen. De er ligeglade med, hvordan den blev oprettet, så længe de kan gøre det, de har brug for.  Et godt eksempel på denne funktionsparitet er understøttelsen af planlagte kommentarer. Selvom selve funktionen muligvis fungerer en smule anderledes for hver rapporttype, vil du kunne bruge kommentarer til begge.

### <a name="is-there-a-report-viewer-control-for-paginated-reports-in-the-power-bi-service"></a>Er der et kontrolelement til rapportfremviser for sideinddelte rapporter i Power BI-tjenesten?

Nej, kontrolelementet til rapportfremviser er i øjeblikket ikke tilgængeligt.

### <a name="can-you-search-for-paginated-reports-from-the-new-home-experience-in-the-power-bi-service"></a>Kan man søge efter sideinddelte rapporter fra den nye Hjem-oplevelse i Power BI-tjenesten?

Ja, du kan nu søge efter dine sideinddelte rapporter fra Hjem.  Du kan også se dem i andre dele af den nye Hjem-oplevelse.

## <a name="considerations-and-troubleshooting"></a>Overvejelser og fejlfinding
Det er noget, du skal huske på, når du arbejder med dato/klokkeslæt-felter i sideinddelte rapporter.

- Der er i øjeblikket nogen globaliseringsbegrænsninger, der er knyttet til dato/klokkeslæt-parametre. Alle parametre for dato/klokkeslæt i Power BI-tjenesten hentes i amerikansk format (MM/DD/ÅÅÅÅ), uanset hvordan du designer dato/klokkeslæt i Power BI Report Builder.

Når du får vist sideinddelte rapporter i Power BI-tjenesten, kan der opstå timeout for sessioner, der præsenterer brugeren med følgende meddelelse:

:::image type="content" source="media/paginated-reports-faq/expired-session-notification.png" alt-text="Sideinddelte rapporter under fanen Kapacitetsindstillinger":::

- Sessionen får timeout efter 60 minutter med inaktivitet eller tidligere, når enheden er låst eller inaktiv, eller når rapporten ikke vises på den aktive fane i browseren.

## <a name="next-steps"></a>Næste trin

- [Installér Power BI Report Builder fra Microsoft Download Center](https://aka.ms/pbireportbuilder)
- [Selvstudium: Opret en sideinddelt rapport](paginated-reports-quickstart-aw.md)
