---
title: Mange til mange-relationer i Power BI Desktop
description: Du kan bruge relationer med en mange til mange-kardinalitet i Power BI Desktop
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-transform-model
ms.topic: conceptual
ms.date: 12/19/2019
LocalizationGroup: Transform and shape data
ms.openlocfilehash: 5f64a9a896fbb5ea3e080e1d07f6cc7d980430b8
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96415697"
---
# <a name="apply-many-many-relationships-in-power-bi-desktop"></a>Anvend mange til mange-relationer i Power BI Desktop

Med *relationer med en mange til mange-kardinalitet* i Power BI Desktop kan du joinforbinde tabeller, der bruger en kardinalitet på *mange til mange*. Du kan nemmere og mere intuitivt oprette datamodeller, der indeholder to eller flere datakilder. *Relationer med en mange til mange-kardinalitet* er en del af den mere omfattende funktionalitet til *sammensatte modeller* i Power BI Desktop.

![En mange til mange-relation i ruden "Rediger relation", Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_01.png)

En *relation med en mange til mange-kardinalitet* i Power BI Desktop består af en del af tre relaterede funktioner:

* **Sammensatte modeller**: En *sammensat model* gør det muligt for en rapport at have to eller flere dataforbindelser, herunder DirectQuery-forbindelser eller Import, i en hvilken som helst kombination. Du kan finde flere oplysninger under [Brug sammensatte modeller i Power BI Desktop](desktop-composite-models.md).

* **Relationer med en mange til mange-kardinalitet**: Via sammensatte modeller kan du oprette *relationer med en mange til mange-kardinalitet* mellem tabeller. Med denne tilgang fjernes kravene for entydige værdier i tabeller. Tidligere midlertidige løsninger, f.eks. introduktion af nye tabeller kun for at oprette relationer, fjernes også. Funktionen er beskrevet nærmere i denne artikel.

* **Lagringstilstand**: Du kan nu angive, hvilke visualiseringer der kræver en forespørgsel til back end-datakilder. Visuelle elementer, der ikke kræver en forespørgsel, importeres, også selvom de er baseret på DirectQuery. Denne funktion hjælper med at forbedre ydeevnen og reducere belastningen af back-end. Tidligere startede selv enkle visualiseringer, som f.eks. udsnit, forespørgsler, der blev sendt til back end-kilderne. Du kan finde flere oplysninger i [Lagringstilstand i Power BI Desktop](desktop-storage-mode.md).

## <a name="what-a-relationship-with-a-many-many-cardinality-solves"></a>Hvad en relation med en mange til mange-kardinalitet løser

Før *relationer med en mange til mange-kardinalitet* blev tilgængelig, var relationen mellem to tabeller defineret i Power BI. Mindst en af tabelkolonnerne i relationen skulle indeholde entydige værdier. Men ofte indeholdt ingen af kolonnerne entydige værdier.

To tabeller kan f.eks. have en kolonne med navnet Land. Værdierne i kolonnen Land var dog ikke entydige i nogen af tabellerne. Du skulle oprette en midlertidig løsning for at joinforbinde sådanne tabeller. Det kan være en midlertidig løsning at oprette ekstra tabeller med de nødvendige entydige værdier. Med *relationer med en mange til mange-kardinalitet* kan du forbinde sådanne tabeller direkte ved hjælp af en relation med en kardinalitet på *mange til mange*.

## <a name="use-relationships-with-a-many-many-cardinality"></a>Brug relationer med en mange til mange-kardinalitet

Når du definerer en relation mellem to tabeller i Power BI, skal du definere kardinaliteten af relationen. Relationen mellem ProductSales og Product&mdash;ved hjælp af kolonnerne ProductSales[ProductCode] og Product[ProductCode]&mdash;ville f.eks. defineres som *Mange-1*. Vi definerer relationen på denne måde, fordi hvert produkt har mange salg, og kolonnen i tabellen Product(ProductCode) er entydig. Når du definerer en relations kardinalitet som *Mange-1*, *1-Mange* eller *1-1*, validerer Power BI den, så den valgte kardinalitet stemmer overens med de faktiske data.

Se f.eks. nærmere på den enkle model på dette billede:

![Tabellen ProductSales og Product, visningen Relationer, Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_02.png)

Forestil dig nu, at der kun vises to rækker i tabellen **Product**, som vist:

![Visualisering af tabellen Product med to rækker, Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_03.png)

Forestil dig også, at der kun er fire rækker i tabellen Sales, herunder en række for produkt C. På grund af et problem med referentiel integritet eksisterer rækken for produkt C ikke i tabellen **Product**.

![Visualisering af tabellen Sales med fire rækker, Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_04.png)

**ProductName** og **Price** (fra tabellen **Product**) samt totalen af **Qty** for hvert produkt (fra tabellen ProductSales) ville blive vist på følgende måde:

