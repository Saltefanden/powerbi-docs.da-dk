---
title: Eksempler på Power BI-visualiseringer
description: I denne artikel præsenteres eksempler på Power BI-visualiseringer, herunder udsnit, mere end 20 typer diagrammer, WebGL og R-visualiseringer og -scripts.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 03/17/2019
ms.openlocfilehash: 076ad6549cb68660313dcd8da5ccf8eb1f8f26c7
ms.sourcegitcommit: 50b21718a167c2b131313b4135c8034c6f027597
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 10/14/2020
ms.locfileid: "92049148"
---
# <a name="samples-of-power-bi-visuals"></a>Eksempler på Power BI-visualiseringer

Du kan downloade, bruge og ændre disse Power BI-visualiseringer fra GitHub. Disse eksempler illustrerer, hvordan du kan håndtere almindelige situationer, når du udvikler med Power BI.

## <a name="slicers"></a>Udsnit

Et udsnit begrænser den del af data, der vises i andre visualiseringer i en rapport. Udsnit er en af flere måder at filtrere data på i Power BI.

| <img src="media/samples/chiclet-slicer.png" alt="Screenshot shows Chiclet Slicer." width="200">  | <img src="media/samples/timeline-slicer.png" alt="Screenshot shows Timeline slicer." width="200"> | <img src="media/samples/sample-slicer.png" alt="Screenshot shows Slicer sample." width="200">|
| ------------- | ------------- | -------------|
| [Firkantudsnitsværktøj](https://github.com/Microsoft/powerbi-visuals-chicletslicer/)  </br>Vis billede og/eller tekstknapper, der fungerer som et lærredsfilter på andre visualiseringer | [Tidslinjeudsnitsværktøj](https://github.com/Microsoft/powerbi-visuals-timeline/) </br>Valg af grafisk datoområde, der filtrerer efter dato | [Eksempel på udsnit](https://github.com/Microsoft/powerbi-visuals-sampleslicer/) </br>Demonstrerer brugen af API'en til avanceret filtrering

## <a name="charts"></a>Diagrammer

Hent inspiration i vores galleri, herunder søjlediagrammer, cirkeldiagrammer, Word Cloud med flere.

| <img src="media/samples/aster-plot.png" alt="Screenshot shows Aster Plot." width="200">  | <img src="media/samples/bullet-chart.png" alt="Screenshot shows Bullet chart." width="200"> | <img src="media/samples/Chord.png" alt="Screenshot shows Chord." width="200">|
| ------------- | ------------- | -------------|
| [Aster-diagram](https://github.com/Microsoft/powerbi-visuals-asterplot/)  </br>En ny vinkel på et standardkransediagram med en anden værdi til at køre udfaldsvinklen | [Punktdiagram](https://github.com/Microsoft/powerbi-visuals-bulletchart/) </br>Et søjlediagram med ekstra visualiseringer, der tilfører yderligere nyttige sammenhænge til at spore mål | [Korde](https://github.com/Microsoft/powerbi-visuals-chord/) </br>En grafisk metode til at vise de indbyrdes relationer mellem data i en matrix
| <img src="media/samples/dot-plot.png" alt="Screenshot shows Dot plot." width="200"> | <img src="media/samples/dual-kpi.png" alt="Screenshot shows Dual K P I." width="200">| <img src="media/samples/enhanced-scatter.png" alt="Screenshot shows Enhanced Scatter." width="200"> 
| [Punktvisning](https://github.com/Microsoft/powerbi-visuals-dotplot/) </br>Vis hyppighedsfordelingen på en flot måde | [Dobbelt-KPI](https://github.com/Microsoft/powerbi-visuals-dualkpi/) </br>Visualiserer effektivt to målinger over tid og viser deres tendens på en fælles tidslinje | [Forbedret punktdiagram](https://github.com/Microsoft/powerbi-visuals-enhancedscatter/) </br>Forbedringer af det eksisterende punktdiagram
| <img src="media/samples/forcegraph.png" alt="Screenshot shows Force Graph." width="200">| <img src="media/samples/gantt.png" alt="Screenshot shows Gantt." width="200">| <img src="media/samples/table-heatmap.png" alt="Screenshot shows Table Heatmap." width="200">
| [Force-graf](https://github.com/Microsoft/powerbi-visuals-forcegraph/) </br>Force-layoutdiagram med kurvet sti, der er velegnet til at vise forbindelser mellem enheder | [Gantt](https://github.com/Microsoft/powerbi-visuals-gantt/) </br>En type søjlediagram, som illustrerer et projekts tidslinje eller tidsplan med ressourcer | [Heatmaptabel](https://github.com/Microsoft/powerbi-visuals-heatmap/) </br>Sammenlign data let og intuitivt ved hjælp af farver i en tabel
| <img src="media/samples/histogram-chart.png" alt="Screenshot shows Histogram chart." width="200"> | <img src="media/samples/linedot-chart.png" alt="Screenshot shows LineDot chart." width="200"> | <img src="media/samples/mekko-chart.png" alt="Screenshot shows Mekko chart." width="200"> 
| [Histogram](https://github.com/Microsoft/powerbi-visuals-histogram/) </br>Visualiserer distribution af data over et fortløbende interval eller en bestemt tidsperiode | [LineDot-diagram](https://github.com/Microsoft/powerbi-visuals-linedotchart/) </br>Et animeret kurvediagram med animerede punkter, der er velegnet til at engagere en målgruppe med data | [Mekko-diagram](https://github.com/Microsoft/powerbi-visuals-mekkochart/) </br>En blanding af 100 % stablet søjlediagram og 100 % stablet liggende søjlediagram kombineret i én visning
| <img src="media/samples/multikpi.png"alt="Skærmbillede, der viser Multi KPI." width="200"> | <img src="media/samples/powerkpi.png"alt="Skærmbillede, der viser Power-KPI." width="200"> | <img src="media/samples/powerkpi.png"alt="Skærmbillede, der viser Power-KPI-matrix." width="200"> 
| [Multi-KPI](https://github.com/microsoft/PowerBI-visuals-MultiKPI/) </br> En effektiv visualisering med flere KPI'er med en vigtig KPI sammen med flere minidiagrammer med understøttende data | [Power-KPI](https://github.com/microsoft/PowerBI-visuals-PowerKPI/) </br>En effektiv KPI-indikator med flerkurvediagram og mærkater for dags dato, værdi og afvigelser | [Power-KPI-matrix](https://github.com/microsoft/PowerBI-visuals-PowerKPIMatrix/) </br>Overvåg videnregnskaber og et ubegrænset antal målepunkter og KPI'er på en kompakt og letlæselig liste
| <img src="media/samples/pulse-chart.png" alt="Screenshot shows Pulse chart." width="200">| <img src="media/samples/radar-chart.png" alt="Screenshot shows Radar chart." width="200"> | <img src="media/samples/sankey-chart.png" alt="Screenshot shows Sankey chart." width="200"> 
| [Impulsdiagram](https://github.com/Microsoft/powerbi-visuals-pulsechart/) </br>Dette kurvediagram med vigtige begivenheder er perfekt til at fortælle historier med data| [Radardiagram](https://github.com/Microsoft/powerbi-visuals-radarchart/) </br>Repræsenterer flere målinger, der er afbildet over en kategoriakse, og er nyttigt til at sammenligne attributter | [Sankey-diagram](https://github.com/Microsoft/powerbi-visuals-sankey/) </br>Rutediagram, hvor bredden på serien er proportional med mængden af strømmen
| <img src="media/samples/stream-graph.png" alt="Screenshot shows Stream graph." width="200"> | <img src="media/samples/sunburst.png" alt="Screenshot shows Sunburst chart." width="200">| <img src="media/samples/tornado.png" alt="Screenshot shows Tornado chart." width="200">
| [Stream-graf](https://github.com/Microsoft/powerbi-visuals-streamgraph/) </br>Et stablet områdediagram med jævn interpolering, som ofte bruges til at vise værdier over tid | [Solstrålediagram](https://github.com/Microsoft/powerbi-visuals-sunburst/) </br>Kransediagram med flere niveauer til effektiv visualisering af hierarkiske data| [Tornadodiagram](https://github.com/Microsoft/powerbi-visuals-tornado/) </br>Sammenlign den relative vigtighed af variabler mellem to grupper
 | <img src="media/samples/word-cloud.png" alt="Screenshot shows Word Cloud." width="200">
 | [Ordcloud](https://github.com/Microsoft/powerbi-visuals-wordcloud/) </br>Opret en sjov visualisering fra hyppig tekst i dine data

## <a name="webgl"></a>WebGL

WebGL gør det muligt at bruge en API på webindhold, der er baseret på OpenGL ES 2.0, til at foretage gengivelse i 2D og 3D på et HTML-lærred.

| <img src="media/samples/globe-map.png" alt="Screenshot shows Globe Map." width="250">|
| ------------- |
| [Globuskort](https://github.com/Microsoft/powerbi-visuals-globemap/) </br>Afbild placeringer på et interaktivt 3D-kort

## <a name="r-visuals"></a>R-visualiseringer

Disse eksempler viser, hvordan du kan udnytte den analytiske og visuelle styrke af R-visualiseringer og R-scripts.

| <img src="media/samples/association-rules.png" alt="Screenshot shows Association rules." width="200">| <img src="media/samples/clustering.png" alt="Screenshot shows Clustering." width="200">| <img src="media/samples/clustering-with-outliers.png" alt="Screenshot shows Clustering with outliers." width="200">|
|------------- |------------- |------------- |------------- |
| [Tilknytningsregler](https://github.com/Microsoft/powerbi-visuals-assorules/) </br>Afdæk relationer mellem tilsyneladende ikke-relaterede data ved hjælp af if-then-sætninger | [Clustering](https://github.com/Microsoft/powerbi-visuals-clustering-kmeans/) </br>Find lighedsgrupper i dine data ved hjælp af k-means-algoritmen | [Clustering med udenforliggende værdier](https://github.com/microsoft/PowerBI-visuals-dbscan/) </br>Find lighedsgrupper og udenforliggende værdier i dine data
| <img src="media/samples/correlation-plot.png" alt="Screenshot shows Correlation plot." width="200"> | <img src="media/samples/decision-tree-chart.png" alt="Screenshot shows Decision tree chart." width="200"> | <img src="media/samples/forecasting-tbats.png" alt="Screenshot shows Forecasting T B A T S." width="200"> 
| [Korrelationsdiagram](https://github.com/Microsoft/powerbi-visuals-corrplot/) </br>Fremhæv de mest korrelerede variabler i en datatabel | [Beslutningstrædiagram](https://github.com/Microsoft/powerbi-visuals-decision-tree/) </br>Skematisk træformet diagram til bestemmelse af statistisk sandsynlighed ved hjælp af rekursiv partitionering | [Prognose-TBATS](https://github.com/Microsoft/powerbi-visuals-forcasting-tbats/) </br>Tidsserieprognose for serier, der har flere sæsonudsving, ved hjælp af TBATS-modellen
| <img src="media/samples/forecasting-with-ARIMA.png" alt="Screenshot shows Forecasting with ARIMA." width="200"> | <img src="media/samples/funnel-plot.png" alt="Screenshot shows Funnel plot." width="200"> | <img src="media/samples/outliers-detection.png" alt="Screenshot shows Outliers detection." width="200"> 
| [Prognose med ARIMA](https://github.com/Microsoft/powerbi-visuals-forcastingarima/) </br>Forudsig fremtidige værdier på baggrund af historiske data ved hjælp af ARIMA (Autoregressive Integrated Moving Avg) | [Tragtafbildning](https://github.com/Microsoft/powerbi-visuals-funnel/) </br>Find udenforliggende værdier i dine data ved hjælp af en tragtafbildning | [Registrering af udenforliggende værdier](https://github.com/Microsoft/powerbi-visuals-outliers-det/) </br>Find udenforliggende værdier i dine data ved hjælp af den mest passende metode og afbildning
| <img src="media/samples/spline-chart.png" alt="Screenshot shows Spline chart." width="200"> | <img src="media/samples/time-series-decomposition-chart.png" alt="Screenshot shows Time Series decomposition chart." width="200"> | <img src="media/samples/time-series-forecasting-chart.png" alt="Screenshot shows Time series forecasting chart." width="200">
| [Sløjfediagram](https://github.com/Microsoft/powerbi-visuals-spline/) </br>Visualiser og forstå støjende data | [Diagram med tidsserieopdeling](https://github.com/Microsoft/powerbi-visuals-timeseriesdecomposition/) </br>Forstå tidsseriekomponenterne ved hjælp af "Seasonal and Trend decomposition using Loess" | [Diagram med tidsserieprognose](https://github.com/Microsoft/powerbi-visuals-forcasting-exp/) </br>Brug af en eksponentiel udjævningsmodel til at forudsige fremtidige værdier, der er baseret på tidligere observerede værdier

## <a name="next-steps"></a>Næste trin

Se [Udvikling af en Power BI-cirkelkortvisualisering](develop-circle-card.md) for at prøve at oprette Power BI-visualiseringer.
