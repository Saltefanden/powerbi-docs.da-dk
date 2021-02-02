---
title: Introduktion til formatering af Power BI-visualiseringer
description: Tilpas titler, baggrunde, mærkater og signaturforklaringer i visualiseringer
author: mihart
ms.author: mihart
ms.reviewer: mihart
featuredvideoid: removed
ms.custom: video-OgjX-pFGgfM, video-RE4IY3L
ms.service: powerbi
ms.subservice: pbi-visuals
ms.topic: how-to
ms.date: 1/13/2021
LocalizationGroup: Visualizations
ms.openlocfilehash: 8cfba48839f4055c7d48bf01a475cf2804053239
ms.sourcegitcommit: 2e81649476d5cb97701f779267be59e393460097
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/02/2021
ms.locfileid: "99422323"
---
# <a name="customize-visualization-titles-backgrounds-labels-and-legends"></a>Tilpas titler, baggrunde, mærkater og signaturforklaringer i visualiseringer

[!INCLUDE[consumer-appliesto-nyyn](../includes/consumer-appliesto-nyyn.md)]

I dette selvstudium lærer du, hvordan du kan tilpasse dine visualiseringer, på flere måder. Du har mange muligheder for at tilpasse dine visualiseringer. Den bedste måde, du kan lære om dem alle på, er at udforske ruden **Format** (vælg malerrulleikonet). For at hjælpe dig i gang kan du i denne artikel se, hvordan du tilpasser en titel, en signaturforklaring, en baggrund, en mærkat og et lag samt tilføjer et tema i en visualisering.

