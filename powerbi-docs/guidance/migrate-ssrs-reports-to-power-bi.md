---
title: Overfør SQL Server Reporting Services-rapporter til Power BI
description: Vejledning til, hvordan du kan overføre dine SSRS-rapporter (SQL Server Reporting Services) til Power BI.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 01/03/2020
ms.openlocfilehash: f1b9b710c9f9e4ade80866026f728ddbe3ae6971
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96393180"
---
# <a name="migrate-sql-server-reporting-services-reports-to-power-bi"></a>Overfør SQL Server Reporting Services-rapporter til Power BI

Denne artikel er rettet mod forfattere af SSRS-rapporter (SQL Server Reporting Services) og Power BI-administratorer. Den indeholder en vejledning, der kan hjælpe dig med at overføre dine RDL-rapporter ([Report Definition Language](/sql/reporting-services/reports/report-definition-language-ssrs)) til Power BI.

> [!NOTE]
> Det er kun muligt at overføre RDL-rapporter. I Power BI kaldes RDL-rapporter _sideinddelte rapporter_.

Vejledningen er opdelt i fire stadier. Vi anbefaler, at du først læser hele artiklen, før du overfører dine rapporter.

1. [Inden du starter](#before-you-start)
1. [Stadie før overførsel](#pre-migration-stage)
1. [Overførselsstadie](#migration-stage)
1. [Stadie efter overførsel](#post-migration-stage)

Du kan opnå overførsel uden nedetid for dine SSRS-servere, eller du kan afbryde dine rapportbrugere. Det er vigtigt at forstå, at ingen data eller rapporter skal fjernes. Det betyder, at du kan holde dit aktuelle miljø på plads, indtil du er klar til at gå på pension.

## <a name="before-you-start"></a>Inden du starter

Før du starter overførslen, skal du kontrollere, at dit miljø opfylder visse forudsætninger. Vi beskriver disse forudsætninger og introducerer også et nyttigt overførselsværktøj.

### <a name="preparing-for-migration"></a>Forberedelse til overførsel

Når du forbereder overførsel af dine rapporter til Power BI, skal du først bekræfte, at din organisation har et [Power BI Premium](../admin/service-premium-what-is.md)-abonnement. Dette abonnement er påkrævet for at hoste og køre dine sideinddelte rapporter i Power BI.

### <a name="supported-versions"></a>Understøttede versioner

Du kan overføre SSRS-instanser, der kører i det lokale miljø eller på Virtual Machines, der hostes af cloud-udbydere, f.eks. Azure.

På følgende liste beskrives de SQL Server-versioner, der understøttes af overførsel til Power BI:

> [!div class="checklist"]
> - SQL Server 2012
> - SQL Server 2014
> - SQL Server 2016
> - SQL Server 2017
> - SQL Server 2019

Overførsel fra Power BI-rapportserver kan også udføres.

### <a name="migration-tool"></a>Overførselsværktøj

Vi anbefaler, at du bruger [RDL-overførselsværktøjet](https://github.com/microsoft/RdlMigration) til at klargøre og overføre dine rapporter. Dette værktøj er udviklet af Microsoft for at hjælpe kunder med at overføre RDL-rapporter fra deres SSRS-servere til Power BI. Det er tilgængeligt i GitHub, og det indeholder en komplet gennemgang af overførselsscenariet.

Værktøjet automatiserer følgende opgaver:

* Kontrol af [ikke-understøttede datakilder](../paginated-reports/paginated-reports-data-sources.md) og [ikke-understøttede rapportfunktioner](../paginated-reports/paginated-reports-faq.md#what-paginated-report-features-in-ssrs-arent-yet-supported-in-power-bi)
* Konverterer alle _delte_ ressourcer til _integrerede_ ressourcer:
  * Delte **datakilder** bliver integrerede datakilder
  * Delte **datasæt** bliver integrerede datasæt
* Publicerer rapporter (der består kontrol) som sideinddelte rapporter til et angivet Power BI-arbejdsområde (på en Premium-kapacitet)

Det ændrer eller fjerner ikke dine eksisterende rapporter. Når værktøjet er færdigt, viser det en oversigt over alle handlinger, der er afsluttet – gennemført eller mislykket.

Med tiden kan værktøjet blive forbedret af Microsoft. Communityet opfordres til at bidrage og kan også forbedre det.

## <a name="pre-migration-stage"></a>Stadie før overførsel

Når du har bekræftet, at din organisation opfylder forudsætningerne, er du klar til at starte stadiet _Før overførsel_. Dette stadie har tre faser:

1. Find
1. Vurder
1. Forbered

### <a name="discover"></a>Find

Målet for fasen _Find_ er at identificere dine eksisterende SSRS-instanser. Denne proces omfatter scanning af netværket for at identificere alle SQL Server-instanser i din organisation.

Du kan bruge [Microsoft Assessment og Planning Toolkit](https://www.microsoft.com/download/details.aspx?id=7826). Det er også kendt som "MAP Toolkit", der registrerer og rapporterer om dine SQL Server-instanser, versioner og installerede funktioner. Det er et effektivt lager-, vurderings- og rapporteringsværktøj, der kan forenkle din planlægning af overførselsprocessen.

### <a name="assess"></a>Vurder

Når dine SSRS-instanser er registreret, er målet for fasen _Vurder_ at forstå alle SSRS-rapporter – eller serverelementer – der ikke kan overføres.

Det er kun RDL-rapporter, der kan overføres fra dine SSRS-servere til Power BI. Hver overført RDL-rapport bliver en sideinddelt rapport i Power BI.

Følgende SSRS-elementtyper kan dog ikke overføres til Power BI:

- Delte datakilder <sup>1</sup>
- Delte datasæt <sup>1</sup>
- Ressourcer, f.eks. billedfiler
- KPI'er (SSRS 2016 eller nyere – kun Enterprise Edition)
- Mobilrapporter (SSRS 2016 eller nyere – kun Enterprise Edition)
- Rapportmodeller (frarådes)
- Rapportdele (frarådes)

<sup>1</sup> [RDL-overførselsværktøjet](https://github.com/microsoft/RdlMigration) konverterer automatisk delte datakilder og delte datasæt – forudsat at de bruger understøttede datakilder.

Hvis dine RDL-rapporter bruger funktioner, [der endnu ikke understøttes af sideinddelte rapporter i Power BI](../paginated-reports/paginated-reports-faq.md#what-paginated-report-features-in-ssrs-arent-yet-supported-in-power-bi), kan du planlægge at udvikle dem igen som [Power BI-rapporter](../consumer/end-user-reports.md). Selvom dine RDL-rapporter kan overføres, anbefaler vi, at du overvejer at modernisere dem som Power BI-rapporter, når det giver mening.

Hvis dine RDL-rapporter skal hente data fra _datakilder i det lokale miljø_, kan de ikke bruge enkeltlogon (SSO). Al datahentning fra disse kilder udføres i øjeblikket ved hjælp af sikkerhedskonteksten for _brugerkontoen for datakildens gateway_. Det er ikke muligt for SQL Server Analysis Services (SSAS) at gennemtvinge sikkerhed på rækkeniveau for hver enkelt bruger.

Sideinddelte rapporter i Power BI er generelt optimeret til **udskrivning** eller **generering af PDF**. Power BI-rapporter er optimeret til **udforskning og interaktivitet**. Du kan få flere oplysninger i [Her skal du bruge sideinddelte rapporter i Power BI](report-paginated-or-power-bi.md).

### <a name="prepare"></a>Forbered

Målet med fasen _Forbered_ indebærer, at du bliver klar til det hele. Den dækker konfiguration af Power BI-miljøet, planlægning af, hvordan du sikrer og publicerer dine rapporter, og idéer til at genudvikle SSRS-elementer, der ikke overføres.

1. Sørg for, at [arbejdsbelastningen Sideinddelte rapporter](../admin/service-admin-premium-workloads.md#paginated-reports) er aktiveret for din Power BI Premium-kapacitet, og at den har tilstrækkelig hukommelse.
1. Bekræft support til [datakilder](../paginated-reports/paginated-reports-data-sources.md) for din rapport, og opret en [Power BI Gateway](../connect-data/service-gateway-onprem.md) for at tillade forbindelse til alle datakilder i det lokale miljø.
1. Bliv fortrolig med Power BI-sikkerhed, og planlæg, [hvordan du genopretter dine SSRS-mapper og tilladelser](/sql/reporting-services/security/secure-folders) med [Power BI-arbejdsområder og arbejdsområderoller](../collaborate-share/service-new-workspaces.md).
1. Bliv fortrolig med Power BI-deling, og planlæg, hvordan du distribuerer indhold ved at udgive [Power BI-apps](../collaborate-share/service-create-distribute-apps.md).
1. Overvej at bruge [delte Power BI-datasæt](../connect-data/service-datasets-build-permissions.md) i stedet for dine SSRS-delte datakilder.
1. Brug [Power BI Desktop](../fundamentals/desktop-what-is-desktop.md) til at udvikle mobiloptimerede rapporter. Du kan evt. bruge [den brugerdefinerede visualisering til Power KPI](https://appsource.microsoft.com/product/power-bi-visuals/WA104381083?tab=Overview) i stedet for dine SSRS-mobilrapporter og-KPI'er.
1. Revaluer brugen af det indbyggede felt **UserID** i dine rapporter. Hvis du bruger **UserID** til at sikre rapportdata, skal du forstå, at brugerens hovednavn (UPN) returneres for sideinddelte rapporter (når de hostes i Power BI-tjenesten). Så i stedet for at returnere NT-kontonavnet, f.eks. _AW\mblythe_, returnerer det indbyggede felt noget i stil med _m.Blythe&commat;adventureworks.com_. Du skal revidere definitionerne for dine datasæt og muligvis kildedataene. Når de er revideret og publiceret, anbefaler vi, at du tester dine rapporter grundigt for at sikre, at datatilladelserne fungerer som forventet.
1. Revaluer brugen af det indbyggede felt **ExecutionTime** i dine rapporter. Det indbyggede felt returnerer dato/klokkeslæt _i UTC (Coordinated Universal Time)_ for sideinddelte rapporter (når de hostes i Power BI-tjenesten). Det kan påvirke standardværdierne for rapportparameteren og rapportere mærkater for udførelsestid (typisk føjet til rapport sidefødder).
1. Hvis din datakilde er SQL Server (i det lokale miljø), skal du bekræfte, at rapporterne ikke benytter kortvisualiseringer. Kortvisualiseringen afhænger af SQL Server-afstandsdatatyper, og disse typer understøttes ikke af gatewayen. Du kan finde flere oplysninger under [Vejledning til hentning af data for sideinddelte rapporter (komplekse datatyper i SQL Server)](report-paginated-data-retrieval.md#sql-server-complex-data-types).
1. Sørg for, at dine rapportforfattere har [Power BI Report Builder](../paginated-reports/report-builder-power-bi.md) installeret, og at de senere udgaver nemt kan distribueres i hele organisationen.

## <a name="migration-stage"></a>Overførselsstadie

Når du har klargjort dit Power BI-miljø og dine rapporter, er du klar til fasen _Overførsel_.

Der er to overførselsmuligheder: _manuelt_ og _automatisk_. Manuel overførsel er velegnet til et lille antal rapporter eller rapporter, der skal ændres før overførsel. Automatisk overførsel er velegnet til overførsel af et stort antal rapporter.

### <a name="manual-migration"></a>Manuel overførsel

Alle, der har tilladelse til at få adgang til SSRS-instansen og Power BI-arbejdsområdet, kan manuelt overføre rapporter til Power BI. Disse trin skal følges:

1. Åbn den SSRS-portal, der indeholder de rapporter, du vil overføre.
1. Hent hver rapportdefinition, og gem .rdl-filerne lokalt.
1. Åbn _den seneste version_ af Power BI Report Builder, og opret forbindelse til Power BI-tjenesten ved hjælp af dine legitimationsoplysninger til Microsoft Azure Active Directory.
1. Åbn hver rapport i Power BI Report Builder, og gør derefter følgende:
   1. Bekræft, at alle datakilder og datasæt er integreret i rapportdefinitionen, og at de er [understøttede datakilder](../paginated-reports/paginated-reports-data-sources.md).
   1. Få vist et eksempel på rapporten for at sikre, at den gengives korrekt.
   1. Vælg indstillingen _Gem som_, og vælg derefter _Power BI-tjeneste_.
   1. Vælg det arbejdsområde, der skal indeholde rapporten.
   1. Kontrollér, at rapporten gemmes. Hvis visse funktioner i dit rapportdesign endnu ikke understøttes, vil handlingen Gem ikke blive udført. Du får besked om årsagerne. Derefter skal du redigere rapportdesignet og prøve at gemme igen.

### <a name="automated-migration"></a>Automatisk overførsel

Der er to muligheder for automatisk overførsel. Du kan bruge:

- RDL-overførselsværktøjet
- De offentligt tilgængelige API'er til SSRS og Power BI

[RDL-overførselsværktøjet](#migration-tool) er allerede blevet beskrevet i denne artikel.

Du kan også bruge de offentligt tilgængelige SSRS- og Power BI-API'er til at automatisere overførslen af dit indhold. Da RDL-overførselsværktøjet bruger disse API'er allerede, kan du udvikle et brugerdefineret værktøj, der passer til dine krav.

Du kan få flere oplysninger om API'erne her:

- [Reference til Power BI REST API](../developer/automation/rest-api-reference.md)
- [SQL Server Reporting Services REST API'er](/sql/reporting-services/developer/rest-api)

## <a name="post-migration-stage"></a>Stadie efter overførsel

Når du har gennemført overførslen, er du klar til stadiet _Efter overførsel_. Denne fase forudsætter, at der arbejdes med en række opgaver, der udføres efter overførsel, for at sikre, at alt fungerer korrekt og effektivt.

### <a name="configure-data-sources"></a>Konfigurer datakilder

Når rapporter er blevet overført til Power BI, skal du sørge for, at deres datakilder er konfigureret korrekt. Det kan involvere tildeling til gatewaydatakilder og [sikker lagring af legitimationsoplysninger til datakilden](../paginated-reports/paginated-reports-data-sources.md#azure-sql-database-authentication). Disse handlinger udføres ikke af RDL-overførselsværktøjet.

### <a name="review-report-performance"></a>Gennemse rapportens ydeevne

Vi anbefaler på det kraftigste, at du fuldfører følgende handlinger for at sikre den bedst mulige brugeroplevelse med rapporter:

1. Test rapporterne i hver [browser, der understøttes af Power BI](../fundamentals/power-bi-browsers.md), for at bekræfte, at rapporten gengives korrekt.
1. Kør testene for at sammenligne rapporternes gengivelsestid i SSRS og Power BI. Kontrollér, at Power BI-rapporter gengives inden for en acceptabel tid.
1. Hvis Power BI-rapporter ikke gengives, fordi der ikke er tilstrækkelig hukommelse, skal du tildele [yderligere ressourcer til Power BI Premium-kapacitet](../admin/service-admin-premium-workloads.md#paginated-reports).
1. I forbindelse med rapporter med lang gengivelse kan du overveje at få Power BI til at levere dem til dine rapportbrugere som [mailabonnementer med rapporter som vedhæftede filer](../consumer/paginated-reports-subscriptions.md).
1. For Power BI-rapporter, der er baseret på Power BI-datasæt, skal du gennemgå modeldesign for at sikre, at de er fuldt optimerede.

### <a name="reconcile-issues"></a>Afhjælp problemer

Fasen Efter overførsel er afgørende for, hvordan du afhjælper eventuelle problemer, og at du håndterer eventuelle problemer med ydeevnen. Tilføjelse af arbejdsbelastningen for sideinddelte rapporter til en kapacitet kan bidrage til langsom ydeevne – for sideinddelte rapporter _og andet indhold_, der er lagret i kapaciteten.

Du kan finde flere oplysninger om disse problemer, herunder bestemte trin til at forstå og afhjælpe dem, i følgende artikler:

- [Optimering af Premium-kapaciteter](../admin/service-premium-capacity-optimize.md)
- [Overvåg Premium-kapaciteter i appen](../admin/service-admin-premium-monitor-capacity.md)

## <a name="next-steps"></a>Næste trin

Du kan finde flere oplysninger om denne artikel i følgende ressourcer:

- [Hvad er sideinddelte rapporter i Power BI Premium?](../paginated-reports/paginated-reports-report-builder-power-bi.md)
- [Vejledning til datahentning for sideinddelte rapporter](report-paginated-data-retrieval.md)
- [Hvornår bruges sideinddelte rapporter i Power BI](report-paginated-or-power-bi.md)
- [Sideinddelte rapporter i Power BI: Ofte stillede spørgsmål](../paginated-reports/paginated-reports-faq.md)
- [Onlinekursus: Sideinddelte rapporter på én dag](../learning-catalog/paginated-reports-online-course.md)
- [Ofte stillede spørgsmål til Power BI Premium](../admin/service-premium-faq.md)
- [RDL-overførselsværktøj](https://github.com/microsoft/RdlMigration)
- Har du spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
- Forslag? [Få ideer til at forbedre Power BI](https://ideas.powerbi.com)

Der findes Power BI-partnere, som kan hjælpe din organisation med at gennemføre overførselsprocessen. Hvis du vil i kontakt med en Power BI-partner, skal du gå til [Power BI-partnerportalen](https://powerbi.microsoft.com/partners/).
