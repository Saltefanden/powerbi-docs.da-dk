---
title: Hent flere data fra Power BI i en integreret Power BI-analyse for at få bedre integreret BI-indsigt
description: I denne artikel gennemgås det, hvordan segmenteret hentning af store datasæt for Power BI-visualiseringer aktiveres. Aktivér bedre integreret BI-indsigt ved hjælp af Power BI-integreret analyse.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 12/13/2020
ms.openlocfilehash: 345efe91be1af5ee61d713c576f04657b182ad47
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 01/05/2021
ms.locfileid: "97886298"
---
# <a name="fetch-more-data-from-power-bi"></a>Hent flere data fra Power BI

API'en for `fetchMoreData` gør det muligt for Power BI-visualiseringer at omgå den hårde grænse på datavisning af 30.000 rækker. Med den nye 3.4 API-version udvides funktionaliteten af API'en for `fetchMoreData` til at understøtte en ny tilgang til indlæsning af datasegmenter. Ud over den eksisterende tilgang, der samler alle de anmodede segmenter, understøtter API'en kun indlæsning af trinvise datasegmenter.

Den nye tilgang giver større fleksibilitet i den måde, som yderligere datasegmenter indlæses i visualiseringen på. Hvis du vil forbedre ydeevnen, kan du konfigurere segmentstørrelsen, så den passer til din use case.

## <a name="limitations-of-fetchmoredata"></a>Begrænsninger i fetchMoreData

* Vinduesstørrelsen er begrænset til et interval på 2 til 30.000.
* Det samlede antal rækker i datavisning er begrænset til 1.048.576 rækker.
* I segmentsammenlægningstilstand er hukommelsesstørrelsen for datavisning begrænset til 100 MB.

## <a name="enable-a-segmented-fetch-of-large-datasets"></a>Aktivér en segmenteret hentning af store datasæt

I segmenteringstilstanden `dataview` skal du definere en vinduesstørrelse for `dataReductionAlgorithm` i visualiseringens  *capabilities.json*-fil for den påkrævede `dataViewMapping`. `count` fastsætter størrelsen af vinduet, hvilket begrænser antallet af nye datarækker, der kan føjes til `dataview` ved hver opdatering.

Tilføj følgende kode i filen *capabilities.json*:

```typescript
"dataViewMappings": [
    {
        "table": {
            "rows": {
                "for": {
                    "in": "values"
                },
                "dataReductionAlgorithm": {
                    "window": {
                        "count": 100
                    }
                }
            }
    }
]
```

Nye segmenter føjes til den eksisterende `dataview` og leveres til visualiseringen som et `update`-kald.

## <a name="usage-in-the-power-bi-visual"></a>Brug i visualiseringer i Power BI

I Power BI kan du bruge `fetchMoreData` i segmentaggregeringstilstand, der er standard, eller i tilstanden med trinvise opdateringer. 

### <a name="using-segments-aggregation-mode-default"></a>Brug af segmentaggregeringstilstand (standard)

I denne tilstand indeholder den datavisning, der er angivet til visualiseringen, de akkumulerede data for alle de forrige `fetchMoreData requests`. Derfor forventes datavisningens størrelse at vokse med hver opdatering. Hvis der f. eks. forventes i alt 100.000 rækker, og vinduets størrelse er angivet til 10.000, skal den første opdateringsdatavisning indeholde 10.000 rækker, den anden opdateringsdatavisning skal inkludere 20.000 rækker osv.

Du vælger denne tilstand ved at kalde `fetchMoreData` med `aggregateSegments = true`.

Du kan se, om dataene findes, ved at kontrollere, om `dataView.metadata.segment` findes:

```typescript
    public update(options: VisualUpdateOptions) {
        const dataView = options.dataViews[0];
        console.log(dataView.metadata.segment);
        // output: __proto__: Object
    }
```

Du kan også se, om det er den første eller en efterfølgende opdatering, ved at kontrollere `options.operationKind`. I følgende kode refererer `VisualDataChangeOperationKind.Create` til det første segment, mens `VisualDataChangeOperationKind.Append` refererer til efterfølgende segmenter.

Se følgende kodestykke for at se et eksempel på implementering:

