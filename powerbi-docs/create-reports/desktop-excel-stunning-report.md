---
title: 'Selvstudium: Fra Excel-projektmappe til imponerende rapport i Power BI Desktop'
description: I dette selvstudium kan du se, hvordan du hurtigt kan oprette en imponerende rapport fra en Excel-projektmappe.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: tutorial
ms.date: 07/21/2020
ms.author: maggies
LocalizationGroup: Data from files
ms.openlocfilehash: 275a83c8588bb9489361d467c6c6ab458abc86b2
ms.sourcegitcommit: be424c5b9659c96fc40bfbfbf04332b739063f9c
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 10/01/2020
ms.locfileid: "91635326"
---
# <a name="tutorial-from-excel-workbook-to-stunning-report-in-power-bi-desktop"></a>Selvstudium: Fra Excel-projektmappe til imponerende rapport i Power BI Desktop

I dette selvstudium opretter du en fantastisk rapport fra start til slut på 20 minutter! 

Din chef vil gerne have en rapport over dine seneste salgstal. Ledelsen har anmodet om en oversigt over: 

- Hvilken måned og hvilket år var avancen størst? 
- Hvor har virksomheden størst succes (pr. land)? 
- Hvilket produkt og segment skal virksomheden fortsat at investere i? 

Med vores eksempelprojektmappe kan vi hurtigt oprette denne rapport. Sådan ser den færdige rapport ud. Lad os komme i gang! 

:::image type="content" source="media/desktop-excel-stunning-report/power-bi-excel-formatted-report.png" alt-text="Skærmbillede af Power BI-rapporten i Power BI-tjenesten."::: 

I dette selvstudium lærer du, hvordan du:

> [!div class="checklist"]
> * Downloader eksempeldata
> * Forbereder dine data med nogle få transformationer
> * Opretter en rapport med en titel, tre visualiseringer og et udsnit
> * Publicerer din rapport til Power BI-tjenesten, så du kan dele den med dine kolleger

## <a name="prerequisites"></a>Forudsætninger

