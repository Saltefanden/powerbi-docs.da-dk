---
title: Microsoft Power BI Premium-kapacitetsscenarier
description: Beskriver almindelige Power BI Premium-kapacitetsscenarier.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-premium
ms.topic: conceptual
ms.date: 11/11/2020
ms.custom: ''
LocalizationGroup: Premium
ms.openlocfilehash: a3835ff26bf86024b827edf69e19d6f603e66c2c
ms.sourcegitcommit: cc20b476a45bccb870c9de1d0b384e2c39e25d24
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 11/11/2020
ms.locfileid: "94512878"
---
# <a name="premium-capacity-scenarios"></a>Premium-kapacitetsscenarier

I denne artikel beskrives scenarier i den virkelige verden, hvor Power BI Premium-kapaciteter er implementeret. Almindelige problemer og udfordringer beskrives, herunder hvordan du kan identificere problemer og hjælpe med at løse dem:

- [Sådan holdes datasæt opdateret](#keeping-datasets-up-to-date)
- [Sådan identificeres datasæt med lange svartider](#identifying-slow-responding-datasets)
- [Sådan identificeres årsager til datasæt med sporadisk langsomme svartider](#identifying-causes-for-sporadically-slow-responding-datasets)
- [Sådan fastlægges det, om der er tilstrækkelig hukommelse](#determining-whether-there-is-enough-memory)
- [Sådan fastlægges det, om der er tilstrækkelig CPU](#determining-whether-there-is-enough-cpu)

Fremgangsmåden samt eksemplerne på diagrammer og tabeller er fra **appen Power BI Premium Capacity Metrics**, som en Power BI-administrator har adgang til.

> [!NOTE]
> Power BI Premium har for nylig udgivet en ny version af Premium med navnet **Premium Gen2**, der i øjeblikket er tilgængelig som prøveversion. Premium Gen2 forenkler administrationen af Premium-kapaciteter og reducerer administrationsomkostningerne. Du kan finde flere oplysninger under [Power BI Premium – Generation 2 (prøveversion)](service-premium-what-is.md#power-bi-premium-generation-2-preview).

## <a name="keeping-datasets-up-to-date"></a>Sådan holdes datasæt opdateret

I dette scenarie blev en undersøgelse udløst, da brugerne klagede over, at rapportdata nogle gange forekom gamle eller "forældede".

I appen interagerer administratoren med visualiseringen **Refreshes**, der sorterer datasæt efter statistikken **Max Wait Time** i faldende rækkefølge. Dette visual hjælper dem med at registrere de datasæt, der har de længste ventetider, grupperet efter navn på arbejdsområde.

![Datasætopdateringer sorteret i faldende rækkefølge efter maksimal ventetid, grupperet efter arbejdsområde](media/service-premium-capacity-scenarios/dataset-refreshes.png)

I visualiseringen **Gennemsnitlige opdateringsventetider pr. time** lægger de desuden mærke til, at opdateringsventetiderne er på deres højeste omkring kl. 16.00 hver dag.

![Opdateringsventetider peaker periodisk kl. 16.00](media/service-premium-capacity-scenarios/peak-refresh-waits.png)

Der er flere mulige forklaringer til disse resultater:

- Der kan opstå for mange opdateringsforsøg på samme tid, som overskrider de grænser, der er defineret af kapacitetsnoden. I dette tilfælde seks samtidige opdateringer på en P1 med standardallokering af hukommelse.

- De datasæt, der skal opdateres, kan være for store til at passe til den tilgængelige hukommelse (kræver mindst 2 x den påkrævede hukommelse til en fuld opdatering).
- Ineffektiv logik i Power-forespørgslen kan resultere i en spidsbelastning af hukommelsesforbruget under opdateringen af datasæt. I en travl kapacitet kan denne spidsbelastning undertiden nå den fysiske grænse, hvilket bevirker, at opdateringen mislykkes og kan påvirke andre rapportvisningshandlinger for kapaciteten.
- Datasæt, der ofte forespørges, som skal forblive i hukommelsen, kan påvirke muligheden for, at andre datasæt opdateres, på grund af begrænset tilgængelig hukommelse.

Til at undersøge dette kan Power BI-administratoren søge efter følgende ting:

- Manglende hukommelse på tidspunktet for opdateringen af data, når den tilgængelige hukommelse er mindre end 2 gange størrelsen på det datasæt, der skal opdateres.
- Datasæt, der ikke opdateres og ikke var i hukommelsen før opdatering, men alligevel begyndte at vise interaktiv trafik på tidspunkter med mange opdateringer. Hvis du vil se, hvilke datasæt der indlæses i hukommelsen på et givet tidspunkt kan en Power BI-administrator se på datasætområdet under fanen **Datasæt** i appen. Administratoren kan derefter filtrere på tværs til et givent tidspunkt ved at klikke på en af søjlerne i **Antal indlæste datasæt pr. time**. En lokal stigning (vist på billedet nedenfor) angiver en time, hvor flere datasæt blev indlæst i hukommelsen, hvilket kan udskyde starten af planlagte opdateringer.
- Der sker en øget fjernelse af datasæt, når dataopdateringer er planlagt til start. Fjernelser kan angive, at der er et højt hukommelsesforbrug, som skyldes, at der er for mange forskellige interaktive rapporter før opdateringen. Visualiseringen **Hourly Dataset Evictions and Memory Consumption** viser tydlige stigninger i antallet af fjernelser.

På følgende billede vises en lokal stigning i indlæste datasæt, hvilket antyder, at interaktive forespørgsler forsinkede påbegyndelsen af opdateringerne. Hvis du vælger en bestemt periode i visualiseringen **Antal indlæste datasæt pr. time**, filtreres visualiseringen **Størrelser af datasæt** på tværs.

![En lokal stigning i de indlæste datasæt antyder, at interaktive forespørgsler forsinkede påbegyndelsen af opdateringerne](media/service-premium-capacity-scenarios/hourly-loaded-dataset-counts.png)

Power BI-administratoren kan forsøge at løse problemet ved at sikre, at tilstrækkelig hukommelse er tilgængelig for at dataopdateringerne kan starte, ved at:

- Kontakte datasætejerne og bede dem om at forskyde og lave mellemrum i tidsplanerne for opdateringer.
- Reducere indlæsningen af datasætforespørgsler ved at fjerne unødvendige dashboards eller dashboardfelter, især indhold, der gennemtvinger sikkerhed på rækkeniveau.
- Sætte fart på opdatering af data ved at optimere Microsoft Power Query til Excel-logic. Øge modellerings beregnede kolonner eller tabeller. Reducere datasætstørrelsen eller konfigurere større datasæt for at udføre trinvis opdatering af data.

## <a name="identifying-slow-responding-datasets"></a>Sådan identificeres datasæt med lange svartider

I dette scenarie blev der igangsæt en undersøgelse, da brugerne klagede over, at det tog lang tid at åbne visse rapporter. Nogle gange holdt rapporterne op med at svare.

I appen kan Power BI-administratoren bruge visualiseringen **Query Durations** til at fastsætte, hvilke datasæt der har den dårligste ydeevne, ved at sortere datasættene efter **gennemsnitlig varighed**. Denne visualisering viser også antallet af datasætforespørgsler, så du kan se, hvor ofte datasættene forespørges.

![Datasæt med den dårligste ydeevne](media/service-premium-capacity-scenarios/worst-performing-datasets.png)

Administratoren kan referere til visual'et **Distribution af forespørgselsvarighed**, der viser en overordnet fordeling af ydeevnen for bucketforespørgsler (< = 30ms, 0-100 MS osv.) for den filtrerede tidsperiode. De fleste brugere anser forespørgsler, der kræver et sekund eller mindre for at have en god ydeevne. Forespørgsler, der varer længere, anses ofte for at have en dårlig ydeevne.

I visualiseringen **Hourly Query Duration Distribution** kan Power BI-administratoren identificere entimes perioder, hvor kapacitetsydeevnen kan være blevet opfattet som dårlig. Jo større de søjler, der repræsenterer varigheder over ét sekund for forespørgsler, er, desto større er risikoen for, at brugerne oplever det som dårlig ydeevne.

Visualiseringen er interaktiv, og når en del af søjlen vælges, filtreres den tilsvarende tabelvisualisering **Query Durations** på rapportsiden på tværs for at vise de datasæt, den repræsenterer. Denne filtrering på tværs gør det muligt for Power BI-administratoren nemt at identificere datasæt med lange svartider.

På følgende billede vises en visualisering, der er filtreret efter **Hourly Query Duration Distributions**, og som fokuserer på datasættet med den dårligste ydeevne i buckets på én time.

![Filtreringen af visualiseringen Hourly Query Duration Distributions viser datasættet med den dårligste ydeevne](media/service-premium-capacity-scenarios/hourly-query-duration-distributions.png)

Efter at datasættet med dårlig ydeevne i en bestemt tidsperiode på én time er identificeret, kan Power BI-administratoren undersøge, om den dårlige ydeevne er forårsaget af en overbelastet kapacitet eller skyldes et datasæt eller en rapport i et dårligt design. Administratoren kan se visual'et **Ventetid for forespørgsler** og sortere datasæt efter faldende gennemsnitlig ventetid for forespørgsler. Hvis en stor procentdel af forespørgslerne venter, er en høj efterspørgsel efter datasættet sandsynligvis årsagen til de mange forsinkede forespørgsler. Hvis den gennemsnitlige ventetid for forespørgsler er meget lang (> 100 millisekunder), kan det være en god ide at gennemse datasættet og rapporten for at se, om der kan foretages optimeringer. For eksempel færre visuals på en given rapportside eller en optimering af DAX-udtryk.

![Visualiseringen Query Wait Times hjælper med at vise datasæt med en dårlig ydeevne](media/service-premium-capacity-scenarios/query-wait-times.png)

Der er flere mulige årsager til, at ventetider for forespørgsler hober sig up i datasæt:

- Et knapt så optimalt modeldesign, målingsudtryk eller endda rapportdesign – alle sammen omstændigheder, der kan bidrage til langvarige forespørgsler, der bruger meget CPU. Dette tvinger nye forespørgsler til at vente, indtil CPU-tråde bliver tilgængelige, og kan skabe en prop, hvilket ofte ses på travle tidspunkter. Siden **Query Waits** er den primære ressource til at afgøre, om datasæt har en høj gennemsnitlig forespørgselsventetid.
- Et højt antal samtidige kapacitetsbrugere (hundredvis eller tusindvis), der forbruger den samme rapport eller det samme datasæt. Selv veludformede datasæt kan have en dårlig ydeevne, hvis grænsen for samtidighed overskrides. Dette problem med ydeevnen er angivet af et enkelt datasæt, der viser en dramatisk højere værdi for forespørgselsantallet end andre datasæt. Du kan f. eks. 300.000 forespørgsler for ét datasæt i forhold til < 30.000 forespørgsler for alle andre datasæt. På et tidspunkt bliver forespørgselsventetiderne for dette datasæt forskudt, hvilket kan ses i visual'et **Forespørgselsvarigheder**.
- Mange forskellige datasæt, der forespørges samtidigt, og som medfører hukommelsesudskiftning, da datasæt ofte bevæger sig ind og ud af hukommelsen. Denne situation medfører, at brugerne oplever langsom ydeevne, når datasættet indlæses i hukommelsen. Power BI-administratoren kan benytte visual'et **Fjernelser af datasæt og hukommelsesforbrug pr. time** for at få bekræftet dette, hvilket også kan indikere, at et højt antal datasæt, der indlæses i hukommelsen, gentagne gange fjernes.

## <a name="identifying-causes-for-sporadically-slow-responding-datasets"></a>Sådan identificeres årsager til datasæt med sporadisk langsomme svartider

I dette scenarie blev en undersøgelse igangsat, da brugerne beskrev, at visualiseringer i rapporter nogle gange svarede langsomt eller slet ikke svarede. På andre tidspunkter var rapportvisualiseringernes svartid acceptabel.

Afsnittet **Query Durations** i appen blev brugt til at finde det pågældende datasæt på følgende måde:

- I visualiseringen Query Durations filtrerede administratoren datasæt efter datasæt (startende med de datasæt, der forespørges mest hyppigt) og undersøgte de krydsfiltrerede søjler i visualiseringen **Hourly Query Distributions**.
- Eftersom en enkelt 1-times søjle viste betydelige ændringer i forholdet mellem alle grupper for forespørgselsvarigheder i forhold til andre 1-times søjler for dette datasæt (f.eks. forholdet mellem farverne ændres drastisk), betyder det, at dette datasæt viste en sporadisk ændring i ydeevne.
- De én-timers søjler, der viser en uregelmæssig del af forespørgsler med dårlig ydeevne, viste en tidsperiode, hvor datasættet blev påvirket af andre datasæts aktiviteter.

På billedet nedenfor vises én time den 30. januar, hvor der opstod en betydelig tilbagegang i et datasæts ydeevne, hvilket er angivet af størrelsen "(3,10s]" på udførelsesvarigheden for den pågældende bucket. Hvis der klikkes på den 1-times søjle, vises alle de datasæt, der blev indlæst i hukommelsen på det pågældende tidspunkt, og dermed de datasæt, der muligvis skaber problemerne.

![Søjle, der viser datasættene med den dårligste](media/service-premium-capacity-scenarios/worst-performing-queries.png)

Når et problematisk tidsrum er blevet identificeret (f.eks. i løbet af den 30. januar på billedet ovenfor), kan Power BI-administratoren fjerne alle datasætfiltre og derefter filtrere efter dette tidsrum for at afgøre, hvilke datasæt der blev aktivt forespurgt i denne periode. Det datasæt, der er årsag til problemet, er typisk det hyppigst forespurgte datasæt eller det datasæt, der har den længste gennemsnitlige forespørgselsvarighed.

En løsning på dette problem kunne være at distribuere de pågældende datasæt over forskellige arbejdsområder i forskellige Premium-kapaciteter eller i en delt kapacitet, hvis datasætstørrelsen, forbrugskravene og mønstrene for dataopdateringer understøttes.

Det modsatte kan også være tilfældet. Power BI-administratoren kan identificere de tidspunkter, hvor forespørgselsydeevnen for et datasæt forbedres og lægge mærke til, hvad der forsvandt. Hvis der mangler visse oplysninger på dette tidspunkt, kan det være med til at pege på problemet.

## <a name="determining-whether-there-is-enough-memory"></a>Sådan fastlægges det, om der er tilstrækkelig hukommelse

Power BI-administratoren kan benytte visualiseringen **Consumed Memory Percentages** på fanen **Datasæt** i appen til at bestemme, om der er tilstrækkelig hukommelse til, at kapaciteten kan fuldføre dens arbejdsbelastninger. **Al** hukommelse (i alt) repræsenterer den hukommelse, der forbruges af datasæt, der indlæses i hukommelsen, uanset om de aktivt forespørges eller behandles. **Aktiv** hukommelse repræsenterer den hukommelse, der forbruges af datasæt, der behandles aktivt.

Visualiseringen i en sund kapacitet ser ud som følger og viser et mellemrum mellem al hukommelse (i alt) og aktiv hukommelse:

![I en sund kapacitet vises et mellemrum mellem al hukommelse (i alt) og aktiv hukommelse](media/service-premium-capacity-scenarios/memory-healthy-capacity.png)

I en kapacitet, hvor hukommelsen belastes, viser det samme visual tydeligt, at den aktive hukommelse og den samlede hukommelse konvergerer, hvilket betyder, at det er umuligt at indlæse ekstra datasæt i hukommelsen på det pågældende tidspunkt. I dette tilfælde kan Power BI-administratoren klikke på **Genstart af kapacitet** (i **Avancerede indstillinger**  i området med kapacitetsindstillinger i administrationsportalen). Genstart af kapaciteten resulterer i, at alle datasæt trækkes fra hukommelsen og indlæses igen i hukommelsen efter behov (af forespørgsler eller dataopdateringer).

> [!NOTE]
> Hukommelsesforbruget behøver ikke at blive sporet for Premium Gen2. Den eneste begrænsning i Premium Gen2 er af hukommelsesforbruget for en enkelt artefakt. Forbruget må ikke overstige den hukommelse, der er tilgængelig på kapaciteten. Du kan finde flere oplysninger om Premium Gen2 i [Power BI Premium – Generation 2 (prøveversion)](service-premium-what-is.md#power-bi-premium-generation-2-preview).

![**Aktiv** hukommelse konvergerer med **al** hukommelse](media/service-premium-capacity-scenarios/memory-unhealthy-capacity.png)

## <a name="determining-whether-there-is-enough-cpu"></a>Sådan fastlægges det, om der er tilstrækkelig CPU

Generelt skal en kapacitets gennemsnitlige CPU-forbrug forblive under 80 %. Hvis denne værdi overskrides, betyder det, at kapaciteten nærmer sig CPU-mætning.

Konsekvenserne af CPU-mætning kommer til udtryk ved, at handlinger tager længere tid, end de skal, på grund af at kapaciteten udfører mange skift af CPU-kontekstparametre, når den forsøger at behandle alle handlinger. I en Premium-kapacitet med et højt antal samtidige forespørgsler, er dette angivet af lange forespørgselsventetider. En konsekvens af lange forespørgselsventetider er langsommere svartider end normalt. Power BI-administratoren kan let kan identificere, når CPU'en er mættet ved at få vist visualiseringen **Hourly Query Wait Time Distributions**. Periodiske spidsbelastninger af forespørgselsventetider indikerer en potentiel CPU-mætning.

![Periodiske spidsbelastninger af forespørgselsventetider indikerer en potentiel CPU-mætning](media/service-premium-capacity-scenarios/peak-query-wait-times.png)

Et tilsvarende mønster kan nogle gange registreres i handlinger i baggrunden, hvis de bidrager til CPU-mætning. En Power BI-administrator kan søge efter en periodisk stigning i opdateringstiderne for et bestemt datasæt, hvilket kan indikere CPU-mætning på det pågældende tidspunkt (sandsynligvis på grund af andre igangværende datasætopdateringer og/eller interaktive forespørgsler). I dette tilfælde afslører visningen **System** i appen ikke nødvendigvis, at CPU'en er på 100 %. Visningen **System** viser timgegennemsnitten, men CPU'en kan blive mættet under adskillige minutter med mange handlinger, hvilket vises som stigninger i ventetider.

Effekten af CPU-mætningen kan ses flere steder. Selvom antallet af forespørgsler, der venter er vigtigt, opstår der altid forespørgselsventetider til en vis grad, uden at det giver anledning til forringelse af ydeevnen. For visse datasæt (med længere gennemsnitlige forespørgselstider, hvilket skyldes kompleksitet eller størrelse) er mere udsatte for konsekvenserne af CPU-mætning end andre. Power BI-administratoren kan nemt finde disse datasæt ved at søge efter ændringer i farvesammensætningen af søjlerne i visualiseringen **Hourly Wait Time Distribution**. Når en søjle med udenforliggende værdier er blevet fundet, kan administratoren søge efter de datasæt, der havde forespørgselsventetid på det pågældende tidspunkt og også kigge på den gennemsnitlige forespørgselsventetid sammenlignet med den gennemsnitlige varighed af forespørgslen. Når disse to målinger har den samme størrelse og arbejdsbelastningen for forespørgslen for datasættet ikke er ubetydelig, er det sandsynligt, at datasættet er påvirket af utilstrækkelig CPU.

Denne effekt kan være særligt synlig, når et datasæt forbruges i korte bursts bestående af forespørgsler med høj hyppighed af flere brugere (f.eks. i en træningssession), hvilket resulterer i CPU-mætning under hvert burst. I dette tilfælde kan der opstå betydelige forespørgselsventetider for dette datasæt, og andre datasæt i kapaciteten kan også blive påvirket.

I nogle tilfælde kan Power BI-administratorer anmode datasætejerne om at oprette en mindre svingende forespørgselsarbejdsbelastning ved at oprette et dashboard (som forespørger med jævne mellemrum med datasætopdateringer af cachelagrede felter) i stedet for en rapport. Dette kan forhindre stigninger, når dashboardet indlæses. Denne løsning er ikke altid mulig for det givne forretningsmæssige krav, men det kan være en effektiv måde at undgå CPU-mætning på uden at ændre datasættet.

> [!NOTE]
> For Premium Gen2 spores CPU-tidsforbruget pr. artefakt, og det er synligt i appen for kapacitetsudnyttelse. Den samlede udnyttelse af CPU-tid i et givent tidsrum vises for hver artefakt. Du kan finde flere oplysninger om Premium Gen2 i [Power BI Premium – Generation 2 (prøveversion)](service-premium-what-is.md#power-bi-premium-generation-2-preview).

## <a name="acknowledgments"></a>Bekræftelser

Denne artikel er skrevet af Peter Myers, som er Data Platform MVP og uafhængig BI-ekspert hos [Bitwise Solutions](https://www.bitwisesolutions.com.au/).

## <a name="next-steps"></a>De næste trin

> [!div class="nextstepaction"]
> [Overvåg Premium-kapaciteter vha. appen](service-admin-premium-monitor-capacity.md)    
> [!div class="nextstepaction"]
> [Overvåg kapaciteter på administrationsportalen](service-admin-premium-monitor-portal.md)   

Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)

Power BI har introduceret Power BI Premium Gen2 som et prøveversionstilbud, der forbedrer Power BI Premium-oplevelsen på følgende områder:
* Ydeevne
* Licens pr. bruger
* Større skalering
* Forbedrede målepunkter
* Automatisk skalering
* Reducerede administrationsomkostninger

Du kan finde flere oplysninger om Power BI Premium Gen2 under [Power BI-Premium – Generation 2 (prøveversion)](service-premium-what-is.md#power-bi-premium-generation-2-preview).

