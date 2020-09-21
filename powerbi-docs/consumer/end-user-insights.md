---
title: Kør og få vist indsigt på dashboardfelter
description: Find ud af, hvordan du som Power BI-slutbruger kan få indsigt i dine dashboardfelter.
author: mihart
ms.reviewer: mihart
featuredvideoid: et_MLSL2sA8
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 09/09/2020
ms.author: mihart
LocalizationGroup: Dashboards
ms.openlocfilehash: 21bccbd11f8d2060b648e22c8ed8aa9471c820f0
ms.sourcegitcommit: 002c140d0eae3137a137e9a855486af6c55ad957
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 09/10/2020
ms.locfileid: "89642552"
---
# <a name="view-data-insights-on-dashboard-tiles-with-power-bi"></a>Få vist dataindsigt på dashboardfelter med Power BI

[!INCLUDE[consumer-appliesto-yyny](../includes/consumer-appliesto-yyny.md)]

Hvert enkelt [visualiseringsfelt](end-user-tiles.md) på dashboardet er en indgang til at udforske data. Når du vælger et felt, åbnes en rapport, eller [Spørgsmål og svar åbnes](end-user-q-and-a.md), hvor du kan filtrere, sortere og fordybe dig i datasættet bag rapporten. Når du kører indsigt, udfører Power BI denne udforskning af data for dig.

![Ellipsemenuen, hvor Vis indsigter vises som en indstilling](./media/end-user-insights/power-bi-insight.png)

Kør indsigt for at generere interessante interaktive visualiseringer på baggrund af dine data. Indsigt kan køres på et bestemt dashboardfelt, og du kan tilmed køre indsigt for en indsigt.

Funktionen Quick Insights er baseret på et voksende [sæt avancerede analytiske algoritmer](end-user-insight-types.md), der er udviklet sammen med Microsoft Research, som vi vil fortsætte med at bruge for at gøre det muligt for flere personer at finde indsigter i deres data på nye og intuitive måder.

## <a name="run-insights-on-a-dashboard-tile"></a>Kør indsigt på et dashboardfelt
Når du kører indsigt på et dashboardfelt, søger Power BI kun i de data, der bruges til at oprette dette enkelte dashboardfelt. 

1. [Åbn et dashboard](end-user-dashboards.md).
2. Peg på et felt. vælg **Flere indstillinger** (...), og vælg **Vis indsigt**. 

    ![Skærmbillede med valg af ellipsemenuen, hvor der vises en rulleliste](./media/end-user-insights/power-bi-hover.png)


3. Feltet åbnes i [Fokustilstand](end-user-focus.md) med indsigtskortene vist langs højre.    
   
    ![Fokustilstand](./media/end-user-insights/power-bi-insights-tiles.png)    
4. Er der en indsigt, der vækker din interesse? Vælg indsigtskortet for at udforske mere. Den valgte indsigt vises til venstre, og nye indsigtskort, som udelukkende er baseret på dataene i den enkelte indsigt, vises til højre.    

 ## <a name="interact-with-the-insight-cards"></a>Interager med indsigtskortene
Når du har åbnet en indsigt, kan du fortsætte med at udforske.

   * Filtrer visualiseringen på lærredet.  Du kan få vist filtrene ved at vælge pilen i det øverste højre hjørne for at udvide ruden Filtre.

      ![Indsigt med menuen Filtre udvidet](./media/end-user-insights/power-bi-filter.png)
   
   * Kør indsigt på selve indsigtskortet. Dette kaldes ofte **relateret indsigt**. Vælg et indsigtskort for at aktivere det. Det flyttes til venstre side af rapportlærredet, og nye kort, som udelukkende er baseret på dataene i den enkelte indsigt, vises til højre.
   
      ![Relateret indsigt med menuen Filtre udvidet](./media/end-user-insights/power-bi-insights-card.png)
   
     
Vælg **Afslut Fokustilstand** i øverste venstre hjørne for at vende tilbage til din rapport.

## <a name="considerations-and-troubleshooting"></a>Overvejelser og fejlfinding
- **Vis indsigter** fungerer ikke med alle typer af dashboardfelter. Det er f.eks. ikke tilgængeligt for brugerdefinerede Power BI-visuals.<!--[Power BI visuals](end-user-custom-visuals.md)-->


## <a name="next-steps"></a>Næste trin

Kør indsigt på visualiseringer i rapporter [ved hjælp af funktionen Analysér](end-user-analyze-visuals.md)    
Få mere at vide om de [tilgængelige typer indsigter](end-user-insight-types.md)

