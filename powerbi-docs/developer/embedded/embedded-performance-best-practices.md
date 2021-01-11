---
title: Den bedste praksis i forbindelse med ydeevnen i en integreret Power BI-analyse for at få bedre integreret BI-indsigt
description: Denne artikel indeholder en vejledning til bedste praksis for integreret analyse i Power BI. Aktivér bedre integreret BI-indsigt ved hjælp af Power BI-integreret analyse.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 12/12/2018
ms.openlocfilehash: f8bf41ae9a4b6f2e16aae2c05df8fa4448a0457c
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 01/05/2021
ms.locfileid: "97888782"
---
# <a name="power-bi-embedded-analytics-performance-best-practices"></a>Bedste praksis for ydeevnen i en integreret Power BI-analyse

Denne artikel indeholder anbefalinger til hurtigere gengivelse af rapporter, dashboards og felter i dit program.

> [!Note]
> Husk, at indlæsningstiden hovedsageligt afhænger af de elementer, der er relevante for selve rapporten og dataene, herunder visualiseringer, størrelsen af dataene og kompleksiteten af forespørgslerne og de mål. Du kan finde flere oplysninger i [Optimeringsvejledning til Power BI](../../guidance/power-bi-optimization.md).

## <a name="update-tools-and-sdk-packages"></a>Opdater værktøjer og SDK-pakker

Hold værktøjer og SDK-pakker opdateret.

