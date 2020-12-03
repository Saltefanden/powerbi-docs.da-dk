---
title: Få mere viden fra kunder i forbindelse med migrering til Power BI
description: Få mere viden fra kunder, når der migreres til Power BI.
author: peter-myers
ms.author: v-pemyer
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 08/20/2020
ms.openlocfilehash: fd5490eae689a4119566474da2ef4d19017a8134
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96419170"
---
# <a name="learn-from-customer-power-bi-migrations"></a>Få mere viden fra kunder i forbindelse med migrering til Power BI

Denne artikel, som er den sidste i serien om migrering til Power BI, indeholder vigtige erfaringer, som to kunder gjorde i forbindelse med deres vellykkede migrering til Power BI.

## <a name="international-consumer-goods-company"></a>International virksomhed med forbrugsvarer

En international virksomhed med forbrugsvarer, der sælger hundredvis af produkter, tog i 2017 beslutningen om at indføre en cloudstrategi. En af de største grunde til, at virksomheden valgte Power BI som platform til business intelligence (BI), er den dybe integration med Azure og Microsoft 365.

### <a name="conduct-a-phased-migration"></a>Udfør en faseinddelt migrering

I 2017 begyndte virksomheden at bruge Power BI. Det indledende organisatoriske formål var at introducere Power BI som et ekstra BI-værktøj. Den beslutning gav indholdsforfattere, forbrugere og it-medarbejdere tid til at vænne sig til den nye måde at levere BI på. Det gav dem også mulighed for at opbygge ekspertise inden for Power BI.

I anden halvdel af 2018 kom der en formel meddelelse om, at Power BI var det godkendte BI-værktøj i organisationen. Og derfor skulle alt nyt BI-udviklingsarbejde foregå i Power BI. Tilgængeligheden af Power BI Premium var en vigtig drivkraft for at træffe denne beslutning. På dette tidspunkt frarådede organisationen brug af den tidligere BI-platform, og planlægningen af overgangen påbegyndte.

Hen imod slutningen af 2019 begyndte arbejdet med at migrere eksisterende indhold fra den tidligere BI-platform til Power BI. Nogle af de tidlige brugere migrerede deres indhold hurtigt. Det hjalp med at skabe endnu mere momentum for Power BI i hele organisationen. Indholdsejere og -forfattere blev derefter bedt om at påbegynde forberedelserne, så de fuldt ud kunne migrere til Power BI inden udgangen af 2020. Organisationen står stadig overfor udfordringer i forbindelse med færdigheder, tid og finansiering – men ingen af problemerne er relateret til selve teknologiplatformen.

> [!IMPORTANT]
> Power BI var allerede en succes og veletableret i organisationen, inden de forskellige forretningsenheder blev bedt om at foretage en formel migrering fra den tidligere BI-platform.

### <a name="prepare-to-handle-varying-responses"></a>Forbered dig på at håndtere forskellige reaktioner

I denne store decentraliserede organisation var der forskellige niveauer af modtagelighed og villighed til at overgå til Power BI. Ud over bekymringer relateret til tid og budget var der medarbejdere, der havde investeret betydeligt i at opbygge deres færdigheder i den tidligere BI-platform. Så bekendtgørelsen om at standardisere til Power BI blev ikke taget godt imod af alle. Idet hver forretningsenhed har sit eget budget, kunne enkelte forretningsenheder anfægte beslutninger som denne. Da beslutninger om it-værktøjer blev truffet fra centralt sted, resulterede det i nogle udfordringer, som skulle håndteres af ledelsen og BI-lederne.

> [!IMPORTANT]
> Det var altafgørende at kommunikere med de ledende teams i hele forretningsenheden for at sikre, at de forstod de fordele på øverste niveau i organisationen, som standardisering til Power BI ville medføre. Effektiv kommunikation blev endnu vigtigere, i takt med at migreringen blev udført, og datoen for at tage den tidligere BI-platform ud af drift nærmede sig.

### <a name="focus-on-the-bigger-picture"></a>Fokusér på det større billede

Virksomheden fandt ud af, at nogle migrerede rapporter kunne replikere den oprindelige rapport nøje, men at det ikke var hver eneste rapport, der kunne replikeres nøjagtigt i Power BI. Det var dog forventeligt, da alle BI-platforme er forskellige. Det kastede også lys over, at en anden designtankegang var påkrævet.

Indholdsforfattere fik vejledningen: Fokusér på at oprette rapporter, der passer til formålet i Power BI, i stedet for at forsøge at skabe en nøjagtig replika af den gamle rapport. Derfor skal eksperter inden for emnet være tilgængelige under migreringsprocessen med henblik på konsultation og validering. Der blev gjort en indsats for at tage højde for formålet med rapportdesignet og forbedre det, når det var nødvendigt.