![Visualisering med visning af produktnavn, pris og antal, Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_05.png)

Som du kan se på foregående billede, er en tom række med navnet **ProductName** knyttet til salg for produkt C. Denne tomme række står for følgende:

* Alle rækker i tabellen **ProductSales**, hvor der ikke findes nogen tilsvarende række i tabellen **Product**. Vi kan se, at der er et problem med referentiel integritet for produkt C i dette eksempel.

* Alle rækker i tabellen **ProductSales**, hvor kolonnen med den fremmede nøgle er null.

Af disse årsager står den tomme række for de salg, hvor **ProductName** og **Price** er ukendt.

Nogle gange er tabellerne joinforbundet af to kolonner, men ingen af kolonnerne er entydige. Du kan f.eks. overveje disse to tabeller:

* I tabellen **Sales** vises salgsdata efter **State**, og hver række indeholder salgsbeløbet for den type salg i den pågældende delstat. Staterne omfatter CA, WA og TX.

    ![Tabellen Sales viser salg efter delstat, Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_06.png)

* I tabellen **CityData** vises data om byer, herunder indbyggertal og delstat (som f.eks. CA, WA og New York).

    ![Tabellen Sales viser by, delstat og indbyggertal, Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_07.png)

Der er nu en kolonne for **State** i begge tabeller. Det giver god mening at ville rapportere for både det samlede salg efter stat og det samlede indbyggertal for hver stat. Der findes dog et problem: Kolonnen **State** er ikke entydig i nogen af tabellerne.

## <a name="the-previous-workaround"></a>Tidligere midlertidig løsning

Før udgivelsen af Power BI Desktop i juli 2018 kunne du ikke oprette en direkte relation mellem disse tabeller. En almindelig midlertidig løsning var at:

* Oprette en tredje tabel, der kun indeholder de entydige id'er for State. Tabellen kunne være en eller alle af:
  * En beregnet tabel (defineret ved hjælp af Data Analysis Expressions [DAX]).
  * En tabel baseret på en forespørgsel, der er defineret i Forespørgselseditor, som kunne vise de entydige id'er, der er trukket fra en af tabellerne.
  * Hele sættet kombineret.

* Opret derefter en relation mellem de to oprindelige tabeller til den nye tabel ved hjælp af almindelige *Mange-1*-relationer.

Du kan gøre tabellen med midlertidige løsninger synlig. Eller du kan skjule tabellen med midlertidige løsninger, så den ikke vises på listen **Felter**. Hvis du skjuler tabellen, vil relationen *Mange-1* ofte være angivet til at filtrere i begge retninger, og du kan bruge feltet State fra begge tabeller. Den senere tværgående filtrering vil blive overført til den anden tabel. Denne tilgang er vist på følgende billede:

![Tabellen Hidden State, visningen Relationer, Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_08.png)

En visualisering, der viser **State** (fra tabellen **CityData**) sammen med totalen af **Population** og totalen af **Sales**, vil derefter se ud på følgende måde:

![Skærmbillede, der viser en tabel med data for State, Population og Sales.](media/desktop-many-to-many-relationships/many-to-many-relationships_09.png)

> [!NOTE]
> Da delstaten fra tabellen **CityData** bruges i denne midlertidige løsning, vises der kun delstater fra den tabel, så delstaten TX vises ikke. Rækken Total indeholder oplysninger om alt **Sales** (inklusive for TX), men i modsætning til *Mange-1*-relationer vises der ikke en tom række for sådanne rækker, der ikke stemmer overens. På samme måde vil en tom række ikke dække **Sales**, hvor der er en null-værdi for **State**.

Lad os antage, at du også føjer en by til denne visualisering. **Sales**, der vises for City vil simpelthen være en gentagelse af **Sales** for den tilsvarende **State**, selvom indbyggertallet pr. City er kendt. Dette scenarie forekommer normalt, når kolonnegrupperingen ikke er relateret til en samlet måling som vist her:

![State, City Population og Sales, Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_10.png)

Lad os sige, at du definerer den nye tabel Sales som en kombination af alle delstater her, og vi gør den synlig på listen **Felter**. Den samme visualisering ville vise **State** (i den nye tabel), den samlede **Population** og det samlede **Sales**:

![Visualisering af State, Population og Sales, Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_11.png)

Som du kan se, er &mdash;TX med **Sales**-data, men ukendte *Population*-data&mdash;og New York&mdash;med kendte **Population**-data, men ingen **Sales**-data&mdash;inkluderet. Denne midlertidige løsning er ikke optimal, og der er mange problemer forbundet med den. For relationer med en mange til mange-kardinalitet bliver de medfølgende problemer løst, som beskrevet i næste afsnit.

## <a name="use-a-relationship-with-a-many-many-cardinality-instead-of-the-workaround"></a>Brug en relation med en mange til mange-kardinalitet i stedet for den midlertidige løsning

