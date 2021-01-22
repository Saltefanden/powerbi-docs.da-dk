---
title: 'Selvstudium: Fra dimensionsmodel til enestående rapport i Power BI Desktop'
description: I dette selvstudium starter du med en dimensionsmodel og opretter en fantastisk rapport fra start til slut på 20 minutter.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: tutorial
ms.date: 01/19/2021
LocalizationGroup: Reports
ms.openlocfilehash: 03eac7aefdebb31eac353c969db2bf8810173395
ms.sourcegitcommit: 77912d4f6ef2a2b1ef8ffccc50691fe5b38ee97a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/22/2021
ms.locfileid: "98687349"
---
# <a name="tutorial-from-dimensional-model-to-stunning-report-in-power-bi-desktop"></a>Selvstudium: Fra dimensionsmodel til enestående rapport i Power BI Desktop 

I dette selvstudium starter du med en dimensionsmodel og opretter en fantastisk rapport fra start til slut på 45 minutter.

Du arbejder i AdventureWorks, og din chef vil gerne se en rapport med dine seneste salgstal. Ledelsen har anmodet om en oversigt over følgende: 

- Hvilken dag blev der solgt mest i februar 2019? 
- I hvilket land har virksomheden størst succes? 
- Hvilken produktkategori og hvilke forretningstyper som forhandler bør firmaet fortsat investere i? 

