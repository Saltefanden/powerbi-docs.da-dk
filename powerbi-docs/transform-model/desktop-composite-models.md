---
title: Brug af sammensatte modeller i Power BI Desktop
description: Opret datamodeller med flere dataforbindelser og mange-til-mange-relationer i Power BI Desktop
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-transform-model
ms.topic: conceptual
ms.date: 01/19/2021
LocalizationGroup: Transform and shape data
ms.openlocfilehash: cbf41315f6b33483b7fdd0797bf4dfbcebb605c3
ms.sourcegitcommit: 96080432af4c8e3fe46c23274478ccffa0970efb
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 01/20/2021
ms.locfileid: "98597679"
---
# <a name="use-composite-models-in-power-bi-desktop"></a>Brug af sammensatte modeller i Power BI Desktop

Tidligere i Power BI Desktop når du brugte en DirectQuery i en rapport, var ingen andre dataforbindelser, hverken DirectQuery eller Import, tilladt for den pågældende rapport. Denne begrænsning er nu fjernet med sammensatte modeller. En rapport kan uden problemer indeholde dataforbindelser fra mere end én DirectQuery eller importdataforbindelse i en hvilken som helst kombination, du vælger.

Sammensatte modeller-funktionaliteten i Power BI Desktop består af tre relaterede funktioner:

* **Sammensatte modeller**: Gør det muligt for en rapport at have to eller flere dataforbindelser fra forskellige kildegrupper, f.eks. som en eller flere DirectQuery-forbindelser og en importforbindelse, to eller flere DirectQuery-forbindelser eller en hvilken som helst kombination af disse. I denne artikel beskrives sammensatte modeller i detaljer.

* **Mange til mange-relationer**: Med sammensatte modeller kan du etablere *mange til mange-relationer* mellem tabeller. Med denne tilgang fjernes kravene for entydige værdier i tabeller. Tidligere midlertidige løsninger, f.eks. introduktion af nye tabeller kun for at oprette relationer, fjernes også. Du kan finde flere oplysninger under [Anvend mange til mange-relationer i Power BI Desktop](desktop-many-to-many-relationships.md).

* **Lagringstilstand**: Du kan nu angive, hvilke visualiseringer der forespørger back end-datakilder. Visuelle elementer, der ikke kræver en forespørgsel, importeres, også selvom de er baseret på DirectQuery. Denne funktion hjælper med at forbedre ydeevnen og reducere belastningen af back-end. Tidligere ville selv enkle visualiseringer, f.eks. udsnit, starte forespørgsler til back end-kilderne. Du kan finde flere oplysninger i [Administrer lagringstilstand i Power BI Desktop](desktop-storage-mode.md).

## <a name="use-composite-models"></a>Brug sammensatte modeller

Med sammensatte modeller kan du oprette forbindelse til forskellige typer datakilder, når du bruger Power BI Desktop eller Power BI-tjenesten. Du kan oprette disse dataforbindelser på flere måder:

* Ved at importere data til Power BI, hvilket er den mest almindelige måde at hente data på.
* Ved at oprette direkte forbindelse til data i det oprindelige kildelager ved hjælp af DirectQuery. Du kan finde flere oplysninger om DirectQuery under [DirectQuery i Power BI](../connect-data/desktop-directquery-about.md).

Når du bruger DirectQuery, gør sammensatte modeller det muligt at oprette en Power BI-model (f.eks. en enkelt *PBIX* Power BI Desktop-fil), der resulterer i en eller begge af følgende handlinger:

* kombinerer data fra en eller flere DirectQuery-kilder.
* Kombinerer data fra DirectQuery-kilder og importdata.

Ved hjælp af sammensatte modeller kan du f.eks. bygge en model, der kombinerer følgende typer data:

* Salgsdata fra et virksomheds-data warehouse.
* Salgsmåldata fra en afdelings SQL Server-database.
* Data, der er importeret fra et regneark.

En model, der kombinerer data fra mere end én DirectQuery-kilde, eller som kombinerer DirectQuery med importdata, kaldes en sammensat model.

