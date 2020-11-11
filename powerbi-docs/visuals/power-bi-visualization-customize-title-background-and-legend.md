---
title: Introduktion til formatering af Power BI-visualiseringer
description: Tilpas visualiseringens titel, baggrund og forklaring
author: msftrien
ms.reviewer: mihart
featuredvideoid: IkJda4O7oGs
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 03/06/2020
ms.author: rien
LocalizationGroup: Visualizations
ms.openlocfilehash: 0d19d7366dce571e2d89ba5cbc6ffbe936ec50e2
ms.sourcegitcommit: 5ccab484cf3532ae3a16acd5fc954b7947bd543a
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 11/06/2020
ms.locfileid: "93410986"
---
# <a name="customize-visualization-titles-backgrounds-and-legends"></a>Tilpas visualiseringernes titler, baggrunde og forklaringer

[!INCLUDE[consumer-appliesto-nyyn](../includes/consumer-appliesto-nyyn.md)]    


I dette selvstudium lærer du, hvordan du kan tilpasse dine visualiseringer, på flere måder. Du har mange muligheder for at tilpasse dine visualiseringer. Den bedste måde, du kan lære om dem alle på, er at udforske ruden **Format** (vælg malerrulleikonet). I denne artikel kan du se, hvordan du tilpasser en visualiseringstitel, en forklaring og en baggrund samt tilføjer et tema.

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

    a. Vælg rullelisten, og vælg en farve fra **Temafarver** , **Seneste farver** eller **Brugerdefineret farve**.
    
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

1. Åbn rapportsiden **Overview** , og vælg diagrammet **Total Sales Variance by FiscalMonth and District Manager**.

1. Under fanen **Visualiseringer** skal du vælge malerrulleikonet for at åbne ruden Formatering.

1. Udvid indstillingerne under **Forklaring** :

    ![Skærmbillede af kortet Forklaring.](media/power-bi-visualization-customize-title-background-and-legend/power-bi-legends.png)

1. Flyt skyderen **Forklaring** til **Til**.

1. Flyt forklaringen til venstre side af visualiseringen.

1. Føj en titel til forklaringen ved at slå **Titel** **Til**.

1. Skriv *Manager* i feltet **Navn på forklaring**.

1. Vælg sort under **Farve**.

Gem de ændringer, du har foretaget, og gå til næste sektion.

Hvis du vil genindlæse alle ændringerne, skal du vælge **Vend tilbage til standard** nederst i tilpasningsruden **Forklaring**.

## <a name="customize-colors-using-a-theme"></a>Tilpas farver ved hjælp af et tema

Med rapporttemaer kan du anvende designændringer på hele rapporten, f.eks. bruge virksomhedsfarver, ændre ikonsæt eller anvende ny visualstandardformatering. Når du anvender et rapporttema, anvendes farver og formatering fra det valgte tema på alle visuals i rapporten.

Hvis du vil anvende et tema på din rapport, skal du vælge **Skift tema** fra menulinjen. Vælg et tema.  I rapporten nedenfor bruges temaet **Sollys**.

 
![Rapport med temaet Sollys med gule, orange og røde farver](media/power-bi-visualization-customize-title-background-and-legend/power-bi-theme.png)

## <a name="visualization-types-that-you-can-customize"></a>Visualiseringstyper, du kan tilpasse

Her er en liste over de visualiseringer og tilpasningsindstillinger, der er tilgængelige for de enkelte:

| Visualisering | Titel | Baggrund | Forklaring |
|:--- |:--- |:--- |:--- |
| Område | ja | ja |ja |
| Liggende søjle | ja | ja |ja |
| Kort | ja | ja |i/t |
| Kort med flere rækker | ja | ja | i/t |
| Kolonne | ja | ja | ja |
| Kombinationsdiagram | ja | ja | ja |
| Krans | ja | ja | ja |
| Kartogram | ja | ja | ja |
| Tragt | ja | ja | i/t |
| Måler | ja | ja | i/t |
| Nøgleinfluencer | ja | ja | i/t |
| KPI | ja | ja | i/t |
| Linje | ja | ja | ja |
| Kort | ja | ja | ja |
| Matrix | ja | ja | i/t |
| Cirkel | ja | ja | ja |
| Spørgsmål og svar | ja | ja | i/t |
| Punktdiagram | ja | ja | ja |
| Form | ja | ja | ja |
| Udsnit | ja | ja | i/t |
| Tabel | ja | ja | i/t |
| Tekstfelt | nej | ja | i/t |
| Træstruktur | ja | ja | ja |
| Vandfaldsdiagram | ja | ja | ja |

## <a name="next-steps"></a>Næste trin

- [Tilpas egenskaberne for X- og Y-aksen](power-bi-visualization-customize-x-axis-and-y-axis.md)

- [Introduktion til farveformatering og akseegenskaber](service-getting-started-with-color-formatting-and-axis-properties.md)

Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)