> [!IMPORTANT]
> Nogle gange er det bedre, at udføre forbedringer under migreringen. Andre gange er det bedre at levere præcis den samme værdi som før – uden markante forbedringer – så tidslinjen for migreringen ikke bringes i fare.

### <a name="cautiously-assess-priorities"></a>Vurder prioriteringer varsomt

Den tidligere BI-platform blev analyseret for at forstå brugen af den fuldt ud. Den tidligere BI-platform havde tusindvis af udgivne rapporter, hvoraf cirka halvdelen havde været åbnet i det forgangne år. Dette tal kunne halveres yderligere under vurderingen af, hvilke rapporter der blev anset for at give organisationen markant værdi. Disse rapporter blev prioriteret først i forbindelse med migreringen.

> [!IMPORTANT]
> Det er nemt at komme til at overvurdere, hvor vigtig en rapport faktisk er. For rapporter, der ikke bruges ofte, bør du vurdere, om de kan tages helt ud af drift. Nogle gange er det billigst og nemmest ikke at gøre noget.

### <a name="cautiously-assess-complexity"></a>Vurder kompleksiteten varsomt

I de første prioriterede rapporter blev tidsestimater indsamlet på baggrund af estimerede indsatsniveauer: enkel, mellem eller kompleks. Selvom det lyder som en relativ simpel proces, skal du ikke forvente, at tidsestimaterne er nøjagtige for hver enkelt rapport. Du oplever måske, at et estimat kan være meget unøjagtigt. Virksomheden havde f.eks. en rapport, som blev vurderet til at være meget kompleks. Konsulenterne gav den et konverteringsestimat på 50 dage. Den redesignede rapport i Power BI blev dog fuldført på omkring 50 timer.

> [!IMPORTANT]
> Selvom tidsestimaterne ofte er nødvendige for at skaffe finansiering og medarbejderopgaver, er de sandsynligvis mest værdifulde i samlingen.

### <a name="decide-how-change-management-is-handled"></a>Beslut, hvordan administration af ændringer håndteres

Med så stor en mængde BI-ressourcer udgjorde administration af ændringer for de virksomhedsejede rapporter en udfordring. Rapporter, der administreres af it-medarbejdere, blev håndteret i henhold til standardpraksis for administration af ændringer. Men på grund af den store mængde var det ikke muligt at udføre ændringer fra centralt sted for forretningsejet indhold.

> [!IMPORTANT]
> Forretningsenheden får yderligere ansvar, når det er upraktisk at administrere ændringer fra ét centralt team.

### <a name="create-an-internal-community"></a>Opret et internt community

Virksomheden har etableret et COE (Center of Excellence) for at levere intern oplæring og ressourcer. Dette COE fungerer også som en intern konsulentgruppe, der er klar til at hjælpe indholdsforfattere med tekniske problemer, løse forhindringer og vejlede om bedste praksis.

Der er også et internt Power BI-community, som har været en betydelig succes, og som har mere end 1.600 medlemmer. Community'et administreres i Yammer. Medlemmer kan stille internt relevante spørgsmål og få svar, der overholder bedste praksis, og som er inden for organisationens begrænsninger. Denne type bruger til bruger-interaktion letter en stor del af supportbyrden fra COE. COE overvåger dog spørgsmål og svar, og det er involveret i samtaler, når det er relevant.

En udvidelse af det interne community er et nyere Power BI-ekspertnetværk. Det omfatter et mindre antal forudvalgte Power BI-mestre fra organisationen. De er yderst dygtige Power BI-brugere fra forretningsenheden, som er entusiastiske mestre, og som gerne aktivt vil løse udfordringer i virksomheden. Medlemmer af Power BI-ekspertnetværket forventes at overholde bedste praksis og de vejledninger, der er fastlagt af COE, og hjælpe det bredere interne Power BI-community med at forstå og implementere dem. Selvom Power BI-ekspertnetværket samarbejder med COE og kan modtage dedikeret oplæring, handler Power BI-eksperter uafhængigt af COE. Hver Power BI-ekspert kan definere parametrene for, hvordan de fungerer, med tanke på at de har andet ansvar og andre prioriteter i deres officielle rolle.

> [!IMPORTANT]
> Definer præcist, hvad COE skal gøre, f.eks.: indførelse, styring, vejledning, bedste praksis, oplæring, support og muligvis praktisk udvikling. Selvom et COE er utroligt værdifuldt kan det være svært at måle dets investeringsafkast.

### <a name="monitor-migration-progress-and-success"></a>Overvåg migreringsfremskridtet og succesen

