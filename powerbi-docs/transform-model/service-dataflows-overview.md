---
title: Få mere at vide om dataflows i Power BI
description: Få mere at vide om, hvordan dataflows fungerer i Power BI
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/01/2019
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: 2bb23da89489966cd3d96bb2c4daaa6302a96326
ms.sourcegitcommit: 9350f994b7f18b0a52a2e9f8f8f8e472c342ea42
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 09/22/2020
ms.locfileid: "90859721"
---
# <a name="self-service-data-prep-in-power-bi"></a>Selvbetjent dataforberedelse i Power BI

Efterhånden som datamængden vokser, stiger behovet for at konvertere dataene i korrekt udformede oplysninger, som der kan handles på. Vi vil gerne have data, der er klar til analyse, til udfyldning af visuelle elementer, rapporter og dashboards, så vi hurtigt kan konvertere vores datamængder til viden, som der kan handles på. Med **selvbetjening til dataforberedelse** til big data i Power BI kan du gå fra data til Power BI-indsigt med bare nogle få klik.

![Brug dataflow i Power BI](media/service-dataflows-overview/powerbi-dataflows_01.png)

Power BI introducerer **dataflows**, der kan hjælpe virksomheder med at samle data fra forskellige kilder og forberede dem til modellering. Analytikere kan nemt oprette dataflows ved hjælp af velkendte værktøjer til selvbetjening. Dataflows anvendes til at indsamle, transformere, integrere og forbedre big data ved at definere datakildeforbindelser, ETL-logik, opdatere tidsplaner og meget mere. Desuden gør den nye modelbaserede beregningsmotor, som er en del af dataflows, processen med dataforberedelse lettere at håndtere, mere deterministisk og mindre besværlig for såvel dataanalytikere som rapportoprettere. På samme måde som regneark håndterer genberegninger for alle berørte formler, håndterer dataflows alle ændringer af et objekt eller dataelement på dine vegne, hvilket automatiserer opdatering og letter det, der tidligere selv i forbindelse med almindelige dataopdateringer krævede kedelige og tidskrævende logiske kontroller. Med dataflows kan opgaver, der tidligere krævede opsyn af dataeksperter (og tog mange timer eller dage at fuldføre) nu håndteres med nogle få klik af analytikere og rapportoprettere. 

Data gemmes som objekter i [**Common Data Model**](/powerapps/common-data-model/overview) i Azure Data Lake Storage Gen2. Dataflow oprettes og administreres i arbejdsområder ved hjælp af Power BI-tjenesten.  
 
**Dataflows** designes til at anvende **Common Data Model**, en standardiseret, modulær og fleksibel samling af dataskemaer udgivet af Microsoft, som er udviklet til at gøre det nemmere for dig opbygge, bruge og analysere data. Med denne model kan du gå fra datakilder til Power BI-dashboards næsten helt uden friktion.

Du kan bruge dataflows til at indsamle data fra et stort og voksende antal understøttede datakilder i det lokale miljø og cloud-baserede, herunder Dynamics 365, Salesforce, Azure SQL Database, Excel, SharePoint og mange andre.

Du kan derefter knytte dataene til standardobjekter i Common Data Model, redigere og udvide eksisterende objekter og oprette brugerdefinerede objekter. Erfarne brugere kan oprette fuldt brugertilpassede dataflows ved hjælp af en indbygget selvbetjeningsbaseret funktion med begrænset eller ingen programmering til oprettelse af Power-forespørgsler, der svarer til den Power-forespørgsel, som flere millioner Power BI Desktop- og Excel-brugere allerede kender.  

Når du har oprettet et dataflow, kan du bruge Power BI Desktop og Power BI-tjenesten til at oprette datasæt, rapporter, dashboards og apps, der udnytter effekten af Common Data Model, til at få omfattende indsigt i dine forretningsaktiviteter. 

Planlægningen af opdateringen af dataflow styres direkte fra det arbejdsområde, hvor dit dataflow er oprettet, på samme måde som dine datasæt. 

## <a name="how-dataflows-work"></a>Sådan fungerer dataflows

