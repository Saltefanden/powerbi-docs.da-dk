---
title: Føj farver til dine Power BI-visualiseringer i en integreret Power BI-analyse for at få bedre integreret BI-indsigt
description: I denne artikel beskrives det, hvordan du kan føje farver til dine Power BI-visualiseringer, og hvordan du håndterer datapunkter for en visualisering med farve. Aktivér bedre integreret BI-indsigt ved hjælp af Power BI-integreret analyse.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 03/27/2020
ms.openlocfilehash: e6b6fb1dbc1397b93ac12692c8610e6f36d0b8bf
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 01/05/2021
ms.locfileid: "97887977"
---
# <a name="add-colors-to-your-power-bi-visuals"></a>Føj farver til dine Power BI-visualiseringer

I denne artikel beskrives det, hvordan du kan føje farver til dine visualiseringer, og hvordan du håndterer datapunkter for en visualisering med farve.

`IVisualHost` fremviser farve som en af dens tjenester.
Kodeeksemplet i denne artikel ændrer [SampleBarChart-visualiseringen](https://github.com/microsoft/PowerBI-visuals-sampleBarChart).
Se [barChart.ts](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/master/src/barChart.ts) for at få kildekoden.

Se [Udvikling af en Power BI-cirkelkortvisualisering](develop-circle-card.md) for at komme i gang med at oprette visualiseringer.

## <a name="add-color-to-data-points"></a>Føj farve til datapunkter

Hvert datapunkt repræsenteres af en forskellig farve.
Føj farven til `BarChartDataPoint`-grænsefladen som i følgende eksempel:

```typescript
/**
 * Interface for BarChart data points.
 *
 * @interface
 * @property {number} value    - Data value for point.
 * @property {string} category - Corresponding category of data value.
 * @property {string} color    - Color corresponding to data point.
 */
interface BarChartDataPoint {
    value: number;
    category: string;
    color: string;
};
```

## <a name="use-the-color-palette-service"></a>Brug farvepalettjenesten

Tjenesten `colorPalette` administrerer de farver, der bruges i visualiseringen.
En forekomst af tjenesten er tilgængelig på `IVisualHost`.

Definer den i metoden `update`.

```typescript
constructor(options: VisualConstructorOptions) {
        this.host = options.host; // host: IVisualHost
        ...
    }

public update(options: VisualUpdateOptions) {

    let colorPalette: IColorPalette = host.colorPalette;
    ...
}
```

## <a name="assigning-color-to-data-points"></a>Tildeling af farve til datapunkter

Derefter skal du angive `dataPoints`.
I dette eksempel indeholder hver af `dataPoints` værdi, kategori og farve.
`dataPoints` kan også indeholde andre egenskaber.

Metoden `visualTransform` indkapsler beregningen `dataPoints` i `SampleBarChart`.
Metoden er en del af visningsmodellen for søjlediagrammet.
Eftersom metoden gentages gennem beregningen `dataPoints` i `visualTransform`, er det det ideelle sted at tildele farver som vist i følgende kode:

```typescript

public update(options: VisualUpdateOptions) {
    ....
    let viewModel: BarChartViewModel = visualTransform(options, this.host);
    ....
}

function visualTransform(options: VisualUpdateOptions, host: IVisualHost): BarChartViewModel {
    let colorPalette: IColorPalette = host.colorPalette; // host: IVisualHost
    for (let i = 0, len = Math.max(category.values.length, dataValue.values.length); i < len; i++) {
        barChartDataPoints.push({
            category: category.values[i],
            value: dataValue.values[i],
            color: colorPalette.getColor(category.values[i]).value,
        });
    }
}
```

Anvend derefter data fra `dataPoints` på [d3-markeringen](https://d3js.org/) `barSelection` inden for metoden `update`:

```typescript
// This code is actual for d3 v5
// in d3 v5 for this case we should use merge() after enter() and apply changes on barSelectionMerged
this.barSelection = this.barContainer
    .selectAll('.bar')
    .data(this.barDataPoints);

const barSelectionMerged = this.barSelection
    .enter()
    .append('rect')
    .merge(<any>this.barSelection);

barSelectionMerged.classed('bar', true);

barSelectionMerged
.attr("width", xScale.bandwidth())
.attr("height", d => height - yScale(<number>d.value))
.attr("y", d => yScale(<number>d.value))
.attr("x", d => xScale(d.category))
.style("fill", (dataPoint: BarChartDataPoint) => dataPoint.color)
.style("stroke", (dataPoint: BarChartDataPoint) => dataPoint.strokeColor)
.style("stroke-width", (dataPoint: BarChartDataPoint) => `${dataPoint.strokeWidth}px`);

this.barSelection
    .exit()
    .remove();
```

## <a name="next-steps"></a>Næste trin

Du kan finde flere oplysninger i [Egenskaber for Power BI-visualiseringer](capabilities.md).

Du kan få mere at vide om, hvordan du udvikler Power BI-visualiseringer, i [Sådan foretager du fejlfinding af Power BI-visualiseringer](visuals-how-to-debug.md) og [Fejlfinding af Power BI-visualiseringer](power-bi-custom-visuals-troubleshoot.md).