* Brug altid den nyeste version af [Power BI Desktop](https://powerbi.microsoft.com/desktop/).

* Installér den nyeste version af [klient-SDK'en til Power BI](https://github.com/Microsoft/PowerBI-JavaScript). Vi udgiver løbende yderligere forbedringer, så kig forbi regelmæssigt.

## <a name="embed-parameters"></a>Integrer parametre

Metoden `powerbi.embed(element, config)` modtager et element og en konfiguration. Konfigurationsparameteren indeholder felter, der har konsekvenser for ydeevnen.

### <a name="embed-url"></a>Integreret URL-adresse

Undgå at generere den integrerede URL-adresse selv. Sørg i stedet for at få den integrerede URL-adresse ved at kalde API'en for [Hent rapporter](/rest/api/power-bi/reports/getreportsingroup), [Hent dashboards](/rest/api/power-bi/dashboards/getdashboardsingroup) eller [Hent felter](/rest/api/power-bi/dashboards/gettilesingroup). Vi har føjet en ny parameter til URL-adressen kaldet **_config_**, som bruges til forbedringer af ydeevnen.

### <a name="permissions"></a>Tilladelser

Angiv tilladelsen **Vis**, hvis du ikke har til hensigt at integrere en rapport i Redigeringstilstand. På den måde initialiserer integreringskoden ikke komponenter, der bruges i Redigeringstilstand.

### <a name="filters-bookmarks-and-slicers"></a>Filtre, bogmærker og udsnit

Visualiseringer i rapporter gemmes ofte med cachelagrede data. De cachelagrede data bruges til at levere den opfattede ydeevne. Rapporter gengiver cachelagrede data, mens forespørgslerne udføres. Hvis filtre, bogmærker eller udsnit er angivet, er cachelagrede data ikke relevante, og visualiseringerne gengives først, når den visuelle forespørgsel er afsluttet.

Hvis du integrerer rapporter med de samme filtre, bogmærker og udsnit for at forbedre ydeevnen, skal du gemme rapporten med de filtre, bogmærker og udsnit, der allerede er anvendt. Dermed gengives rapporten med de cachelagrede data, hvilket omfatter de pågældende filtre, bogmærker og udsnit.

## <a name="switching-between-reports"></a>Skift mellem rapporter

Når du integrerer flere rapporter i den samme iframe, skal du ikke generere en ny iframe for hver rapport. Brug i stedet `powerbi.embed(element, config)` med en anden konfiguration for at integrere den nye rapport.

> [!NOTE]
> Hvis du skifter mellem rapporter, når du integrerer for dine kunder (også kaldet et "app ejer data"-scenarie), skal du bruge et indlejringstoken med tilladelser til alle rapporter og datasæt. Du kan finde flere oplysninger under [Opret token-API](/rest/api/power-bi/embedtoken/generatetoken).

## <a name="query-caching"></a>Cachelagring af forespørgsel

Organisationer med Power BI Premium-kapacitet eller Power BI Embedded-kapacitet kan drage fordel af cachelagring af forespørgsler for at fremskynde rapporter, der er knyttet til et datasæt.

[Få mere at vide om cachelagring af forespørgsler i Power BI](../../connect-data/power-bi-query-caching.md).

## <a name="preload"></a>Forudindlæs

Brug `powerbi.preload()` til at forbedre ydeevnen for slutbrugeren. Metoden `powerbi.preload()` downloader javascript, css-filer og andre artefakter, der senere bruges til at integrere en rapport.

Kald `powerbi.preload()`, hvis du ikke integrerer rapporten med det samme. Hvis det integrerede Power BI-indhold f.eks. ikke vises på startsiden, skal du bruge `powerbi.preload()` til at downloade og cachelagre de artefakter, der bruges til at integrere indholdet.

## <a name="bootstrapping-the-iframe"></a>Bootstrap af iframe

> [!NOTE]
> Version 2.9 af [klient-SDK'en til Power BI](https://github.com/Microsoft/PowerBI-JavaScript) er påkrævet for at udføre bootstrap af denne iframe.

`powerbi.bootstrap(element, config)` tillader, at du begynder at integrere, før alle påkrævede parametre er tilgængelige. Bootstrap-API'en forbereder og initialiserer din iframe.
Når du bruger bootstrap-API'en, skal du stadig kalde `powerbi.embed(element, config)` på det samme HTML-element.

En af denne funktions use cases er f.eks. at køre iframe bootstrap og back-end-kald til parallel integration.
> [!TIP]
> Brug bootstrap-API'en, når det er muligt at oprette en iframe, før den er synlig for slutbrugeren.

[Få mere at vide om iframe bootstrap](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Bootstrap-For-Better-Performance).

## <a name="measure-performance"></a>Mål ydeevne

### <a name="performance-events"></a>Hændelser i forbindelse med ydeevne

Hvis du vil måle den integrerede ydeevne, kan du bruge to hændelser:

1. Indlæst hændelse: Tiden, indtil rapporten er initialiseret (Power BI-logoet forsvinder, når indlæsningen er fuldført).
2. Gengivet hændelse: Tiden, indtil rapporten er fuldt gengivet med de faktiske data. Den gengivne hændelse vises, hver gang rapporten gengives igen (f.eks. efter der er anvendt filtre). Hvis du vil måle en rapport, skal du sørge for at foretage beregningerne for den første fremhævede hændelse.

Cachelagrede data gengives, når de er tilgængelige, men der genereres ingen yderligere hændelse.

[Få mere at vide om håndtering af hændelser](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Handling-Events).

### <a name="performance-analyzer"></a>Effektivitetsanalyse

Hvis du vil undersøge ydeevnen af rapportelementerne, kan du bruge Effektivitetsanalyse i Power BI Desktop.
Med Effektivitetsanalyse kan du se og registrere logge, der måler, hvordan hver af dine rapportelementer klarer sig.

[Få mere at vide om Effektivitetsanalyse](../../create-reports/desktop-performance-analyzer.md).

> [!NOTE]
> Husk altid at sammenligne ydeevnen af den integrerede rapport med ydeevnen på powerbi.com. Det kan muligvis hjælpe dig med at forstå, hvor dine problemer med ydeevnen opstod

## <a name="next-steps"></a>Næste trin

* [Optimeringsvejledning til Power BI](../../guidance/power-bi-optimization.md)
* [Sådan foretager du fejlfinding af problemer med en integreret Power BI-analyse](embedded-troubleshoot.md)
* [Ofte stillede spørgsmål om en integreret Power BI-analyse](embedded-faq.md)