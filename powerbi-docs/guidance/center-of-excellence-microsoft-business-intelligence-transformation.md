---
title: Microsofts BI-transformation
description: Få mere at vide om, hvordan Microsoft fremmer en datakultur til forretningsmæssige beslutninger. I artiklen beskrives deres strategi og vision for BI.
author: peter-myers
ms.author: v-pemyer
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 08/19/2020
ms.openlocfilehash: fa3f8c553fd55e77e92b4a933df332bdd8c4dc6d
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96394445"
---
# <a name="microsofts-bi-transformation"></a>Microsofts BI-transformation

Denne artikel er rettet mod it-medarbejdere og it-ledere. Du får mere at vide om vores BI-strategi og -vision, der gør det muligt for os løbende at udnytte vores data som et aktiv. Du får også mere at vide om, hvordan vi fremmer en datakultur, hvor Power BI danner grundlag for vores beslutningstagning.

Først en smule baggrundsviden: I dag påvirker den enorme mængde data både forbrugere og virksomheder i en halsbrækkende fart. Succes i et så dataintensivt miljø kræver analytikere og ledere, der kan gøre de enorme datamængder til koncis indsigt. Udviklingen af Microsofts BI-værktøjer har ændret den måde, som Microsoft selv udforsker deres data og når frem til den rigtige indsigt på, hvilket er nødvendigt for at gøre en forskel i virksomheden.

Hvordan kan din organisation også revolutionere den måde, den arbejder med data på? Lad os hjælpe dig med nå frem til en forståelse ved at dele historien bag vores BI-transformationsrejse.

## <a name="microsoft-journey"></a>Microsofts rejse

For flere år siden tilskyndede vores organisationskultur hos Microsoft personer til at have fuldt ejerskab over data og indsigt. Der var også en stærk kulturel modstand mod at gøre ting på en standardiseret måde. Den organisatoriske kultur førte derfor til rapporterings- og analysemæssige udfordringer. Den førte mere specifikt til:

- Inkonsekvente datadefinitioner, hierarkier, målepunkter og KPI'er (nøgletalsindikatorer). Hvert land havde f.eks. deres egen måde at rapportere om nye indtægter på. Der var ingen konsistens, men en høj grad af forvirring.
- Analytikere brugte 75 % af tiden på at indsamle og kompilere data.
- 78 % af rapporterne blev oprettet i offlinemiljøer.
- Mere end 350 centrale økonomiværktøjer og -systemer.
- Et forbrug på ca. $30.000.000 årligt på "skyggeprogrammer".

Disse udfordringer fik os til at tænke over, hvordan vi kunne gøre tingene bedre. Økonomiafdelingen og andre interne teams fik ledelsens støtte til at transformere processen til gennemgang af forretningen, hvilket førte til udvikling af en samlet BI-platform som en enkelt kilde til sandheden. (Vi fortæller mere om vores BI-platform senere i denne artikel). I sidste ende førte disse innovationer til, at forretningsgennemgange blev transformeret fra kompakte tabelvisninger til mere detaljerede og indsigtsfulde visualiseringer, der fokuserede på vigtige forretningstemaer.

Hvordan opnåede vi dette vellykkede resultat? Levering af centraliseret BI, der administreres af it, i kombination med SSBI (selvbetjenings-BI) førte til succes. Vi beskriver det på to kreative måder: _disciplin centralt_ og _fleksibilitet hele vejen rundt_.

### <a name="discipline-at-the-core"></a>Disciplin centralt

"Disciplin centralt" betyder, at it-afdelingen bevarer kontrollen ved at varetage en enkelt masterdatakilde. Levering af standardiseret virksomheds-BI og definitionen af ensartede taksonomier og hierarkier af KPI'er er en del af denne disciplin. Datatilladelser gennemtvinges for at sikre, at vores medarbejdere kun kan få adgang til de data, de har brug for.

