---
title: Brug af beregnede objekter i Power BI Premium
description: Få mere at vide om, hvordan du bruger beregnede objekter i Power BI Premium
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 04/02/2019
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: 79ab3a38a6f1df97b445c06adf13a4b53af30d87
ms.sourcegitcommit: 9350f994b7f18b0a52a2e9f8f8f8e472c342ea42
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 09/22/2020
ms.locfileid: "90858019"
---
# <a name="using-computed-entities-on-power-bi-premium"></a>Brug af beregnede objekter i Power BI Premium

Du kan udføre **i lager-beregninger**, når du bruger **dataflow** vha. et Power BI Premium-abonnement. Dermed kan du udføre beregninger af dine eksisterende dataflow og få resultater, der giver dig mulighed for at fokusere på oprettelse af rapporter og analyser. 

![Beregnede objekter i Power BI Premium](media/service-dataflows-computed-entities-premium/computed-entities-premium_00.png)

Hvis du vil udføre **i lager-beregninger**, skal du først oprette dataflowet og hente data ind i det pågældende Power BI-dataflowlager. Når du har et dataflow, der indeholder data, kan du oprette **beregnede objekter**, som er objekter, der udfører i lager-beregninger. 

Der er to måder, du kan oprette forbindelse mellem dataflowdata og Power BI på:

* [Brug af oprettelse af et dataflow vha. selvbetjening](service-dataflows-create-use.md)
* Brug af et eksternt dataflow

I følgende afsnit beskrives, hvordan du kan oprette beregnede objekter for dine dataflowdata.

## <a name="how-to-create-computed-entities"></a>Sådan opretter du beregnede objekter 

Når du har et dataflow med en liste over objekter, kan du udføre beregninger af disse objekter.

I værktøjet til oprettelse af dataflow i Power BI-tjenesten skal du vælge **Rediger objekter**, derefter højreklikke på det objekt, du vil bruge som udgangspunkt for dit beregnede objekt, og som du vil udføre beregninger af. I genvejsmenuen skal du vælge **Reference**.

Du skal markere indstillingen **Aktivér indlæsning**, som vist på nedenstående billede, for at objektet kan vælges som beregnet objekt. Højreklik på objektet for at få vist denne genvejsmenu.

![Markér Aktivér indlæsning i genvejsmenuen](media/service-dataflows-computed-entities-premium/computed-entities-premium_01.png)

Når du markerer **Aktivér indlæsning**, opretter du et nyt objekt, hvor kilden er det refererede objekt. Ikonet ændres, og ikonet **beregnet** vises, som det fremgår af følgende billede.

![Beregnede objekter i Power BI Premium](media/service-dataflows-computed-entities-premium/computed-entities-premium_00.png)

Alle de transformationer, du udfører i forbindelse med det nyligt oprettede objekt, køres vha. de data, der allerede findes i Power BI-dataflowlageret. Det betyder, at forespørgslen ikke køres i forhold til den eksterne datakilde, som dataene blev importeret fra (f.eks. den SQL-database, dataene blev hentet fra), men i stedet udføres på de data, der er placeret i dataflowlageret.

### <a name="example-use-cases"></a>Eksempler på use cases
Hvilken type transformationer kan udføres vha. beregnede objekter? Alle transformationer, du normalt angiver vha. transformationsbrugergrænsefladen i Power BI eller M-editoren, understøttes, når du udfører i lager-beregninger. 

Se følgende eksempel: Du har et *Account*-objekt, der indeholder rådata for alle kunderne fra dit Dynamics 365-abonnement. Du har også rådata om *ServiceCalls* fra Service Center med data fra supportopkald, der blev udført fra den anden konto hver dag hele året.

Forestil dig, at du vil forbedre *Account*-objektet med data fra disse *ServiceCalls*. 

Først skal du samle dataene fra ServiceCalls for at beregne antallet af supportopkald, der blev udført for hver konto i det seneste år. 

![Eksempel på et beregnet objekt i Power BI Premium](media/service-dataflows-computed-entities-premium/computed-entities-premium_02.png)

Derefter vil du flette *Account*-objektet med *ServiceCallsAggregated*-objektet for at beregne den forbedrede **Account**-tabel.

![Eksempel på et beregnet objekt i Power BI Premium](media/service-dataflows-computed-entities-premium/computed-entities-premium_03.png)

Derefter kan du se resultaterne, der vises som *EnrichedAccount* på følgende billede.

![Resultaterne for et beregnet objekt i Power BI Premium](media/service-dataflows-computed-entities-premium/computed-entities-premium_04.png)

Og det er det – transformationen er udført vha. dataene i det dataflow, der er placeret i dit Power BI Premium-abonnement, og ikke på kildedataene.

## <a name="considerations-and-limitations"></a>Overvejelser og begrænsninger

Det er vigtigt at bemærke, at hvis du fjerner arbejdsområdet fra Power BI Premium-kapaciteten, opdateres det tilknyttede dataflow ikke længere. 

Når du arbejder med dataflow, der specifikt er oprettet i en organisations Azure Data Lake Storage Gen2-konto, fungerer tilknyttede enheder og beregnede enheder kun korrekt, når enhederne er placeret i samme lagerkonto. Du kan finde flere oplysninger under [Opret forbindelse til Azure Data Lake Storage Gen2 til dataflowlager (eksempelvisning)](service-dataflows-connect-azure-data-lake-storage-gen2.md).

Linkede objekter ikke tilgængelige for dataflow, der er oprettet via CDM-mapper (Common Data Model). Du kan få flere oplysninger under [Føj en CDM-mappe til Power BI som et dataflow (eksempelvisning)](service-dataflows-add-cdm-folder.md).

Når du udfører beregninger af data, der er joinforbundet i det lokale miljø, og clouddata, skal du som bedste praksis oprette et nyt objekt for at udføre disse beregninger. Dette giver en bedre oplevelse, end når du bruger et eksisterende objekt til beregninger, f.eks. et objekt, der også forespørger om data fra begge kilder og udfører lake-transformationer.

## <a name="next-steps"></a>Næste trin

I denne artikel beskrives beregnede objekter og dataflow, der er tilgængelige i Power BI-tjenesten. Her er nogle flere artikler, der kan være nyttige.

* [Selvbetjent dataforberedelse med dataflow](service-dataflows-overview.md)
* [Opret og brug dataflow i Power BI](service-dataflows-create-use.md)
* [Brug af dataflow med datakilder i det lokale miljø](service-dataflows-on-premises-gateways.md)
* [Udviklerressourcer til Power BI-dataflow](service-dataflows-developer-resources.md)
* [Konfigurer indstillinger for dataflow for et arbejdsområde (prøveversion)](service-dataflows-configure-workspace-storage-settings.md)
* [Føj en CDM-mappe til Power BI som et dataflow (prøveversion)](service-dataflows-add-cdm-folder.md)
* [Opret forbindelse til Azure Data Lake Storage Gen2 til dataflowlager (eksempelvisning)](service-dataflows-connect-azure-data-lake-storage-gen2.md)

Du kan finde flere oplysninger om Power-forespørgsel og planlagt opdatering i disse artikler:
* [Oversigt over forespørgsler i Power BI Desktop](desktop-query-overview.md)
* [Konfiguration af planlagt opdatering](../connect-data/refresh-scheduled-refresh.md)

Du kan finde flere oplysninger om Common Data Model i denne oversigtsartikel:
* [Common Data Model – oversigt](/powerapps/common-data-model/overview)