---
title: Visualiseringsfilter-API'en i Power BI-visualiseringer i en integreret Power BI-analyse for at få bedre integreret BI-indsigt
description: I denne artikel gennemgås det, hvordan Power BI-visualiseringer kan filtrere andre visualiseringer. Aktivér bedre integreret BI-indsigt ved hjælp af Power BI-integreret analyse.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 06/18/2019
ms.openlocfilehash: c03c64c2835ff8bf0b0f1ad3bd555da94aaf3126
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 01/05/2021
ms.locfileid: "97888736"
---
# <a name="the-visual-filters-api-in-power-bi-visuals"></a>Visuelle filtres API i Power BI-visualiseringer

Visual Filters API gør det muligt at filtrere data i Power BI-visualiseringer. Den største forskel i forhold til andre markeringer er, at andre visualiseringer filtreres på en hvilken som helst måde, trods understøttelse af fremhævning i andre visualiseringer.

Hvis du vil aktivere filtrering for en visualisering, skal den indeholde objektet `filter` i kodeafsnittet `general` i *capabilities.json*.

```json
"objects": {
        "general": {
            "displayName": "General",
            "displayNameKey": "formattingGeneral",
            "properties": {
                "filter": {
                    "type": {
                        "filter": true
                    }
                }
            }
        }
    }
```