Du kan ikke tilpasse alle visualiseringer. Se den [komplette liste](#visualization-types-that-you-can-customize) over visualiseringer for at få flere oplysninger.

## <a name="prerequisites"></a>Forudsætninger

- Power BI-tjenesten eller Power BI Desktop

- Rapporten Retail Analysis Sample

> [!NOTE]
> Når du deler din rapport med en Power BI-kollega, kræves det, at I begge har individuelle Power BI Pro-licenser, eller at rapporten er gemt i en Premium-kapacitet. Se [deling af rapporter](../collaborate-share/service-share-reports.md).

## <a name="customize-visualization-titles-in-reports"></a>Tilpas titler på visualiseringer i rapporter

Hvis du vil følge med, skal du logge på Power BI Desktop og åbne rapporten [Retail Analysis Sample](../create-reports/sample-datasets.md).

> [!NOTE]
> Når du fastgør en visualisering på et dashboard, bliver den til et dashboardfelt. Du kan også tilpasse selve felterne med [nye titler og undertitler, links og tilpasning af størrelsen](../create-reports/service-dashboard-edit-tile.md).

1. Gå til siden **New Stores** i rapporten **Retail Analysis Sample**.

1. Vælg det grupperede søjlediagram **Open Store Count by Open Month and Chain**.

1. I ruden **Visualiseringer** skal du vælge ikonet med malerrullen for at få vist formateringsindstillingerne.

1. Vælg **Titel** for at udvide den sektion.

   ![Skærmbillede af formateringsruden med malerrulleikonet fremhævet og en pil til rullelisten Titel.](media/power-bi-visualization-customize-title-background-and-legend/power-bi-format-menu.png)

1. Flyt skyderen **Titel** til **Til**.

1. Hvis du vil ændre titlen, skal du skrive **Store count by month opened** i feltet *Titeltekst*.

    ![Skærmbillede af ruden Format med titelteksten indtastet.](media/power-bi-visualization-customize-title-background-and-legend/power-bi-title.png)

1. Ret **Skriftfarve** til hvid og **Baggrundsfarve** til blå.

    a. Vælg rullelisten, og vælg en farve fra **Temafarver**, **Seneste farver** eller **Brugerdefineret farve**.

    ![Skærmbillede af indstillinger for skriftfarve og baggrundsfarve.](media/power-bi-visualization-customize-title-background-and-legend/power-bi-color.png)

    b. Vælg rullelisten for at lukke farvevinduet.

1. Øg tekststørrelsen til **16 pt**.

1. Den sidste tilpasning, du skal foretage af diagramtitlen, er at justere placeringen, så den står midt i visualiseringen.

    ![Skærmbillede af kontrolelementerne til justering med indstillingen Centrer valgt.](media/power-bi-visualization-customize-title-background-and-legend/power-bi-align.png)

    På dette tidspunkt i selvstudiet ser titlen på dit grupperede søjlediagram nogenlunde sådan ud:

    ![Skærmbillede af det grupperede søjlediagram, der netop er konfigureret.](media/power-bi-visualization-customize-title-background-and-legend/power-bi-table.png)

Gem de ændringer, du har foretaget, og gå til næste sektion.

Hvis du vil genindlæse alle ændringerne, skal du vælge **Vend tilbage til standard** nederst i tilpasningsruden **Titel**.

![Skærmbillede af indstillingen Vend tilbage til standard.](media/power-bi-visualization-customize-title-background-and-legend/power-bi-revert.png)

## <a name="customize-visualization-backgrounds"></a>Tilpas baggrunden i en visualisering

Udvid indstillingerne under **Baggrund** i det samme grupperede søjlediagram.

1. Flyt skyderen **Baggrund** til **Til**.

1. Vælg rullelisten, og vælg en grå farve.

1. Ret **Gennemsigtighed** til **74 %** .

På dette tidspunkt i selvstudiet ser baggrunden på dit grupperede søjlediagram nogenlunde sådan ud:

![Skærmbillede af grupperet søjlediagram med opdateret baggrundsfarve.](media/power-bi-visualization-customize-title-background-and-legend/power-bi-background.png)

Gem de ændringer, du har foretaget, og gå til næste sektion.

Hvis du vil genindlæse alle ændringerne, skal du vælge **Vend tilbage til standard** nederst i tilpasningsruden **Baggrund**.

## <a name="customize-visualization-legends"></a>Tilpas forklaringer i en visualisering

1. Åbn rapportsiden **Overview**, og vælg diagrammet **Total Sales Variance by FiscalMonth and District Manager**.

1. Under fanen **Visualiseringer** skal du vælge malerrulleikonet for at åbne ruden Formatering.

1. Udvid indstillingerne under **Forklaring**:

    ![Skærmbillede af kortet Forklaring.](media/power-bi-visualization-customize-title-background-and-legend/power-bi-legends.png)

1. Flyt skyderen **Forklaring** til **Til**.

1. Flyt forklaringen til venstre side af visualiseringen.

1. Føj en titel til forklaringen ved at slå **Titel** **Til**.

1. Skriv *Manager* i feltet **Navn på forklaring**.

1. Vælg sort under **Farve**.

Gem de ændringer, du har foretaget, og gå til næste sektion.

Hvis du vil genindlæse alle ændringerne, skal du vælge **Vend tilbage til standard** nederst i tilpasningsruden **Forklaring**.

## <a name="customize-total-labels-for-stacked-visuals"></a>Tilpas totalmærkater for stablede visualiseringer

Der kan vises datamærkater og totalmærkater i stablede visualiseringer. I et stablet søjlediagram identificerer datamærkater værdien for hver del af en søjle. Totalmærkater viser totalværdien for hele den samlede søjle. 

Se, hvordan Rien føjer totalmærkater til et stablet diagram, og følg derefter trinnene herunder for at prøve det selv.

> [!VIDEO https://www.youtube.com/embed/OgjX-pFGgfM]

1. Åbn rapportsiden **Oversigt**, og vælg det liggende søjlediagram **Gennemsnitlig størrelse af salgsområde efter kæde og butikstype**.

1. Under fanen **Visualisering** skal du vælge ![ikonet for det stablede liggende søjlediagram](media/power-bi-visualization-customize-title-background-and-legend/power-bi-stacked-bar.png) for at konvertere dette liggende søjlediagram til et stablet liggende søjlediagram. Bemærk, at visualiseringen bevarer sine datamærkater.

    ![Skærmbillede af det nye stablede liggende søjlediagram.](media/power-bi-visualization-customize-title-background-and-legend/power-bi-stacked-chart.png)

1. Under fanen **Visualiseringer** skal du vælge malerrulleikonet for at åbne ruden Formatering.

1. Flyt skyderen **Totalmærkater** til **Til**. 

    ![Skærmbillede, der viser skyderen Totalmærkater angivet som Til.](media/power-bi-visualization-customize-title-background-and-legend/power-bi-totals.png)

1. Alternativt kan du formatere totalmærkaterne. I dette eksempel har vi ændret farven til sort, øget skriftstørrelsen og valgt at vise værdierne som **tusinder**.

    ![Skærmbillede af det nye stablede liggende søjlediagram med totalmærkater.](media/power-bi-visualization-customize-title-background-and-legend/power-bi-bar-totals.png)

## <a name="customize-layer-order"></a>Tilpas rækkefølgen af lag

Skift rækkefølgen af lagene for visualiseringer og figurer i dine rapporter. Rækkefølgen af lag bestemmer, hvilke objekter der kommer forrest, når de vælges. Når du vælger et objekt på rapportlærredet, aktiveres det og flyttes til det øverste lag. I forbindelse med visualiseringer gør dette det lettere at interagere med den valgte visualisering. Men for figurer og baggrunde vil du måske gerne fastgøre dem til det nederste lag, så du ikke vælger dem ved et uheld og dækker eller skjuler visualiseringerne i dine rapporter. 

Kontrolelementer til lag er tilgængelige i Power BI-tjenesten, Power BI Desktop, Mobil og rapportserver. I denne artikel kan du se, hvordan du ændrer funktionsmåden for rækkefølgen af lag i Power BI-tjenesten.

Se, hvordan Rien ændrer funktionsmåden for rækkefølgen af lag, og følg derefter nedenstående trin, så du selv kan prøve det.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4IY3L]

1. Tilføj en ny rapportside ved at vælge det gule plustegn.

1. Føj en figur til lærredet. Her har vi tilføjet et blåt rektangel.

    ![Skærmbillede af den nye rapportside med et blåt rektangel.](media/power-bi-visualization-customize-title-background-and-legend/power-bi-shape.png)

1. Kopiér og indsæt en visualisering fra en anden side i rapporten.

    ![Skærmbillede af den nye rapportside med et blåt rektangel og et cirkeldiagram.](media/power-bi-visualization-customize-title-background-and-legend/power-bi-layer.png)

    Nu, hvor du har to lag, kan du prøve at vælge cirkeldiagrammet og derefter baggrunden. Når du vælger cirkeldiagrammet, aktiverer Power BI dette objekt og viser dets overskriftsmenu. Når du vælger rektanglet, aktiverer Power BI dette objekt og placerer det forrest, hvor det skjuler cirkeldiagrammet. Du kan ændre denne standardfunktionsmåde.

1. Vælg rektanglet, og åbn formateringsruden. Udvid **Generelt**, og find til/fra-knappen **Bevar rækkefølge af lag**. Gem rapportændringerne, og skift til læsevisning.

    ![Skærmbillede af den nye rapportside og Bevar rækkefølge af lag angivet til Til.](media/power-bi-visualization-customize-title-background-and-legend/power-bi-maintain-layer.png)

1. Når du vælger det blå rektangel i læsevisning, forbliver det på det bageste lag.

## <a name="customize-colors-using-a-theme"></a>Tilpas farver ved hjælp af et tema

Med rapporttemaer kan du anvende designændringer på hele rapporten, f.eks. bruge virksomhedsfarver, ændre ikonsæt eller anvende ny visualstandardformatering. Når du anvender et rapporttema, anvendes farver og formatering fra det valgte tema på alle visuals i rapporten.

Hvis du vil anvende et tema på din rapport, skal du vælge **Skift tema** fra menulinjen. Vælg et tema.  I rapporten nedenfor bruges temaet **Sollys**.

![Rapport med temaet Sollys med gule, orange og røde farver](media/power-bi-visualization-customize-title-background-and-legend/power-bi-theme.png)

## <a name="visualization-types-that-you-can-customize"></a>Visualiseringstyper, du kan tilpasse

Her er en liste over de visualiseringer og tilpasningsindstillinger, der er tilgængelige for de enkelte:

| Visualisering | Titel | Baggrund | Forklaring | Totalmærkater
|:--- |:--- |:--- |:--- |:--- |
| Område | ja | ja |ja | ja  |
| Liggende søjle | ja | ja |ja | ja |
| Kort | ja | ja |i/t | i/t |
| Kort med flere rækker | ja | ja | i/t | i/t |
| Kolonne | ja | ja | ja |  ja |
| Kombinationsdiagram | ja | ja | ja | ja |
| Krans | ja | ja | ja | i/t |
| Kartogram | ja | ja | ja |i/t |
| Tragt | ja | ja | i/t |i/t |
| Måler | ja | ja | i/t |i/t |
| Nøgleinfluencer | ja | ja | i/t |i/t |
| KPI | ja | ja | i/t |i/t |
| Linje | ja | ja | ja |i/t |
| Kort | ja | ja | ja |i/t |
| Matrix | ja | ja | i/t |ja |
| Cirkel | ja | ja | ja |i/t |
| Spørgsmål og svar | ja | ja | i/t |i/t |
| Punktdiagram | ja | ja | ja |i/t |
| Form | ja | ja | ja |i/t |
| Udsnit | ja | ja | i/t |i/t |
| Tabel | ja | ja | i/t |ja |
| Tekstfelt | nej | ja | i/t |i/t |
| Træstruktur | ja | ja | ja |i/t |
| Vandfaldsdiagram | ja | ja | ja |i/t |

## <a name="next-steps"></a>Næste trin

- [Tilpas egenskaberne for X- og Y-aksen](power-bi-visualization-customize-x-axis-and-y-axis.md)

- [Introduktion til farveformatering og akseegenskaber](service-getting-started-with-color-formatting-and-axis-properties.md)

Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
