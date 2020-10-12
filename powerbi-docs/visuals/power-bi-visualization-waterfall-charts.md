---
title: Vandfaldsdiagrammer i Power BI
description: Vandfaldsdiagrammer i Power BI
author: mihart
ms.reviewer: ''
featuredvideoid: maTzOJSRB3g
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 12/5/2019
ms.author: rien
LocalizationGroup: Visualizations
ms.openlocfilehash: 148fe66039cb273d4ee20521762d5720252c7492
ms.sourcegitcommit: be424c5b9659c96fc40bfbfbf04332b739063f9c
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 10/01/2020
ms.locfileid: "91635717"
---
# <a name="waterfall-charts-in-power-bi"></a>Vandfaldsdiagrammer i Power BI

[!INCLUDE[consumer-appliesto-nyyn](../includes/consumer-appliesto-nyyn.md)]

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

Vandfaldsdiagrammer viser en løbende total, efterhånden som Power BI lægger værdier til eller trækker dem fra. Det er nyttigt at forstå dem for at se, hvordan en indledende værdi (f.eks. årets resultat) påvirkes af en række positive og negative ændringer.

Kolonnerne er farvekodet, så du hurtigt kan se stigninger og fald. Kolonnerne med den indledende og endelige værdi [starter ofte på den vandrette akse](https://support.office.com/article/Create-a-waterfall-chart-in-Office-2016-for-Windows-8de1ece4-ff21-4d37-acd7-546f5527f185#BKMK_Float "start på den vandrette akse"), mens de mellemliggende værdier er flydende kolonner. Vandfaldsdiagrammer kaldes også brodiagrammer på grund af deres format.

## <a name="when-to-use-a-waterfall-chart"></a>Hvornår skal du bruge et vandfaldsdiagram?

Vandfaldsdiagrammer er et godt valg:

* Når der er ændringer af målingen på tværs af tid, en serie eller forskellige kategorier.

* Til overvågning af overordnede ændringer, der bidrager til den samlede værdi.

* Til afbildning af virksomhedens årsresultatet ved at vise flere omsætningskilder og opnå det samlede resultat.

* Til illustration af antal medarbejdere ved årets start og slutning.

* Til visualisering af, hvor mange penge du tjener og bruger hver måned, samt den løbende kontosaldo.

## <a name="prerequisite"></a>Forudsætning

I dette selvstudium bruges [PBIX-filen med eksemplet Detailhandelsanalyse](https://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix).

1. Vælg **Fil** > **Åbn** i øverste venstre afsnit af menulinjen
   
2. Find din kopi af **PBIX-filen med eksemplet Detailhandelsanalyse**

1. Åbn **PBIX-filen med eksemplet Detailhandelsanalyse** i rapportvisning ![ikon for skærmbillede af rapportvisning.](media/power-bi-visualization-kpi/power-bi-report-view.png).

1. Markér ![Skærmbillede af den gule fane.](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) for at tilføje en ny side.

> [!NOTE]
> Når du deler din rapport med en Power BI-kollega, kræves det, at I begge har individuelle Power BI Pro-licenser, eller at rapporten er gemt i en Premium-kapacitet.    

## <a name="create-a-waterfall-chart"></a>Opret et vandfaldsdiagram

Du opretter et vandfaldsdiagram, der viser afvigelsen i salg (anslået salg i forhold til faktisk salg) pr. måned.

### <a name="build-the-waterfall-chart"></a>Byg vandfaldsdiagrammet

1. I ruden **Felter** skal du markere **Sales** > **Total Sales Variance**.

   ![Skærmbillede af Salg > Varians for samlet salg og den visualisering, der oprettes.](media/power-bi-visualization-waterfall-charts/power-bi-bar.png)

1. Vælg ikonet for vandfaldsdiagram ![Skærmbillede af ikonet for vandfaldsdiagram](media/power-bi-visualization-waterfall-charts/power-bi-waterfall-icon.png)

    ![Visualiseringsskabeloner](media/power-bi-visualization-waterfall-charts/convert-waterfall.png)

1. Vælg **Time** > **FiscalMonths** for at føje det til området **Category**.

    ![Vandfaldsdiagram](media/power-bi-visualization-waterfall-charts/power-bi-waterfall-month.png)

### <a name="sort-the-waterfall-chart"></a>Sortér vandfaldsdiagrammet

1. Kontrollér, at Power BI har sorteret vandfaldsdiagrammet kronologisk efter måned. Vælg **Flere indstillinger** (...) i øverste højre hjørne af diagrammet.

    I dette eksempel skal du vælge **Sortér efter** og **FiscalMonth**. En gul indikator ud for dit valg angiver, hvornår valgindstillingen anvendes.

    ![Vælg Sortér efter > FiscalMonth](media/power-bi-visualization-waterfall-charts/power-bi-sort-by-fiscalmonth.png)
    
    Hvis du vil have vist måneder i kronologisk rækkefølge, skal du vælge **Sortér stigende**. Kontrollér, som i det foregående trin, at der er en gul indikator til venstre for **Sortér stigende**. Dette angiver, at din valgte indstilling anvendes.

    ![Vælg Sortér efter > Stigende rækkefølge](media/power-bi-visualization-waterfall-charts/power-bi-waterfall-ascending.png)

    

    Bemærk, at dit diagram er sorteret fra januar til august for FiscalMonth.  

### <a name="explore-the-waterfall-chart"></a>Udforsk vandfaldsdiagrammet

Se lidt nærmere på, hvad der bidrager mest til ændringerne måned for måned.

1.  Vælg **Butik** > **Distrikt**, hvorved **Distrikt** føjes til bucket'en **Opdeling**.

    ![Skærmbillede, der viser tilføjelse af Distrikt til området Opdeling.](media/power-bi-visualization-waterfall-charts/power-bi-waterfall-breakdown.png)

    Power BI bruger værdien i **Opdeling** til at føje yderligere data til visualiseringen. De fem største bidragydere føjes til stigninger eller fald for hver regnskabsmåned. Det betyder f. eks., at der nu er seks datapunkter i stedet for kun én i februar.  

    ![Viser Store i bucket'en Opdeling](media/power-bi-visualization-waterfall-charts/power-bi-waterfall-breakdown-default.png)

    Lad os antage, at du kun er interesseret i de to største bidragydere.

1. I ruden **Formatér** skal du vælge **Breakdown** og angive **Maks. opdelinger** til **2**.

    ![Formatér > Opdeling](media/power-bi-visualization-waterfall-charts/power-bi-waterfall-breakdown-two.png)

    En hurtig gennemgang viser, at områderne Ohio og Pennsylvania er de største bidragydere til bevægelser, både negative og positive, i vandfaldsdiagrammet.

    ![vandfaldsdiagram](media/power-bi-visualization-waterfall-charts/power-bi-axis-waterfall.png)

## <a name="next-steps"></a>Næste trin

* [Rediger, hvordan visualiseringer interagerer i en Power BI-rapport](../create-reports/service-reports-visual-interactions.md)

* [Visualiseringstyper i Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)

