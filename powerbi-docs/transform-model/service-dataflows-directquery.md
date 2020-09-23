---
title: Brug DirectQuery med dataflow i Power BI (prøveversion)
description: Lær, hvordan du bruger DirectQuery med dataflow i Power BI
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 05/21/2020
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: 76c42c52ba877b3e6477a2baee11aef4a531161c
ms.sourcegitcommit: 9350f994b7f18b0a52a2e9f8f8f8e472c342ea42
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 09/22/2020
ms.locfileid: "90861561"
---
# <a name="use-directquery-with-dataflows-in-power-bi-preview"></a>Brug DirectQuery med dataflow i Power BI (prøveversion)

Du kan bruge DirectQuery til at oprette direkte forbindelse til dataflow og dermed oprette direkte forbindelse til dit dataflow uden at skulle importere dets data. 

Brug af DirectQuery med dataflow muliggør følgende forbedringer af dine processer for Power BI og dataflow:

* **Undgå separate opdateringsplaner** – DirectQuery opretter direkte forbindelse til et dataflow, hvilket fjerner behovet for at oprette et importeret datasæt. Derfor betyder brug af DirectQuery med dine dataflow, at du ikke længere har brug for separate opdateringsplaner for dataflowet og datasættet for at sikre, at dine data er synkroniseret.

* **Filtrering af data** – DirectQuery er nyttig til at arbejde med en filtreret visning af dataene i et dataflow. Hvis du vil filtrere data og dermed arbejde med en mindre delmængde af dataene, kan du bruge DirectQuery (og beregningsprogrammet) til at filtrere data i dataflow og arbejde med den filtrerede delmængde, du har brug for.


## <a name="using-directquery-for-dataflows"></a>Brug af DirectQuery til dataflow

Brug af DirectQuery med dataflow er en prøveversionsfunktion, som blev tilgængelig med Power BI Desktop-versionen fra maj 2020. 

Der er også nogle forudsætninger for at bruge DirectQuery med dataflow:

* Dit dataflow skal befinde sig i et Power BI Premium-aktiveret arbejdsområde
* **Beregningsprogrammet** skal være slået til. Du kan finde flere oplysninger om beregningsprogrammet under [det forbedrede beregningsprogram](service-dataflows-enhanced-compute-engine.md).

## <a name="enable-directquery-for-dataflows"></a>Aktivér DirectQuery til dataflow

Det forbedrede beregningsprogram skal være i sin optimerede tilstand for at sikre, at dit dataflow er tilgængeligt til DirectQuery-adgang. Du aktiverer DirectQuery til dataflow ved at angive den nye indstilling **Forbedret beregningsprogram** til **Til**. På følgende billede kan du se, hvordan indstillingen er korrekt valgt.

![Aktivér det forbedrede beregningsprogram til dataflow](media/service-dataflows-directquery/dataflows-directquery-01.png)

Når du har anvendt denne indstilling, skal du opdatere dataflowet, før optimeringen træder i kraft. 


## <a name="considerations-and-limitations"></a>Overvejelser og begrænsninger

Der er nogle få kendte begrænsninger med DirectQuery og dataflow, som forklaret på følgende liste.

* I prøveperioden for denne funktion kan nogle kunder opleve timeout eller problemer med ydeevnen, når de bruger DirectQuery med dataflow. Sådanne problemer bliver aktivt håndteret i prøveperioden.

* Sammensatte/blandede modeller, der har import- og DirectQuery-datakilder, understøttes ikke i øjeblikket.

* Store dataflow kan have problemer med timeout ved visning af visualiseringer. Denne begrænsning forventes at blive fjernet som en del af denne funktions generelle tilgængelighed. Samtidig bør store dataflow, hvor der er problemer med timeout, bruge importtilstand.

* Under indstillinger for datakilde viser dataflow-connectoren ugyldige legitimationsoplysninger, hvis du bruger DirectQuery. Dette påvirker ikke funktionsmåden, og datasættet fungerer korrekt. Dette problem vil blive løst, når funktionen bliver offentlig tilgængelig.



## <a name="next-steps"></a>Næste trin

Følgende artikler indeholder nyttige oplysninger og scenarier, når du bruger dataflow:

* [Selvbetjent dataforberedelse med dataflow](service-dataflows-overview.md)
* [Brug af beregnede objekter i Power BI Premium](service-dataflows-computed-entities-premium.md)
* [Brug af dataflow med datakilder i det lokale miljø](service-dataflows-on-premises-gateways.md)
* [Udviklerressourcer til Power BI-dataflow](service-dataflows-developer-resources.md)
* [Integration af dataflow og Azure Data Lake (prøveversion)](service-dataflows-azure-data-lake-integration.md)

Du kan finde flere oplysninger om Common Data Model i denne oversigtsartikel:
* [Common Data Model – oversigt](/powerapps/common-data-model/overview)
* [Få mere at vide om Common Data Model-skemaet og objekter på GitHub](https://github.com/Microsoft/CDM)

Relaterede artikler om Power BI Desktop:

* [Opret forbindelse til datasæt i Power BI-tjenesten fra Power BI Desktop](../connect-data/desktop-report-lifecycle-datasets.md)
* [Oversigt over forespørgsler i Power BI Desktop](desktop-query-overview.md)

Relaterede artikler om Power BI-tjenesten:
* [Konfigurering af planlagt opdatering](../connect-data/refresh-scheduled-refresh.md)