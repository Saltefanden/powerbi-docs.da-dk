---
title: Bedste praksis i forbindelse med dataflow
description: En samling af links til bedste praksis og vejledning til dataflow
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 11/13/2020
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: 5adfcc3d4ff7d78335f250b92b856bcd14d64c0a
ms.sourcegitcommit: bd133cb1fcbf4f6f89066165ce065b8df2b47664
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 11/17/2020
ms.locfileid: "94674733"
---
# <a name="dataflows-best-practices"></a>Bedste praksis i forbindelse med dataflow

Power BI-**dataflow** er en løsning til dataforberedelse i virksomheden, som gør det muligt at aktivere et økosystem af data, der er klar til forbrug, genbrug og integration. Denne artikel indeholder en liste over den bedste praksis med links til artikler og andre oplysninger, der kan hjælpe dig med at forstå og få mest muligt ud af dataflow.


## <a name="dataflows-best-practices-table-and-links"></a>Tabel over links til bedste praksis i forbindelse med dataflow

Følgende tabel indeholder en samling links til artikler, der beskriver den bedste praksis du opretter eller arbejder med dataflow. Linkene indeholder oplysninger om udvikling af forretningslogik, udvikling af komplekse dataflow, genbrug af dataflow, og hvordan du kan opnå skalering på virksomhedsniveau med din dataflow.


|**Emne**  |**Vejledningsområde**  |**Link til artikel eller indhold**  |
|---------|---------|---------|
|Power-forespørgsel     | Tip og tricks til at få mest muligt ud af din data-wrangling-oplevelse        |[Bedste praksis i Power Query](https://docs.microsoft.com/power-query/best-practices)        |
|Brug af beregnede enheder     |Der er ydeevnefordele ved at bruge beregnede enheder i et dataflow         |[Scenarie med beregnede enheder](https://docs.microsoft.com/power-query/dataflows/computed-entities-scenarios)         |
|Udvikling af komplekse dataflow     |Mønstre til udvikling af dataflow i stor skala med høj ydeevne         |[Komplekse dataflow](https://docs.microsoft.com/power-query/dataflows/best-practices-developing-complex-dataflows)         |
|Genbrug af dataflow     |Mønstre, vejledning og use cases         |[Genbrug af dataflow](https://docs.microsoft.com/power-query/dataflows/best-practices-reusing-dataflows)         |
|Implementeringer i stor skala     |Brug i stor skala og vejledning til, hvordan virksomhedsarkitekturen suppleres         |[Data warehousing ved hjælp af dataflow](https://docs.microsoft.com/power-query/dataflows/best-practices-for-data-warehouse-using-dataflows)         |
|Brug af forbedret beregning     |Du kan forbedre dataflowydeevnen op til 25 gange         |[Forbedret beregningsprogram](dataflows-premium-workload-configuration.md#using-the-compute-engine-to-improve-performance)         |
|Optimering af indstillingerne for arbejdsbelastning     |Få mest muligt ud af din dataflowinfrastruktur ved at forstå de parametre, du kan påvirke for at maksimere ydeevnen         |[Konfiguration af dataflowarbejdsbelastning](dataflows-premium-workload-configuration.md)         |
|Sammenføjning og udvidelse af tabeller     |Oprettelse af joinforbindelser med høj ydeevne         |[Optimer handlinger til udvidelse af tabeller](https://docs.microsoft.com/power-query/optimize-expanding-table-columns)         |
|Vejledning til forespørgselsfoldning     |Sådan sætte rdu fart i transformationer ved hjælp af kildesystemet         |[Forespørgselsfoldning](https://docs.microsoft.com/power-query/power-query-folding)         |
|Brug af dataprofilering     |Om kolonnekvalitet, -distribution og -profil         |[Værktøjer til dataprofilering](https://docs.microsoft.com/power-query/data-profiling-tools)         |
|Implementering af fejlhåndtering     |Udvikling af robuste dataflow, der er modstandsdygtige over for opdateringsfejl, med forslag         |[Mønstre for almindelige fejl](https://docs.microsoft.com/power-query/dealing-with-errors)  </br> [Kompleks fejlhåndtering](https://docs.microsoft.com/power-query/error-handling)      |
|Brug skemavisning      |Få bedre oprettelsesmuligheder, når du arbejder med en bred tabel og udfører handlinger på skemaniveau         |[Skemavisning](https://docs.microsoft.com/power-query/schema-view)         |
|||


        
## <a name="next-steps"></a>Næste trin

Du kan finde flere oplysninger om dataflow og Power BI i følgende artikler:

* [Introduktion til dataflow og selvbetjent dataforberedelse](dataflows-introduction-self-service.md)
* [Oprettelse af et dataflow](dataflows-create.md)
* [Konfigurer og brug et dataflow](dataflows-configure-consume.md)
* [Premium-funktioner for dataflow](dataflows-premium-features.md)
* [Konfiguration af dataflowlager til brug af Azure Data Lake Gen 2](dataflows-azure-data-lake-storage-integration.md)
* [AI med dataflow](dataflows-machine-learning-integration.md)
* [Begrænsninger og overvejelser i forbindelse med dataflow](dataflows-features-limitations.md)