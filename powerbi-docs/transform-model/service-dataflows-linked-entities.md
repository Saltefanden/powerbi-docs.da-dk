---
title: Link objekter mellem dataflow i Power BI
description: Få mere at vide om, hvordan du linke objekter i dataflow i Power BI
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 01/08/2020
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: 608389e10e225517d6e50c14058732cf5fedb16f
ms.sourcegitcommit: 9350f994b7f18b0a52a2e9f8f8f8e472c342ea42
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 09/22/2020
ms.locfileid: "90861055"
---
# <a name="link-entities-between-dataflows-in-power-bi"></a>Link objekter mellem dataflow i Power BI

Med dataflow i Power BI kan du have en enkelt lagerkilde med organisationsdata, hvor forretningsanalytikere kan forberede og administrere deres data én gang og derefter genbruge dem i forskellige analyseapps i organisationen. 

Når du linker objekter mellem dataflow, kan du genbruge objekter, der allerede er blevet indført, renset og transformeret af andre dataflow, som ejes af andre, uden at der er behov for at vedligeholde disse data. Du skal bare pege de linkede objekter på objekter i andre dataflow og *undlade* at kopiere eller duplikere dataene.

![Linkede objekter i Power BI](media/service-dataflows-linked-entities/linked-entities_00.png)

Linkede objekter er **skrivebeskyttet**. Hvis du vil oprette transformationer for et linket objekt, skal du oprette et nyt beregnet objekt med en reference til det linkede objekt.

## <a name="linked-entity-availability"></a>Tilgængelighed af linket objekt

Der kræves et [Power BI Premium](../admin/service-premium-what-is.md)-abonnement for at opdatere linkede objekter. Linkede objekter er tilgængelige i et hvilket som helst dataflow i et arbejdsområde, der er hostet på Power BI Premium-kapaciteten. Der er ingen begrænsninger på kildedataflowet.

Linkede objekter fungerer kun korrekt i nye Power BI-arbejdsområder. Du kan få mere at vide om [nye Power BI-arbejdsområder](../collaborate-share/service-create-the-new-workspaces.md). Alle linkede dataflow skal findes i nye arbejdsområder, for at de fungerer korrekt.

> [!NOTE]
> Objekter varierer, afhængigt af om de er standardenheder eller beregnede enheder. Standardobjekter (ofte blot kaldet objekter) forespørger en ekstern datakilde, f.eks. en SQL-database. Beregnede objekter kræver Premium-kapacitet på Power BI og kører deres transformationer på data, der er allerede i Power BI-lageret. 
>
>Hvis dit dataflow ikke er i et arbejdsområde til Premium-kapacitet, kan du stadig henvise til en enkelt forespørgsel eller kombinere to eller flere forespørgsler, så længe transformationerne ikke er defineret som transformationer i lageret. Disse henvisninger betragtes som standardobjekter. Hvis du vil gøre det, skal du slå indstillingen **Aktivér indlæsning** fra for de forespørgsler, der henvises til, for at forhindre, at dataene materialiseres og overføres til lageret. Herfra kan du henvise til de forespørgsler af typen **Aktivér indlæsning = falsk** og kun angive **Aktivér indlæsning** til **Til** for de forespørgselsresultater, du vil materialisere.


## <a name="how-to-link-entities-between-dataflows"></a>Sådan linker du objekter mellem dataflow

Der er flere måder, du kan linke objekter på mellem dataflow i Power BI. Du kan vælge **Tilføj linkede objekter** i værktøjet til oprettelse af dataflow, som vist på følgende billede. 

![Linkede objekter i Power BI](media/service-dataflows-linked-entities/linked-entities_00.png)

Du kan også vælge **Tilføj linkede objekter** i menupunktet **Tilføj objekter** i Power BI-tjenesten.

![Linkede objekter i Power BI](media/service-dataflows-linked-entities/linked-entities_01.png)

Hvis du vil linke objekter, skal du logge på med dine legitimationsoplysninger til Power BI.

