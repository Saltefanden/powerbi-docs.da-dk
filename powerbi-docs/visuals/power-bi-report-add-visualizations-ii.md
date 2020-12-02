---
title: Del 2, Føj visualiseringer til en rapport i Power BI
description: Del 2, Føj visualiseringer til en rapport i Power BI
author: mihart
ms.author: mihart
ms.reviewer: mihart
ms.service: powerbi
ms.subservice: pbi-visuals
ms.topic: how-to
ms.date: 05/06/2020
LocalizationGroup: Visualizations
ms.openlocfilehash: 6ddee012d01c64e0f35ac491d2b20ba362f2da90
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96412454"
---
# <a name="add-visuals-to-a-power-bi-report-part-2"></a>Føj visualiseringer til en Power BI-rapport (del 2)

[!INCLUDE[consumer-appliesto-nyyn](../includes/consumer-appliesto-nyyn.md)]    

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

I [Del 1](power-bi-report-add-visualizations-i.md) oprettede du en grundlæggende visualisering ved at markere afkrydsningsfelter ud for feltnavne.  I Del 2 lærer du, hvordan du bruger træk og slip samt benytter ruderne **Felter** og **Visualiseringer** til at oprette og redigere visualiseringer.


## <a name="create-a-new-visualization"></a>Opret en ny visualisering
I dette selvstudium gennemgår vi vores datasæt for detailhandelanalyse og opretter nogle få vigtige visualiseringer.

## <a name="prerequisites"></a>Forudsætninger

I dette selvstudium bruges [PBIX-filen med eksemplet på detailhandelsanalyse](https://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix).

1. Vælg **Fil** > **Åbn** på menulinjen i øverste venstre afsnit af Power BI Desktop
   
2. Find din kopi af **PBIX-filen med eksemplet Detailhandelsanalyse**

1. Åbn **PBIX-filen med eksemplet Detailhandelsanalyse** i rapportvisning ![ikon for skærmbillede af rapportvisning.](media/power-bi-visualization-kpi/power-bi-report-view.png).

1. Markér ![Skærmbillede af den gule fane.](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) for at tilføje en ny side.

## <a name="add-visualizations-to-the-report"></a>Tilføj visualiseringer i rapporten

Opret en visualisering ved at vælge et felt i ruden **Felter**. Den type visualisering, der oprettes, afhænger af den valgte felttype. Power BI bruger datatypen til at afgøre, hvilken visualisering der skal bruges til at vise resultaterne. Du kan ændre visualiseringen ved at vælge et andet ikon i ruden Visualiseringer. Husk, at det ikke er alle visualiseringer, som kan vise dine data. Geografiske data vises f.eks. ikke særligt godt i et tragtformet diagram eller et kurvediagram. 


### <a name="add-an-area-chart-that-looks-at-this-years-sales-compared-to-last-year"></a>Tilføj et områdediagram, som indeholder en oversigt over dette års salg sammenlignet med sidste år

1. I tabellen **Sales** skal du vælge **This Year Sales** > **Value** og **Last Year Sales**. Power BI opretter et søjlediagram.  Dette diagram er lidt interessant, og du vil gerne se mere. Hvordan ser salget ud pr. måned?  
   
   ![Skærmbillede med søjlediagram](media/power-bi-report-add-visualizations-ii/power-bi-start.png)

2. I tabellen Tid skal du trække **Regnskabsmåned** ind i området **Akse**.  
   ![Skærmbillede med søjlediagram og Regnskabsmåned som akse](media/power-bi-report-add-visualizations-ii/power-bi-fiscalmonth.png)

3. [Skift visualiseringen](power-bi-report-change-visualization-type.md) til et områdediagram.  Der er mange visualiseringstyper at vælge imellem. Se [beskrivelser af hver, tip til bedste praksis og selvstudier](power-bi-visualization-types-for-reports-and-q-and-a.md) for at få hjælp til at vælge, hvilken type du vil bruge. Vælg ikonet for områdediagram i ruden Visualiseringer ![ikon for områdediagram i ruden Visualiseringer](media/power-bi-report-add-visualizations-ii/power-bi-area-chart.png).

4. Sortér visualiseringen ved at vælge **Flere handlinger** (...) og vælge **Sortér efter** >  **Regnskabsmåned**.

5. [Tilpas størrelsen af visualiseringen](power-bi-visualization-move-and-resize.md) ved at vælge visualiseringen, tage fat i en af konturcirklerne og trække. Gør den bred nok, så rullepanelet fjernes, men lille nok, så der er plads nok til at tilføje endnu en visualisering.
   
   ![skærmbillede af visualisering som områdediagram](media/power-bi-report-add-visualizations-ii/pbi_part2_7b.png)
6. [Gem rapporten](../create-reports/service-report-save.md).

### <a name="add-a-map-visualization-that-looks-at-sales-by-location"></a>Tilføj en kortvisualisering med salg efter placering

1. I tabellen **Store** skal du vælge **Område**. Træk **Total Stores** ind i området Størrelse. Power BI genkender, at Område er en placering, og opretter en visualisering med et kort.  
   ![Områdediagram](media/power-bi-report-add-visualizations-ii/power-bi-map1.png)

2. Tilføj en forklaring.  Hvis du vil se dataene efter butiksnavn, skal du trække **Butik** > **Kæde** til området Forklaring.  
   ![rapportlærred med pil fra kæden på feltlisten til kæden i forklaringsbucket'en](media/power-bi-report-add-visualizations-ii/power-bi-chain.png)

> [!NOTE]
> Når du deler din rapport med en Power BI-kollega, kræves det, at I begge har individuelle Power BI Pro-licenser, eller at rapporten er gemt i en Premium-kapacitet. Se [deling af rapporter](../collaborate-share/service-share-reports.md).

## <a name="next-steps"></a>Næste trin
* Få mere at vide om [Visualiseringer i Power BI-rapporter](power-bi-report-visualizations.md).  
* Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)