Ved hjælp af vores [Excel-projektmappe med salgseksemplet til AdventureWorks](https://github.com/microsoft/powerbi-desktop-samples/blob/main/AdventureWorks%20Sales%20Sample/AdventureWorks%20Sales.xlsx) kan vi oprette denne rapport på ingen tid. Sådan ser den færdige rapport ud. 

:::image type="content" source="media/desktop-dimensional-model-report/adventureworks-finished-report.png" alt-text="Færdig AdventureWorks-rapport.":::

Vil du se det færdige produkt? Du kan også downloade den [færdige .pbix-fil fra Power BI](https://github.com/microsoft/powerbi-desktop-samples/blob/main/AdventureWorks%20Sales%20Sample/AdventureWorks%20Sales.pbix).

Lad os komme i gang! 

I dette selvstudium lærer du, hvordan du kan:

> [!div class="checklist"]
> * Forbereder dine data med nogle få transformationer
> * Opretter en rapport med en titel, tre visualiseringer og et udsnit
> * Publicerer din rapport til Power BI-tjenesten, så du kan dele den med dine kolleger

## <a name="prerequisites"></a>Forudsætninger

- Før du starter, skal du [downloade Power BI Desktop](../fundamentals/desktop-get-the-desktop.md). 
- Hvis du planlægger at publicere din rapport til Power BI-tjenesten og ikke har tilmeldt dig endnu, kan du [tilmelde dig en gratis prøveperiode](../fundamentals/service-self-service-signup-for-power-bi.md). 

## <a name="get-data-download-the-sample"></a>Hent data: Download eksemplet 

1. Download [Excel-projektmappen med salgseksemplet til AdventureWorks](https://github.com/microsoft/powerbi-desktop-samples/blob/main/AdventureWorks%20Sales%20Sample/AdventureWorks%20Sales.xlsx). 

1. Åbn Power BI Desktop. 

1. I afsnittet **Data** på båndet **Start** skal du vælge **Excel**. 

1. Gå til det sted, hvor du gemte eksempelprojektmappen, og vælg **Åbn**. 

## <a name="prepare-your-data"></a>Forbered dine data 

I ruden Navigator har du mulighed for at  *transformere* eller *indlæse* dataene. Navigator viser et eksempel på dine data, så du kan kontrollere, at du har det rette datainterval. Numeriske datatyper står i kursiv. I dette selvstudium transformerer vi dataene før indlæsning.

Vælg alle tabeller, og vælg **Transformér data**. Undlad at markere arkene (markeret med *_data*). 

:::image type="content" source="media/desktop-dimensional-model-report/desktop-load-tables.png" alt-text="Indlæs tabeller i Navigator.":::

Kontrollér, at kolonnernes datatyper stemmer overens med datatyperne i følgende tabel. Hvis du vil lade Power BI registrere datatyper for dig, skal du vælge en forespørgsel og derefter vælge en eller flere kolonner. På fanen **Omdan** skal du vælge **Find data type**. Hvis du vil foretage ændringer af den registrerede datatype, skal du under fanen **hjem** vælge **datatype** og derefter vælge den relevante datatype fra tabellen.

:::image type="content" source="media/desktop-dimensional-model-report/power-query-change-data-types.png" alt-text="Kontrollér kolonnernes datatyper.":::


|Forespørgsel  |Kolonne  |Datatype  |
|---------|---------|---------|
|Kunde  |  Kundenøgle | Helt tal |
|Dato | DateKey |    Helt tal     |
|     | Dato | Dato      |
|     | MonthKey  | Helt tal |
|Produkt  | ProductKey | Helt tal  | 
|     | Standardomkostninger | Decimaltal  | 
|     | Listepris | Decimaltal  | 
|Reseller  | ResellerKey | Helt tal  | 
|Sales   | SalesOrderLineKey | Helt tal  | 
|     | ResellerKey  | Helt tal  | 
|     | Kundenøgle | Helt tal  | 
|     | ProductKey  | Helt tal  | 
|     | Ordredatonøgle | Helt tal  | 
|     | Forfaldsdatonøgle  | Helt tal  | 
|     | Leveringsdatonøgle | Helt tal  | 
|     | SalesTerritoryKey | Helt tal  | 
|     | Ordremængde   | Helt tal  | 
|     | Enhedspris  | Decimaltal  | 
|     | Udvidet beløb  | Decimaltal  | 
|     | Rabat i procent på enhedspris | Procent  | 
|     | Standardomkostninger for produkt | Decimaltal  | 
|     | Samlede produktomkostninger | Decimaltal  | 
|     | Salgsbeløb | Decimaltal  | 
| SalesTerritory  | SalesTerritoryKey | Helt tal  | 
|  Salgsordre   |  SalesOrderLineKey | Helt tal  | 

Tilbage på fanen **Hjem** skal du vælge  **Luk og anvend**. 

:::image type="content" source="media/desktop-dimensional-model-report/power-query-close-and-apply.png" alt-text="Knappen Luk og anvend for Power Query.":::

## <a name="model-your-data"></a>Udform dine data 

De indlæste data er næsten klar til rapportering. Lad os gennemse datamodellen og foretage nogle ændringer. 

Vælg **Modelvisning** til venstre. 

:::image type="content" source="media/desktop-dimensional-model-report/desktop-select-model-view.png" alt-text="Vælg Modelvisning i Power BI Desktop.":::

Din datamodel bør ligne følgende billede med hver tabel i en boks. 

:::image type="content" source="media/desktop-dimensional-model-report/desktop-data-model-1.png" alt-text="Den datamodel, der skal startes med.":::

### <a name="create-relationships"></a>Opret relationer

Denne model er et typisk *stjerneskema*, som du kan se fra data warehouses: Det ligner en stjerne. Midten af stjernen er en faktatabel. De omgivende tabeller kaldes dimensionstabeller, som er relateret til faktatabellen med relationer. Faktatabellen indeholder numeriske oplysninger om salgstransaktioner, f.eks. Salgsbeløb og Standardomkostninger for produkt. Dimensionstabellerne giver dig en kontekst, så du blandt andet kan analysere: 

- Hvilket produkt blev solgt... 
- til hvilken kunde... 
- af hvilken forhandler... 
- i hvilket salgsområde.  

Hvis du kigger nærmere efter, vil du bemærke, at alle dimensionstabeller er relateret til faktatabellen med en relation med undtagelse af tabellen Dato. Lad os nu føje nogle relationer til tabellen Dato. Træk DateKey fra tabellen Dato til OrderDateKey i tabellen Salg. Du har oprettet en såkaldt "en til mange"-relation fra Dato til Salg, som angivet af **1** og stjernen * (mange) i de to ender af linjen.  

Relationen er "en til mange", da vi har en eller flere salgsordrer for en bestemt dato. Hvis der kun havde været én salgsordre for hver dato, ville relationen være "en til en". Den lille pil i midten af linjen angiver "krydsfiltreringsretning". Det betyder, at du kan bruge værdier fra tabellen Dato til at filtrere tabellen Salg, så relationen giver dig mulighed for at analysere, hvornår en salgsordre blev afgivet.  

:::image type="content" source="media/desktop-dimensional-model-report/desktop-date-sales-relationship.png" alt-text="Relation mellem tabellerne Salg og Dato.":::

Tabellen Salg indeholder flere oplysninger om datoer, der er relateret til salgsordrer, f.eks. forfaldsdato og afsendelsesdato. Lad os føje to relationer mere til tabellen Dato ved at trække: 

- DateKey til DueDateKey 
- DateKey til ShipDateKey 
    
:::image type="content" source="media/desktop-dimensional-model-report/desktop-date-sales-relationships-done.png" alt-text="Tre relationer mellem tabellerne Salg og Dato.":::

Du vil bemærke, at den første relation til OrderDateKey er aktiv, hvilket er vist med den uafbrudte linje. De to andre er inaktive, hvilket er vist med stiplede linjer. Power BI bruger som standard den aktive relation til at relatere til Salg og Dato. Derfor beregnes en sum af SalesAmount efter Ordredato og ikke Forfaldsdato eller Afsendelsesdato. Du kan påvirke denne funktionsmåde. Se [Ekstra kredit: Skriv en måling i DAX](#extra-credit-write-a-measure-in-dax) senere i dette selvstudium.

### <a name="hide-key-columns"></a>Skjul nøglekolonner

Et typisk stjerneskema indeholder flere nøgler, der indeholder relationerne mellem faktatabeller og dimensionstabeller. Normalt vil vi ikke bruge nogen nøglekolonner i vores rapporter. Lad os skjule nøglekolonnerne i visningen, så der vises færre felter på listen Felter, og datamodellen er nemmere at bruge. 

Gennemgå alle tabeller, og skjul enhver kolonne, hvis navn slutter med *Key*: 

Vælg **øjeikonet** ud for kolonnen, og vælg **Skjul i rapportvisning**.

:::image type="content" source="media/desktop-dimensional-model-report/desktop-column-visible.png" alt-text="Synlig kolonne med øjeikon.":::

Du kan også vælge **øjeikonet** ud for kolonnen i ruden Egenskaber.

Skjulte felter har dette ikon: et øje med en streg igennem. 

:::image type="content" source="media/desktop-dimensional-model-report/desktop-column-hidden.png" alt-text="Felt med det skjulte øjeikon.":::
 
Skjul disse felter.

|Tabel  |Kolonne  |
|---------|---------|
|Kunde  | Kundenøgle |
|Dato     | DateKey |
|     | MonthKey |
|Produkt     | ProductKey  |
|Reseller   | ResellerKey  |
|Sales     | Kundenøgle  |
|     | Forfaldsdatonøgle |
|     | Ordredatonøgle |
|     | ProductKey |
|     | ResellerKey        |
|     | SalesOrderLineKey        |
|     | SalesTerritoryKey        |
|     | Leveringsdatonøgle        |
| Salgsordre    | SalesOrderLineKey |
| SalesTerritory  | SalesTerritoryKey |

Din datamodel bør nu ligne denne datamodel med relationer mellem salg og alle andre tabeller samt alle nøglefelter skjult: 

:::image type="content" source="media/desktop-dimensional-model-report/desktop-data-model-2-hidden-columns.png" alt-text="Datamodel med skjulte nøglekolonner.":::

### <a name="create-hierarchies"></a>Oprette hierarkier

Nu, hvor vores datamodel er nemmere at bruge pga. de skjulte kolonner, kan vi tilføje nogle *hierarkier* for at gøre det endnu nemmere at bruge modellen. Hierarkier muliggør nemmere navigation i grupperinger. Byer er f.eks. i Stat eller Provins, som er i et Land eller et Område. 

Opret følgende hierarkier. 

1. Højreklik på det højeste niveau eller det mindst detaljerede felt i hierarkiet, og vælg **Opret hierarki**. 

1. I ruden **Egenskaber** skal du angive **Navn** for hierarkiet og angive niveauerne. 

1. **Anvend derefter niveauændringer**. 

    :::image type="content" source="media/desktop-dimensional-model-report/desktop-hierarchy-properties.png" alt-text="Ruden Egenskaber for hierarki.":::

Du kan også omdøbe niveauer i et hierarki i ruden Egenskaber, efter du har tilføjet dem. Du skal omdøbe niveauet År og Kvartal i hierarkiet Regnskab i tabellen Dato. 

Her er de hierarkier, du skal oprette.

| Tabel |Navn på hierarki |Niveauer  |
|---------|---------|---------|
|Kunde     | Geografi   | Land-område  |
|     | | State-Province  |
|     |         | City |
|Row4     |         | Postnummer |
|Row5     |         | Kunde   |
|Dato     | Regnskab  | År (regnskabsår)  |
|     |         | Kvartal (regnskabskvartal) |
|     |         | Month |
|     |         | Dato |
| Product  | Produkter | Kategori |
|     |         | Underkategori |
|     |         | Modellering |
|     |         | Product |
| Reseller   | Geografi | Land-område |
|     |         | State-Province |
|     |         | City  |
|     |         | Postnummer  |
|     |         | Reseller |
| SalesOrder  | Salgsordrer | Salgsordre |
|     |         | Salgsordrelinje |
| SalesTerritory    | Salgsområder | Group |
|     |         | Country |
|     |         | Region |
 
Din datamodel bør nu ligne følgende datamodel. Den har de samme tabeller, men hver dimensionstabel indeholder et hierarki: 

:::image type="content" source="media/desktop-dimensional-model-report/desktop-data-model-3-added-hierarchies.png" alt-text="Datamodel med dimensionstabeller med hierarkier.":::

### <a name="rename-tables"></a>Omdøb tabeller

For at fuldføre udformningen omdøber vi følgende tabeller i ruden Egenskaber: 

|Tidligere tabelnavn  |Nyt tabelnavn  |
|---------|---------|
|SalesTerritory    |  Sales Territory   |
|SalesOrder  |  Sales Order   |

Dette trin er nødvendigt, fordi Excel-tabelnavne ikke må indeholde mellemrum.

Nu er din endelige datamodel klar.

:::image type="content" source="media/desktop-dimensional-model-report/desktop-data-model-4-renamed-tables.png" alt-text="Fuldført datamodel med omdøbte tabeller.":::

## <a name="extra-credit-write-a-measure-in-dax"></a>Ekstra kredit: Skriv en måling i DAX 

Skrivning af *målinger* i formelsproget DAX er et meget effektivt middel til datamodellering. Du kan få mere [at vide om DAX i Power BI-dokumentationen](/dax/). Lad os på nuværende tidspunkt skrive en grundlæggende måling, der beregner det samlede salgsbeløb efter forfaldsdato for salgsordren i stedet for standardordredatoen. Denne måling bruger [funktionen USERELATIONSHIP](/dax/userelationship-function-dax) til at aktivere relationen mellem Salg og Dato for DueDate for målingens kontekst. Derefter bruger den [CALCULATE](/dax/calculate-function-dax) til at opsummere Salgsbeløb i denne kontekst.

1. Vælg Datavisning til venstre. 

    :::image type="content" source="media/desktop-dimensional-model-report/desktop-open-data-view.png" alt-text="Vælg Datavisning til venstre.":::

1. Vælg tabellen Salg på listen Felter.

    :::image type="content" source="media/desktop-dimensional-model-report/desktop-select-sales-table.png" alt-text="Vælg tabellen Salg på listen Felter.":::

1. På båndet  **Hjem** skal du vælge **Ny måling**. 

1. Vælg eller skriv denne måling for at beregne det samlede salgsbeløb efter forfaldsdato for salgsordren i stedet for standardordredatoen:

    ```dax
    Sales Amount by Due Date = CALCULATE(SUM(Sales[Sales Amount]), USERELATIONSHIP(Sales[DueDateKey],'Date'[DateKey]))
    ```

1. Vælg markeringen for at bekræfte. 

    :::image type="content" source="media/desktop-dimensional-model-report/desktop-adding-a-dax-measure.png" alt-text="Vælg fluebenet for at bekræfte DAX-målingen.":::

## <a name="build-your-report"></a>Opbyg din rapport 

Nu, hvor du har udformet dine data, er det tid til at oprette din rapport. Gå til Rapportvisning. Du kan se felterne i den datamodel, du har oprettet, i ruden Felter til højre.

Lad os opbygge den endelige rapport, én visualisering ad gangen. 

:::image type="content" source="media/desktop-dimensional-model-report/adventureworks-finished-report-with-numbers.png" alt-text="Den færdige rapport med tal, der markerer hver visualisering":::

### <a name="visual-1-add-a-title"></a>Visualisering 1: Tilføj en titel 

1. På båndet **Indsæt** skal du vælge **Tekstboks**. Skriv "Sammenfatning – salgsrapport". 

1. Vælg den tekst, du har skrevet. Angiv skriftstørrelsen til **20** og **Fed**. 

    :::image type="content" source="media/desktop-dimensional-model-report/executive-summary-text-box.png" alt-text="Formatér teksten til Sammenfatning.":::

1. I ruden Visualiseringer skal du skifte **Baggrund** til **Fra**. 

1. Tilpas feltets størrelse, så den passer til én linje. 

### <a name="visual-2-sales-amount-by-date"></a>Visualisering 2: Salgsbeløb efter Dato 

Derefter skal du oprette et kurvediagram for at se, hvilken måned og hvilket år der havde det højeste salgsbeløb.

1. I ruden Felter skal du trække feltet **Salgsbeløb** fra tabellen **Salg** til et tomt område på rapportlærredet. Power BI viser som standard et søjlediagram med én kolonne, Salgsbeløb. 

1. Træk feltet **Måned** fra hierarkiet **Regnskab** i tabellen **Dato**, og slip det i søjlediagrammet. 

    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-amount-by-year.png" alt-text="Opret et søjlediagram med en kolonne for hvert år.":::

1. I afsnittet **Felter** i ruden Visualiseringer skal du fjerne felterne **År** og **Kvartal**: 

    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-amount-by-year-remove-year-and-quarter.png" alt-text="I afsnittet Felter i ruden Visualiseringer skal du fjerne felterne År og Kvartal.":::

1. I ruden Visualiseringer skal du ændre visualiseringstypen til **Områdediagram**. 

    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-amount-by-year-change-to-area.png" alt-text="Ret søjlediagrammet til et områdediagram.":::

1. Hvis du har tilføjet DAX-målingen i ekstra kredit ovenfor, skal du også føje den til **Værdier**. 
1. Åbn ruden Formatér, åbn Datafarver, og ret farven på **Salgsbeløb efter forfaldsdato** til en farve med mere kontrast, f.eks. rød.

    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-amount-by-year-add-DAX-measure.png" alt-text="Salgsbeløb efter forfaldsdato som områdediagram.":::

    Som du kan se, halter Salgsbeløb efter Forfaldsdato en smule efter Salgsbeløb. Dette beviser, at den bruger relationen mellem tabellerne Salg og Dato, som bruger DueDateKey. 

 

### <a name="visual-3-order-quantity-by-reseller-country"></a>Visualisering 3: Ordreantal efter Forhandlerland 

Nu skal vi oprette et kort for at se, i hvilket land forhandlerne har det højeste ordrebeløb.

1. I ruden Felter skal du trække feltet **Land-Område** fra tabellen **Forhandler** til et tomt område på dit rapportlærred. Power BI opretter et kort. 

1. Træk feltet **Ordreantal** fra tabellen **Salg**, og slip det på kortet. Sørg for, at **Land-Område** er i brønden **Placering**, og at **Ordreantal** er i brønden **Størrelse**. 

    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-order-quantity-by-reseller-country.png" alt-text="Kort over ordreantal efter land/område.":::

### <a name="visual-4-sales-amount-by-product-category-and-reseller-business-type"></a>Visualisering 4: Salgsbeløb efter Produktkategori og Forretningstype som forhandler 

Derefter skal vi oprette et søjlediagram for at undersøge, hvilke produkter der sælges af hvilken type forhandlerforretning.

1. Træk de to diagrammer, du har oprettet, så de ligger side om side i den øverste halvdel af lærredet. Lad et område stå tomt i venstre side af lærredet. 

1. Vælg et tomt område i den nederste halvdel af rapportlærredet. 

1. I ruden Felter skal du vælge **Salgsbeløb** fra **Salg**, **Produktkategori** fra **Produkt** og **Forretningstype** fra **Forhandler**.
    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-amount-by-product-category-field-well.png" alt-text="Kontrollér, at kategorien og forretnings typen er på rækker, og at salgsbeløbet er valgt som værdier.":::
    
    Power BI opretter automatisk et grupperet søjlediagram. Skift visualiseringen til en **Matrix**: 

    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-amount-by-product-category-change-to-matrix.png" alt-text="Skift det grupperede søjlediagram til en matrix.":::

1. Med matrixen markeret skal du i ruden Filtre under **Forretningstype** **vælge alle** og derefter rydde feltet **[Ikke tilgængelig]** . 

    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-amount-by-product-category-filter-not-applicable.png" alt-text="Bortfiltrer forretningstypen Ikke tilgængelig.":::

1. Træk matrixen, så den er bred nok til at udfylde pladsen under de to øverste diagrammer. 

    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-amount-by-product-category-increase-width.png" alt-text="Udvid matrixen for at udfylde rapporten.":::

1. Åbn afsnittet **Betinget formatering** i ruden Formatering for matrixen, og slå **Datalinjer** til. Vælg **Avancerede kontrolelementer**, og angiv en lysere farve for den positive linje. Vælg **OK**. 

1. Øg bredden af kolonnen Sales Amount, så den dækker hele området ved at trække matrixen.

    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-amount-by-product-category-add-databars.png" alt-text="Matrix med datalinjer for Salgsbeløb.":::

Det ser ud til, at der er et højere samlet Salgsbeløb for Cykler, og at forhandlerne sælger mest – skarpt forfulgt af varehuse. For Komponenter sælger varehusene mere end forhandlerne. 

 

### <a name="visual-5-fiscal-calendar-slicer"></a>Visualisering 5: Udsnit af regnskabskalender 

Udsnit er et værdifuldt værktøj til filtrering af visualiseringer på en rapportside til en bestemt markering. I dette tilfælde kan vi oprette et udsnit for at fokusere på resultaterne for hver måned, hvert kvartal og hvert år. 

1. I ruden Felter skal du vælge hierarkiet **Regnskab** fra tabellen **Dato** og trække det til det tomme område til venstre på lærredet. 

1. I ruden Visualiseringer skal du vælge **Udsnit**. 

    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-add-fiscal-calendar-slicer.png" alt-text="Føj et udsnit af kalenderen for salg til rapporten.":::

1. Fjern **Kvartal** og **Dato** under afsnittet Felter i ruden Visualiseringer, så det kun er **År** og **Måned**, der er tilbage. 
 
    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-add-fiscal-calendar-slicer-remove-quarter-and-date.png" alt-text="Fjern Kvartal og Dato fra udsnittet Regnskab.":::

Hvis din chef nu beder om kun at se data for en bestemt måned, kan du bruge udsnittet til at skifte mellem år eller bestemte måneder i hvert år. 

## <a name="extra-credit-format-the-report"></a>Ekstra kredit: Formatér rapporten 

Hvis du vil finpudse formateringen af denne rapport, kan du følge disse enkle trin. 

### <a name="theme"></a>Tema 

- På båndet  **Vis** skal du vælge **Temaer** og ændre temaet til  **Eksekutiv**. 

    :::image type="content" source="media/desktop-dimensional-model-report/formatting-report-change-theme.png" alt-text="Vælg temaet Eksekutiv.":::

### <a name="spruce-up-the-visuals"></a>Gør visualiseringen klar 

Foretag følgende ændringer under fanen  **Formatér** i ruden Visualiseringer. 

:::image type="content" source="media/desktop-dimensional-model-report/formatting-report-formatting-pane.png" alt-text="Skærmbillede af fanen Formatér i ruden Visualiseringer.":::

**Visualisering 2, Salgsbeløb efter Dato**

1. Vælg Visualisering 2, Salgsbeløb efter Dato. 
1. Hvis du ikke tilføjede DAX-målingen i afsnittet **Titel** , skal du ændre teksten i  **Titel** til "Salgsbeløb efter Ordredato". 

    Hvis du tilføjede DAX-målingen, skal du ændre **Titeltekst** til "Salgsbeløb efter Ordredato/Forfaldsdato". 

1. Angiv størrelsen af **teksten** til  **16 pkt**. 
1. Slå **Skygge**  **Til**. 

**Visualisering 3, Ordreantal efter Forhandlerland**

1. Vælg Visualisering 3, Ordreantal efter Forhandlerland. 
1. I afsnittet **Korttypografier** skal du ændre **Tema** til **Gråtoneskala**. 
1. I afsnittet  **Titel** skal du ændre **Titeltekst** til "Ordreantal efter Forhandlerland".
1. Angiv **Tekststørrelse** til  **16 pkt**. 
1. Slå **Skygge**  **Til**.  

**Visualisering 4, Salgsbeløb efter Produktkategori og Forretningstype som forhandler**

1. Vælg Visualisering 4, Salgsbeløb efter Produktkategori og Forretningstype som forhandler. 
1. I afsnittet  **Titel** skal du ændre **Titelteksten** til "Salgsbeløb efter Produktkategori og Forretningstype som forhandler".
1. Angiv **Tekststørrelse** til  **16 pkt**. 
1. Slå **Skygge**  **Til**. 

**Visualisering 5, Udsnit af regnskabskalender**

1. Vælg Visualisering 5, Udsnit af regnskabskalender.
1. I afsnittet **Kontrolelementer til markering** skal du slå indstillingen **Vis "Vælg alle"**  **Til**. 
1. I afsnittet  **Udsnit af overskrift** skal du angive **Tekststørrelse** til  **16 pkt**. 

### <a name="add-a-background-shape-for-the-title"></a>Tilføj en baggrundsform til titlen 

1. På båndet **Indsæt** skal du vælge **Figurer** > **Rektangel**. 
1. Placer den øverst på siden, og stræk den, så den fylder bredden på siden og højden på overskriften. 
1. I ruden **Formatér figur** under afsnittet **Linje** skal du ændre **Gennemsigtighed** til  **100 %** . 
1. I afsnittet **Udfyld** skal du ændre **Udfyldningsfarve** til **Temafarve 5 #6B91C9 (blå)** . 
1. Under fanen **Formatér** skal du vælge **Send bagud** > **Placer bagest**. 
1. Vælg teksten i Visualisering 1, titlen, og skift **Skriftfarve** til  **Hvid**. 

## <a name="finished-report"></a>Færdig rapport 

Vælg **FY2019** i udsnittet.

:::image type="content" source="media/desktop-dimensional-model-report/adventureworks-finished-report.png" alt-text="Din endelige færdige rapport.":::

For at opsummere besvarer denne rapport din chefs vigtigste spørgsmål: 

- Hvilken dag blev der solgt mest i februar 2019? 
    25. februar med et salgsbeløb på 253.915,47 USD. 

- I hvilket land har virksomheden størst succes? 
    I USA med et ordreantal på 132.748. 

- Hvilken produktkategori og hvilke forretningstyper som forhandler bør firmaet fortsat investere i? 
    Virksomheden skal fortsat investere i kategorien Cykler samt forhandlere og varehuse. 

## <a name="save-your-report"></a>Gem din rapport 

- I menuen **Filer** skal du vælge **Gem**. 


## <a name="publish-to-the-power-bi-service-to-share"></a>Publicer til Power BI-tjenesten for at dele 

Hvis du vil dele din rapport med din chef og dine kolleger, kan du publicere den på Power BI-tjenesten. Når du deler med kollegaer, der har en Power BI-konto, kan de interagere med din rapport, men de kan ikke gemme ændringerne.

1. I Power BI Desktop skal du på båndet **Hjem** vælge **Publicer**. 
1. Det er muligvis nødvendigt at logge på Power BI-tjenesten. Hvis du endnu ikke har en konto, kan du  [tilmelde dig en gratis prøveversion](https://app.powerbi.com/signupredirect?pbi_source=web). 

1. Vælg en destination, f.eks. Mit arbejdsområde i Power BI-tjenesten >  **Vælg**. 

1. Vælg  **Åbn "dit-filnavn" i Power BI**. Din færdige rapport åbnes i browseren. 

1. Vælg **Del** øverst i rapporten for at dele din rapport med andre.

## <a name="next-steps"></a>Næste trin 

- Download den [færdige .pbix-fil fra Power BI](https://github.com/microsoft/powerbi-desktop-samples/blob/main/AdventureWorks%20Sales%20Sample/AdventureWorks%20Sales.pbix)
- Få mere at vide om [DAX og dataudformning i Power BI Desktop](/learn/modules/dax-power-bi-models/)

Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
