---
title: Brug af forbedrede metadata for datasæt i Power BI Desktop
description: I denne artikel beskrives det, hvordan du bruger forbedrede metadata for datasæt i Power BI.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: conceptual
ms.date: 12/08/2020
LocalizationGroup: Connect to data
ms.openlocfilehash: 661e50617094d396e8beb887ac0e4a27c28c2ca7
ms.sourcegitcommit: 30d0668434283c633bda9ae03bc2aca75401ab94
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/09/2020
ms.locfileid: "96906956"
---
# <a name="using-enhanced-dataset-metadata"></a>Brug af forbedrede metadata for datasæt

Når der oprettes rapporter i Power BI Desktop, oprettes der også metadata for datasæt i de tilsvarende PBIX- og PBIT-filer. Tidligere blev metadataene lagret i et format, der var specifikt for Power BI Desktop. Metadataene brugte base-64-kodede M-udtryk og datakilder. Power BI formodede, hvordan disse metadata blev gemt.

Med udgivelsen af funktionen til **forbedrede metadata for datasæt** er mange af disse begrænsninger fjernet. PBIX-filer opgraderes automatisk til forbedrede metadata, når filen åbnes. Når funktionen til **forbedrede metadata for datasæt** er aktiveret, bruger metadata, der er oprettet af Power BI Desktop, et format, der ligner det, der bruges til tabellariske Analysis Services-modeller, baseret på den [tabellariske objektmodel](/analysis-services/tom/introduction-to-the-tabular-object-model-tom-in-analysis-services-amo).


Funktionen til **forbedrede metadata for datasæt** er strategisk og grundlæggende. Fremtidens Power BI-funktionalitet bliver bygget på dens metadata. Denne anden funktionalitet vil drage fordel af forbedrede metadata for datasæt:

- [Læsning/skrivning af XMLA](/power-platform-release-plan/2019wave2/business-intelligence/xmla-readwrite) til administration af Power BI-datasæt
- Migrering af Analysis Services-arbejdsbelastninger til Power BI for at drage fordel af fremtidens funktioner.

## <a name="limitations"></a>Begrænsninger
Før understøttelsen af forbedrede metadata føjede Power BI Desktop en oprindelig forespørgsel til datamodellen for SQL Server, Oracle, Teradata og ældre HANA-forbindelser. Denne forespørgsel bruges af datamodeller i Power BI-tjenesten. Med understøttelsen af forbedrede metadata gendanner datamodellen i Power BI-tjenesten den oprindelige forespørgsel på kørselstidspunktet. Den bruger ikke den forespørgsel, som Power BI Desktop oprettede. I de fleste tilfælde vil denne hentning løse sig selv korrekt, men nogle transformationer fungerer ikke, uden at de underliggende data læses. Du ser måske nogle fejl i rapporter, der tidligere fungerede. Der står f.eks. i fejlmeddelelsen: 

"En M-forespørgsel kunne ikke konverteres til en oprindelig kildeforespørgsel i tabellen "Dimensionsby". Prøv igen senere, eller kontakt support. Hvis du kontakter support, skal du angive disse oplysninger." 

Du kan løse problemer med dine forespørgsler tre forskellige steder i Power BI Desktop:

- Når du anvender ændringer eller foretager en opdatering.
- På en advarselslinje i Power Query-editor, hvor du får besked om, at udtrykket ikke kan foldes til datakilden.
    :::image type="content" source="media/desktop-enhanced-dataset-metadata/enhanced-metadata-apply-query-changes.png" alt-text="Skærmbillede af meddelelsen Anvend ændringer af forespørgsel: Det var ikke muligt at folde udtrykket til datakilden.":::
- Når du kører evalueringer i forbindelse med åbning af en rapport for at kontrollere, om du har forespørgsler, der ikke understøttes. Kørsel af disse evalueringer kan resultere i konsekvenser for ydeevnen.


## <a name="next-steps"></a>Næste trin

Du kan gøre mange forskellige ting med Power BI Desktop. Du kan finde flere oplysninger om funktionerne i følgende ressourcer:

* [Hvad er Power BI Desktop?](../fundamentals/desktop-what-is-desktop.md)
* [Nyheder i Power BI Desktop](../fundamentals/desktop-latest-update.md)
* [Oversigt over forespørgsler i Power BI Desktop](../transform-model/desktop-query-overview.md)
* [Datatyper i Power BI Desktop](desktop-data-types.md)
* [Udform og kombiner data med Power BI Desktop](desktop-shape-and-combine-data.md)
* [Almindelige forespørgselsopgaver i Power BI Desktop](../transform-model/desktop-common-query-tasks.md)
