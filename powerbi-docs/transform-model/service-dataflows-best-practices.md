---
title: Bedste fremgangsmåder i forbindelse med Power BI-dataflows
description: Bedste fremgangsmåder i forbindelse med Power BI-dataflows
author: mohaali
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 09/19/2019
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: d4b23039d8516375e98233254c92b2f7bbeb648d
ms.sourcegitcommit: 9350f994b7f18b0a52a2e9f8f8f8e472c342ea42
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 09/22/2020
ms.locfileid: "90861607"
---
# <a name="dataflows-best-practice"></a>Bedste fremgangsmåder i forbindelse med dataflows

Denne artikel indeholder oplysninger om de bedste fremgangsmåder i forbindelse med dataflows i Power BI. Du kan bruge denne vejledning til at få mere at vide om, hvordan du opretter dataflows og anvende disse fremgangsmåder på dine egne dataflows.

> [!NOTE]
> De anbefalinger, der er angivet i denne artikel, er retningslinjer. Der kan være legitime grunde til at afvige fra denne vejledning for den enkelte bedste fremgangsmåde i denne artikel. 
> 
> 

### <a name="split-ingestion-and-transformation-to-use-the-enhanced-compute-engine"></a>Opdel dataindtagelse og transformering for at bruge det forbedrede beregningsprogram

Når du opretter dataflows, kan du blive fristet til at oprette en enkelt dataflow med alle enheder, transformationer, joinforbindelser og forbedringer på ét sted. For mindre datasæt kan et enkelt dataflow være effektivt. Men når det drejer sig om større datamængder, kan joinforbindelser eller visse transformationer nogle gange resultere i begrænsninger eller hukommelsesgrænser. For at løse disse problemer har vi udgivet et forbedret program til Power BI Premium-brugere, der kan skaleres til meget større datamængder. Det forbedrede beregningsprogram fungerer kun i forbindelse med sammenkædede eller beregnede enheder, så oprettelsen af et separat dataflow til dataindtagelse og et sammenkædet dataflow til at udføre alle de komplekse fletninger og transformationer kan drage fordel af det forbedrede program.

Det er også en fordel at opdele dataflows for at diagnosticere og foretage fejlfinding af opdateringsproblemer, især når du arbejder med kilder, der har begrænsninger.

### <a name="perform-actions-that-can-use-the-enhanced-compute-engine"></a>Udfør handlinger, der kan bruge det forbedrede beregningsprogram

Sørg for, at du bruger det forbedrede beregningsprogram ved at sikre, at du udfører joinforbindelser og filtrerer transformationer i en beregnet enhed først, før du udfører andre typer transformationer.

### <a name="split-dataflows-when-connecting-to-sharepoint"></a>Opdel dataflows, når der oprettes forbindelse til SharePoint

Når du arbejder med SharePoint og opretter forbindelse til flere filer, kan der opstå sporadiske fejl. SharePoint begrænser anmodninger for at sikre, at programmet forbliver pålideligt og dynamisk. Når du opretter forbindelse til Excel-filer fra SharePoint, kan du derfor være tilbøjelig til at hente alle filer i et enkelt dataflow. Hvis du henter mange filer, mere end 20, skal du oprette to dataflows eller mere for at opdele opdateringsbelastningen og afhjælpe begrænsningen i SharePoint.

### <a name="avoid-scheduling-refresh-for-linked-entities-inside-the-same-workspace"></a>Undgå at planlægge opdatering af sammenkædede enheder i det samme arbejdsområde

Hvis du jævnligt låses ud af dine dataflows, der indeholder sammenkædede enheder, er det muligvis et resultat af, at tilsvarende afhængige dataflow i det samme arbejdsområde låses under opdateringen af dataflowet. En sådan låsning sikrer transaktionsnøjagtighed og at begge dataflows opdateres, men den kan forhindre dig i at redigere. 

Hvis du konfigurerer en separat tidsplan for det sammenkædede dataflow, kan dataflows blive unødvendigt opdateret og forhindre dig i at redigere dataflowet. Der er to anbefalinger til at undgå dette problem: 

* Undgå at angive en tidsplan for opdatering af et sammenkædet dataflow i det samme arbejdsområde som kildedataflowet
* Hvis du vil konfigurere en tidsplan for opdatering separat, og du vil undgå at låse funktionsmåden, skal du adskille dataflowet i et separat arbejdsområde.

### <a name="create-a-separate-workspace-for-ingestion-transformation"></a>Opret et separat arbejdsområde til dataindtagelse og transformation

Hvis du vil give adgang til data i underliggende dataflow for mange brugere, uden at du skal give adgang til rådata for det underliggende kildesystem, skal du oprette et separat arbejdsområde, der indeholder alle de data, du har brug for at dele, og tildele tilladelser. Individuelle tilladelser til dataflow understøttes ikke i øjeblikket.

### <a name="ensure-capacity-is-in-the-same-region"></a>Sørg for, at kapaciteten er i det samme område

Dataflows understøtter i øjeblikket ikke flere geografiske områder. Premium-kapaciteten skal oprettes i det samme område som din Power BI-lejer.

### <a name="separate-on-premises-sources-from-cloud-sources"></a>Adskil kilder i det lokale miljø fra kilder i cloudmiljøet

Ud over de tidligere beskrevne bedste fremgangsmåder kan du oprette et separat dataflow for hver kildetype, f.eks. i det lokale miljø, i cloudmiljøet, på SQL Server, i Spark, Dynamics osv. Det anbefales på det kraftigste at opdele dit dataflow efter datakildetype. En sådan adskillelse efter kildetype gør det muligt hurtigt at foretage fejlfinding og undgå interne grænser ved opdatering af dine dataflows.

### <a name="separate-dataflows-into-a-separate-capacity"></a>Adskil dataflows i en separat kapacitet

Hvis du oplever begrænsninger, eller hvis du oplever almindelige fejl på dine dataflows på grund af hukommelsesgrænser for din kapacitet, kan du overveje at adskille dine dataflows eller skalere din Premium-kapacitet til ekstra hukommelse.

## <a name="next-steps"></a>Næste trin

I denne artikel kan du finde oplysninger om de bedste fremgangsmåder til dataflows. Du kan finde flere oplysninger om dataflow i følgende artikler:

* [Selvbetjent dataforberedelse med dataflow](service-dataflows-overview.md)
* [Opret og brug dataflow i Power BI](service-dataflows-create-use.md)
* [Brug af beregnede objekter i Power BI Premium](service-dataflows-computed-entities-premium.md)
* [Brug af dataflow med datakilder i det lokale miljø](service-dataflows-on-premises-gateways.md)

Du kan finde oplysninger om CDM udviklings- og selvstudium ressourcer her:
* [Common Data Model – oversigt](/powerapps/common-data-model/overview)
* [CDM-mapper](/common-data-model/data-lake)
* [Definition af CDM-modelfil](/common-data-model/model-json)


Du kan finde flere oplysninger om Power-forespørgsel og planlagt opdatering i disse artikler:
* [Oversigt over forespørgsler i Power BI Desktop](desktop-query-overview.md)
* [Konfiguration af planlagt opdatering](../connect-data/refresh-scheduled-refresh.md)