- Før du starter, skal du [downloade Power BI Desktop](https://powerbi.microsoft.com/desktop/).
- Hvis du planlægger at publicere din rapport til Power BI-tjenesten og ikke har tilmeldt dig endnu, kan du [tilmelde dig en gratis prøveperiode](https://app.powerbi.com/signupredirect?pbi_source=web).

## <a name="download-the-sample"></a>Download eksemplet

For at følge med skal du downloade eksempelprojektmappen. 

1. Download [Excel-projektmappen Økonomieksempel](https://go.microsoft.com/fwlink/?LinkID=521962).
1. Åbn Power BI Desktop.
1. I afsnittet **Data** på båndet **Start** skal du vælge **Excel**.
1. Gå til det sted, hvor du gemte eksempelprojektmappen, og vælg **Åbn**.

## <a name="prepare-your-data"></a>Forbered dine data 

I **Navigator** kan du vælge at *transformere* eller *indlæse* dataene. Navigator viser et eksempel på dine data, så du kan kontrollere, at du har det rette datainterval. Numeriske datatyper står i kursiv. Hvis du vil foretage ændringer, skal du transformere dine data, før du indlæser dem. For at gøre det nemmere at læse visualiseringerne senere vil vi gerne transformere dataene nu. Hver gang du udfører en transformation, kan du se, at den føjes til listen under **Forespørgselsindstillinger** i **Anvendte trin** 

1. Markér tabellen **Økonomi**, og vælg **Transformér data**. 

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-financial-navigator.png" alt-text="Skærmbillede af Power BI-rapporten i Power BI-tjenesten."::: 

1. Vælg kolonnen **Solgte enheder**. På fanen **Start** skal du vælge **Datatype** og derefter **Heltal**. Vælg **Erstat aktuel** for at ændre kolonnetypen. 

    Det trin, som brugerne oftest foretager i forbindelse med datarensning, er at skifte datatype. I dette tilfælde er antallet af solgte enheder i decimalform. Det giver ikke mening at have 0,2 eller 0,5 solgte enheder, vel? Så lad os ændre det til heltal. 

    :::image type="content" source="media/desktop-excel-stunning-report/power-query-whole-number.png" alt-text="Skærmbillede af Power BI-rapporten i Power BI-tjenesten."::: 

1. Vælg kolonnen **Segment**. På fanen **Transformer** skal du vælge **Format** og derefter **STORE BOGSTAVER**.

    Vi vil også gøre det nemmere at se segmenterne i diagrammet på et senere tidspunkt. Lad os formatere kolonnen Segment. 

     :::image type="content" source="media/desktop-excel-stunning-report/power-query-upper-case.png" alt-text="Skærmbillede af Power BI-rapporten i Power BI-tjenesten.":::

1. Lad os forkorte kolonnenavnet fra **Månedsnavn** til bare **Måned**. Dobbeltklik på kolonnen **Månedsnavn**, og omdøb den til bare **Måned**.  

     :::image type="content" source="media/desktop-excel-stunning-report/power-query-month-name.png" alt-text="Skærmbillede af Power BI-rapporten i Power BI-tjenesten.":::

1. I kolonnen **Produkt** skal du vælge rullelisten og fjerne markeringen af afkrydsningsfeltet ud for **Montana**. 

     Vi ved, at produktet Montana udgik i sidste måned, så vi vil gerne filtrere disse data fra vores rapport for at undgå forvirring. 

     :::image type="content" source="media/desktop-excel-stunning-report/power-query-montana.png" alt-text="Skærmbillede af Power BI-rapporten i Power BI-tjenesten.":::

1. Du kan se, at hver transformation er føjet til listen under **Forespørgselsindstillinger** i **Anvendte trin**.

    :::image type="content" source="media/desktop-excel-stunning-report/power-query-applied-steps.png" alt-text="Skærmbillede af Power BI-rapporten i Power BI-tjenesten.":::

1. Tilbage på fanen **Start** skal du vælge **Luk og anvend**. Vores data er næsten klar til oprettelse af en rapport. 

    Kan du se Sigma-symbolet på listen Felter? Power BI har registreret, at disse felter er numeriske. Power BI angiver også datofeltet med et kalendersymbol.

     :::image type="content" source="media/desktop-excel-stunning-report/power-bi-fields-list-sigmas-date.png" alt-text="Skærmbillede af Power BI-rapporten i Power BI-tjenesten.":::

### <a name="extra-credit-write-a-measure-in-dax"></a>Ekstra kredit: Skriv en måling i DAX

Skrivning af *målinger* i formelsproget *DAX* er et meget effektivt middel til datamodellering. Du kan læse meget mere om DAX i Power BI-dokumentationen. Lad os indtil videre skrive en basismåling og forbinde to tabeller. 

1. Vælg **Datavisning** til venstre. 
 
    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-data-view.png" alt-text="Skærmbillede af Power BI-rapporten i Power BI-tjenesten.":::

1. På båndet **Hjem** skal du vælge **Ny tabel**. 

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-new-table.png" alt-text="Skærmbillede af Power BI-rapporten i Power BI-tjenesten.":::

1. Indtast denne måling for at generere en kalendertabel med alle datoer mellem den 1. januar 2013 og den 31. december 2014.  

    `Calendar = CALENDAR(DATE(2013,01,01),Date(2014,12,31))` 

2. Vælg markeringen for at bekræfte.

     :::image type="content" source="media/desktop-excel-stunning-report/power-bi-dax-expression.png" alt-text="Skærmbillede af Power BI-rapporten i Power BI-tjenesten.":::

1. Vælg nu **Modelvisning** til venstre. 

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-model-view.png" alt-text="Skærmbillede af Power BI-rapporten i Power BI-tjenesten.":::

1. Træk feltet **Dato** fra tabellen Økonomi til feltet **Dato** i tabellen Kalender for at forbinde tabellerne, og opret en *Relation* mellem dem.  

     :::image type="content" source="media/desktop-excel-stunning-report/power-bi-date-relationship.png" alt-text="Skærmbillede af Power BI-rapporten i Power BI-tjenesten.":::

## <a name="build-your-report"></a>Opbyg din rapport 

Nu, hvor du har transformeret og indlæst dine data, er det tid til at oprette din rapport. Du kan se felterne i den datamodel, du har oprettet, i ruden Felter til højre. 

Lad os opbygge den endelige rapport, én visualisering ad gangen. 

:::image type="content" source="media/desktop-excel-stunning-report/power-bi-report-by-numbers.png" alt-text="Skærmbillede af Power BI-rapporten i Power BI-tjenesten.":::

### <a name="visual-1-add-a-title"></a>Visualisering 1: Tilføj en titel 

1. På båndet **Indsæt** skal du vælge **Tekstboks**. Skriv "Resume af udførelsen – økonomirapport". 
1. Vælg den tekst, du har skrevet. Indstil skriftstørrelsen til 20 og fed skrift. 

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-title-executive-summary.png" alt-text="Skærmbillede af Power BI-rapporten i Power BI-tjenesten.":::

1. I ruden Visualiseringer skal du skifte **Baggrund** til **Fra**. 
1. Tilpas feltets størrelse, så den passer til én linje. 

### <a name="visual-2-profit-by-date"></a>Visualisering 2: Profit efter dato 

Nu kan du oprette et kurvediagram for at se, hvilken måned og hvilket år der gav den højeste avance. 

1. Fra ruden Felter skal du trække feltet **Avance** til et tomt område på rapportlærredet. Power BI viser som standard et søjlediagram med én kolonne, Avance. 
1. Træk feltet **Dato** til den samme visualisering. Power BI opdaterer kolonnediagrammet for at vise avancen efter de to år.

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-column-year.png" alt-text="Skærmbillede af Power BI-rapporten i Power BI-tjenesten.":::

1. I afsnittet **Felter** i ruden Visualiseringer skal du vælge rullelisten i værdien **Akse**. Skift **Dato** fra **Datohierarki** til **Dato**.

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-date-hierarchy.png" alt-text="Skærmbillede af Power BI-rapporten i Power BI-tjenesten.":::

    Power BI opdaterer kolonnediagrammet for at vise avancen for hver måned.

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-column-month.png" alt-text="Skærmbillede af Power BI-rapporten i Power BI-tjenesten.":::

1. I ruden Visualiseringer skal du ændre visualiseringstypen til **Kurvediagram**. 

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-profit-date-line-chart.png" alt-text="Skærmbillede af Power BI-rapporten i Power BI-tjenesten.":::

    Nu kan du nemt se, at avancen var størst i december 2014.

### <a name="visual-3-profit-by-country"></a>Visualisering 3: Profit efter land 

Opret et kort for at se, hvilket land der havde den højeste avance.

1. I ruden Felter skal du trække feltet **Land** til et tomt område på dit rapportlærred for at oprette et kort.
1. Træk feltet **Avance** til kortet.

    Power BI opretter en kortvisual med bobler, der repræsenterer avancen for hver af de enkelte placeringer. 

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-map-visual.png" alt-text="Skærmbillede af Power BI-rapporten i Power BI-tjenesten.":::

    Det lader til, at Europa klarer sig bedre end Nordamerika. 

### <a name="visual-4-sales-by-product-and-segment"></a>Visualisering 4: Salg efter produkt og segment 

Opret et liggende søjlediagram for at bestemme, hvilke virksomheder og segmenter der skal investeres i.

1. Træk de to diagrammer, du har oprettet, så de ligger side om side i den øverste halvdel af lærredet. Lad et område stå tomt i venstre side af lærredet. 
1. Vælg et tomt område i den nederste halvdel af rapportlærredet. 

1. I ruden Felter skal du markere felterne **Salg**, **Produkt** og **Segment**. 

    Power BI opretter automatisk et grupperet søjlediagram. 

1. Træk diagrammet, så det er bredt nok til at fylde pladsen under de to øverste diagrammer.

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-clustered-column-chart.png" alt-text="Skærmbillede af Power BI-rapporten i Power BI-tjenesten.":::

    Virksomheden skal tilsyneladende fortsætte med at investere i Paseo-produktet og fokusere på segmenterne Små virksomheder og Offentlige myndigheder.  

### <a name="visual-5-year-slicer"></a>Visualisering 5: Årsudsnit 

Udsnit er et værdifuldt værktøj til filtrering af visualiseringer på en rapportside til en bestemt markering. I dette tilfælde kan vi oprette et udsnit for at fokusere på resultaterne for hver måned og hvert år.  

1. I ruden Felter skal du vælge feltet **Dato** og trække det til det tomme område til venstre på lærredet. 
2. I ruden Visualiseringer skal du vælge **Udsnit**. 
3. I afsnittet Felter i ruden Visualiseringer skal du vælge rullelisten i **Felter**. Fjern Kvartal og Dag, så kun År og Måned er tilbage. 

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-date-hierarchy-trim.png" alt-text="Skærmbillede af Power BI-rapporten i Power BI-tjenesten.":::

4. Udvid hvert år, og tilpas størrelsen på visualiseringen, så alle måneder er synlige.

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-hierarchy-date-slicer.png" alt-text="Skærmbillede af Power BI-rapporten i Power BI-tjenesten.":::

Hvis din chef beder om kun at se data fra 2013, kan du bruge udsnittet til at skifte mellem år eller bestemte måneder i hvert år. 

### <a name="extra-credit-format-the-report"></a>Ekstra kredit: Formatér rapporten

Hvis du vil finpudse formateringen af denne rapport, kan du følge disse enkle trin. 

**Tema**

- På båndet **Visning** kan du ændre temaet til **Ledelse**.  

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-theme-executive.png" alt-text="Skærmbillede af Power BI-rapporten i Power BI-tjenesten."::: 

**Gør visualiseringen klar** 

Foretag følgende ændringer under fanen **Format** i ruden Visualiseringer.

:::image type="content" source="media/desktop-excel-stunning-report/power-bi-format-tab-visualizations.png" alt-text="Skærmbillede af Power BI-rapporten i Power BI-tjenesten." og **Tekststørrelse** til **16 pkt.** . Sæt **Skygge** på **Til**. 

1. Vælg visualisering 3. I afsnittet **Kortformater** skal du ændre **Tema** til **Gråtoneskala**. I afsnittet **Titel** skal du ændre titlen **Tekststørrelse** til **16 pkt.** . Sæt **Skygge** på **Til**.

1. Vælg visualisering 4. I afsnittet **Titel** skal du ændre titlen **Tekststørrelse** til **16 pkt.** . Sæt **Skygge** på **Til**.

1. Vælg visualisering 5. I afsnittet **Kontrolelementer til markering** skal du skifte **Vis indstillingen "Markér alle"** til **Til**. I afsnittet **Udsnitsoverskrift** skal du øge **Tekststørrelse** til **16 pkt.** . 

**Tilføj en baggrundsform til titlen**

1. På båndet **Indsæt** skal du vælge **Former** > **Rektangel**. Placer den øverst på siden, og stræk den, så den fylder bredden på siden og højden på overskriften. 
1. I ruden **Formatform** skal du i afsnittet **Linje** ændre **Gennemsigtighed** til **100 %** . 
1. I afsnittet **Fyld** skal du ændre **Fyldfarve** til **Temafarve 5 #6B91C9** (blå). 

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-theme-color-5.png" alt-text="Skærmbillede af Power BI-rapporten i Power BI-tjenesten.":::

1. På fanen **Format** skal du vælge **Send bagud** > **Placer bagest**. 
1. Vælg teksten i Visualisering 1, titlen, og skift skriftfarve til **Hvid**. 

**Tilføj en baggrundsform til visualisering 2 og 3**

1. På båndet **Indsæt** skal du vælge **Forme** > **Rektangel** og strække den til bredden og højden af visualisering 2 og 3. 
1. I ruden **Formatform** skal du i afsnittet **Linje** ændre **Gennemsigtighed** til **100 %** . 
1. På fanen **Format** skal du vælge **Send bagud** > **Placer bagest**. 

### <a name="finished-report"></a>Færdig rapport

Her kan du se, hvordan den endelige rapport kommer til at se ud:  

:::image type="content" source="media/desktop-excel-stunning-report/power-bi-excel-formatted-report.png" alt-text="Skærmbillede af Power BI-rapporten i Power BI-tjenesten.":::

For at opsummere besvarer denne rapport din chefs vigtigste spørgsmål: 

- Hvilken måned og hvilket år var avancen størst? 

    December 2014 

- I hvilket land har virksomheden størst succes? 

    I Europa, specifikt Frankrig og Tyskland. 

- Hvilket produkt og segment skal virksomheden fortsat at investere i? 

    Virksomheden skal fortsætte med at investere i Paseo-produktet og fokusere på segmenterne Små virksomheder og Offentlige myndigheder. 

## <a name="save-your-report"></a>Gem din rapport

- I menuen **Filer** skal du vælge **Gem**.

## <a name="publish-to-the-power-bi-service-to-share"></a>Publicer til Power BI-tjenesten for at dele 

Hvis du vil dele din rapport med din chef og dine kolleger, kan du publicere den på Power BI-tjenesten. Når du deler med kollegaer, der har en Power BI-konto, kan de interagere med din rapport, men de kan ikke gemme ændringerne. 

1. I Power BI Desktop skal du vælge **Publicer** på båndet **Start**. 

    Det er muligvis nødvendigt at logge på Power BI-tjenesten. Hvis du endnu ikke har en konto, kan du [tilmelde dig en gratis prøveversion](https://app.powerbi.com/signupredirect?pbi_source=web).

1. Vælg en destination, f. eks. **Mit arbejdsområde** i Power BI-tjenesten > **Vælg**.
1. Vælg **Åbn 'dit-filnavn' i Power BI**.

    :::image type="content" source="media/desktop-excel-stunning-report/open-power-bi.png" alt-text="Skærmbillede af Power BI-rapporten i Power BI-tjenesten.":::

    Din færdige rapport åbnes i browseren.

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-excel-report-service.png" alt-text="Skærmbillede af Power BI-rapporten i Power BI-tjenesten."::: 

1. Hvis du vil dele din rapport med andre, skal du vælge **Del** øverst i rapporten.

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-share-report.png" alt-text="Skærmbillede af Power BI-rapporten i Power BI-tjenesten.":::

## <a name="next-steps"></a>Næste trin

- [Selvstudium: Analysér salgsdata fra Excel og et OData-feed](../connect-data/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed.md)

Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/).