Du kan oprette relationer mellem tabeller, som du altid har gjort, selvom de pågældende tabeller kommer fra forskellige kilder. Alle relationer, der er på tværs af kilder, oprettes med en kardinalitet på mange til mange, uanset hvad deres faktiske kardinalitet er. Du kan ændre dem til én til mange, mange til én eller én til én. Uanset hvilken kardinalitet du har angivet, har relationer på tværs af kilder forskellige funktionsmåder. Du kan ikke bruge DAX-funktioner (Data Analysis Expressions) til at hente værdier på `one`-siden fra `many`-siden. Du oplever måske også en indvirkning på ydeevnen i forhold til mange til mange-relationer i samme kilde.

> [!NOTE]
> I forbindelse med sammensatte modeller er alle importerede tabeller reelt en enkelt kilde, uafhængigt af den faktiske underliggende datakilde.

## <a name="example-of-a-composite-model"></a>Eksempel på en sammensat model

Hvis du vil se et eksempel på en sammensat model, kan du overveje at bruge en rapport, der er forbundet til virksomhedens data warehouse i SQL Server ved hjælp af DirectQuery. I denne instans indeholder data warehouse data for **salg efter land**, **kvartal** og **cykel (produkt)** , som vist på følgende billede:

![Relationsvisning for sammensatte modeller](media/desktop-composite-models/composite-models_04.png)

På dette tidspunkt kan du oprette simple visuals ved hjælp af felter fra denne kilde. Følgende billede viser f.eks. det samlede salgsbeløb efter *ProductName* for et valgt kvartal.

![Visual baseret på data](media/desktop-composite-models/composite-models_05.png)

Men hvad nu hvis du har data i et Office Excel-regneark om den produktchef, der er tildelt til de enkelte produkter, sammen med marketingprioriteten? Hvis du vil have vist **salgsbeløb** efter **produktchef**, er det måske ikke muligt at føje disse lokale data til virksomhedens data warehouse. Eller det kan i bedste fald tage flere måneder.

Det er måske muligt at importere disse salgsdata fra data warehouse i stedet for at bruge DirectQuery. Og salgsdataene kan derefter kombineres med de data, du har importeret fra regnearket. Denne fremgangsmåde er dog ikke en god ide af de årsager, der i første omgang medfører brugen af DirectQuery. Årsagerne kunne omfatte:

* Nogle kombinationer af sikkerhedsreglerne gennemtvinges i den underliggende kilde.
* Behovet for at kunne få vist de nyeste data.
* Alene skaleringen af dataene.

Det er her, sammensatte modeller kommer ind i billedet. Sammensatte modeller giver dig mulighed for at oprette forbindelse til data warehouse ved hjælp af DirectQuery og derefter at bruge **Hent data** til yderligere kilder. I dette eksempel opretter vi først DirectQuery-forbindelse til virksomhedens data warehouse. Vi bruger **Hent data**, vælger **Excel** og navigerer derefter til det regneark, som indeholder vores lokale data. Til sidst importerer vi det regneark, der indeholder *produktnavnene*, den tildelte **salgschef** og **prioriteten**.  

![Vinduet Navigator](media/desktop-composite-models/composite-models_06.png)

På listen **Fields** kan du se to tabeller: den oprindelige tabel **Bike** fra SQL Server og en ny tabel **ProductManagers**. Den nye tabel indeholder de data, der er importeret fra Excel.

![Feltvisning i tabeller](media/desktop-composite-models/composite-models_07.png)

På samme måde ser vi nu i **relationsvisningen** i Power BI Desktop endnu en tabel kaldet **ProductManagers**.

![Relationsvisning for tabeller](media/desktop-composite-models/composite-models_08.png)

Nu skal vi relatere disse tabeller til de andre tabeller i modellen. Som altid skal vi oprette en relation mellem tabellen **Bike** fra SQL Server og den importerede tabel **ProductManagers**. Det vil sige, at relationen findes mellem **Bike[ProductName]** og **ProductManagers[ProductName]** . Som beskrevet tidligere, skal alle relationer, der går på tværs af kilden, have standardkardinaliteten på mange til mange.