KPI'er (Key Performance Indicators) overvåges løbende under migreringen til Power BI. De hjælper virksomheden med at forstå tendenser for målepunkter, f.eks. antallet af rapportbesøg, antallet af aktive rapporter og individuelle brugere pr. måned. Øget forbrug af Power BI måles sammen med det reducerede forbrug af den tidligere BI-platform med det formål at opnå en omvendt relation. Målene opdateres hver måned, så de passer til ændringerne. Hvis forbruget ikke sker i det ønskede tempo, er der identificeret flaskehalse, så der kan foretages passende handlinger.

> [!IMPORTANT]
> Opret et migreringsscorecard med business intelligence, der kan handles på, for at overvåge, om migreringen lykkes.

## <a name="large-transportation-and-logistics-company"></a>Stor transport- og logistikvirksomhed

En stor nordamerikansk transport- og logistikvirksomhed investerer aktivt i moderniseringen af sin datainfrastruktur og sine analysesystemer.

### <a name="allow-a-period-of-gradual-growth"></a>Giv plads til en periode med gradvis vækst

Virksomheden begyndte at bruge Power BI i 2018. I midten af 2019 blev Power BI den foretrukne platform til alle nye use cases i BI. I 2020 begyndte virksomheden så at fokusere på at udfase deres eksisterende BI-platform foruden en række brugerdefinerede ASP.NET BI-løsninger.

> [!IMPORTANT]
> Power BI havde mange aktive brugere på tværs af organisationen, før udfasningen af deres tidligere BI-platform og -løsninger blev påbegyndt.

### <a name="balance-centralized-and-distributed-groups"></a>Afstem centraliserede og distribuerede grupper

Der er to typer BI-teams i virksomheden: et centralt BI-team og analysegrupper distribueret på tværs af organisationen. Det centrale BI-team har ansvaret for Power BI som en platform, men det ejer ikke noget af indholdet. På den måde er det centrale BI-team en teknisk hub til muliggørelse, der understøtter de distribuerede analysegrupper.

Hver analysegruppe er dedikeret til en bestemt forretningsenhed eller en delt tjenestefunktion. Der kan være en enkelt analytiker i en mindre gruppe, mens der kan være 10-15 analytikere i en større gruppe.

> [!IMPORTANT]
> De distribuerede analysegrupper består af eksperter inden for emnet, som kender de daglige forretningsbehov. Denne adskillelse giver det centrale BI-team mulighed for primært at fokusere på teknisk muliggørelse og support af BI-tjenesterne og -værktøjerne.

### <a name="focus-on-dataset-reusability"></a>Fokusér på genanvendeligheden af datasæt

Tilliden til brugerdefinerede ASP.NET BI-løsninger forhindrede udvikling af nye BI-løsninger. De påkrævede kompetencer betød, at antallet af forfattere af indhold til selvbetjening var lille. Da Power BI er et meget mere håndterbart værktøj – særligt designet til selvbetjent BI – spredte det sig hurtigt i organisationen, efter det først blev frigivet.

Bemyndigelsen af dataanalytikerne i virksomheden resulterede øjeblikkeligt i positive resultater. I forbindelse med Power BI-udvikling var det indledende fokus på visualisering. Selvom det resulterede i værdifulde BI-løsninger, resulterede dette fokus på et stort antal Power BI Desktop-filer, som hver havde en en til en-relation mellem rapporten og dens datasæt. Det resulterede i mange datasæt og duplikering af data og forretningslogik. For at kunne reducere duplikeringen af data, logik og indsatsen sørgede virksomheden for oplæring af og support til indholdsforfattere.

> [!IMPORTANT]
> Inkluder oplysninger om vigtigheden af genanvendeligheden af data i din interne oplæringsindsats. Håndter vigtige koncepter, så snart det er praktisk.

### <a name="test-data-access-multiple-ways"></a>Test dataadgang på flere måder

Virksomhedens data warehouse-platform er DB2. På baggrund af det aktuelle data warehouse-design fandt virksomheden ud af, at DirectQuery-modeller – i stedet for Import-modeller – fungerede bedst til deres behov.

> [!IMPORTANT]
> Udfør en teknisk POC (proof of concept) for at vurdere, hvilken lagringstilstand for modellen der fungerer bedst. Lær også dataudformere om lagringstilstande for modeller, og hvordan de kan vælge en passende tilstand for deres projekt.

### <a name="educate-authors-about-premium-licensing"></a>Oplær forfattere om Premium-licensering