Først blev vi klar over, at vores BI-transformation ikke var et teknologiproblem. For at opnå succes lærte vi, at vi først skulle definere succes og derefter oversætte den til vigtige målepunkter. Det var meget vigtigt for os at opnå konsistens i definitionen på tværs af vores data.

Vores transformation fandt ikke sted over natten. Vi prioriterede leveringen af scorecards til vores datterselskaber, der består af ca. 30 KPI'er. Derefter har vi gradvist over flere år udvidet antallet og dybden af emneområderne og oprettet mere komplekse KPI-hierarkier. I dag giver det os mulighed for at akkumulere KPI'er på kundeniveau til KPI'er på virksomhedsniveau. Vores samlede antal KPI'er overstiger nu 2000, og den enkelte KPI er en vigtig måling af vores succes, der justeres i forhold til virksomhedens målsætninger. På tværs af hele virksomheden har vi nu virksomhedsrapporter og SSBI-løsninger med KPI'er, der er veldefinerede, konsistente og sikre.

### <a name="flexibility-at-the-edge"></a>Fleksibilitet hele vejen rundt

Analytikerne i vores økonomi-, salgs- og marketingteams er blevet mere fleksible og agile. De kan nu drage fordel af muligheden for at analysere data hurtigere. Dette scenarie er mere formelt beskrevet som _administreret SSBI (selvbetjenings-BI)_ . Vi ved nu, at administreret SSBI handler om _gensidige fordele_ for it og analytikere. Vi opnåede også optimeringer ved at fremme standardisering, viden og genbrug af vores data og BI-løsninger. Som virksomhed fandt vi den rigtige balance mellem centraliseret BI og administreret SSBI og opnåede en synergieffekt.

### <a name="our-solution"></a>Vores løsning

**Starlight** er det navn, vi giver vores interne dataharmoniserings- og analyseplatform, der understøtter økonomi, salg, marketing og engineering. Dens mission er at levere en robust, delt og skalerbar dataplatform. Platformen blev bygget udelukkende af økonomiafdelingen og er fortsat i drift i dag med de nyeste Microsoft-produkter.

**KPI-søen** er ikke en Azure Data Lake. Det er snarere en Starlight-drevet semantisk BI-tabelmodel, der hostes i Azure IaaS ved hjælp af Microsoft SQL Server Analysis Services. Den semantiske BI-model leverer data, som hentes fra mere end 100 interne kilder, og definerer adskillige hierarkier og KPI'er. Dens mission er at muliggøre rapportering af virksomhedsresultater og analyseteams på tværs af økonomi, marketing og salg. Det gør den ved at hente rettidig, nøjagtig indsigt med god ydeevne gennem samlede semantiske BI-modeller fra relevante kilder.

Det var en spændende tid, da den først blev udrullet, fordi den semantiske BI-tabelmodel resulterede i øjeblikkelige og målbare fordele. Den første version centraliserede C+E Finance- og Marketing BI-platforme. I de seneste seks år er den blevet udvidet til at konsolidere yderligere BI-løsninger. I dag er den fortsat under udvikling og udgør grundlaget for vores globale og kommercielle forretningsgennemgange samt standardrapportering og SSBI. Ibrugtagningen af modellen har oversteget vores vildeste forventninger.

Her er en oversigt over de vigtigste fordele:

- Den styrer scorecards for vores datterselskaber, virksomhedsgennemgange over hele verden samt økonomi-, marketing- og salgsrapporter og -analyser.
- Den understøtter selvbetjeningsanalyse og gør det muligt for analytikere at finde indsigt, der er skjult i data.
- Den ligger til grund for rapportering og analyser i forbindelse med incitamentsaflønnings-, marketing- og driftsanalyser, målepunkter for salg, gennemgange af den øverste ledelse samt den årlige planlægningsproces.
- Den leverer automatiseret og dynamisk rapportering og analyser fra en _enkelt kilde til sandheden_.

