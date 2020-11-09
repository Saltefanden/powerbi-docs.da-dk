---
title: Optimeringsvejledning til Power BI
description: Optimeringsvejledning til Power BI.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 02/16/2020
ms.author: v-pemyer
ms.openlocfilehash: 3a541c46f78c5e5cd25b47a94394a011fd61954f
ms.sourcegitcommit: 4ac9447d1607dfca2e60948589f36a3d64d31cb4
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 10/29/2020
ms.locfileid: "92916538"
---
# <a name="optimization-guide-for-power-bi"></a>Optimeringsvejledning til Power BI

Denne artikel indeholder en vejledning, der gør det muligt for udviklere og administratorer at producere og vedligeholde optimerede Power BI-løsninger. Du kan optimere din løsning i forskellige arkitektoniske lag. Lagene omfatter:

- Datakilden/-erne
- Datamodellen
- Visualiseringer, herunder dashboards, Power BI-rapporter og sideinddelte Power BI-rapporter
- Miljøet, herunder kapaciteter, datagateways og netværket

## <a name="optimizing-the-data-model"></a>Optimering af datamodellen

Datamodellen understøtter hele visualiseringsfunktionaliteten. Datamodeller hostes enten eksternt eller internt, og i Power BI refereres de til som _datasæt_. Det er vigtigt at forstå dine muligheder og vælge den rette type datasæt for din løsning. De tre tilstande for datasæt: Import, DirectQuery og Sammensat. Du kan finde flere oplysninger i [Datasæt i Power BI-tjenesten](../connect-data/service-datasets-understand.md) og [Datasættilstande i Power BI-tjenesten](../connect-data/service-dataset-modes-understand.md).

Du kan finde en vejledning til en bestemt datasættilstand i:

- [Teknikker til datareduktion i forbindelse med importmodeller](import-modeling-data-reduction.md)
- [Vejledning til DirectQuery-model i Power BI Desktop](directquery-model-guidance.md)
- [Vejledning til sammensatte modeller i Power BI Desktop](composite-model-guidance.md)

## <a name="optimizing-visualizations"></a>Optimering af visualiseringer

Power BI-visualiseringer kan være dashboards, Power BI-rapporter eller sideinddelte Power BI-rapporter. Hver har forskellige arkitekturer, og de har hver deres egne retningslinjer. 

### <a name="dashboards"></a>Dashboards

