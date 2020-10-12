---
title: Kurvediagrammer i Power BI
description: Kurvediagrammer i Power BI
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/05/2020
ms.author: rien
LocalizationGroup: Visualizations
ms.openlocfilehash: 59cede1cae716661be8d3796330bde7da44170eb
ms.sourcegitcommit: be424c5b9659c96fc40bfbfbf04332b739063f9c
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 10/01/2020
ms.locfileid: "91634590"
---
# <a name="line-charts-in-power-bi"></a>Kurvediagrammer i Power BI

[!INCLUDE[consumer-appliesto-nyyn](../includes/consumer-appliesto-nyyn.md)]

Et kurvediagram er en række datapunkter, der er repræsenteret af prikker og forbundet med lige linjer. Et kurvediagram kan have en eller flere linjer. Kurvediagrammer har en X- og en Y-akse. 

![simpelt kurvediagram](media/power-bi-line-charts/power-bi-line.png)



## <a name="create-a-line-chart"></a>Opret et kurvediagram
I denne vejledning bruges appen Sales and Marketing Sample til at oprette et kurvediagram, der viser dette års salg efter kategori. Hvis du vil følge med, skal du hente eksempelappen fra appsource.com.

> [!NOTE]
> Når du deler din rapport med en Power BI-kollega, kræves det, at I begge har individuelle Power BI Pro-licenser, eller at rapporten er gemt i en Premium-kapacitet.

1. Start på en tom rapportside. Hvis du bruger Power BI-tjenesten, skal du åbne rapporten i [redigeringsvisning](../create-reports/service-interact-with-a-report-in-editing-view.md).

2. Vælg **Salgsfakta** \> **Enheder i alt** i ruden Felter, og vælg **Dato** > **Måned**.  Power BI opretter et søjlediagram på dit rapportlærred.

    ![Vælg i ruden Felter](media/power-bi-line-charts/power-bi-step1.png)

4. Konvertér til et kurvediagram ved at vælge skabelonen for kurvediagrammer i ruden Visualiseringer. 

    ![konvertér til kurvediagram](media/power-bi-line-charts/power-bi-convert-to-line.png)
   

4. Filtrer dit kurvediagram, så det viser data for årene 2012-2014. Hvis filtreringsruden er skjult, skal du udvide den nu. I ruden Felter skal du vælge **Dato** \> **År** og trække det til ruden Filtre. Slip det under overskriften **Filters on this visual**. 
     
    ![linje ud for ruden Felter](media/power-bi-line-charts/power-bi-year-filter.png)

    Skift **Advanced filters** til **Basic filters**, og vælg **2012**, **2013** og **2014**.

    ![Filtrer efter år](media/power-bi-line-charts/power-bi-filter-year.png)

6. Du kan eventuelt [tilpasse størrelsen og farven på diagrammets tekst](power-bi-visualization-customize-title-background-and-legend.md). 

    ![Øg skriftstørrelsen, og skift skrifttypen for Y-aksen](media/power-bi-line-charts/power-bi-line-3years.png)

## <a name="add-additional-lines-to-the-chart"></a>Tilføj flere kurver i diagrammet
Kurvediagrammer kan have mange forskellige kurver. Og i nogle tilfælde kan værdierne på kurverne være så divergerende, at det ikke er godt at vise dem sammen. Lad os se på, hvordan vi tilføjer ekstra kurver i vores nuværende diagram, og lær, hvordan du formaterer diagrammet, når de værdier, der er repræsenteret af kurverne, er meget forskellige. 

### <a name="add-additional-lines"></a>Tilføj flere kurver
I stedet for at kigge på enheder i alt for alle områder som en enkelt kurve i diagrammet kan vi opdele enheder i alt efter område. Tilføj flere kurver ved at trække **Geo** > **Region** til området med forklaring.

   ![Én kurve for hvert område](media/power-bi-line-charts/power-bi-line-regions.png)


### <a name="use-two-y-axes"></a>Brug to Y-akser
Hvad nu, hvis du vil se nærmere på det samlede salg og enheder i alt i det samme diagram? Salgstal er meget højere end antal enheder, så kurvediagrammet bliver ubrugeligt. Faktisk ser den røde kurve for enheder i alt ud til at være nul.

   ![Skærmbillede, der viser, hvordan brug af en enkelt y-akse viser det samlede antal enheder som en grundlæggende flad og ubrugelig sammenligning med salgstallene.](media/power-bi-line-charts/power-bi-diverging.png)

Hvis du vil have vist meget divergerende værdier i ét diagram, kan du bruge et kombinationsdiagram. Du kan få mere at vide om kombinationsdiagrammer ved at læse [Kombinationsdiagrammer i Power BI](power-bi-visualization-combo-chart.md). I eksemplet nedenfor kan vi få vist salg og enheder i alt sammen i ét diagram ved at tilføje endnu en Y-akse. 

   ![Skærmbillede, der viser salgsværdierne som et liggende søjlediagram med y-aksen til venstre og det samlede antal enheder som en kurve med y-aksen til højre.](media/power-bi-line-charts/power-bi-dual-axes.png)

## <a name="highlighting-and-cross-filtering"></a>Fremhævning og krydsfiltrering
Du kan få mere at vide om brug af ruden Filters under [Føj et filter til en rapport](../create-reports/power-bi-report-add-filter.md).

Hvis vi vælger et datapunkt i et kurvediagram, fører det til tværgående fremhævning og krydsfiltrering af andre visualiseringer på rapportsiden... og omvendt. Hvis du vil følge med, skal du åbne fanen **Markedsandel**.  

I et kurvediagram er et enkelt datapunkt skæringspunktet for et punkt på X- og Y-aksen. Når du vælger et datapunkt, tilføjer Power BI mærker, der angiver, hvilket punkt (for en enkelt kurve) eller hvilke punkter (hvis der er to eller flere kurver) der er kilden til den tværgående fremhævning og krydsfiltrering af de andre visualiseringer på rapportsiden. Hvis din visualisering er meget tæt, vælger Power BI det punkt, der er nærmest i forhold til, hvor du klikker på visualiseringen.

I dette eksempel har vi valgt et datapunkt, der omfatter: July 2014, %Units Market Share R12 på 33.16 og %Units Market Share på 34.74.

![vælg et enkelt datapunkt i et kurvediagram](media/power-bi-line-charts/power-bi-single-select.png)

Bemærk, hvordan søjlediagrammet fremhæves på tværs, og hvordan måleren er krydsfiltreret.

Hvis du vil administrere, hvordan diagrammer krydsfremhæver og krydsfiltrerer hinanden, skal du se [Interaktioner mellem visualiseringer i en Power BI-rapport](../create-reports/service-reports-visual-interactions.md)

## <a name="considerations-and-troubleshooting"></a>Overvejelser og fejlfinding
* Et kurvediagram kan ikke have to Y-akser.  Du skal i stedet bruge et kombinationsdiagram.
* I ovenstående eksempler blev diagrammerne formateret til at øge skriftstørrelsen, ændre skriftfarven, tilføje aksetitler, centrere diagramtitel og forklaring, starte begge akser på nul og meget mere. Formateringsruden (ikonet med malerrullen) indeholder et uendeligt antal indstillinger, du kan bruge til at få dine diagrammer til at se ud, som du ønsker det. Den bedste måde, du kan lære det på, er at åbne formateringsruden og udforske dem.

## <a name="next-steps"></a>Næste trin

[Visualiseringstyper i Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)