Her er nogle eksempler på, hvad du kan bruge dataflows til:

* Organisationer kan knytte deres data til standardobjekter i en Common Data Model eller oprette deres egne brugerdefinerede objekter. Disse objekter kan derefter bruges som skabeloner til at oprette rapporter, dashboards og apps, der fungerer lige fra starten, og distribuere dem til brugere på tværs af organisationen. 

* Den omfattende samling af Microsoft-dataforbindelser gør det muligt for organisationer at forbinde deres egne datakilder med dataflows ved hjælp af Power-forespørgsel for at tilknytte dataene fra deres oprindelse og overføre dem til Power BI. Når dataene er importeret af et dataflow (og opdateret med en angivet hyppighed), kan disse dataflowenheder bruges til at oprette overbevisende rapporter og dashboards i Power BI Desktop-programmet. 

## <a name="how-to-use-dataflows"></a>Sådan bruges dataflows

I det forrige afsnit beskrives en række måder, hvorpå dataflows kan bruges til hurtigt at oprette effektive analyser i Power BI. I dette afsnit får du en gennemgang af, hvor hurtigt du kan oprette viden ved hjælp af dataflows i en organisation, få en hurtig visning af, hvordan BI-teknikere kan oprette deres egne dataflows og tilpasse viden til deres egen organisation.

> [!NOTE]
> Du skal have en betalt Power BI-konto for at bruge dataflow, f.eks. en Power BI Pro- eller Power BI Premium-konto, men du opkræves ikke særskilt for brug af dataflow. 

### <a name="extend-the-common-data-model-for-your-business-needs"></a>Udvid den fælles datamodel til dine forretningsbehov
For organisationer, der ønsker at udvide Common Data Model (CDM), gør dataflows det muligt for business intelligence-teknikere at tilpasse standardobjekterne eller oprette nye. Denne selvbetjente tilgang til tilpasning af datamodellen kan derefter anvendes sammen med dataflows til at bygge apps og Power BI-dashboards, som er skræddersyet til en organization.

### <a name="define-dataflows-programmatically"></a>Definer dataflows ved hjælp af programmering
Du kan også udvikle dine egne programmatiske løsninger til oprettelse af dataflows. Med offentlige API'er og muligheden for at oprette brugerdefinerede definitionsfiler til dataflow (model.json) ved hjælp af programmering kan du udvikle en brugerdefineret løsning, der opfylder din organisations unikke data- og analysebehov. 

Offentlige API'er gør det nemt og hurtigt for udviklere at interagere med Power BI og dataflows.

### <a name="extend-your-capabilities-with-azure"></a>Udvid dine muligheder med Azure
Azure Data Lake Storage Gen2 er inkluderet i alle betalte Power BI-abonnementer (10 GB pr. bruger, 100 TB pr. P1-node). Det gør det nemt at komme i gang med selvbetjent dataforberedelse på Azure Data Lake. 

Power BI kan konfigureres til at gemme dataflowdata på din organisations Azure Data Lake Storage Gen2-konto. Når Power BI er forbundet til dit Azure-abonnement, kan dataudviklere og datateknikere udnytte effektive Azure-produkter som f.eks. Azure Machine Learning, Azure Databricks, Azure Data Factory og mange flere.

Power BI kan også oprette forbindelse til mapper med skematiserede data i Common Data Model-formatet, som er gemt på din organisations Azure Data Lake Storage-konto. Disse mapper kan oprettes af tjenester som f.eks. Azure-datatjenester. Ved at oprette forbindelse til disse mapper kan analytikere arbejde problemfrit med disse data i Power BI. 

Du kan finde flere oplysninger om Azure Data Lake Storage Gen2 og dataflowintegration, herunder hvordan du opretter dataflow, der er placeret i organisationens Azure Data Lake, under [Integration af dataflow og Azure Data Lake (prøveversion)](service-dataflows-azure-data-lake-integration.md).

## <a name="dataflow-capabilities-on-power-bi-premium"></a>Egenskaber for dataflow i Power BI Premium