Det er vigtigt at forstå, at Power BI vedligeholder en cache til dine dashboardfelter – undtagen dynamiske rapportfelter og streamingfelter. Du kan finde flere oplysninger i [Dataopdatering i Power BI (Feltopdatering)](../connect-data/refresh-data.md#tile-refresh). Hvis dit datasæt gennemtvinger dynamisk [sikkerhed på rækkeniveau (RLS)](../admin/service-admin-rls.md), skal du sørge for at forstå konsekvenserne for ydeevnen, efterhånden som felter cachelagres for hver enkelt bruger.

Når du fastgør dynamiske rapportfelter til et dashboard, bliver de ikke betjent fra forespørgselscachen. I stedet fungerer de på samme måde som rapporter og afgiver forespørgsler til back-end-kerner ad hoc.

Som navnet antyder sikrer modtagelse af data fra cachen en bedre og mere ensartet ydeevne end at være afhængig af datakilden. Én måde at drage fordel af denne funktionalitet på er ved at gøre dashboards til den første landingsside for dine brugere. Fastgør ofte brugte og hyppigt anvendte visuelle elementer til dashboardene. På denne måde bliver dashboards et praktisk "første forsvarsværk", som leverer konsekvent ydelse med mindre belastning af kapaciteten. Brugerne kan stadig klikke sig gennem til en rapport for at analysere detaljerne.

Denne forespørgselscache opdateres regelmæssigt ved at forespørge om datakilden i forbindelse med DirectQuery og dynamiske datasæt. Som standard sker det hver time, selvom du kan konfigurere en anden frekvens i indstillingerne for datasæt. Hver cacheopdatering sender forespørgsler til den underliggende datakilde om at opdatere cachen. Antallet af forespørgsler, der oprettes, afhænger af antallet af visuelle elementer, der er fastgjort til dashboards, der afhænger af den pågældende datakilde. Bemærk, at hvis sikkerhed på rækkeniveau er aktiveret, så genereres forespørgsler for hver særskilte sikkerhedskontekst. Du kan f.eks. overveje, at der er to forskellige roller til kategorisering af brugerne, og at de har to forskellige visninger af dataene. Power BI genererer to sæt forespørgsler under opdateringen af forespørgselscachen.

### <a name="power-bi-reports"></a>Power BI-rapporter

Der er flere anbefalinger til optimering af Power BI-rapportdesign.

> [!NOTE]
> Når rapporter er baseret på et DirectQuery-datasæt, kan du få yderligere anbefalinger til optimering af rapportdesign i [DirectQuery-modelvejledning i Power BI Desktop (Optimer rapportdesign)](directquery-model-guidance.md#optimize-report-designs).

#### <a name="apply-the-most-restrictive-filters"></a>Anvend de mest restriktive filtre

Jo flere data et visuelt element skal vise, jo langsommere er indlæsningen af det pågældende visuelle element. Dette princip kan synes indlysende, men glemmes dog let. Et eksempel: Lad os antage, at du har et stort datasæt. Oven i dette datasæt opretter du en rapport med en tabel. Slutbrugere benytter udsnitsværktøj på siden for at få adgang til de ønskede rækker – de er typisk kun interesserede i et fåtal af rækker.

En almindelig fejl er, hvis man ikke lader standardvisningen af tabellen være ufiltreret, dvs. alle +100 millioner rækker. Dataene til disse rækker indlæses i hukommelsen og dekomprimeres ved hver opdatering. Denne behandling belaster i høj grad hukommelsen. Løsningen: Brug filteret "Top N" til at reducere det maksimale antal elementer, som tabellen viser. Du kan indstille det maksimale antal elementer til at være større, end brugeren har brug for, f.eks. 10.000. Resultatet er, at slutbrugerens oplevelse ikke ændres, men hukommelsesbrugen falder markant. Det vigtigste er, at ydeevnen forbedres.

En tilsvarende tilgang til ovenstående anbefales for alle visualiseringer i din rapport. Stil dig selv spørgsmålet, om alle dataene i dette visuelle element er nødvendige. Kan mængden af de viste data i visualiseringen på nogen måde filtreres uden at påvirke slutbrugerens oplevelse? Husk, at især tabeller kan være dyre.

#### <a name="limit-visuals-on-report-pages"></a>Begræns visuelle elementer på rapportsider

Ovenstående princip gælder tilsvarende for antallet af visualiseringer, der føjes til en rapportside. Det anbefales på det kraftigste, at du begrænser antallet af visualiseringer på en relevant rapportside til det mest nødvendige. [Detaljeadgangssider](report-drillthrough.md) og [værktøjstip til rapportsider](report-page-tooltips.md) kan med stor fordel bruges til at få vist yderligere detaljer uden at proppe yderligere visualiseringer ind i rapporten.

#### <a name="evaluate-custom-visual-performance"></a>Evaluer brugerdefinerede visualiseringers ydeevne

Sørg for at gennemprøve hvert brugerdefinerede visuelle element for at sikre høj ydeevne. Power BI-visuals med dårlig optimering kan påvirke hele rapportens ydeevne negativt.

### <a name="power-bi-paginated-reports"></a>Sideinddelte rapporter i Power BI

Design af sideinddelte rapporter i Power BI kan optimeres ved at anvende bedste praksis-design til rapportens datahentning. Du kan finde flere oplysninger under [Vejledning til hentning af data for sideinddelte rapporter](report-paginated-data-retrieval.md).

Du skal også sikre, at din kapacitet har tilstrækkelig hukommelse til [arbejdsbelastningen for sideinddelte rapporter](../admin/service-admin-premium-workloads.md#paginated-reports).

## <a name="optimizing-the-environment"></a>Optimering af miljøet

Du kan optimere Power BI-miljøet ved at konfigurere kapacitetsindstillinger, tilpasse størrelsen på datagateways og reducere netværksventetid.

### <a name="capacity-settings"></a>Kapacitetsindstillinger

Når du bruger kapaciteter – som er tilgængelige med Power BI Premium (P-SKU'er) eller Power BI Embedded (A-SKU'er, A4-A6), kan du administrere kapacitetsindstillinger. Du kan finde flere oplysninger under [Administration af Premium-kapacitet](../admin/service-premium-capacity-manage.md). Du kan finde en vejledning i, hvordan du optimerer din kapacitet, under [Optimering af Premium-kapaciteter](../admin/service-premium-capacity-optimize.md).

### <a name="gateway-sizing"></a>Tilpasning af gateway-størrelse

En gateway er påkrævet, når Power BI skal have adgang til data, der ikke er tilgængelige direkte via internettet. Du kan installere en [datagateway i det lokale miljø](../connect-data/service-gateway-onprem.md) på en server i det lokale miljø eller på en VM-hostet IaaS (Infrastruktur som en service).

Hvis du vil vide mere om gatewayarbejdsbelastninger og have anbefalinger til tilpasning af størrelsen, skal du se [Tilpasning af størrelse på datagateway i det lokale miljø](gateway-onprem-sizing.md).

### <a name="network-latency"></a>Netværksventetid

Netværksventetid kan påvirke rapporters ydeevne ved at øge den tid, der kræves for anmodninger om at oprette forbindelse til Power BI-tjenesten, og for at svarene leveres. Lejere i Power BI tildeles et bestemt område.

> [!TIP]
> Du kan få hjælp til at se, hvor din lejer er placeret, under [Hvor findes min Power BI-lejer?](../admin/service-admin-where-is-my-tenant-located.md)

Når brugere fra en lejer tilgår Power BI-tjenesten, så føres vedkommendes anmodninger altid til dette område. Når anmodninger kommer til Power BI-tjenesten, sender tjenesten muligvis flere anmodninger, f.eks. til den underliggende datakilde eller datagatewayen, som også er underlagt netværksventetid.

Funktioner som f.eks. [Azure Speed Test](https://azurespeedtest.azurewebsites.net/) giver en praj om netværksventetiden mellem klienten og Azure-området. Generelt bør du begrænse indvirkningen af netværksventetider ved at stræbe efter at holde datakilder, gateways og din Power BI-klynge så tæt på hinanden som muligt. De skal helst ligge i det samme område. Hvis netværksventetid er et problem, kan du prøve at finde gateways og datakilder, der ligger tættere på din Power BI-klynge ved at placere dem på virtuelle maskiner, der hostes i et cloudmiljø.

## <a name="monitoring-performance"></a>Overvågning af ydeevne

Du kan overvåge ydeevnen for at identificere flaskehalse. Langsomme forespørgsler – eller rapportvisualiseringer – bør være omdrejningspunktet for fortsat optimering. Overvågning kan udføres på designtidspunktet i Power BI Desktop eller på produktionsarbejdsbelastninger i Power BI Premium-kapaciteter. Du kan finde flere oplysninger under [Overvågning af rapportens ydeevne i Power BI](monitor-report-performance.md).

## <a name="next-steps"></a>Næste trin

Du kan finde flere oplysninger om denne artikel i følgende ressourcer:

- [Power BI-vejledning](index.yml)
- [Overvågning af rapportens ydeevne](monitor-report-performance.md)
- Whitepaper: [Planlægning af en Power BI Enterprise-udrulning](https://go.microsoft.com/fwlink/?linkid=2057861)
- Har du spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
- Forslag? [Få ideer til at forbedre Power BI](https://ideas.powerbi.com/)