Da det var nemmere at komme i gang med Power BI (sammenlignet med deres tidligere BI-platform), var mange af de tidlige brugere personer, der ikke havde licens til det forrige BI-værktøj. Som forventet steg antallet af indholdsforfattere markant. Disse indholdsforfattere ville forståeligt nok gerne dele deres indhold med andre, hvilket resulterede i et fortsat behov for yderligere Power BI Pro-licenser.

Virksomheden foretog en stor investering i Premium-arbejdsområder primært for at distribuere Power BI-indhold til mange brugere med gratis Power BI-licenser. Supportteamet arbejder sammen med indholdsforfattere for at sikre, at de bruger Premium-arbejdsområder, når det er relevant. Dermed undgås unødvendig allokering af Power BI Pro-licenser, når en bruger kun har brug for at anvende indhold.

> [!IMPORTANT]
> Der opstår tit spørgsmål om licensering. Vær forberedt på at oplære og hjælpe indholdsforfattere med at håndtere spørgsmål om licensering. Valider, at brugeranmodninger om Power BI Pro-licenser er berettigede.

### <a name="understand-the-data-gateways"></a>Forstå datagateways

Meget tidligt havde virksomheden mange personlige gateways. Når du bruger en datagatewayklynge i det lokale miljø skifter administrationsindsatsen til det centrale BI-team, hvilket giver community'et for indholdsforfattere mulighed for at fokusere på at producere indhold. Det centrale BI-team arbejdede sammen med det interne Power BI-brugercommunity for at reducere antallet af personlige gateways.

> [!IMPORTANT]
> Hav en plan for oprettelse og administration af datagateways i det lokale miljø. Beslut, hvem der har tilladelse til at installere og bruge en personlig gateway og håndhæve den med gatewaypolitikker.

### <a name="formalize-your-support-plan"></a>Formaliser din supportplan

I takt med at indførelsen af Power BI steg i organisationen, fandt virksomheden ud af, at en supporttilgang på flere niveauer fungerede godt:

- **Niveau 1: Intrateam:** Hver dag lærer folk af og uddanner andre.
- **Niveau 2: Power BI-community:** Folk stiller spørgsmål til det interne Teams-community for at lære af hinanden og kommunikere vigtige oplysninger.
- **Niveau 3: Centralt BI-team og COE:** Folk indsender mailanmodninger for at få hjælp. Sessioner af typen _Tid på kontoret_ afholdes to gange om ugen, så der samlet kan drøftes problemer og deles idéer.

> [!IMPORTANT]
> Selvom de første to niveauer er mindre formelle, er de lige så vigtige som det tredje supportniveau. Erfarne brugere har tendens til at stole mest på personer, de kender, hvorimod nye brugere (eller dem, som er dataanalytiker alene for en forretningsenhed eller en delt tjeneste) har en tendens til at stole mere på formel support.

### <a name="invest-in-training-and-governance"></a>Invester i oplæring og styring

I løbet af det seneste år har virksomheden forbedret sine tilbud om intern oplæring og sit program til datastyring. Styringsudvalget omfatter vigtige medlemmer fra hver af de distribuerede analysegrupper samt COE.

Der er nu seks interne Power BI-kurser i deres interne katalog. Kurset [Dashboard på en dag](https://powerbi.microsoft.com/diad/) er fortsat et populært kursus for begyndere. For at hjælpe brugerne med at udbygge deres færdigheder leverer de en serie bestående af tre Power BI-kurser og to DAX-kurser.

Hvilket er en af deres vigtigste beslutninger i forbindelse med datastyring, som er relateret til administration af Premium-kapaciteter. Virksomheden valgte at tilpasse deres kapacitet til vigtige analyseområder i forretningsenheder og delte tjenester. Så hvis der er ineffektivitet, mærkes effekten kun inden for dette ene område, og administratorerne af den decentraliserede kapacitet kan administrere kapaciteten, efter hvad de finder passende.

> [!IMPORTANT]
> Vær opmærksom på, hvordan Premium-kapaciteter bruges, og hvordan arbejdsområder tildeles til dem.

## <a name="next-steps"></a>Næste trin

Andre nyttige ressourcer omfatter:

- [Microsofts BI-transformation](center-of-excellence-microsoft-business-intelligence-transformation.md)
- [Whitepaper om planlægning af en udrulning af Power BI i en virksomhed](https://aka.ms/PBIEnterpriseDeploymentWP)
- [Dashboard på en dag](https://powerbi.microsoft.com/diad/)
- Har du spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
- Forslag? [Få ideer til at forbedre Power BI](https://ideas.powerbi.com/)

Der findes erfarne Power BI-partnere, som kan hjælpe din organisation med at gennemføre migreringsprocessen. Hvis du vil i kontakt med en Power BI-partner, skal du gå til [Power BI-partnerportalen](https://powerbi.microsoft.com/partners/).