**KPI-søen** er en fantastisk succeshistorie. Vi præsenterer den ofte for vores kunder for at vise et eksempel på, hvordan man effektivt kan bruge vores nyeste teknologier. Ikke overraskende vækker den genklang hos mange.

#### <a name="how-it-works"></a>Sådan fungerer det

Starlight-platformen administrerer dataflowet fra anskaffelsen af data, til behandlingen og derefter hele vejen til udgivelsen:

1. Robust og fleksibel dataintegration foregår efter en tidsplan, hvor data samles fra over 100 forskellige rå kilder. Kildedatasystemerne omfatter relationsdatabaser, Azure Data Lake Storage og Azure Synapse-databaser. Emneområderne omfatter økonomi, marketing, salg og engineering.
2. Når dataene er gemt, bliver de tilpasset og forbedret ved hjælp af masterdata og forretningslogik. De indlæses derefter til data warehouse-tabeller. Den semantiske BI-tabelmodel opdateres derefter.
3. Analytikere i virksomheden bruger Excel og Power BI til at levere indsigt og analyse fra den semantiske BI-tabelmodel. Den gør det muligt for virksomhedsejere at mestre definitioner af målepunkter for deres egen forretning. Når det er nødvendigt, opnås skalering ved hjælp af Azure-IaaS med belastningsjustering.

## <a name="deliver-success"></a>Sådan får du succes

Alle vil gerne have én version af sandheden ... så længe det er deres egen. Men for nogle organisationer er det deres realitet. De har flere versioner af sandheden som følge af enkeltpersoner, der tager fuldt ejerskab over data og indsigt. For disse organisationer er denne ikke-administrerede tilgang ikke en måde at opnå succes på.

Det er derfor, vi mener, at I har brug for _et COE_ (Center of Excellence). Et COE er et centralt team, der er ansvarligt for at definere målepunkter og definitioner for hele virksomheden og meget mere. Det er også en forretningsfunktion, der organiserer personer, processer og teknologikomponenter i et omfattende sæt forretningskompetencer og -funktioner.

Der er meget, der tyder på, at et omfattende og robust COE er vigtigt for at kunne levere værdi og opnå større succes i virksomheden. Det kan omfatte ændringsforslag, standardprocesser, roller, retningslinjer, bedste fremgangsmåder, support, uddannelse og meget mere.

Vi inviterer dig til at læse artiklerne i denne COE-serie for at få mere at vide. Lad os hjælpe dig med at finde ud af, hvordan din organisation kan få succes ved at omfavne forandringer.

## <a name="next-steps"></a>Næste trin

Du kan finde flere oplysninger om denne artikel i følgende ressourcer:

- [Etabler et Center of Excellence](center-of-excellence-establish.md)
- Har du spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
- Forslag? [Få ideer til at forbedre Power BI](https://ideas.powerbi.com/)

I den [næste artikel i denne serie](center-of-excellence-establish.md) kan du få mere at vide om, hvordan et COE hjalp os hos Microsoft med at oprette en standardiseret analyse- og dataplatform til at give adgang til indsigt fra vores data.

### <a name="professional-services"></a>Professionelle tjenester

Der findes certificerede Power BI-partnere, som kan hjælpe din organisation med at lykkes, når du konfigurerer et COE. De kan give dig omkostningseffektiv træning eller overvågning af dine data. Hvis du vil i kontakt med en Power BI-partner, skal du gå til [Power BI-partnerportalen](https://powerbi.microsoft.com/partners/).

Du kan også interagere med erfarne konsulentpartnere. De kan hjælpe dig med at [vurdere](https://appsource.microsoft.com/marketplace/consulting-services?product=power-bi&serviceType=assessment&country=ALL&region=ALL), [evaluere](https://appsource.microsoft.com/marketplace/consulting-services?product=power-bi&serviceType=proof-of-concept&country=ALL&region=ALL) eller [implementere](https://appsource.microsoft.com/marketplace/consulting-services?product=power-bi&serviceType=implementation&country=ALL&region=ALL&page=1) Power BI.