For at kunne køre dataflowfunktioner og arbejdsbelastninger på et Power BI Premium-abonnement skal dataflowarbejdsbelastningen være aktiveret for den pågældende Premium-kapacitet. I følgende tabel beskrives dataflowfunktionerne og deres kapaciteter ved brug af en Power BI Pro-konto, og hvordan det kan sammenlignes med brug af Power BI Premium.


|Dataflow-funktionalitet | Power BI Pro |   Power BI Premium |
|---------|---------|---------|
|Planlagt opdatering| 8 pr. dag|  48|
|Samlet lagerplads| 10 GB pr. bruger  |100 TB pr. node|
|Oprettelse af dataflow med Power-forespørgsel online|    +   |+|
|Administration af dataflow i Power BI|   +|  +|
|Dataflows Data Connector i Power BI Desktop|  +|  +|
|Integration med Azure|    +|  +|
|Beregnede enheder (transformationer i lageret via M) | |   +|
|Alle connectors|    +|  +|
|Trinvis opdatering af dataflow|  |   +|
|Kører på Power BI Premium-kapacitet/Parallel udførelse af transformationer|   |   +|
|Dataflow-tilknyttede enheder| |        +|
|Standardiseret skema/indbygget understøttelse af Common Data Model|  +|  +|

Du kan finde flere oplysninger om, hvordan du aktiverer dataflowarbejdsbelastninger i forbindelse med Premium-kapacitet, under [Konfigurer arbejdsbelastninger i en Premium-kapacitet](../admin/service-admin-premium-workloads.md). Arbejdsbelastninger i dataflow er ikke tilgængelige i øjeblikket i Multi-Geo-kapaciteter.

## <a name="summary-of-self-service-data-prep-for-big-data-in-power-bi"></a>Oversigt over selvbetjent dataforberedelse til big data i Power BI
Som tidligere nævnt i denne artikel er der flere scenarier og eksempler, hvor **dataflows** gør det muligt at få bedre styring – og hurtigere indsigt – fra dine virksomhedsdata. Ved hjælp af en standarddatamodel (skema) defineret af Common Data Model kan dataflows importere dine værdifulde forretningsdata og hurtigt klargøre dataene til modellering og oprettelse af BI-indsigt – som tidligere tog flere måneder eller mere at oprette. 

Ved at gemme forretningsdata i standardiseret format af **Common Data Model**, kan BI-teknikerne (eller udviklerne) udvikle apps, der genererer hurtige, nemme og automatiske visuals og rapporter. Dette omfatter, men er ikke begrænset til:


* Tilknytning af dine data til standardobjekter i Common Data Model for at samle data og udnytte det kendte skema for at skabe indsigt klar til brug
* Oprettelse af dine egne brugerdefinerede objekter til samling af data på tværs af din organisation 
* Brug og opdatering af **eksterne data** som en del af et dataflow og muliggøre import af disse data for at skabe indsigt
* Kom i gang med dataflows for udviklere


## <a name="next-steps"></a>Næste trin

Denne artikel giver et overblik over dataforberedelse af big data til selvbetjening i Power BI og de mange måder, du kan bruge det på. De følgende artikler kommere nærmere ind på almindelige forbrugsscenarier for dataflows. 

* [Opret og brug dataflow i Power BI](service-dataflows-create-use.md)
* [Brug af beregnede objekter i Power BI Premium](service-dataflows-computed-entities-premium.md)
* [Brug af dataflow med datakilder i det lokale miljø](service-dataflows-on-premises-gateways.md)
* [Udviklerressourcer til Power BI-dataflow](service-dataflows-developer-resources.md)
* [Integration af dataflow og Azure Data Lake](service-dataflows-azure-data-lake-integration.md)

Du kan finde flere oplysninger om Power-forespørgsel og planlagt opdatering i disse artikler:
* [Oversigt over forespørgsler i Power BI Desktop](desktop-query-overview.md)
* [Konfiguration af planlagt opdatering](../connect-data/refresh-scheduled-refresh.md)

Du kan finde flere oplysninger om Common Data Model i denne oversigtsartikel:
* [Common Data Model – oversigt](/powerapps/common-data-model/overview)