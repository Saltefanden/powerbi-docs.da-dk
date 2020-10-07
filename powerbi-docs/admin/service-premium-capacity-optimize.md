---
title: Optimering af Microsoft Power BI Premium-kapaciteter
description: Beskriver optimeringsstrategier for Power BI Premium-kapaciteter.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-premium
ms.topic: conceptual
ms.date: 04/09/2019
ms.custom: seodec18
LocalizationGroup: Premium
ms.openlocfilehash: 21aa643c82887ec9beaca659d9e2e97a0f1cdcc9
ms.sourcegitcommit: 51b965954377884bef7af16ef3031bf10323845f
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 09/30/2020
ms.locfileid: "91599310"
---
# <a name="optimizing-premium-capacities"></a>Optimering af Premium-kapaciteter

Når der opstår problemer med ydeevnen i en Premium-kapacitet, er det almindeligt først at optimere eller justere dine løsninger for at gendanne acceptable svartider. Begrundelsen for dette er at undgå at købe ekstra Premium-kapacitet, medmindre det er berettiget.

Når der kræves ekstra Premium-kapacitet, er der to muligheder, som beskrives i denne artikel:

- Opskalering af en eksisterende Premium-kapacitet
- Tilføjelse af en ny Premium-kapacitet

Til sidst i denne artikel gennemgår vi testmetoder og tilpasning af størrelsen på Premium-kapacitet.

## <a name="best-practices"></a>Bedste praksis

Når du forsøger at opnå den bedste udnyttelse og ydeevne, er der nogle anbefalede fremgangsmåder, herunder:

- Brug af arbejdsområder i stedet for personlige arbejdsområder.
- Adskillelse af forretningskritisk og SSBI (Self-Service BI) i forskellige kapaciteter.

  ![Adskillelse af forretningskritisk og SSBI (Self-Service BI) i forskellige kapaciteter](media/service-premium-capacity-optimize/separate-capacities.png)

- Hvis indhold kun deles med Power BI Pro-brugere, er der ingen grund til at gemme indholdet i en dedikeret kapacitet.
- Brug dedikeret kapacitet, når du ønsker at opnå et bestemt opdateringstidspunkt, eller når specifikke funktioner er påkrævet. For eksempel med store datasæt eller sideinddelt rapportering.

### <a name="addressing-common-questions"></a>Svar på almindelige spørgsmål

Optimering af udrulninger af Power BI Premium er et kompliceret emne, der involverer en forståelse af arbejdsbelastningskrav, tilgængelige ressourcer og effektiv udnyttelse af disse ressourcer.

I denne artikel tager vi fat på syv almindelige supportspørgsmål, der beskriver mulige problemer og forklaringer og oplysninger om, hvordan du kan identificere og løse problemerne.

### <a name="why-is-the-capacity-slow-and-what-can-i-do"></a>Hvorfor er kapaciteten langsom, og hvad kan jeg gøre?

Der kan være mange årsager til en langsom Premium-kapacitet. Dette spørgsmål kræver yderligere oplysninger for at forstå, hvad der menes med langsom. Tager det for lang tid at indlæse rapporter? Eller kan de slet ikke indlæses? Tager det for lang tid at indlæse eller opdatere visualiseringerne, når brugerne interagerer med rapporten? Tager opdateringerne længere tid at fuldføre end forventet eller end tidligere?

Når du har fået en forståelse af årsagen, kan du begynde at foretage en undersøgelse. Svar på seks følgende spørgsmål kan hjælpe dig med at håndtere mere specifikke problemer.

### <a name="what-content-is-using-up-my-capacity"></a>Hvilket indhold bruger al kapaciteten?

Du kan bruge appen **Power BI Premium Capacity Metrics** til at filtrere efter kapacitet og gennemse metrikværdier for arbejdsområdeindholdets ydeevne. Det er muligt at gennemse målepunkterne for ydeevnen og ressourceforbruget efter time for de seneste syve dage for alt indhold, der er lagret i en Premium-kapacitet. Overvågning er ofte det første skridt, når du skal lokalisere fejl i forbindelse med ydeevnen for en Premium-kapacitet.

Vigtige målepunkter, der bør overvåges:

- Gennemsnitlig CPU og antal gange med høj udnyttelse.
- Gennemsnitlig hukommelse og antal gange med høj udnyttelse samt hukommelsesforbrug for bestemte datasæt, dataflows og sideinddelte rapporter.
- Aktive datasæt, der er indlæst i hukommelsen.
- Gennemsnitlige og maksimale varigheder for forespørgsler.
- Gennemsnitlige ventetider for forespørgsler.
- Gennemsnitlige opdateringstider for datasæt og dataflows.

I appen Power BI Premium Capacity Metrics viser den aktive hukommelse den samlede mængde hukommelse, der er allokeret til en rapport, der ikke kan fjernes, fordi den har været i brug inden for de sidste tre minutter. En stor stigning i ventetiden for opdateringer kan skyldes et stort/eller aktivt datasæt.

I diagrammet **Top 5 efter gennemsnitlig varighed** vises de fem datasæt, sideinddelte rapporter og dataflows, der forbruger flest kapacitetsressourcer. Indholdet på top fem-listerne bør undersøges og muligvis optimeres.

### <a name="why-are-reports-slow"></a>Hvorfor er rapporterne langsomme?

I følgende tabel vises mulige problemer og måder at identificere og håndtere dem på.

#### <a name="insufficient-capacity-resources"></a>Utilstrækkelige kapacitetsressourcer