![Vinduet "Opret relation"](media/desktop-composite-models/composite-models_09.png)

Nu, hvor vi har oprettet denne relation, vises den i **relationsvisningen** i Power BI Desktop som forventet.

![Den nye relationsvisning](media/desktop-composite-models/composite-models_10.png)

Vi kan nu oprette visuals ved hjælp af et af felterne på listen **Fields**. Denne fremgangsmåde blander uden problemer data fra flere kilder. Det samlede *SalesAmount* for hver *Product Manager* vises f.eks. på følgende billede:

![Ruden Felter](media/desktop-composite-models/composite-models_11.png)

I følgende eksempel vises en fælles brug af en *dimensionstabel*, f.eks. **Product** eller **Customer**, der er udvidet med nogle ekstra data, som er importeret et andet sted fra. Det er også muligt at få tabeller til at bruge DirectQuery til at oprette forbindelse til forskellige kilder. I forlængelse af vores eksempel antager vi nu, at **Sales Targets** pr. **Country** og **Period** er lagret i en separat afdelingsdatabase. Som sædvanlig kan du bruge **Hent data** til at oprette forbindelse til disse data, som vist på følgende billede:

![Vinduet Navigator](media/desktop-composite-models/composite-models_12.png)

Som tidligere kan vi oprette relationer mellem den nye tabel og andre tabeller i modellen og derefter oprette visuals, der kombinerer tabeldataene. Lad os igen se på **relationsvisningen**, hvor vi har oprettet de nye relationer:

![Relationsvisningen med mange tabeller](media/desktop-composite-models/composite-models_13.png)

Det næste billede er baseret på de nye data og de relationer, vi har oprettet. Det visual, der ses nederst til venstre, viser det samlede *Sales Amount* i forhold til *Target*, og beregningen af afvigelsen viser forskellen. Dataene for **Sales Amount** og **Target** kommer fra to forskellige SQL Server-databaser.

![Billede, der viser flere data](media/desktop-composite-models/composite-models_14.png)

## <a name="set-the-storage-mode"></a>Indstil lagringstilstanden

Hver tabel i en sammensat model har en lagringstilstand, der angiver, om tabellen er baseret på DirectQuery eller import. Lagringstilstanden kan vises og redigeres i ruden **Egenskaber**. Hvis du vil have vist lagringstilstanden, skal du højreklikke på en tabel på listen **Fields** og derefter vælge **Egenskaber**. På følgende billede vises lagringstilstanden for tabellen **SalesTargets**.

Lagringstilstanden kan også ses på værktøjstippet for hver tabel.

![Værktøjstip, der viser lagringstilstanden](media/desktop-composite-models/composite-models_16.png)

For alle Power BI Desktop-filer (en *PBIX*-fil), der indeholder nogle tabeller fra DirectQuery og nogle importtabeller, viser statuslinjen en lagringstilstand, der kaldes **Blandet**. Du kan klikke på elementet på statuslinjen og let skifte alle tabeller til import.

Du kan finde flere oplysninger om lagringstilstand i [Administrer lagringstilstand i Power BI Desktop](desktop-storage-mode.md).  

> [!NOTE]
> Du kan bruge *kombineret* lagringstilstand i Power BI Desktop og i Power BI-tjenesten.

## <a name="calculated-tables"></a>Beregnede tabeller

Du kan føje beregnede tabeller til en model, der bruger DirectQuery. Den DAX (Data Analysis Expressions), der definerer den beregnede tabel, kan enten referere til importerede tabeller eller DirectQuery-tabeller eller en kombination af de to.

Beregnede tabeller importeres altid, og dataene i disse tabeller opdateres, når du opdaterer tabellen. Hvis en beregnet tabel refererer til en DirectQuery-tabel, viser visuals, der refererer til DirectQuery-tabellen, altid de nyeste værdier i den underliggende kilde. Alternativt viser visuals, der refererer til den beregnede tabel, værdierne på det tidspunkt, hvor den beregnede tabel senest blev opdateret.

## <a name="security-implications"></a>Sikkerhedsmæssige konsekvenser

