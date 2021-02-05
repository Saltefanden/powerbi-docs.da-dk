---
title: Tilstande for datasæt i Power BI-tjenesten
description: 'Om tilstande for datasæt i Power BI-tjenesten: Import, DirectQuery og Sammensat.'
author: davidiseminger
ms.author: davidi
manager: asaxton
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: conceptual
ms.date: 12/01/2020
ms.openlocfilehash: 5f03a994085e139da714219ce2e9095bde3a35d6
ms.sourcegitcommit: afdc9d41da6a4fced63030648d3f976425131732
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/05/2021
ms.locfileid: "99570031"
---
# <a name="dataset-modes-in-the-power-bi-service"></a>Tilstande for datasæt i Power BI-tjenesten

Denne artikel indeholder en teknisk forklaring af tilstande for datasæt i Power BI. Den gælder for datasæt, der repræsenterer en direkte forbindelse til en eksternt hostet Analysis Services-model og også for modeller, der er udviklet i Power BI Desktop. I artiklen forklares det teoretiske grundlag for hver enkelt tilstand og eventuelle konsekvenser for Power BI-kapacitetens ressourcer.

De tre tilstande for datasæt er:

- [Importér](#import-mode)
- [DirectQuery](#directquery-mode)
- [Sammensat](#composite-mode)

## <a name="import-mode"></a>Importtilstand

Tilstanden _Importér_ er den mest almindelige tilstand, der bruges til at udvikle modeller. Denne tilstand giver en ekstremt hurtig ydeevne takket være forespørgsler i hukommelsen. Den giver også designfleksibilitet til modeludviklere og understøttelse af bestemte funktioner i Power BI-tjenesten (Spørgsmål og svar, Hurtig indsigt osv.). Disse styrker gør den til standardtilstanden, når du opretter en ny Power BI Desktop-løsning.

Det er vigtigt at forstå, at importerede data altid lagres på disken. Når dataene forespørges eller opdateres, skal de være fuldt indlæst i hukommelsen i Power BI-kapaciteten. Når importmodellerne er i hukommelsen, kan de opnå meget hurtige forespørgselsresultater. Det er også vigtigt at forstå, at der ikke findes en importmodel, der indlæses delvist i hukommelsen.

Når dataene opdateres, komprimeres og optimeres de og gemmes på disken af VertiPaq-programmet. Når den er indlæst fra disken i hukommelsen, er det muligt at se komprimering med faktor 10. Det er derfor rimeligt at forvente, at 10 GB kildedata kan komprimeres til en størrelse på ca. 1 GB. Lagerstørrelsen på disken opnå en reduktion på 20 % i forhold til den komprimerede størrelse. Forskellen i størrelse kan bestemmes ved at sammenligne Power BI Desktop-filstørrelsen med filens hukommelsesforbrug i Jobliste.

Du kan opnå fleksibilitet i designet på tre forskellige måder. Datamodellører kan:

- Integrere data ved at cachelagre data fra dataflow og eksterne datakilder, uanset datakildetypen eller -formatet
- Udnytte hele sættet af funktioner i [Power Query-formelsproget](/powerquery-m/) (også kaldet M) til oprettelsen af forespørgsler, når du opretter forespørgsler til forberedelse af data
- Udnytte hele sættet af [DAX-funktioner (Data Analysis Expressions)](/dax/), når modellen forbedres med forretningslogik. Der er understøttelse af beregnede kolonner, beregnede tabeller og målinger.

Som vist på følgende billede kan en importmodel integrere data fra et vilkårligt antal understøttede datakildetyper.

![En importmodel kan integrere data fra et vilkårligt antal eksterne datakildetyper](media/service-dataset-modes-understand/import-model.png)

Selvom der er mange overbevisende fordele forbundet med importmodeller, er der dog også nogle ulemper:

- Hele modellen skal indlæses i hukommelsen, før Power BI kan forespørge modellen, hvilket kan øge presset på tilgængelige kapacitetsressourcer, især efterhånden som antallet af og størrelsen på importmodeller vokser
- Modeldata er kun så aktuelle som den seneste opdatering, hvorfor importmodeller normalt skal opdateres efter en tidsplan
- En fuld opdatering fjerner alle data fra alle tabeller og genindlæser dem fra datakilden. Denne operation kan være meget dyr både med hensyn til tid og ressourcer for Power BI-tjenesten og datakilden eller -kilderne.

    > [!NOTE]
    > Power BI kan opnå en trinvis opdatering for at undgå at afkorte og genindlæse hele tabeller. Denne funktion understøttes dog kun, hvis datasættet er hostet i arbejdsområder på Premium-kapaciteter. Du kan få flere oplysninger i artiklen [Trinvis opdatering i Power BI Premium](../admin/service-premium-incremental-refresh.md).

Fra et ressourcemæssigt perspektiv i Power BI-tjenesten kræver importmodeller:

- Tilstrækkelig hukommelse til at indlæse modellen, når den forespørges eller opdateres
- Behandling af ressourcer og yderligere hukommelsesressourcer til at opdatere data.

## <a name="directquery-mode"></a>DirectQuery-tilstand

Tilstanden _DirectQuery-_ er et alternativ til tilstanden Importér. Modeller, der er udviklet i tilstanden DirectQuery, importerer ikke data. I stedet består de kun af metadata, der definerer modelstrukturen. Når der sendes en forespørgsel til modellen, bruges oprindelige forespørgsler til at hente data fra den underliggende datakilde.

![En DirectQuery-model frigiver oprindelige forespørgsler til den underliggende datakilde](media/service-dataset-modes-understand/direct-query-model.png)

Der er to primære årsager til at overveje at udvikle en DirectQuery-model:

- Når datamængderne er for store – selv når der anvendes [metoder til reduktion af data](../guidance/import-modeling-data-reduction.md) – til at blive indlæst i en model eller simpelthen for store til at blive opdateret
- Når rapporter og dashboards skal levere data næsten i realtid, ud over hvad der kan opnås inden for planlagte opdateringsgrænser. (De planlagte opdateringsgrænser er otte gange om dagen for delt kapacitet og 48 gange om dagen for en Premium-kapacitet).

Der er flere fordele ved at bruge DirectQuery-modeller:

- Der er ingen størrelsesgrænser for importmodeller
- Modellerne behøver ikke at blive opdateret
- Rapportbrugere får vist de nyeste data, når de interagerer med rapportfiltre og udsnit. Rapportbrugere kan også opdatere hele rapporten for at hente aktuelle data.
- Rapporter i realtid kan udvikles ved hjælp af funktionen [Automatisk sideopdatering](../create-reports/desktop-automatic-page-refresh.md)
- Felter i dashboardet kan, når de er baseret på DirectQuery-modeller, blive opdateret automatisk så ofte som hvert 15. minut

Men der er dog visse begrænsninger forbundet med DirectQuery-modeller:

- DAX-formularer er begrænset til kun at bruge funktioner, der kan omdannes til oprindelige forespørgsler, som forstås af datakilden. Beregnede kolonner understøttes ikke.
- Hurtig indsigt funktioner understøttes ikke

Fra et ressourcemæssigt perspektiv i Power BI-tjenesten kræver DirectQuery-modeller:

- Minimal hukommelse til at indlæse modellen (kun metadata), når der sendes der en forespørgsel
- Nogle gange skal Power BI-tjenesten bruge betydelige processorressourcer til at generere og behandle forespørgsler, der sendes til datakilden. Når denne situation opstår, kan det påvirke dataoverførselshastigheden, især når brugere forespørger modellen samtidig.

Du kan finde flere oplysninger i [Brug DirectQuery i Power BI Desktop](desktop-use-directquery.md).

## <a name="composite-mode"></a>Tilstanden Sammensat

Tilstanden _Sammensat_ kan blande tilstandene Importér og DirectQuery eller integrere flere DirectQuery-datakilder. Modeller, der er udviklet i sammensat tilstand,understøtter konfiguration af lagringstilstanden for hver modeltabel. Den understøtter også beregnede tabeller (defineret med DAX).

Tabellagringstilstanden kan konfigureres som Import, DirectQuery eller Dobbelt. En tabel, der konfigureres som en tabeltilstanden Dobbelt, består både af Importér og DirectQuery, og det giver Power BI-tjenesten mulighed for at bestemme, hvilken tilstand der er mest effektiv at bruge for en forespørgsel for den enkelte forespørgsel.

![En sammensat model er en kombination af lagringstilstandene Importér og DirectQuery, der er konfigureret på tabelniveau](media/service-dataset-modes-understand/composite-model.png)

Sammensatte modeller har til formål at levere det bedste fra tilstandene Import og DirectQuery. Når sådanne modeller er konfigureret korrekt, kan de kombinere en høj forespørgselsydeevne for modeller i hukommelsen med muligheden for at hente data i næsten realtid fra datakilder.

Udviklere, der udvikler sammensatte modeller, konfigurerer sandsynligvis tabeller af dimensionstypen i lagringstilstanden Importér eller Dobbelt og faktatypetabeller i tilstanden DirectQuery. Du kan finde flere oplysninger om modeltabelroller i [Forstå, hvad et stjerneskema er, og hvorfor det er vigtigt for Power BI](../guidance/star-schema.md).

Lad os f.eks. tage en model med en **Produkt**-dimensionstypetabel i tilstanden Dobbelt og en **Salg**-faktatypetabel i tilstanden DirectQuery. **Produkt** tabellen kan forespørges hurtigt og effektivt fra hukommelsen for at gengive et rapportudsnit. **Salgs** tabellen kan også forespørges i tilstanden DirectQuery med den relaterede **Produkt** tabel. Den sidste forespørgsel kan muliggøre genereringen af en enkelt effektiv oprindelig SQL-forespørgsel for at forbinde **Produkt** og **Salg**-tabellerne og filtrere efter udsnitsværdierne.

Du kan finde flere oplysninger under [Brug sammensatte modeller i Power BI Desktop](../transform-model/desktop-composite-models.md).

## <a name="next-steps"></a>Næste trin

- [Datasæt i Power BI-tjenesten](service-dataset-modes-understand.md)
- [Lagringstilstand i Power BI Desktop](../transform-model/desktop-storage-mode.md)
- [Brug af DirectQuery in Power BI](desktop-directquery-about.md)
- [Brug sammensatte modeller i Power BI Desktop](../transform-model/desktop-composite-models.md)
- Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