| Mulige forklaringer | Sådan identificeres problemet | Sådan løses problemet |
| --- | --- | --- |
| Højt hukommelsesforbrug i alt (model kan ikke fjernes, da den har været i brug inden for de sidste tre minutter).<br><br> Flere store stigninger i forespørgselsventetider.<br><br> Flere store stigninger i opdateringsventetider. | Overvåg målepunkter for hukommelse \[[1](#endnote-1)\] og antallet af fjernelser \[[2](#endnote-2)\]. | Reducer modelstørrelsen, eller konverter til DirectQuery-tilstand. Se afsnittet [Optimering af modeller](#optimizing-models) i denne artikel.<br><br> Opskaler kapaciteten.<br><br> Tildel indholdet til en anden kapacitet. |

#### <a name="inefficient-report-designs"></a>Ineffektive rapportdesign

| Mulige forklaringer | Sådan identificeres problemet | Sådan løses problemet |
| --- | --- | --- |
| Rapportsider, der indeholder for mange visualiseringer (interaktiv filtrering kan udløse mindst én forespørgsel pr. visualisering).<br><br> Visualiseringer henter flere data end nødvendigt. | Gennemse rapportdesign.<br><br> Interview rapportbrugere for at forstå, hvordan de interagerer med rapporterne.<br><br> Overvåg målepunkter for datasætforespørgsler \[[3](#endnote-3)\]. | Omdesign rapporter med færre visualiseringer pr. side. |

#### <a name="dataset-is-slow-especially-when-reports-have-previously-performed-well"></a>Datasættet er langsomt – især når rapporter tidligere har kørt godt

| Mulige forklaringer | Sådan identificeres problemet | Sådan løses problemet |
| --- | --- | --- |
| Stigende mængder af importdata.<br><br> Kompleks eller ineffektiv beregningslogik, inklusive RLS-roller.<br><br> Modellen er ikke fuldt optimeret.<br><br> (DQ/live) Ventetid for gateway.<br><br> Langsomme forespørgselssvartider for DQ-kilde. | Gennemse modeldesign.<br><br> Overvåg ydelsestællere for gateway. | Se afsnittet [Optimering af modeller](#optimizing-models) i denne artikel. |

#### <a name="high-concurrent-report-usage"></a>Højt samtidigt forbrug af rapporter

| Mulige forklaringer | Sådan identificeres problemet | Sådan løses problemet |
| --- | --- | --- |
| Lange forespørgselsventetider.<br><br> CPU-mætning.<br><br> Grænserne for DQ-/liveforbindelse er blevet overskredet. | Overvåg målepunkter for CPU-forbruget \[[4](#endnote-4)\], forespørgselsventetider og udnyttelse af DQ-/liveforbindelser \[[5](#endnote-5)\] samt forespørgselsvarigheder. Hvis de er svingende, kan det tyde på problemer med samtidighed. | Opskaler kapaciteten, eller tildel indholdet til en anden kapacitet.<br><br> Omdesign rapporter med færre visualiseringer pr. side. |

**Noter:**    
<a name="endnote-1"></a>\[1\] Gennemsnitligt hukommelsesforbrug (GB) og højeste hukommelsesforbrug (GB).   
<a name="endnote-2"></a>\[2\] Fjernelser af datasæt.   
<a name="endnote-3"></a>\[3\] Dataset Queries, Dataset Average Query Duration (ms), Dataset Wait Count og Dataset Average Wait Time (ms).   
<a name="endnote-4"></a>\[4\] CPU High Utilization Count og CPU Time of Highest Utilization (de seneste syv dage).   
<a name="endnote-5"></a>\[5\] DQ/LC High Utilization Count and DQ/LC Time of Highest Utilization (de seneste syv dage).   

### <a name="why-are-reports-not-loading"></a>Hvorfor indlæses rapporter ikke?

Når rapporter ikke indlæses, er det et sikkert tegn på, at kapaciteten ikke har tilstrækkelig hukommelse og er overbebyrdet. Dette kan ske, når alle indlæste modeller bliver forespurgt aktivt og derfor ikke kan fjernes, og hvis opdateringshandlinger er blevet sat på pause eller forsinket. Power BI-tjenesten forsøger at indlæse datasættet i 30 sekunder, og brugeren får besked om fejlen med et forslag til at prøve igen om et øjeblik.

Der er i øjeblikket ingen metrikværdier til at overvåge fejl i forbindelse med rapportindlæsninger. Du kan identificere risikoen for dette problem ved at overvåge systemhukommelsen, især den højeste udnyttelse og tidspunktet for den højeste udnyttelse. Mange fjernelser af datasæt og en lang gennemsnitlig ventetid kan tyde på, at dette problem er ved at opstå.

Hvis det sker sjældent, betragtes det muligvis ikke som en prioritet. Rapportbrugere bliver informeret om, at tjenesten er optaget, og at de skal prøve igen efter et øjeblik. Hvis det sker for ofte, kan problemet løses ved at skalere Premium-kapaciteten op eller ved at tildele indholdet til en anden kapacitet.

Kapacitetsadministratorer (og administratorer af Power BI-tjenesten) kan overvåge metrikværdien **forespørgselsfejl** for at bestemme, hvornår dette sker. De kan også genstarte kapaciteten for at nulstille alle handlinger i tilfælde af, at systemet overbelastes.

### <a name="why-are-refreshes-not-starting-on-schedule"></a>Hvorfor starter opdateringer ikke efter planen?

Der er ikke garanti for starttidspunkterne for planlagte opdateringer. Husk, at Power BI-tjenesten altid prioriterer interaktive handlinger over handlinger i baggrunden. Opdatering er en handling i baggrunden, der kan opstå, når to betingelser er opfyldt:

- Der er tilstrækkelig hukommelse
- Antallet af understøttede samtidige opdateringer for Premium-kapaciteten ikke er overskredet

Hvis betingelserne ikke opfydes, sættes opdateringen i kø, indtil betingelserne er opfyldt.

Husk, at der for en fuld opdatering kræves mindst det dobbelte af den aktuelle hukommelsesstørrelse for datasættet. Hvis der ikke er tilstrækkelig hukommelse tilgængelig, kan opdateringen ikke påbegyndes, før modelfjernelse frigør hukommelse – det betyder forsinkelser, indtil et eller flere datasæt bliver inaktive og kan fjernes.

Husk, at det maksimale antal samtidige opdateringer, der understøttes, er angivet til 1,5 gange backend-v-kernerne, rundet op.

En planlagt opdatering mislykkes, når den ikke kan påbegyndes, før den næste planlagte opdatering skal påbegyndes. En opdatering efter behov, der er udløst manuelt fra brugergrænsefladen, vil forsøge at køre op til tre gange, før der opstår en fejl.

Kapacitetsadministratorer (og administratorer af Power BI-tjenesten) kan overvåge metrikværdien **den gennemsnitlig opdateringsventetid (minutter)** for at bestemme den gennemsnitlige forsinkelse mellem det planlagte tidspunkt og begyndelsen af handlingen.

Selvom det normalt ikke er en administrativ prioritet, kan påvirkningen af rettidige dataopdateringer sikre, at der er tilstrækkelig tilgængelig hukommelse. Dette kan gøres ved at isolere datasæt til kapaciteter, man ved har tilstrækkeligt med ressourcer. Det er også muligt, at administratorer kan koordinere med datasætejere for at hjælpe med at forskyde eller reducere planlagte dataopdateringer og på den måde minimere antallet af kollisioner. Bemærk, at det ikke er muligt for en administrator at få vist opdateringskøen eller at hente tidsplaner for datasætopdateringer.

### <a name="why-are-refreshes-slow"></a>Hvorfor kører opdateringerne langsomt?

Opdateringer kan være langsomme – eller opfattes som langsomme (som de forrige almindelige spørgsmål omhandler).

Når opdateringen rent faktisk er langsom, kan det skyldes flere årsager:

- Utilstrækkelig CPU (opdateringer kan være meget CPU-krævende).
- Utilstrækkelig hukommelse, hvilket resulterer i, at opdateringen afbrydes midlertidigt (som kræver, at opdateringen starter forfra, når betingelser for at starte forfra er opfyldt).
- Årsager, der ikke har med kapaciteten at gøre, herunder svartiden for datakildesystemet, netværksventetid, ugyldige tilladelser eller gatewaygennemløb.
- Datamængde – en god grund til at konfigurere trinvise opdateringer, som beskrevet nedenfor.

Kapacitetsadministratorer (og administratorer af Power BI-tjenesten) kan overvåge metrikværdien **den gennemsnitlige opdateringsvarighed (minutter)** for at have en benchmark til sammenligning over tid og metrikværdien **gennemsnitlig opdateringsventetid (minutter)** for at fastsætte den gennemsnitlige mellemliggende tid mellem det planlagte tidspunkt og den faktiske start af handlingen.

Trinvise opdateringer kan reducere dataopdateringsvarigheden væsentligt, især for store modeltabeller. Der er fire fordele, der er forbundet med trinvis opdatering:

- **Opdateringerne sker hurtigere** – Kun et undersæt af en tabel skal indlæses, hvilket nedbringer CPU- og hukommelsesforbruget, og parallelitet kan være højere ved opdatering af flere partitioner.
- **Opdateringerne sker kun, når det er påkrævet** – Politikker for trinvis opdatering kan konfigureres til kun at indlæses, når data er blevet ændret.
- **Opdateringerne er mere pålidelige** – Kortere kørende forbindelser til ustabile datakildesystemer er mindre sårbare over for afbrydelser.
- **Modellerne forbliver trimmede** – Politikker for trinvis opdatering kan konfigureres til automatisk at fjerne historik ud over et skydevindue.

Du kan få mere at vide under [Trinvis opdatering i Power BI Premium](service-premium-incremental-refresh.md).

### <a name="why-are-data-refreshes-not-completing"></a>Hvorfor fuldføres dataopdateringer ikke?

Når dataopdateringen påbegyndes, men ikke fuldføres, kan det skyldes flere årsager:

- Utilstrækkelig hukommelse, selvom der er kun én model i Premium-kapaciteten, dvs. størrelsen på modellen er meget stor.
- Årsager, der ikke har med kapaciteten at gøre, herunder afbrydelse af forbindelsen til datakildesystemet, ugyldige tilladelser eller gatewayfejl.

Kapacitetsadministratorer (og administratorer af Power BI-tjenesten) kan overvåge metrikværdien **opdateringsfejl pga. manglende hukommelse**.

## <a name="optimizing-models"></a>Optimering af modeller

Et optimalt modeldesign er afgørende for leveringen af en effektiv og skalerbar løsning. En komplet diskussion af dette emne er dog ikke inden for rammerne af denne artikel. I stedet indeholder dette afsnit vigtige områder, som bør overvejes ve doptimering f modeller.

### <a name="optimizing-power-bi-hosted-models"></a>Optimering af Power BI-hostede modeller

Det er muligt at optimere de modeller, der hostes i en Premium-kapacitet, i datakilden eller -kilderne og modellagene.

Overvej optimeringsmulighederne for en importmodel:

![Optimeringsmuligheder for en importmodel](media/service-premium-capacity-optimize/import-model-optimizations.png)

På datakildelaget:

- Relationelle datakilder kan optimeres for at sikre, den hurtigst mulige opdatering ved på forhånd at integrere data, anvende relevante indekser, definere tabelpartitioner, der er i overensstemmelse med trinvise opdateringsperioder, og oprette beregninger (i stedet for beregnede modeltabeller og kolonner) eller føje beregningslogik til visninger.
- Ikke-relationelle datakilder kan forudintegreres med relationelle lagre.
- Sørg for, at gateways har tilstrækkelige ressourcer, helst på dedikerede maskiner med tilstrækkelig netværksbåndbredde og tæt på datakilderne.

På modellaget:

- Design af Power-forespørgsler kan minimere eller fjerne komplekse transformationer og især dem, der fletter forskellige datakilder (datalagre opnår dette i fasen Udtræk-Transformer-Indlæs). Sikring af der angives relevante niveauer for beskyttelse af personlige oplysninger for datakilder kan forhindre, at Power BI skal indlæse komplette resultater for at generere et kombineret resultatet på tværs af forespørgsler.
- Modelstrukturen bestemmer de data, der skal indlæses, og har en direkte indvirkning på modelstørrelsen. Det kan designes til at undgå at indlæse unødvendige data ved at fjerne kolonner, fjerne rækker (især historiske data) eller ved at indlæse opsummerede data (i stedet for at indlæse detaljerede data). En væsentlig reduktion af størrelsen kan opnås ved at fjerne kolonner med høj kardinalitet (især tekstkolonner), som hverken kan gemmes eller komprimeres særligt effektivt.
- Ydeevnen for modelforespørgsler kan forbedres ved at konfigurere relationer i én retning, medmindre der er en meget god grund til at tillade tovejsfiltrering. Du kan også bruge funktionen [CROSSFILTER](/dax/crossfilter-function) i stedet for tovejsfiltrering.
- Med akkumuleringstabeller kan du opnå hurtige forespørgsler ved at indlæse data, der er opsummerede på forhånd, men dette vil forøge størrelsen af modellen og resulterer i længere opdateringstider. Akkumuleringstabeller bør generelt benyttes til design med meget store modeller eller sammensatte modeller.
- Beregnede tabeller og kolonner forøger størrelsen på modellen og resulterer i længere opdateringstider. En mindre lagerstørrelse og en hurtigere opdateringstid kan generelt opnås, når dataene er oprettet eller beregnet i datakilden. Hvis dette ikke er muligt, kan brug af brugerdefinerede kolonner i Power-forespørglser forbedre lagerkomprimeringen.
- Det kan være muligt at optimere DAX-udtryk for målinger og RLS-regler og måske omskrive logik for at undgå dyre formler.
- Trinvis opdatering reducerer opdateringstiden væsentligt og sparer hukommelse og CPU. Den trinvise opdatering kan også være konfigureret til at fjerne historiske data ved at holde modelstørrelserne trimmede.
- En model kan ændres til to modeller, når der er forskellige og modstridende forespørgselsmønstre. Nogle rapporter rummer f.eks. aggregeringer på højt niveau over al historik og kan tolerere ventetid for 24 timer. Andre rapporter beskæftiger sig med dagens data og har brug for detaljeret adgang til individuelle transaktioner. Du kan også oprette to modeller, der er optimeret til ethvert behov, i stedet for at designe en enkelt model, der opfylder alle rapportbehov.

Overvej optimeringsmulighederne for en DirectQuery-model. Eftersom modellen udsteder forespørgselsanmodninger til den underliggende datakilde, er optimering af datakilden afgørende for leveringen af dynamiske modelforespørgsler.

 ![Optimeringsmuligheder for en DirectQuery-model](media/service-premium-capacity-optimize/direct-query-model-optimizations.png)

På datakildelaget:

- Datakilden kan optimeres for at sikre den hurtigst muligt forespørgsel ved at integrere data på forhånd (hvilket ikke er muligt på modellaget), anvender relevante indekser, definere tabelpartitioner, oprette opsummerede data (med indekserede visninger) og minimere mængden af beregninger. Den bedste oplevelse opnås, når passthrough-forespørgsler kun skal filtrere og udføre indre joinforbindelser mellem indekserede tabeller eller visninger.
- Sørg for, at gateways har tilstrækkelige ressourcer, helst på dedikerede maskiner med tilstrækkelig netværksbåndbredde og tæt på datakilden.

På modellaget:

- Design af Power-forespørgsler helst skal ikke anvende transformationer – ellers skal transformationer holdes på et absolut minimum.
- Ydeevnen for modelforespørgsler kan forbedres ved at konfigurere relationer i én retning, medmindre der er en meget god grund til at tillade tovejsfiltrering. Modelrelationer skal desuden konfigureres til at antage, at referentiel integritet gennemtvinges (når det er tilfældet) og medfører, at datakildeforespørgsler bruger flere indre joinforbindelser (i stedet for ydre joinforbindelser).
- Undgå at oprette brugerdefinerede kolonner i Power-forespørgsler eller modelberegnede kolonner – de bør materialiseres i datakilden, når det er muligt.
- Det kan være muligt at optimere DAX-udtryk for målinger og RLS-regler og måske omskrive logik for at undgå dyre formler.

Overvej optimeringsmulighederne for en sammensat model: Husk, at en sammensat model gør det muligt at blande import- og DirectQuery-tabeller.

![Optimeringsmuligheder for en sammensat model](media/service-premium-capacity-optimize/composite-model-optimizations.png)

- Optimeringen af import- og DirectQuery-modeller gælder generelt for de sammensatte modeltabeller, der anvender disse lagertilstande.
- Du skal bestræbe dig op at opnå et balanceret design ved at konfigurere tabeller af dimensionstypen (repræsenterer forretningsobjekter) som tabeller med dobbelt lagringstilstand og tabeller af oplysningstypen (ofte store tabeller, der repræsenterer driftsmæssige fakta) som lagringstilstanden DirectQuery. Dobbelt lagringstilstand betyder både import- og DirectQuery-lagringstilstandene og gør det muligt for Power BI-tjenesten at bestemme den mest effektive lagringstilstand, der skal bruges til at generere en oprindelig forespørgsel for passthrough.
- Sørg for, at gateways har tilstrækkelige ressourcer, helst på dedikerede maskiner, med den nødvendige netværksbåndbredde og i nærheden af datakilderne.
- Akkumuleringstabeller, der er konfigureret som importlagringstilstand kan resultere i en væsentlig forbedring af forespørgselsydeevnen, når de bruges til at opsummere tabeller af faktatypen i DirectQuery-lagringstilstand. I dette tilfælde øger akkumuleringstabeller størrelsen af modellen og øger opdateringstiden, hvilket ofte er et acceptabelt kompromis for at opnå hurtigere forespørgsler.

### <a name="optimizing-externally-hosted-models"></a>Optimering af eksternt hostede modeller

Mange af de optimeringsmuligheder, der er beskrevet i afsnittet [Optimering af Power BI-hostede modeller](#optimizing-power-bi-hosted-models) gælder også for modeller, der er udviklet med Azure Analysis Services og SQL Server Analysis Services. Der er dog undtagelser i form af bestemt funktioner, der ikke understøttes i øjeblikket, bl.a. sammensatte modeller og akkumuleringstabeller.

I forbindelse med eksternt hostede datasæt bør du tage databasehostingen i forhold til Power BI-tjenesten med i dine overvejelser. For Azure Analysis Services betyder det, at Azure-ressourcen skal oprettes i samme område som Power BI-lejeren (det lokale område). I forbindelse med IaaS i SQL Server Analysis Services betyder det, at den virtuelle maskine skal hostes i samme område, og hvis der er tale om det lokale miljø, skal der sørges for en effektiv gatewaykonfiguration.

Det skal også nævnes, at Azure Analysis Services-databaser og SQL Server Analysis Services-tabeldatabaser kræver, at deres modeller indlæses fuldt ud i hukommelsen, og at de forbliver der hele tiden for at understøtte forespørgsler. På samme måde som Power BI-tjenesten skal der være tilstrækkelig hukommelse til opdatering, hvis modellen skal forblive online under opdateringen. I modsætning til Power BI-tjenesten er der ikke noget behov for, at modellerne tilføjes og fjernes fra hukommelsen i henhold til forbrug. Power BI Premium tilbyder derfor en mere effektiv tilgang til maksimering af modelforespørgsler med et lavere hukommelsesforbrug.

## <a name="capacity-planning"></a>Kapacitetsplanlægning

Størrelsen af en Premium-kapacitet bestemmer den hukommelse og de processorressourcer, der er tilgængelige, og de grænser, der er gælder for kapaciteten. Antallet af Premium-kapaciteter bør også overvejes, da oprettelsen af flere Premium kapaciteter kan hjælpe med at isolere arbejdsbelastninger fra hinanden. Bemærk, at lagring er 100 TB pr. kapacitetsnode, og at det sandsynligvis er mere end rigeligt for en hvilken som helst arbejdsbelastning.

Det kan være udfordrende at fastlægge størrelsen på og antallet af Premium-kapaciteter, især for de første kapaciteter, som du opretter. Det første trin, når du vælger kapacitetstørrelse er at forstå den gennemsnitlige arbejdsbelastning, der repræsenterer det forventede daglige forbrug. Det er vigtigt at forstå, at ikke alle arbejdsbelastninger er ens. I den ene ende af spektret kan du f.eks. have 100 samtidige brugere, der får adgang til en enkelt rapportside, der indeholder en enkelt visualisering, hvilket nemt kan opnås. I den anden ende af spektret kan du have 100 samtidige brugere, der får adgang til 100 forskellige rapporter, der hver har 100 visualiseringer på rapportsiden, hvilket belaster behovet for kapacitetsressourcer på forskellig vis.

Kapacitetsadministratorer skal derfor overveje flere forskellige faktorer, der er specifikke for jeres miljø, indhold og forventet brug. Det overordnede mål er at maksimere udnyttelsen af kapaciteter, samtidig med at der leveres ensartede forespørgselstider samt acceptable ventetider og fjernelsesrater. Følgende faktorer bør overvejes:

- **Modelstørrelse og datakarakteristika** – Importmodeller skal være fuldt indlæst i hukommelsen for at muliggøre forespørgsler eller opdateringer. Datasæt med liveforbindelse eller DQ-datasæt kan kræve betydelig processortid og muligvis også meget hukommelse for at evaluere komplekse målinger eller RLS-regler. Hukommelses- og processorstørrelse og gennemløb for forespørgsler med liveforbindelse eller DQ-forespørgsler er begrænset af kapacitetsstørrelsen.
- **Samtidige aktive modeller** – Den samtidige forespørgsel af forskellige importmodeller leverer den bedste svartid og ydeevne, når de forbliver i hukommelsen. Der skal være tilstrækkelig hukommelse til at hoste alle modeller, der forespørges meget, med ekstra hukommelse for at muliggøre opdateringen af disse modeller.
- **Opdatering af importmodel** – Opdateringstypen (fuld eller trinvis), varigheden og kompleksiteten af Power-forespørgsler og beregnet tabel-/kolonnelogik kan påvirke hukommelsesforbruget og især processorforbruget. Samtidige opdateringer er begrænset af kapacitetsstørrelsen (1,5 x backend v-kerner, rundet op).
- **Samtidige forespørgsler** – Mange samtidige forespørgsler kan resultere i rapporter, der ikke svarer, når processor eller live-/DQ-forbindelser overskrider kapacitetsgrænsen. Dette er især tilfældet for rapportsider, der indeholder mange visualiseringer.
- **Dataflows og sideinddelte rapporter** – Kapaciteten kan konfigureres for at understøtte dataflows og sideinddelte rapporter, der hver især kræver en konfigurerbar maksimal procentdel af kapacitetshukommelsen. Hukommelse allokeres dynamisk til dataflow, men den allokeres statisk til sideinddelte rapporter.

Ud over disse faktorer kan kapacitetsadministratorer overveje at oprette flere kapaciteter. Flere kapaciteter gør det muligt at isolere arbejdsbelastninger og kan konfigureres til at sikre, at prioriterede arbejdsbelastninger har garanterede ressourcer. To kapaciteter kan f.eks. oprettes for at adskille forretningskritiske arbejdsbelastninger fra arbejdsbelastninger i BI-selvbetjeningsportalen (SSBI). Den forretningskritiske kapacitet kan bruges til at isolere store virksomhedsmodeller, der giver dem garanterede ressourcer, hvor det kun er it-afdelingen, der har oprettelesadgang. SSBI-kapaciteten kan bruges til at hoste et stigende antal mindre modeller, som forretningsanalytikere har adgang til. SSBI-kapaciteten kan nogle gange opleve ventetider på forespørgsler eller opdateringer, der er acceptable.

Med tiden kan kapacitetsadministratorer balancere arbejdsområder på tværs af kapaciteter ved at flytte indhold mellem arbejdsområder eller arbejdsområder mellem kapaciteter og ved at skalere kapaciteter op eller ned. Der skaleres som regel op, når man hoster store modeller, og ud i forbindelse med en høj grad af samtidighed.

Husk, at køb af en licens giver lejeren v-kerner. Køb af et **P3-** abonnement kan bruges til at oprette en eller op til fire Premium-kapaciteter, dvs. 1 x P3 eller 2 x P2 eller 4 x P1. Før du konverterer en P2-kapacitet til en P3-kapacitet, kan du også overveje at opdele v-kernerne for at oprette to P1-kapaciteter.

## <a name="testing-approaches"></a>Testmetoder

Når du har valgt en kapacitetsstørrelse, kan test udføres ved at oprette et kontrolleret miljø. En praktisk og økonomisk mulighed er at oprette en Azure-kapacitet (A-SKU'er), hvor en P1-kapacitet har den samme størrelse som en A4-kapacitet, og P2- og P3-kapaciteterne har den samme størrelse som henholdsvis A5- og A6-kapaciteterne. Det er hurtigt at oprette Azure-kapaciteter, og de faktureres på timebasis. Når testen er fuldført, kan de nemt slettes, så du ikke længere faktureres for disse Azure-kapaciteter.

Testindholdet kan føjes til de arbejdsområder, der er oprettet på Azure-kapaciteten, og en enkelt bruger kan derefter køre rapporter for at generere en realistisk og repræsentativ arbejdsbelastning af forespørgsler. Hvis der er importmodeller, skal der også udføres en opdatering af hver model. Overvågningsværktøjer kan derefter bruges til at gennemse alle målepunkter for at forstå ressourceudnyttelsen.

Det er vigtigt, at testene kan gentages. Testene skal køres flere gange, og de skal levere ca. det samme resultat hver gang. Et gennemsnit af disse resultater kan bruges til at ekstrapolere og estimere arbejdsbelastning under ægte produktionsbetingelser.

Hvis du allerede har en kapacitet og de rapporter, du vil udføre en belastningstest for, skal du bruge [værktøjet til generering af PowerShell-belastning](https://aka.ms/PowerBILoadTestingTool) til hurtigt at generere en belastningstest. Værktøjet giver dig mulighed for at vurdere, hvor mange instanser af hver rapport der kan køres af din kapacitet på en time. Du kan bruge værktøjet til at vurdere din kapacitets evne til individuel rapportgengivelse eller til at gengive flere forskellige rapporter parallelt. Du kan finde flere oplysninger i videoen [Microsoft Power BI: Premium-kapacitet](https://www.youtube.com/watch?time_continue=1860&v=C6vk6wk9dcw).

Hvis du vil generere en mere kompleks test, bør du overveje at udvikle et program til belastningstest for at simulere en realistisk arbejdsbelastning. Du kan finde flere oplysninger i webinaret om [belastningstest af Power BI-programmer med Visual Studio-belastningstest](https://powerbi.microsoft.com/blog/week-4-11-webinars-load-testing-power-bi-applications-with-visual-studio-load-test-and-getting-started-with-cds-for-apps-based-model-driven-apps/).

## <a name="acknowledgements"></a>Referencer

Denne artikel er skrevet af Peter Myers, som er Data Platform MVP og uafhængig BI-ekspert hos [Bitwise Solutions](https://www.bitwisesolutions.com.au/).

## <a name="next-steps"></a>Næste trin

> [!div class="nextstepaction"]
> [Scenarier med Premium-kapacitet](service-premium-capacity-scenarios.md)   
  
Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)