Sammensatte modeller har nogle sikkerhedsmæssige konsekvenser. En forespørgsel, der sendes til en datakilde, kan indeholde dataværdier, der er hentet fra en anden kilde. I det tidligere eksempel sender den visualisering, som viser **Sales Amount** efter **Product Manager**, en SQL-forespørgsel til relationsdatabasen Sales. Denne SQL-forespørgsel kan indeholde navnene på produktcheferne og deres tilknyttede produkter.

![Script, der viser sikkerhedsmæssige konsekvenser](media/desktop-composite-models/composite-models_17.png)

Oplysninger, der er lagret i regnearket, inkluderes derfor nu i en forespørgsel, der sendes til relationsdatabasen. Hvis disse oplysninger er fortrolige, skal du overveje de sikkerhedsmæssige konsekvenser. Overvej især følgende punkter:

* En hvilken som helst administrator af databasen, der kan se sporinger eller overvågningslogge, kan se disse oplysninger, også selvom vedkommende ikke har tilladelse til dataene i den oprindelige kilde. I dette eksempel skal administratoren have tilladelse til Excel-filen.

* Krypteringsindstillingerne for de enkelte kilder skal overvejes. Du vil helst undgå at hente oplysninger fra én kilde af en krypteret forbindelse og derefter ved en fejl inkludere dem i en forespørgsel, der sendes til en anden kilde af en ukrypteret forbindelse.

Der vises en advarsel i Power BI Desktop, når du opretter en sammensat model, for at det kan bekræftes, at du har taget alle sikkerhedsmæssige konsekvenser i betragtning.  

Hvis en forfatter desuden føjer *Tabel1* fra *Model A* til en sammensat model (vi kalder den som reference *Model C*), kan en bruger, der får vist en rapport, som er baseret på *Model C*, sende en forespørgsel til **en hvilken som helst tabel** i *Model A*, der ikke er beskyttet af sikkerhed på rækkeniveau.

Af samme årsager skal du være forsigtig, når du åbner en Power BI Desktop-fil, der er sendt fra en kilde, der ikke er tillid til. Hvis filen indeholder sammensatte modeller, sendes der oplysninger, som en person henter fra én kilde ved hjælp af legitimationsoplysningerne for den bruger, der åbner filen, til en anden datakilde som en del af forespørgslen. Oplysningerne kan ses af den ondsindede forfatter af Power BI Desktop-filen. Når du første gang åbner en Power BI Desktop-fil, der indeholder flere kilder, viser Power BI Desktop en advarsel. Advarslen svarer til den, der vises, når du åbner en fil, der indeholder oprindelige SQL-forespørgsler.  

## <a name="performance-implications"></a>Konsekvenser for ydeevne  

Når du bruger DirectQuery, skal du altid være opmærksom på ydeevnen primært for at sikre, at backend-kilden har tilstrækkelige ressourcer til at give brugerne en god oplevelse. En god oplevelse betyder, at visuals opdateres efter fem sekunder eller mindre. Du kan finde flere oplysninger om ydeevne i [Om brug af DirectQuery i Power BI](../connect-data/desktop-directquery-about.md).

Når du bruger sammensatte modeller, skal du have yderligere overvejelser. Et enkelt visual kan resultere i, at der sendes forespørgsler til flere datakilder, som ofte overfører resultaterne fra én forespørgsel til en anden kilde. Denne situation kan føre til følgende scenarier:

* **En SQL-forespørgsel, der indeholder et stort antal konstantværdier**: Et visual, der anmoder om det samlede **salgsbeløb** for nogle valgte **produktchefer**, skal først finde ud af, hvilke **produkter** der er administreret af disse produktchefer. Denne sekvens skal finde sted, før den pågældende visualisering sender en SQL-forespørgsel, der inkluderer alle produkt-id'erne i en `WHERE`-delsætning.

* **En SQL-forespørgsel, der forespørger på et lavere granularitetsniveau, og dataene derefter aggregeres lokalt**: Da antallet af **produkter**, der opfylder filterkriterierne i **Product Manager**, bliver større og større, kan det blive ineffektivt eller umuligt at medtage alle produkter i en `WHERE`-delsætning. Du kan i stedet forespørge relationskilden på det lavere niveau for **produkter** og derefter aggregere resultaterne lokalt. Hvis kardinaliteten for **produkter** overskrider en grænse på 1 mio., mislykkes forespørgslen.

