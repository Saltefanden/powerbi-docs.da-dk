---
title: Tilføj understøttelse af bogmærker i Power BI-visualiseringer
description: Power BI-visualiseringer kan håndtere skift mellem bogmærker
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 06/18/2019
ms.openlocfilehash: aeea5ea3a9d1d2bd375c44b6c6b7eac57eb65aff
ms.sourcegitcommit: 6bc66f9c0fac132e004d096cfdcc191a04549683
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2020
ms.locfileid: "91748994"
---
# <a name="add-bookmark-support-for-power-bi-visuals"></a>Tilføj understøttelse af bogmærker i Power BI-visualiseringer

Med bogmærker i Power BI-rapporter kan du registrere en konfigureret visning af en rapportside med visualiseringens markeringstilstand og dens filtreringstilstand. Dette kræver dog yderligere handlinger i forbindelse med Power BI-visualiseringer for at understøtte bogmærket og reagere korrekt på ændringer.

Du kan finde flere oplysninger om bogmærker under [Brug bogmærker til at dele indsigt og oprette tekstenheder i Power BI](../../create-reports/desktop-bookmarks.md).

## <a name="report-bookmarks-support-in-your-visual"></a>Understøttelse af bogmærker i rapporter for din visualisering

Hvis din visualisering interagerer med andre visualiseringer, vælger datapunkter eller filtrerer andre visualiseringer, skal du gendanne tilstanden fra egenskaberne.

## <a name="add-report-bookmarks-support"></a>Tilføj understøttelse af bogmærker i rapporter

