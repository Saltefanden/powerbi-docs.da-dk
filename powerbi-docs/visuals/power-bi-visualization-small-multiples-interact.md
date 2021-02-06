---
title: Arbejd med små multipla i Power BI (eksempelvisning)
description: I denne artikel forklares det, hvordan du interagerer med små multipla eller trellising.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: mihart
ms.service: powerbi
ms.subservice: pbi-visuals
ms.topic: how-to
ms.date: 02/05/2021
LocalizationGroup: Visualizations
ms.openlocfilehash: 6d700d4a4bb7453f7630c76c5a3f265ee022e02a
ms.sourcegitcommit: f17acb16018752c234db6bff1f51f5130be12c58
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/06/2021
ms.locfileid: "99617321"
---
# <a name="interact-with-small-multiples-in-power-bi-preview"></a>Arbejd med små multipla i Power BI (eksempelvisning)

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-desktop](../includes/yes-desktop.md)] [!INCLUDE [yes-service](../includes/yes-service.md)]

Små multipla eller trellising, opdeler en visualisering i flere forskellige versioner af sig selv. I denne artikel forklares det, hvordan du får mest muligt ud af interinteragere med dem.

:::image type="content" source="media/power-bi-visualization-small-multiples/small-mulitple-sales-category-region.png" alt-text="Skærmbillede af små multipla for kategori og område.":::

Vil du oprette små multipla? Se [Opret små multipla i Power bi (prøveversion)](power-bi-visualization-small-multiples.md).

## <a name="scroll-in-a-small-multiple"></a>Rul i et lille multiplum

Små multipla kan indeholde flere individuelle diagrammer, der kan være i gitteret. Hvis det er tilfældet, kan du rulle ned for at se de øvrige kategorier.

Hvis du har en kategori X-akse med mange kategorier, kan du også se et rullepanel for hver kopi af den pågældende akse. Hvis du ruller på aksen, flyttes de sammen. Hvis du bruger et rullehjul, skal du holde Skift nede for at rulle kategori-akserne.

## <a name="select-data-to-cross-highlight"></a>Vælg data for at fremhæve tværgående fremhævning

Du kan vælge forskellige datasæt ved at vælge forskellige dele af det visuelle element.

### <a name="select-data-points"></a>Vælg datapunkter

Peg på datapunktet på et multiplum for at få vist værktøjstippet i det pågældende multiplum. Du kan også se en vejledende linje på X-aksen for kurvediagrammer. Vælg datapunktet for at fremhæve andre visuelle elementer efter både akse værdien og den små-flere kategori, og nedton de andre multipla.

:::image type="content" source="media/power-bi-visualization-small-multiples/small-multiple-select-data-point.png" alt-text="Vælg et datapunkt i et lille multiplum.":::

### <a name="select-a-categorical-axis-value"></a>Vælg en værdi for kategoriakse

Vælg en kategorietiket for at fremhæve andre visuelle elementer efter den pågældende akseværdi.

:::image type="content" source="media/power-bi-visualization-small-multiples/small-multiple-select-category-axis.png" alt-text="Vælg en kategoriakse i et lille multiplum.":::

### <a name="select-a-title"></a>Vælg en titel

Vælg titlen på et multiplum for at fremhæve andre visuelle elementer efter kategorien i den pågældende underoverskrift.

:::image type="content" source="media/power-bi-visualization-small-multiples/small-multiple-select-title.png" alt-text="Vælg en titel i et lille multiplum.":::

### <a name="legend"></a>Forklaring

Vælg en forklarings kategori for at fremhæve andre visuelle elementer og tværgående fremhævning af andre multipla.

:::image type="content" source="media/power-bi-visualization-small-multiples/small-multiple-select-legend.png" alt-text="Vælg et element i forklaringen i et lille multiplum.":::


## <a name="sort"></a>Sort

Med den nye sorterings funktion kan du sortere flere aspekter af en visualisering på én gang. Sortér efter kategorien og også efter aksen i hver flere. 

:::image type="content" source="media/power-bi-visualization-small-multiples/small-multiple-sort.png" alt-text="Sortér de små multipla.":::

## <a name="next-steps"></a>Næste trin

[Opret små multipla i Power BI (eksempelvisning)](power-bi-visualization-small-multiples.md)
