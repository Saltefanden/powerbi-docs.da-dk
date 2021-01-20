---
title: Bedste praksis i forbindelse med dataflow
description: En samling af links til bedste praksis og vejledning til dataflow
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-dataflows
ms.topic: how-to
ms.date: 12/10/2020
LocalizationGroup: Data from files
ms.openlocfilehash: fb688b20fd8b5ee1288f670fba9f7f45fc058680
ms.sourcegitcommit: 1cad78595cca1175b82c04458803764ac36e5e37
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 01/19/2021
ms.locfileid: "98565360"
---
# <a name="dataflows-best-practices"></a>Bedste praksis i forbindelse med dataflow

Power BI-**dataflow** er en løsning til dataforberedelse i virksomheden, som gør det muligt at aktivere et økosystem af data, der er klar til forbrug, genbrug og integration. Denne artikel indeholder en liste over den bedste praksis med links til artikler og andre oplysninger, der kan hjælpe dig med at forstå og få mest muligt ud af dataflow.

## <a name="dataflows-across-the-power-platform"></a>Dataflow på tværs af Power Platform

Dataflow kan bruges på tværs af forskellige Power Platform-teknologier, f.eks. Power Query, Microsoft Dynamics 365 og andre Microsoft-tilbud. Du kan finde flere oplysninger om, hvordan dataflow kan fungere på tværs af Power Platform, under [brug af dataflow på tværs af Microsoft-produkter](/power-query/dataflows/overview-dataflows-across-power-platform-dynamics-365).


## <a name="dataflows-best-practices-table-and-links"></a>Tabel over links til bedste praksis i forbindelse med dataflow

Følgende tabel indeholder en samling links til artikler, der beskriver den bedste praksis du opretter eller arbejder med dataflow. Linkene indeholder oplysninger om udvikling af forretningslogik, udvikling af komplekse dataflow, genbrug af dataflow, og hvordan du kan opnå skalering på virksomhedsniveau med din dataflow.


|**Emne**  |**Vejledningsområde**  |**Link til artikel eller indhold**  |
|---------|---------|---------|
|Power-forespørgsel     | Tip og tricks til at få mest muligt ud af din data-wrangling-oplevelse        |[Bedste praksis i Power Query](/power-query/best-practices)        |
|Brug af beregnede enheder     |Der er ydeevnefordele ved at bruge beregnede enheder i et dataflow         |[Scenarier med beregnede enheder](/power-query/dataflows/computed-entities-scenarios)         |
|Udvikling af komplekse dataflow     |Mønstre til udvikling af dataflow i stor skala med høj ydeevne         |[Komplekse dataflow](/power-query/dataflows/best-practices-developing-complex-dataflows)         |
|Genbrug af dataflow     |Mønstre, vejledning og use cases         |[Genbrug af dataflow](/power-query/dataflows/best-practices-reusing-dataflows)         |
|Implementeringer i stor skala     |Brug i stor skala og vejledning til, hvordan virksomhedsarkitekturen suppleres         |[Data warehousing ved hjælp af dataflow](/power-query/dataflows/best-practices-for-data-warehouse-using-dataflows)         |
|Brug af forbedret beregning     |Du kan forbedre dataflowydeevnen op til 25 gange         |[Forbedret beregningsprogram](dataflows-premium-workload-configuration.md#using-the-compute-engine-to-improve-performance)         |
|Optimering af indstillingerne for arbejdsbelastning     |Få mest muligt ud af din dataflowinfrastruktur ved at forstå de parametre, du kan påvirke for at maksimere ydeevnen         |[Konfiguration af dataflowarbejdsbelastning](dataflows-premium-workload-configuration.md)         |
|Sammenføjning og udvidelse af tabeller     |Oprettelse af joinforbindelser med høj ydeevne         |[Optimer handlinger til udvidelse af tabeller](/power-query/optimize-expanding-table-columns)         |
|Vejledning til forespørgselsfoldning     |Sådan sætte rdu fart i transformationer ved hjælp af kildesystemet         |[Forespørgselsfoldning](/power-query/power-query-folding)         |
|Brug af dataprofilering     |Om kolonnekvalitet, -distribution og -profil         |[Værktøjer til dataprofilering](/power-query/data-profiling-tools)         |
|Implementering af fejlhåndtering     |Udvikling af robuste dataflow, der er modstandsdygtige over for opdateringsfejl, med forslag         |[Mønstre for almindelige fejl](/power-query/dealing-with-errors)  </br> [Kompleks fejlhåndtering](/power-query/error-handling)      |
|Brug skemavisning      |Få bedre oprettelsesmuligheder, når du arbejder med en bred tabel og udfører handlinger på skemaniveau         |[Skemavisning](/power-query/schema-view)         |
|Sammenkædede enheder      |Genbrug og reference til transformationer         |[Sammenkædede enheder](/power-query/dataflows/linked-entities)         |
|Trinvis opdatering      |Indlæs de nyeste eller ændrede data i forhold til en fuld genindlæsning         |[Trinvis opdatering](/power-query/dataflows/incremental-refresh)         |
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