1. Installér (eller opdater) det krævede værktøj, [powerbi-visuals-utils-interactivityutils](https://github.com/Microsoft/PowerBI-visuals-utils-interactivityutils/), version 3.0.0 eller nyere. Det indeholder flere klasser til redigering af valg af tilstand eller filter. Det er påkrævet til visualiseringer med filtrering og alle visualiseringer, der bruger `InteractivityService`.

2. Opdater visualiseringens API til version 1.11.0 for at bruge `registerOnSelectCallback` i en forekomst af `SelectionManager`. Det er påkrævet til visualiseringer uden filtrering, der bruger den almindelige `SelectionManager` i stedet for `InteractivityService`.

### <a name="how-power-bi-visuals-interact-with-power-bi-in-report-bookmarks"></a>Sådan interagerer Power BI-visualiseringer med Power BI i bogmærker i rapporter

Lad os overveje følgende scenarie: du vil oprette flere bogmærker på rapportsiden med en anden markeringstilstand i hvert bogmærke.

Først vælger du et datapunkt i din visualisering. Visualiseringen interagerer med Power BI og andre visualiseringer ved at sende valgene til værten. Derefter vælger du **Tilføj** i ruden **Bogmærke**, og Power BI gemmer de aktuelle valg til det nye bogmærke.

Det sker gentagne gange, når du ændrer valget og tilføjer nye bogmærker. Når du har oprettet bogmærkerne, kan du skifte mellem dem.

Når du vælger et bogmærke, gendanner Power BI det gemte filter eller den gemte markeringstilstand, som sendes til visualiseringerne. Andre visualiseringer markeres eller filtreres i overensstemmelse med den tilstand, der er gemt i bogmærket. Power BI-værten er ansvarlig for handlingerne. Din visualisering er ansvarlig for at afspejle den nye markeringstilstand korrekt (f.eks. ændring af farverne på de gengivne datapunkter).

Den nye markeringstilstand kommunikeres til visualiseringen gennem metoden `update`. Argumentet `options` indeholder en særlig egenskab, `options.jsonFilters`. Det er egenskaben JSONFilter, der kan indeholde værdierne `Advanced Filter` og `Tuple Filter`.

Visualiseringen skal gendanne filterværdierne for at vise den tilsvarende tilstand for visualiseringen for det valgte bogmærke. Eller hvis visualiseringen kun bruger markeringer, kan du bruge den specielle metode `registerOnSelectCallback` i ISelectionManager, der er registreret til callback-funktionskald.

### <a name="visuals-with-selection"></a>Visualiseringer med markeringer

Hvis din visualisering interagerer med andre visualiseringer ved hjælp af [markering](https://github.com/Microsoft/PowerBI-visuals/blob/master/Tutorial/Selection.md), kan du tilføje bogmærker på en af to måder:

* Hvis visualiseringen ikke allerede har brugt [InteractivityService](https://github.com/microsoft/powerbi-visuals-utils-interactivityutils/blob/master/src/interactivityService.ts), kan du bruge metoden `FilterManager.restoreSelectionIds`.

* Hvis visualiseringen allerede administrerer markeringer ved hjælp af [InteractivityService](https://github.com/microsoft/powerbi-visuals-utils-interactivityutils/blob/master/src/interactivityService.ts), skal du bruge metoden `applySelectionFromFilter` til forekomsten `InteractivityService`.

#### <a name="use-iselectionmanagerregisteronselectcallback"></a>Brug ISelectionManager.registerOnSelectCallback

Når du vælger et bogmærke, kalder Power BI metoden `callback` for visualiseringen med de tilsvarende markeringer. 

```typescript
this.selectionManager.registerOnSelectCallback(
    (ids: ISelectionId[]) => {
        //called when a selection was set by Power BI
    });
);
```

Lad os antage, at du har et datapunkt i din visualisering, der blev oprettet i metoden [visualTransform](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/master/src/barChart.ts#L74).

Desuden ser `datapoints` således ud:

```typescript
visualDataPoints.push({
    category: categorical.categories[0].values[i],
    color: getCategoricalObjectValue<Fill>(categorical.categories[0], i, 'colorSelector', 'fill', defaultColor).solid.color,
    selectionId: host.createSelectionIdBuilder()
        .withCategory(categorical.categories[0], i)
        .createSelectionId(),
    selected: false
});
```

Du har nu `visualDataPoints` som dine datapunkter, og `ids`-matricen overføres til funktionen `callback`.

På dette tidspunkt skal visualiseringen sammenligne matricen i `ISelectionId[]` med markeringen i din `visualDataPoints`-matrix og angive de tilsvarende datapunkter som markeret.

```typescript
this.selectionManager.registerOnSelectCallback(
    (ids: ISelectionId[]) => {
        visualDataPoints.forEach(dataPoint => {
            ids.forEach(bookmarkSelection => {
                if (bookmarkSelection.equals(dataPoint.selectionId)) {
                    dataPoint.selected = true;
                }
            });
        });
    });
);
```

Når du har opdateret datapunkterne, afspejler de den aktuelle markeringstilstand, der er gemt i objektet `filter`. Når datapunkterne derefter gengives, vil markeringstilstanden for den brugerdefinerede visualisering stemme overens med tilstanden i bogmærket.

### <a name="use-interactivityservice-for-control-selections-in-the-visual"></a>Brug af InteractivityService til at styre markeringerne i en visualisering

Hvis din visualisering bruger `InteractivityService`, behøver du ikke yderligere handlinger for at understøtte bogmærkerne i din visualisering.

Når du vælger bogmærker, håndterer hjælpeværktøjet visualiseringens valgtilstand.

### <a name="visuals-with-a-filter"></a>Visualiseringer med filter

Lad os antage, at visualiseringen opretter et filter for data efter datoområde. Du har `startDate` og `endDate` som start- og slutdatoer for intervallet.

Visualiseringen opretter et avanceret filter og kalder værtsmetoden `applyJsonFilter` for at filtrere data efter de relevante betingelser.

Målet er den tabel, der bruges til filtrering.

```typescript
import { AdvancedFilter } from "powerbi-models";

const filter: IAdvancedFilter = new AdvancedFilter(
    target,
    "And",
    {
        operator: "GreaterThanOrEqual",
        value: startDate
            ? startDate.toJSON()
            : null
    },
    {
        operator: "LessThanOrEqual",
        value: endDate
            ? endDate.toJSON()
            : null
    });

this.host.applyJsonFilter(
    filter,
    "general",
    "filter",
    (startDate && endDate)
        ? FilterAction.merge
        : FilterAction.remove
);
```

Hver gang du vælger et bogmærke, modtager den brugerdefinerede visualisering et `update`-kald.

Den brugerdefinerede visualisering skal kontrollere filteret i objektet:

```typescript
const filter: IAdvancedFilter = FilterManager.restoreFilter(
    && options.jsonFilters
    && options.jsonFilters[0] as any
) as IAdvancedFilter;
```

Hvis `filter`-objektet ikke er null, skal visualiseringen gendanne filterbetingelserne fra objektet:

```typescript
const jsonFilters: AdvancedFilter = this.options.jsonFilters as AdvancedFilter[];

if (jsonFilters
    && jsonFilters[0]
    && jsonFilters[0].conditions
    && jsonFilters[0].conditions[0]
    && jsonFilters[0].conditions[1]
) {
    const startDate: Date = new Date(`${jsonFilters[0].conditions[0].value}`);
    const endDate: Date = new Date(`${jsonFilters[0].conditions[1].value}`);

    // apply restored conditions
} else {
    // apply default settings
}
```

Derefter skal den pågældende visualisering ændre sin interne tilstand, så den afspejler de aktuelle betingelser. Den interne tilstand indeholder datapunkterne og visualiseringsobjekterne (linjer, rektangler osv.).

> [!IMPORTANT]
> I scenariet med bogmærker i rapporter skal visualiseringen ikke kalde `applyJsonFilter` for at filtrere andre visualiseringer. De vil allerede blive filtreret af Power BI.

Visualiseringen Tidslinjeudsnitsværktøj skifter områdevælger, så den svarer til dataområderne.

Få mere at vide i [lageret med Tidslinjeudsnitsværktøj](https://github.com/Microsoft/powerbi-visuals-timeline/commit/606f1152f59f82b5b5a367ff3b117372d129e597?diff=unified#diff-b6ef9a9ac3a3225f8bd0de84bee0a0df).

### <a name="filter-the-state-to-save-visual-properties-in-bookmarks"></a>Filtrer tilstanden for at gemme egenskaber for en visualisering i bogmærker

Egenskaben `filterState` opretter en egenskab for en del af filtrering. En visualisering kan gemme flere forskellige værdier i bogmærker.

Hvis du vil gemme egenskabsværdien som en filtertilstand, skal du markere objektets egenskab som `"filterState": true` i filen *capabilities.json*.

Tidslinjeudsnitsværktøjet gemmer f.eks. egenskabsværdierne `Granularity` i et filter. Det gør det muligt at ændre den aktuelle granularitet, når du ændrer bogmærkerne.

Få mere at vide i [lageret med Tidslinjeudsnitsværktøj](https://github.com/microsoft/powerbi-visuals-timeline/commit/8b7d82dd23cd2bd71817f1bc5d1e1732347a185e#diff-290828b604cfa62f1cb310f2e90c52fdR334).