```typescript
// CV update implementation
public update(options: VisualUpdateOptions) {
    // indicates this is the first segment of new data.
    if (options.operationKind == VisualDataChangeOperationKind.Create) {

    }

    // on second or subsequent segments:
    if (options.operationKind == VisualDataChangeOperationKind.Append) {

    }

    // complete update implementation
}
```

Du kan også aktivere metoden `fetchMoreData` fra en hændelsesmanager for brugergrænsefladen som vist her:

```typescript
btn_click(){
{
    // check if more data is expected for the current data view
    if (dataView.metadata.segment) {
        //request for more data if available; as a response, Power BI will call update method
        let request_accepted: bool = this.host.fetchMoreData(true);
        // handle rejection
        if (!request_accepted) {
            // for example, when the 100 MB limit has been reached
        }
    }
}
```

Som svar på kald af metoden `this.host.fetchMoreData` kalder Power BI metoden `update` for visualiseringen med et nyt datasegment.

> [!NOTE]
> Power BI begrænser i øjeblikket det samlede antal hentede data til 100 MB for at undgå begrænsninger af klientens hukommelse. Du kan se, at grænsen er nået, når `fetchMoreData()` returnerer `false`.

### <a name="using-incremental-updates-mode"></a>Brug af tilstand med trinvise opdateringer

I denne tilstand indeholder den datavisning, der er angivet til visualiseringen, kun trinvise data. Datavisningens størrelse ville derfor ikke overskride den definerede vinduesstørrelse. Hvis der f. eks. forventes i alt 101.000 rækker, og vinduesstørrelsen er angivet til 10.000, får visualiseringen 10 opdateringer med en datavisningsstørrelse på 10.000 og én opdatering med en datavisningsstørrelse på 1.000.

Du vælger denne tilstand ved at kalde `fetchMoreData` med `aggregateSegments = false`.

Du kan se, om dataene findes, ved at kontrollere, om `dataView.metadata.segment` findes:

```typescript
    public update(options: VisualUpdateOptions) {
        const dataView = options.dataViews[0];
        console.log(dataView.metadata.segment);
        // output: __proto__: Object
    }
```

Du kan også se, om det er den første eller en efterfølgende opdatering, ved at kontrollere `options.operationKind`. I følgende kode refererer `VisualDataChangeOperationKind.Create` til det første segment, mens `VisualDataChangeOperationKind.Segment` refererer til efterfølgende segmenter.

Se følgende kodestykke for at se et eksempel på implementering:

```typescript
// CV update implementation
public update(options: VisualUpdateOptions) {
    // indicates this is the first segment of new data.
    if (options.operationKind == VisualDataChangeOperationKind.Create) {

    }

    // on second or subsequent segments:
    if (options.operationKind == VisualDataChangeOperationKind.Segment) {
        
    }

    // skip overlapping rows 
    const rowOffset = (dataView.table['lastMergeIndex'] === undefined) ? 0 : dataView.table['lastMergeIndex'] + 1;

    // Process incoming data
    for (var i = rowOffset; i < dataView.table.rows.length; i++) {
        var val = <number>(dataView.table.rows[i][0]); // Pick first column               
            
     }
     
    // complete update implementation
}
```

Du kan også aktivere metoden `fetchMoreData` fra en hændelsesmanager for brugergrænsefladen som vist her:

```typescript
btn_click(){
{
    // check if more data is expected for the current data view
    if (dataView.metadata.segment) {
        //request for more data if available; as a response, Power BI will call update method
        let request_accepted: bool = this.host.fetchMoreData(false);
        // handle rejection
        if (!request_accepted) {
            // for example, when the 100 MB limit has been reached
        }
    }
}
```

Som svar på kald af metoden `this.host.fetchMoreData` kalder Power BI metoden `update` for visualiseringen med et nyt datasegment.

> [!NOTE]
> Selvom dataene fra datavisningen mellem de forskellige opdateringer overvejende er entydige, er der nogen overlapning mellem efterfølgende datavisninger.
> I forbindelse med datatilknytning efter tabel og kategori forventes det, at de første N datavisningsrækker indeholder data, der er kopieret fra den forrige datavisning.
> N kan bestemmes ved at: `(dataView.table['lastMergeIndex'] === undefined) ? 0 : dataView.table['lastMergeIndex'] + 1`