Med versionen af Power BI Desktop fra juli 2018 kan du oprette direkte relationer mellem tabeller, ligesom dem vi beskrev tidligere, uden at skulle ty til lignende midlertidige løsninger. Det er nu muligt at angive kardinaliteten for relationen til *mange til mange*. Denne indstilling indikerer, at ingen af tabellerne indeholder entydige værdier. For sådanne relationer kan du stadig styre, hvilken tabel der filtrerer den anden tabel. Du kan desuden anvende tovejsfiltrering, hvor hver tabel filtrerer den anden.

I Power BI Desktop vil kardinalitet som standard være *mange til mange*, når det er fastslået, at ingen af tabellerne indeholder entydige værdier for kolonnerne med relationer. I sådanne tilfælde bekræfter en advarselsmeddelelse, at du vil angive en relation, og ændringen er ikke den utilsigtede virkning af et dataproblem.

Hvis du f.eks. opretter en relation direkte mellem CityData og Sales,&mdash;hvor filtre skal gå fra CityData til Sales&mdash;vises vinduet **Rediger relation** i Power BI Desktop:

![Dialogboksen Rediger relation, Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_01.png)

Den resulterende **Relationsvisning** vil derefter indeholde den direkte mange til mange-relation mellem de to tabeller. Tabellernes udseende på listen **Felter** og deres senere funktionsmåde, når der oprettes visualiseringer, ligner den samme, som da vi anvendte den midlertidige løsning. I den midlertidige løsning er den ekstra tabel, som viser de enkelte State-data, ikke synlig. Som beskrevet tidligere vises en visualisering, der viser data fra **State**, **Population** og **Sales**:

![Tabellerne State, Population og Sales, Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_12.png)

De primære forskelle mellem *relationer med mange til mange-kardinalitet* og de mere almindelige *Mange-1*-relationer er følgende:

* De viste værdier omfatter ikke en tom række, der står for rækker, som ikke stemmer overens med den anden tabel. Værdierne står heller ikke for rækker, hvor den kolonne, der bruges i relationen i den anden tabel, er null.
* Du kan ikke bruge funktionen `RELATED()`, da der kan være en relation til mere end én række.
* Brug af funktionen `ALL()` i en tabel fjerner ikke de filtre, som er anvendt på andre relaterede tabeller med en mange til mange-relation. I det forrige eksempel fjernede en måling, der er defineret som vist her, ikke filtre på kolonner i den relaterede CityData-tabel:

    ![Eksempel på script](media/desktop-many-to-many-relationships/many-to-many-relationships_13.png)

    En visualisering, der viser data for **State**, **Sales** og **Sales total**, ville resultere i denne grafik:

    ![Tabelvisualisering](media/desktop-many-to-many-relationships/many-to-many-relationships_14.png)

Med de foregående forskelle in mente skal du sørge for, at beregningerne, der bruger `ALL(<Table>)`, f.eks.   *% af totalen*, returnerer de forventede resultater.

## <a name="limitations-and-considerations"></a>Begrænsninger og overvejelser

Der er nogle få begrænsninger for denne udgivelse af *relationer med mange til mange-kardinalitet* og sammensatte modeller.

Følgende Live Connect-kilder (flerdimensionelle) kan ikke bruges sammen med sammensatte modeller:

* SAP HANA
* SAP Business Warehouse
* SQL Server Analysis Services
* Power BI-datasæt
* Azure Analysis Services

Når du opretter forbindelse til disse flerdimensionelle kilder ved hjælp af DirectQuery, kan du ikke oprette forbindelse til en anden DirectQuery-kilde eller kombinere den med importerede data.

De eksisterende begrænsninger ved at bruge DirectQuery gælder stadig, når du bruger *relationer med en mange til mange-kardinalitet*. Mange begrænsninger gælder nu for de enkelte tabeller afhængigt af tabellens lagringstilstand. En beregnet kolonne i en importeret tabel kan f.eks. referere til andre tabeller, men en beregnet kolonne i en DirectQuery-tabel kan stadig kun referere til kolonner i den samme tabel. Andre begrænsninger gælder for hele modellen, hvis nogle af tabellerne i modellen er DirectQuery. Funktionerne Hurtig indsigt og Spørgsmål og svar er f.eks. ikke tilgængelige for en model, hvis en tabel i den har lagringstilstanden DirectQuery.

## <a name="next-steps"></a>Næste trin

Du kan finde flere oplysninger om sammensatte modeller og DirectQuery i følgende artikler:
* [Brug sammensatte modeller i Power BI Desktop](desktop-composite-models.md)
* [Lagringstilstand i Power BI Desktop](desktop-storage-mode.md)
* [Brug DirectQuery i Power BI](../connect-data/desktop-directquery-about.md)
* [Power BI-datakilder](../connect-data/power-bi-data-sources.md)
