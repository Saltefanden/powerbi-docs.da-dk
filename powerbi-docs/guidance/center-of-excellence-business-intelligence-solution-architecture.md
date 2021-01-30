---
title: BI-løsningsarkitektur i COE'et
description: Få mere at vide om, hvordan du designer og udvikler en robust BI-platform.
author: peter-myers
ms.author: kfollis
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 11/11/2020
ms.openlocfilehash: aab11163f2369c0d62437c516d730103796e82a8
ms.sourcegitcommit: fb529c4532fbbdfde7ce28e2b4b35f990e8f21d9
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/30/2021
ms.locfileid: "99088712"
---
# <a name="bi-solution-architecture-in-the-center-of-excellence"></a>BI-løsningsarkitektur i COE'et

Denne artikel er rettet mod it-medarbejdere og it-ledere. Du får mere at vide om BI-løsningsarkitektur i COE'et og de forskellige teknologier, der er anvendt. Teknologierne omfatter Azure, Power BI og Excel. Tilsammen kan de udnyttes til at levere en skalerbar og datadrevet BI-cloudplatform.

Design af en robust BI-platform er lidt som at bygge en bro – en bro, der forbinder transformerede og forbedrede kildedata til dataforbrugere. Udformningen af en så kompleks struktur kræver en teknisk tilgang, selvom det kan være et af de mest kreative og strømlinede it-arkitekturer, du kan designe. I en stor organisation kan ariktekturen i en BI-løsning bestå af:

- Datakilder
- Dataindtagelse
- Big data/dataklargøring
- Data warehouse
- Semantiske BI-modeller
- Rapporter

:::image type="content" source="media/center-of-excellence-business-intelligence-solution-architecture/azure-business-intelligence-platform.png" alt-text="Et diagram, der viser BI-platformens arkitektur fra datakilder til dataindtagelse, big data, lager, data warehouse, modellering af BI-semantik, rapportering og maskinel indlæring.":::

Platformen skal understøtte specifikke krav. Den skal især kunne skaleres og have en ydeevne, der opfylder kravene fra forretningstjenesterne og dataforbrugerne. Samtidig skal den være fuldstændig sikker hele vejen igennem. Den skal også være tilstrækkelig robust til at kunne tilpasse sig til ændringer – da nye data og emneområder skal gøres online med tiden.

## <a name="frameworks"></a>Strukturer

Hos Microsoft vedtog vi i begyndelsen en systemlignende tilgang ved at investere i udviklingen af strukturen. Tekniske og forretningsmæssige processtrukturer øger muligheden for at genbruge design og logik og giver et ensartet resultat. De skaber også en fleksibel arkitektur, hvor mange teknologier udnyttes, og de strømliner og reducerer de tekniske omkostninger via gentagne processer.

Vi har lært, at veldesignede strukturer øger synligheden af dataafstamningen, effektanalyser, vedligeholdelse af forretningslogik, administration af taksonomi og strømlining af styringen. Udviklingen blev også hurtigere, og samarbejdet på tværs af store teams var mere dynamisk og effektivt.

Vi beskriver flere af vores strukturer i denne artikel.

## <a name="data-models"></a>Datamodeller

Datamodeller giver dig kontrol over, hvordan data struktureres og tilgås. For forretningstjenester og dataforbrugere er datamodeller deres grænseflade til BI-platformen.

En BI-platform kan levere tre forskellige typer modeller:

- Virksomhedsmodeller
- Semantiske BI-modeller
- Modeller til maskinel indlæring

### <a name="enterprise-models"></a>Virksomhedsmodeller

**Virksomhedsmodeller** bygges og vedligeholdes af it-arkitekter. De kaldes også dimensionelle modeller eller datacentre. Data lagres typisk i et relationelt format som dimensions- og faktatabeller. Disse tabeller lagrer rene og forbedrede data, der er konsolideret fra mange systemer, og de repræsenterer en autoritativ kilde til rapportering og analyse.

Virksomhedsmodeller leverer en konsistent og enkelt datakilde til rapportering og BI. De bygges én gang og deles som en virksomhedsstandard. Styringspolitikker sikrer, at dataene er beskyttede, så adgangen til følsomme datasæt – f.eks. kundeoplysninger eller finansielle oplysninger – begrænses efter behov. De vedtager navngivningskonventioner, der sikrer konsistens, og giver dermed troværdighed til dataene og kvaliteten.

