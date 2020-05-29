---
title: Brug DirectQuery med dataflow i Power BI (prøveversion)
description: Lær, hvordan du bruger DirectQuery med dataflow i Power BI
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/19/2020
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: 9de8c9611b24eaa627b3ddf044f13d36d7b9a3d4
ms.sourcegitcommit: 250242fd6346b60b0eda7a314944363c0bacaca8
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 05/20/2020
ms.locfileid: "83694567"
---
# <a name="use-directquery-with-dataflows-in-power-bi-preview"></a>Brug DirectQuery med dataflow i Power BI (prøveversion)

Du kan bruge DirectQuery til at oprette direkte forbindelse til dataflow og dermed oprette direkte forbindelse til dit dataflow uden at skulle importere dets data. 

Brug af DirectQuery med dataflow muliggør følgende forbedringer af dine processer for Power BI og dataflow:

* **Undgå separate opdateringsplaner** – DirectQuery opretter direkte forbindelse til et dataflow, hvilket fjerner behovet for at oprette et datasæt. Derfor betyder brug af DirectQuery med dine dataflow, at du ikke længere har brug for separate opdateringsplaner for dataflowet og datasættet for at sikre, at dine data er synkroniseret.

* **Filtrering af data** – DirectQuery er nyttig til at arbejde med en filtreret visning af dataene i et dataflow. Hvis du vil filtrere data og dermed arbejde med en mindre delmængde af dataene, kan du bruge DirectQuery (og beregningsprogrammet) til at filtrere data i dataflow og arbejde med den filtrerede delmængde, du har brug for.


## <a name="using-directquery-for-dataflows"></a>Brug af DirectQuery til dataflow

Brug af DirectQuery med dataflow er en prøveversionsfunktion, som blev tilgængelig med Power BI Desktop-versionen fra maj 2020. 

Der er også nogle forudsætninger for at bruge DirectQuery med dataflow:

* Dit dataflow skal befinde sig i et Power BI Premium-aktiveret arbejdsområde
* **Beregningsprogrammet** skal være slået til. Du kan finde flere oplysninger om beregningsprogrammet under [det forbedrede beregningsprogram](service-dataflows-enhanced-compute-engine.md).

## <a name="enable-directquery-for-dataflows"></a>Aktivér DirectQuery til dataflow

Det forbedrede beregningsprogram skal være i sin optimerede tilstand for at sikre, at dit dataflow er tilgængeligt til DirectQuery-adgang. Du aktiverer DirectQuery til dataflow ved at angive den nye indstilling **Forbedret beregningsprogram** til **Optimeret**. På følgende billede kan du se, hvordan indstillingen er korrekt valgt.

![Aktivér det forbedrede beregningsprogram til dataflow](media/service-dataflows-directquery/dataflows-directquery-01.png)

Når du har anvendt denne indstilling, skal du opdatere dataflowet, før optimeringen træder i kraft. 


## <a name="considerations-and-limitations"></a>Overvejelser og begrænsninger

Der er nogle få kendte begrænsninger med DirectQuery og dataflow, som forklaret på følgende liste.

* DirectQuery til dataflow fungerer ikke med prøveversionsfunktionen **forbedrede metadata** aktiveret. Denne udeladelse forventes at blive fjernet i en kommende månedlig udgivelse af Power BI Desktop.
* I prøveperioden for denne funktion kan nogle kunder opleve timeout eller problemer med ydeevnen, når de bruger DirectQuery med dataflow. Sådanne problemer bliver aktivt håndteret i prøveperioden.


## <a name="next-steps"></a>Næste trin

Følgende artikler indeholder nyttige oplysninger og scenarier, når du bruger dataflow:

* [Selvbetjent dataforberedelse med dataflow](service-dataflows-overview.md)
* [Brug af beregnede objekter i Power BI Premium](service-dataflows-computed-entities-premium.md)
* [Brug af dataflow med datakilder i det lokale miljø](service-dataflows-on-premises-gateways.md)
* [Udviklerressourcer til Power BI-dataflow](service-dataflows-developer-resources.md)
* [Integration af dataflow og Azure Data Lake (prøveversion)](service-dataflows-azure-data-lake-integration.md)

Du kan finde flere oplysninger om Common Data Model i denne oversigtsartikel:
* [Common Data Model – oversigt](https://docs.microsoft.com/powerapps/common-data-model/overview)
* [Få mere at vide om Common Data Model-skemaet og objekter på GitHub](https://github.com/Microsoft/CDM)

Relaterede artikler om Power BI Desktop:

* [Opret forbindelse til datasæt i Power BI-tjenesten fra Power BI Desktop](../connect-data/desktop-report-lifecycle-datasets.md)
* [Oversigt over forespørgsler i Power BI Desktop](desktop-query-overview.md)

Relaterede artikler om Power BI-tjenesten:
* [Konfigurering af planlagt opdatering](../connect-data/refresh-scheduled-refresh.md)