* **Flere SQL-forespørgsler, én pr. gruppe efter værdi**: Når aggregeringen bruger **DistinctCount** og er grupperet efter en relevant kolonne fra en anden kilde, og hvis den eksterne kilde ikke understøtter effektiv overførsel af mange konstantværdier, der definerer grupperingen, er det nødvendigt at sende én SQL-forespørgsel pr. gruppe efter værdi.

   En visualisering, der anmoder om et bestemt antal for **CustomerAccountNumber** fra SQL Server-tabellen efter **produktchefer** (importeret fra regnearket), skal f.eks. overføre oplysningerne fra tabellen **Product Managers** i den forespørgsel, der er sendt til SQL Server. I forhold til andre kilder, f.eks. Redshift, er denne handling ikke mulig. Der sendes i stedet én SQL-forespørgsel pr. **salgschef** op til en given praktisk grænse, hvorefter forespørgslen mislykkes.

Hver af disse scenarier har konsekvenser for ydeevnen, og de præcise detaljer varierer for hver datakilde. Selvom kardinaliteten for de kolonner, der bruges i den relation, der forbinder de to kilder, forbliver lav (nogle få tusind), påvirkes ydeevnen ikke. Efterhånden som denne kardinalitet stiger, skal du være mere opmærksomhed på effekten af ydeevnen.

Desuden betyder brugen af mange til mange-relationer, at særskilte forespørgsler skal sendes til den underliggende kilde for hvert totale eller subtotale niveau fremfor at aggregere de detaljerede værdier lokalt. Et simpelt visual i en tabel med totaler sender to SQL-forespørgsler fremfor ét.

## <a name="limitations-and-considerations"></a>Begrænsninger og overvejelser

Der er nogle få begrænsninger ved denne udgave af sammensatte modeller:

[Gradvis opdatering](../admin/service-premium-incremental-refresh.md) understøttes i øjeblikket kun for sammensatte modeller for datakilder fra SQL, Oracle og Teradata.

Følgende Live Connect-kilder (flerdimensionelle) kan ikke bruges sammen med sammensatte modeller:

* SAP HANA
* SAP Business Warehouse
* SQL Server Analysis Services
* Power BI-datasæt
* Azure Analysis Services

Når du opretter forbindelse til disse flerdimensionelle datakilder ved hjælp af DirectQuery, kan du ikke oprette forbindelse til en anden DirectQuery-kilde eller kombinere den med importdata.

De eksisterende begrænsninger ved DirectQuery gælder stadig, når du bruger sammensatte modeller. Mange af disse begrænsninger gælder nu for de enkelte tabeller afhængigt af tabellens lagringstilstand. En beregnet kolonne i en importeret tabel kan f.eks. referere til andre tabeller, men en beregnet kolonne i en DirectQuery-tabel kan stadig kun referere til kolonner i den samme tabel. Andre begrænsninger gælder for modellen som helhed, hvis nogle af tabellerne i modellen er DirectQuery. Funktionerne QuickInsights og Q&A er f.eks. ikke tilgængelige for en model, hvis nogen af tabellerne i den har lagringstilstanden DirectQuery.

## <a name="next-steps"></a>Næste trin

Du kan finde flere oplysninger om sammensatte modeller og DirectQuery i følgende artikler:

* [Mange til mange-relationer i Power BI Desktop](desktop-many-to-many-relationships.md)
* [Lagringstilstand i Power BI Desktop](desktop-storage-mode.md)
* [Brug DirectQuery i Power BI](../connect-data/desktop-directquery-about.md)
* [Understøttede datakilder i forbindelse med DirectQuery i Power BI](../connect-data/power-bi-data-sources.md)
* [Brug af DirectQuery til Power BI-datasæt og Azure Analysis Services (eksempelvisning)](../connect-data/desktop-directquery-datasets-azure-analysis-services.md)