I en BI-cloudplatform kan virksomhedsmodeller udrulles i en [Synapse SQL-gruppe i Azure Synapse](/azure/synapse-analytics/sql-data-warehouse/sql-data-warehouse-overview-what-is#synapse-sql-pool-in-azure-synapse). Synapse SQL-gruppen bliver derefter den eneste version af sandheden, som organisationen kan stole på til at opnå hurtig og robust indsigt.

### <a name="bi-semantic-models"></a>Semantiske BI-modeller

**Semantiske BI-modeller** repræsenterer et semantisk lag i forhold til virksomhedsmodeller. De bygges og vedligeholdes af BI-udviklere og virksomhedsbrugere. BI-udviklere opretter centrale semantiske BI-modeller, der henter data fra virksomhedsmodeller. Virksomhedsbrugere kan oprette mindre, uafhængige modeller – eller de kan udvide centrale semantiske BI-modeller med afdelingsrelaterede eller eksterne kilder. I semantiske BI-modeller fokuseres der ofte på et enkelt emneområde, og de deles ofte af mange.

Forretningsegenskaber aktiveres ikke kun af data, men af semantiske BI-modeller, der beskriver begreber, relationer, regler og standarder. På denne måde repræsenterer de intuitive og letforståelige strukturer, der definerer datarelationer og indkapsler forretningsregler som beregninger. De kan også gennemtvinge detaljerede datatilladelser og dermed sikre, at de rette personer har adgang til de rette data. Modellerne booster også ydeevnen for forespørgsler, hvilket giver dig meget dynamiske interaktive analyser – også når der er tale om over en terabyte data. På samme måde som virksomhedsmodeller benytter semantiske BI-modeller navngivningskonventioner, hvilke sikrer konsistens.

I en BI-cloudplatform kan BI-udviklere udrulle semantiske BI-modeller til [Azure Analysis Services](/azure/analysis-services/) eller [Power BI Premium-kapaciteter](../admin/service-premium-what-is.md#reserved-capacities). Vi anbefaler, at du udruller til Power BI, når den bruges som dit rapporterings- og analyselag. Disse produkter understøtter forskellige lagringstilstande, der gør det muligt for datamodeltabeller at cachelagre deres data eller at bruge [DirectQuery](directquery-model-guidance.md), som er en teknologi, der sender forespørgsler til den underliggende datakilde. DirectQuery er en ideel lagringstilstand, når modeltabeller repræsenterer store datamængder, eller der er behov for at levere resultater i næsten realtid. De to lagringstilstande kan kombineres: [Sammensatte modeller](composite-model-guidance.md) kombinerer tabeller, der bruger forskellige lagringstilstande i en enkelt model.

I forbindelse med modeller, der hyppigt forespørges, kan [Azure Load Balancer](/azure/load-balancer/load-balancer-overview) bruges til at fordele indlæsningen af forespørgsler ligeligt på tværs af modelreplikaer. Du kan også skalere dine programmer og oprette semantiske BI-modeller med høj tilgængelighed.

### <a name="machine-learning-models"></a>Modeller til maskinel indlæring

[**Modeller til maskinel indlæring**](/windows/ai/windows-ml/what-is-a-machine-learning-model) bygges og vedligeholdes af datateknikere. De udvikles hovedsageligt fra rå kilder i datasøen.

Oplærte modeller til maskinel indlæring kan vise mønstre i dine data. I mange tilfælde kan disse mønstre bruges til at oprette forudsigelser, der kan bruges til at forbedre data. Købsadfærd kan f.eks. bruges til at forudsige kundeafgang eller segmentere kunder. Forudsigelsesresultater kan føjes til virksomhedsmodeller for at muliggøre analyse efter kundesegment.

På en BI-cloudplatform kan du bruge [Azure Machine Learning](/azure/machine-learning/overview-what-is-azure-ml) til at oplære, udrulle, automatisere, administrere og spore modeller til maskinel indlæring.

## <a name="data-warehouse"></a>Data warehouse

I hjertet af en BI-platform er et data warehouse, som er vært for dine virksomhedsmodeller. Det er en kilde til data, der er sanktionerede – på samme måde som et registreringssystem og en hub – der betjener virksomhedsmodeller til rapportering, BI og datavidenskab.

Mange virksomhedstjenester, herunder LOB-programmer (Line-of-Business), kan bruge et data warehouse som en autoritativ og administreret kilde til viden om virksomheden.

Hos Microsoft hostes vores data warehouse i [Azure Data Lake Storage Gen2](/azure/storage/blobs/data-lake-storage-introduction) (ADLS Gen2) og Azure Synapse Analytics.

:::image type="content" source="media/center-of-excellence-business-intelligence-solution-architecture/azure-data-warehouse.png" alt-text="Et billede viser Azure Synapse Analytics, der opretter forbindelse til Azure Data Lake Storage Gen2.":::

- For **ADLS Gen2** er Azure Storage fundamentet til opbygning af virksomhedsdatasøer i Azure. Det er designet til håndtere mange petabyte oplysninger, samtidig med at en dataoverførselshastighed på hundredvis af gigabit opretholdes. Det tilbyder også lagerkapacitet og transaktioner til lave omkostninger. Herudover understøtter det Hadoop-kompatibel adgang, som gør det muligt for dig at administrere og få adgang til data på samme måde som med et HDFS (Hadoop Distributed File System). Faktisk kan [Azure HDInsight](/azure/hdinsight/), [Azure Databricks](/azure/azure-databricks/what-is-azure-databricks) og Azure Synapse Analytics alle få adgang til data, der er gemt i ADLS Gen2. På en BI-platform er det derfor en god ide at lagre rå kildedata, halvforarbejdede eller midlertidigt gemte data samt data, der er klar til produktion. Vi bruger det til at lagre alle vores virksomhedsdata.
- **Azure Synapse Analytics** er en analysetjeneste, der samler virksomhedsdatawarehousing og big data-analyser. Det giver dig frihed til at forespørge på data på dine vilkår enten ved hjælp af serveruafhængige eller klargjorte ressourcer – i stor målestok. Synapse SQL, der er en del af Azure Synapse Analytics, understøtter fuldstændig T-SQL-baserede analyser og er derfor ideelt til at hoste virksomhedsmodeller, der består af dimensions- og faktatabeller. Tabeller kan indlæses effektivt fra ADLS Gen2 ved hjælp af enkle [T-SQL-polybaseforespørgsler](/sql/relational-databases/polybase/polybase-guide). På den måde kan du bruge [MPP](/azure/synapse-analytics/sql-data-warehouse/massively-parallel-processing-mpp-architecture#synapse-sql-mpp-architecture-components) til at køre analyser med høj ydeevne.

### <a name="business-rules-engine-framework"></a>Strukturen Business Rules Engine

Vi har udviklet strukturen **BRE (Business Rules Engine)** til at katalogisere forretningslogik, der kan implementeres i data warehouse-laget. Et BRE kan betyde mange ting, men i forbindelse med et data warehouse er det nyttigt til at oprette beregnede kolonner i relationstabeller. Disse beregnede kolonner repræsenteres normalt som matematiske beregninger eller udtryk ved hjælp af betingede sætninger.

Hensigten er at adskille forretningslogikken fra kernekoden i BI. Virksomhedsregler er traditionelt set hard-coded i SQL-lagrede procedurer, hvorfor det ofte kræver meget arbejde at vedligeholde dem, når virksomhedens behov ændrer sig. I et BRE defineres forretningsregler én gang og bruges flere gange, når de anvendes på forskellige data warehouse-enheder. Hvis den pågældende beregningslogik skal ændres, skal den kun opdateres ét sted og ikke i mange lagrede procedurer. Der er også en fordel: En BRE-struktur er med til at skabe gennemsigtighed og synlighed i implementeret forretningslogik, der kan eksponeres via en række rapporter, der opretter dokumentation, der opdateres automatisk.

## <a name="data-sources"></a>Datakilder

Et data warehouse kan konsolidere data fra næsten enhver datakilde. Det er hovedsageligt baseret på LOB-datakilder, som typisk er relationsdatabaser, der lagrer emnespecifikke data til salg, marketing, økonomiafdelingen osv. Disse databaser kan være hostet i et cloudmiljø, eller de kan være placeret i det lokale miljø. Andre datakilder kan være filbaserede, især weblogs eller IOT-data, der stammer fra enheder. Derudover kan data hentes fra SaaS-leverandører (Software-as-a-Service).

Hos Microsoft skriver nogle af vores interne systemer driftsdata direkte til ADLS Gen2 ved hjælp af RAW-filformater. Ud over vores datasø omfatter andre kildesystemer relationelle LOB-programmer, Excel-projektmapper, andre filbaserede kilder samt MDM-lagre (Master Data Management) og brugerdefinerede datalagre. MDM-lagre giver os mulighed for at administrere vores masterdata for at sikre autoritative, standardiserede og validerede versioner af data.

## <a name="data-ingestion"></a>Dataindtagelse

Med jævne mellemrum og i henhold til virksomhedens behov indtages data fra kildesystemer og indlæses i det pågældende data warehouse. Det kan være én gang om dagen eller hyppigere. Dataindtagelse omfatter udtrækning, transformering og indlæsning af data. Eller omvendt: udtrækning, indlæsning og derefter transformering af data. Forskellen ligger i den placering, hvor transformationen sker. Transformationer anvendes til at rense, overholde standarder, integrere og standardisere data. Du kan finde flere oplysninger under [Udtræk, transformer og Indlæs (ETL = Extract, transform and load)](/azure/architecture/data-guide/relational-data/etl).

Målet er i sidste ende at indlæse de rigtige data i virksomhedsmodellen så hurtigt og effektivt som muligt.

Hos Microsoft bruger vi [ADF (Azure Data Factory)](/azure/data-factory/introduction). Tjenesterne bruges til at planlægge og organisere datavalideringer, transformationer og masseindlæsninger fra eksterne kildesystemer til vores datasø. Det styres af brugerdefinerede strukturer til behandling af data parallelt og skalerbart. Herudover udføres der desuden omfattende logføring for at understøtte fejlfinding, ydelsesovervågning og udløse underretninger, når bestemte betingelser er opfyldt.

I mellemtiden udfører [Azure Databricks](/azure/azure-databricks/what-is-azure-databricks) – en Apache Spark-baseret analyseplatform, der er optimeret til Azure Cloud Services-platformen – transformationer specifikt med henblik på datavidenskab. Det bygger også og udfører ML-modeller ved hjælp af Python-notesbøger. Resultaterne fra disse ML-modeller indlæses i det pågældende data warehouse for at integrere forudsigelser med virksomhedsprogrammer og rapporter. Eftersom Azure Databricks får adgang til datasøfiler direkte, eliminerer eller minimerer det behovet for at kopiere eller hente data.

:::image type="content" source="media/center-of-excellence-business-intelligence-solution-architecture/azure-data-ingestion.png" alt-text="Et billede, der viser Azure Data Factory-kildedata og orkestrering af datapipelines med Azure Databricks Azure Data Lake Storage Gen2.":::

### <a name="ingestion-framework"></a>Indtagelsesstruktur

Vi har udviklet en **indtagelsesstruktur** som et sæt konfigurationstabeller og -procedurer. Det understøtter en datadrevet tilgang til at hente store datamængder med høj hastighed og med minimal kode. Denne struktur forenkler kort og godt processen med at hente data til indlæsning i et data warehouse.

Strukturen afhænger af konfigurationstabeller, der gemmer datakilde- og datadestinationsrelaterede oplysninger, f.eks. kildetype, server, database, skema og tabelrelaterede detaljer. Denne designmetode betyder, at vi ikke behøver at udvikle bestemte ADF-pipelines eller [SSIS-pakker (SQL Server Integration Services)](/sql/integration-services/sql-server-integration-services). Procedurerne skrives i stedet på et sprog efter vores eget valg for at oprette ADF-pipelines, der genereres dynamisk og udføres på kørselstidspunktet. Datahentningen bliver derfor en konfigurationsopgave, der er nem at udføre. Det ville typisk have krævet omfattende udviklingsressourcer til oprettelse af hard-codede ADF- eller SSIS-pakker.

Overførselsstrukturen blev også designet for at forenkle processen med at håndtere ændringer i upstream-kildeskemaet. Det er nemt at opdatere konfigurationsdata, manuelt eller automatisk, når der registreres skemaændringer for at hente nyligt tilføjede attributter i kildesystemet.

### <a name="orchestration-framework"></a>Orkestreringsstruktur

Vi har udviklet en **orkestreringsstruktur** for at drive og orkestrere vores datapipelines. Den bruger et datadrevet design, som afhænger af et sæt konfigurationstabeller. I disse tabeller gemmes metadata, der beskriver pipelineafhængigheder, og hvordan kildedata knyttes til destinationsdatastrukturer. Investeringen i forbindelse med udviklingen af dette tilpassede regelsæt har siden betalt sig ind. Der er ikke længere et krav om at hard-code hver enkelt dataflytning.

## <a name="data-storage"></a>Datalager

En datasø kan lagre store mængder rå data til senere brug sammen med transformationer af midlertidige data.

Hos Microsoft bruger vi ADLS Gen2 som en enkelt kilde til sandheden. Det gemmer rå data ved siden af midlertidige data og data, der er klar til produktion. Det giver en yderst skalerbar og omkostningseffektiv datasøløsning til analyse af big data. Kombinationen af et højtydende filsystem med omfattende skalering betyder, at det er optimeret til arbejdsprocesser i forbindelse med dataanalyser, så det bliver hurtigere at få adgang til indsigt.

Med ADLS Gen2 får I det bedste af to verdener: Et BLOB-lager og et filsystemnavneområde med høj ydeevne, som vi konfigurerer med detaljerede adgangstilladelser.

De tilpassede data gemmes derefter i en relationsdatabase for at levere et højtydende, yderst skalerbart datalager til virksomhedsmodeller, med sikkerhed, styring og administration. De emnespecifikke datacentre lagres i Azure Synapse Analytics, som indlæses af Azure Databricks eller T-SQL-polybaseforespørgsler.

## <a name="data-consumption"></a>Dataforbrug

På rapporteringslaget forbruger forretningstjenester virksomhedsdata, der hentes fra det pågældende data warehouse. De har også adgang til data direkte i datasøen til ad hoc-analyser eller til datavidenskabelige opgaver.

Detaljerede tilladelser gennemtvinges på alle lag: i datasøen, i virksomhedsmodellerne og i de semantiske BI-modeller. Tilladelserne sikrer, at dataforbrugerne kun kan se de data, de har tilladelse til at få adgang til.

Hos Microsoft bruger vi Power BI-rapporter, dashboards og [sideinddelte Power BI-rapporter](../paginated-reports/paginated-reports-report-builder-power-bi.md). Nogle rapporterings- og ad hoc-analyser udføres i Excel – især i forbindelse med finansiel rapportering.

Vi publicerer dataordbøger, som indeholder referenceoplysninger om vores datamodeller. De er gjort tilgængelige for vores brugere, så de kan finde oplysninger om vores BI-platform. I ordbøgerne dokumenteres modeldesign, og de indeholder beskrivelser af objekter, formater, struktur, dataafstamning, relationer og beregninger. Vi bruger [Azure Data Catalog](/azure/data-catalog/overview) for at gøre det nemt at finde og forstå vores datakilder.

Dataforbrugsmønstre varierer typisk fra rolle til rolle:

- **Dataanalytikere** opretter direkte forbindelse til centrale semantiske BI-modeller. Når centrale semantiske BI-modeller indeholder alle de data og den logik, de har brug for, benytter de direkte forbindelser til at oprette Power BI-rapporter og -dashboards. Når de har brug for at udvide modellerne med afdelingsdata, opretter de [sammensatte Power BI-modeller](composite-model-guidance.md). Hvis der er behov for rapporter i regnearksformat, bruger de Excel til at producere rapporter, der er baseret på centrale eller afdelingsrelaterede semantiske BI-modeller.
- **BI-udviklere** og driftsrapportforfattere opretter direkte forbindelse til virksomhedsmodeller. De bruger Power BI Desktop til at oprette analyserapporter med direkte forbindelse. De kan også oprette driftsrelaterede BI-rapporter som f.eks. sideinddelte Power BI-rapporter, skrive oprindelige SQL-forespørgsler for at få adgang til data fra Azure Synapse Analytics Enterprise-virksomhedsmodeller ved hjælp af semantiske T-SQL eller semantiske Power BI-modeller ved hjælp af DAX eller MDX.
- **Dataeksperter** opretter direkte forbindelse til data i datasøen. De bruger Azure Databricks- og Python-notesbøger til at udvikle modeller til maskinel indlæring, som ofte er eksperimentelle og kræver specielle kompetencer til produktionsbrug.

:::image type="content" source="media/center-of-excellence-business-intelligence-solution-architecture/azure-data-warehouse-consumption.png" alt-text="Et billede viser forbruget af Azure Synapse Analytics sammen med Power BI, Excel og Azure Machine Learning.":::

## <a name="next-steps"></a>Næste trin

Du kan finde flere oplysninger om denne artikel i følgende ressourcer:

- [Virksomheds-BI i Azure med Azure Synapse Analytics](/azure/architecture/reference-architectures/data/enterprise-bi-synapse)
- Har du spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
- Forslag? [Få ideer til at forbedre Power BI](https://ideas.powerbi.com/)

### <a name="professional-services"></a>Professionelle tjenester

Der findes certificerede Power BI-partnere, som kan hjælpe din organisation med at lykkes, når du konfigurerer en COE. De kan give dig omkostningseffektiv træning eller overvågning af dine data. Hvis du vil i kontakt med en Power BI-partner, skal du gå til [Power BI-partnerportalen](https://powerbi.microsoft.com/partners/).

Du kan også interagere med erfarne konsulentpartnere. De kan hjælpe dig med at [vurdere](https://appsource.microsoft.com/marketplace/consulting-services?product=power-bi&serviceType=assessment&country=ALL&region=ALL), [evaluere](https://appsource.microsoft.com/marketplace/consulting-services?product=power-bi&serviceType=proof-of-concept&country=ALL&region=ALL) eller [implementere](https://appsource.microsoft.com/marketplace/consulting-services?product=power-bi&serviceType=implementation&country=ALL&region=ALL&page=1) Power BI.