Visual Filters API-grænseflader er tilgængelige i pakken [powerbi-models](https://www.npmjs.com/package/powerbi-models). Pakken indeholder også klasser til oprettelse af filterforekomster.

```cmd
npm install powerbi-models --save
```

Hvis du bruger en ældre version af værktøjerne (før 3.x.x), skal du medtage `powerbi-models` i visualiseringspakken. Du kan finde flere oplysninger i den korte vejledning [Føj API til avanceret filtrering til den brugerdefinerede visualisering](https://github.com/Microsoft/powerbi-visuals-sampleslicer/blob/master/doc/AddingAdvancedFilterAPI.md).

Alle filtre udvider grænsefladen `IFilter` som vist i følgende kode:

```typescript
export interface IFilter {
    $schema: string;
    target: IFilterTarget;
}
```
Hvor:
* `target` er tabelkolonnen i datakilden.

## <a name="the-basic-filter-api"></a>API til grundlæggende filtrering

Den grundlæggende filtergrænseflade vises i følgende kode:

```typescript
export interface IBasicFilter extends IFilter {
    operator: BasicFilterOperators;
    values: (string | number | boolean)[];
}
```

Hvor:
* `operator` er en optælling med værdierne *In*, *NotIn* og *All*.
* `values` er værdier for betingelsen.

Eksempel på grundlæggende filtrering:

```typescript
let basicFilter = {
    target: {
        column: "Col1"
    },
    operator: "In",
    values: [1,2,3]
}
```

Filteret betyder "Giv mig alle rækker, hvor `col1` er lig med en af værdierne 1, 2 eller 3."

Den tilsvarende SQL er:

```sql
SELECT * FROM table WHERE col1 IN ( 1 , 2 , 3 )
```

Hvis du vil oprette et filter, kan du bruge BasicFilter-klassen i `powerbi-models`.

Hvis du bruger en ældre version af værktøjet, skal du hente en forekomst af modellerne i vinduesobjektet ved hjælp af `window['powerbi-models']` som vist i følgende kode:

```javascript
let categories: DataViewCategoricalColumn = this.dataView.categorical.categories[0];

let target: IFilterColumnTarget = {
    table: categories.source.queryName.substr(0, categories.source.queryName.indexOf('.')),
    column: categories.source.displayName
};

let values = [ 1, 2, 3 ];

let filter: IBasicFilter = new window['powerbi-models'].BasicFilter(target, "In", values);
```

En visualisering aktiverer filteret ved hjælp af metoden applyJsonFilter() på den værtsgrænseflade, som IVisualHost leverede til visualiseringen i konstruktøren.

```typescript
visualHost.applyJsonFilter(filter, "general", "filter", FilterAction.merge);
```

## <a name="the-advanced-filter-api"></a>API til avanceret filtrering

[API til avanceret filtrering](https://github.com/Microsoft/powerbi-models) muliggør komplekse forespørgsler for markering og filtrering af datapunkter på tværs af visualiseringer, som er baseret på flere kriterier (f.eks. *LessThan*, *Contains*, *Is* og *IsBlank*).

Filteret blev introduceret i API til visualiseringer 1.7.0.

API til avanceret filtrering kræver også `target` med et `table`- og `column`-navn. Men operatorerne for API til avanceret filtrering er *And* og *Or*. 

Derudover bruger filteret betingelser i stedet for værdier med grænsefladen:

```typescript
interface IAdvancedFilterCondition {
    value: (string | number | boolean);
    operator: AdvancedFilterConditionOperators;
}
```

Betingelsesoperatører for parametren `operator` er *None*, *LessThan*, *LessThanOrEqual*, *GreaterThan*, *GreaterThanOrEqual*, *Contains*, *DoesNotContain*, *StartsWith*, *DoesNotStartWith*, *Is*, *IsNot*, *IsBlank* og "IsNotBlank"`

```javascript
let categories: DataViewCategoricalColumn = this.dataView.categorical.categories[0];

let target: IFilterColumnTarget = {
    table: categories.source.queryName.substr(0, categories.source.queryName.indexOf('.')), // table
    column: categories.source.displayName // col1
};

let conditions: IAdvancedFilterCondition[] = [];

conditions.push({
    operator: "LessThan",
    value: 0
});

let filter: IAdvancedFilter = new window['powerbi-models'].AdvancedFilter(target, "And", conditions);

// invoke the filter
visualHost.applyJsonFilter(filter, "general", "filter", FilterAction.merge);
```

Den tilsvarende SQL er:

```sql
SELECT * FROM table WHERE col1 < 0;
```

Hvis du vil se hele eksempelkoden til brug af API til avanceret filtrering, skal du gå til [lageret med Sampleslicer-visualiseringer](https://github.com/Microsoft/powerbi-visuals-sampleslicer).

## <a name="the-tuple-filter-api-multi-column-filter"></a>API til tupelfilter (filter til flere kolonner)

API til tupelfilter blev introduceret i API til visualiseringer 2.3.0. Den ligner det grundlæggende API-filter, men gør det muligt at definere betingelser for flere kolonner og tabeller.

Filtergrænsefladen vises i følgende kode: 

```typescript
interface ITupleFilter extends IFilter {
    $schema: string;
    filterType: FilterType;
    operator: TupleFilterOperators;
    target: ITupleFilterTarget;
    values: TupleValueType[];
}
```

Hvor:
* `target` er en matrix af kolonner med tabelnavne:

    ```typescript
    declare type ITupleFilterTarget = IFilterTarget[];
    ```

  Filteret kan håndtere kolonner fra forskellige tabeller.

* `$schema` er https://powerbi.com/product/schema#tuple.

* `filterType` er *FilterType.Tuple*.

* `operator` tillader kun brug i operatoren *In*.

* `values` er en matrix af værditupler, og hver tupel repræsenterer én tilladt kombination af værdier for destinationskolonnen. 

```typescript
declare type TupleValueType = ITupleElementValue[];

interface ITupleElementValue {
    value: PrimitiveValueType
}
```

Komplet eksempel:

```typescript
let target: ITupleFilterTarget = [
    {
        table: "DataTable",
        column: "Team"
    },
    {
        table: "DataTable",
        column: "Value"
    }
];

let values = [
    [
        // the first column combination value (or the column tuple/vector value) that the filter will pass through
        {
            value: "Team1" // the value for the `Team` column of the `DataTable` table
        },
        {
            value: 5 // the value for the `Value` column of the `DataTable` table
        }
    ],
    [
        // the second column combination value (or the column tuple/vector value) that the filter will pass through
        {
            value: "Team2" // the value for `Team` column of `DataTable` table
        },
        {
            value: 6 // the value for `Value` column of `DataTable` table
        }
    ]
];

let filter: ITupleFilter = {
    $schema: "https://powerbi.com/product/schema#tuple",
    filterType: FilterType.Tuple,
    operator: "In",
    target: target,
    values: values
}

// invoke the filter
visualHost.applyJsonFilter(filter, "general", "filter", FilterAction.merge);
```

> [!IMPORTANT]
> Rækkefølgen af kolonnenavne og betingelsesværdier har betydning.

Den tilsvarende SQL er:

```sql
SELECT * FROM DataTable WHERE ( Team = "Team1" AND Value = 5 ) OR ( Team = "Team2" AND Value = 6 );
```  

## <a name="restore-the-json-filter-from-the-data-view"></a>Gendan JSON-filteret fra datavisningen

Fra og med API version 2.2.0 kan du gendanne JSON-filteret fra *VisualUpdateOptions* som vist i følgende kode:

```typescript
export interface VisualUpdateOptions extends extensibility.VisualUpdateOptions {
    viewport: IViewport;
    dataViews: DataView[];
    type: VisualUpdateType;
    viewMode?: ViewMode;
    editMode?: EditMode;
    operationKind?: VisualDataChangeOperationKind;
    jsonFilters?: IFilter[];
}
```

Når du skifter bogmærker, kalder Power BI `update`-metoden til visualiseringen, som får et tilsvarende `filter`-objekt. Du kan finde flere oplysninger i [Tilføj understøttelse af bogmærker til visualiseringer i Power BI](bookmarks-support.md).

### <a name="sample-json-filter"></a>Eksempel på JSON-filter

Følgende billede viser et eksempel på en JSON-filterkode:

![JSON-filterkode](media/filter-api/json-filter.png)

### <a name="clear-the-json-filter"></a>Ryd JSON-filtret

API til filtrering accepterer værdien `null` for filteret som *nulstil* eller *ryd*.

```typescript
// invoke the filter
visualHost.applyJsonFilter(null, "general", "filter", FilterAction.merge);
```