Der åbnes et **Navigator**-vindue, hvor du kan vælge et sæt objekter, som du kan oprette forbindelse til. De viste objekter er objekter, du kan have tilladelser til på tværs af alle arbejdsområder i din Power BI-lejer. 

Når dine linkede objekter er valgt, vises de på listen over objekter for dit dataflow i oprettelsesværktøjet, hvor de identificeres som linkede objekter af et særligt ikon.

Du kan også få vist kildedataflowet via dataflowindstillingerne for dit linkede objekt.

## <a name="refresh-logic-of-linked-entities"></a>Opdater logik i forbindelse med linkede objekter
Den opdateringslogik, der anvendes som standard for linkede objekter, ændres alt efter, om kildedataflowet er placeret i samme arbejdsområde som destinationsdataflowet. I følgende afsnit beskrives funktionaliteten af hver enkelt af disse.

### <a name="links-between-workspaces"></a>Links mellem arbejdsområder

Opdatering af links fra objekter i forskellige arbejdsområder, der fungerer som en ekstern datakilde. Når dataflowet opdateres, tager det de nyeste data for objektet fra kildedataflowet. Hvis kildedataflowet opdateres, påvirker det ikke automatisk dataene i destinationsdataflowet.

### <a name="links-in-the-same-workspace"></a>Links i samme arbejdsområde

Når dataene for et kildedataflow opdateres, udløser hændelsen automatisk en opdateringsproces for afhængige objekter i alle desinationsdataflow i samme arbejdsområde, herunder alle beregnede objekter, der er baseret på dem. Alle andre objekter i destinationsdataflowet opdateres i henhold til en tidsplan for dataflowet. Objekter, der afhænger af mere end én kilde, opdaterer deres data, når en af deres kilder opdateres.

Det er værd at bemærke, at hele opdateringsprocessen udføres på én gang. Hvis opdateringen af destinationsdataflowet mislykkes, vil opdateringen af kildedataflowet derfor også mislykkes.

## <a name="permissions-when-viewing-reports-from-dataflows"></a>Tilladelser i forbindelse med visning af rapporter fra dataflow

Når du opretter en Power BI-rapport, der indeholder data, som er baseret på et dataflow, kan brugerne kun se alle linkede objekter, når brugeren har adgang til kildedataflowet.

## <a name="limitations-and-considerations"></a>Begrænsninger og overvejelser

Der er nogle få begrænsninger, som du skal være opmærksom på, når du arbejder med linkede objekter:

* Der er et maksimum på fem refererencehops
* Cykliske afhængigheder af sammenkædede objekter er ikke tilladt
* Dataflowet skal være placeret i et [nyt Power BI-arbejdsområde](../collaborate-share/service-create-the-new-workspaces.md)
* Et linket objekt kan ikke joinforbindes med et almindeligt objekt, der får sine data fra en datakilde i det lokale miljø
* Når en forespørgsel (f.eks. forespørgsel A) bruges i beregningen af en anden forespørgsel (forespørgsel B) i dataflows, bliver forespørgsel B en beregnet enhed. Beregnede enheder kan ikke referere til kilder i det lokale miljø.


## <a name="next-steps"></a>Næste trin

Følgende artikler kan være nyttige, når du opretter eller arbejder med dataflow. 

* [Selvbetjent dataforberedelse i Power BI](service-dataflows-overview.md)
* [Opret og brug dataflow i Power BI](service-dataflows-create-use.md)
* [Brug af beregnede objekter i Power BI Premium](service-dataflows-computed-entities-premium.md)
* [Brug af dataflow med datakilder i det lokale miljø](service-dataflows-on-premises-gateways.md)
* [Udviklerressourcer til Power BI-dataflow](service-dataflows-developer-resources.md)

Du kan finde flere oplysninger om Power-forespørgsel og planlagt opdatering i disse artikler:
* [Oversigt over forespørgsler i Power BI Desktop](desktop-query-overview.md)
* [Konfiguration af planlagt opdatering](../connect-data/refresh-scheduled-refresh.md)

Du kan finde flere oplysninger om Common Data Model i denne oversigtsartikel:
* [Common Data Model – oversigt](/powerapps/common-data-model/overview)