---
title: Forstå, hvordan visualiseringer interagerer i en rapport
description: Dokumentation til Power BI-slutbrugere, der forklarer, hvordan visualiseringer interagerer på en rapportside.
author: mihart
ms.reviewer: mihart
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: how-to
ms.date: 09/11/2020
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: 9124322dbf7656b05c4cd174207e074cd4f807fe
ms.sourcegitcommit: cb606d3ae95300683caf1853e229d8981302a8e2
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 09/18/2020
ms.locfileid: "90763959"
---
# <a name="how-visuals-cross-filter-each-other-in-a-power-bi-report"></a>Sådan krydsfiltrerer visualiseringer hinanden i en Power BI-rapport

[!INCLUDE[consumer-appliesto-yyny](../includes/consumer-appliesto-yyny.md)]

En af de fantastiske funktioner i Power BI er den måde, som alle visualiseringer på rapportside er forbundet på. Hvis du vælger et datapunkt i en af visualiseringerne, ændres alle andre visualiseringer med disse data på siden på baggrund af dette valg. 

![video af interaktion mellem visualiseringer](media/end-user-interactions/interactions.gif)

## <a name="how-visuals-interact-with-each-other"></a>Sådan interagerer visualiseringer med hinanden

Hvis du vælger et datapunkt i én visualisering på en rapportside, udføres der som standard tværgående filtrering og fremhævning af de andre visualiseringer på siden. Lige præcis hvordan visualiseringerne på en side interagerer på, angives af *designeren* af rapporten. *Designere* har mulighed for at slå interaktion mellem visualiseringer til og fra og ændre standardfunktionsmåden for tværgående filtrering, tværgående fremhævning og [analysering](end-user-drill.md). 

Hvis du ikke er stødt på hierarkier eller detailudledning endnu, kan du få mere at vide om disse funktioner ved at læse [detailudledning i Power BI](end-user-drill.md). 

### <a name="cross-filtering-and-cross-highlighting"></a>Krydsfiltrering og krydsfremhævning

Tværgående filtrering og fremhævning kan være nyttigt for at identificere, hvordan en værdi i dine data bidrager til en anden. Begreberne *tværgående filter* og *tværgående fremhævning* bruges til at skelne mellem den funktionsmåde, der er beskrevet her, og hvad der sker, når du bruger ruden **Filtre** til at filtrere og fremhæve visualiseringer.  

Lad os definere disser begreber, i takt med at vi kigger på rapportsiderne nedenfor. Kransediagrammet "Samlet kategorivolumen efter segment" har to værdier: "Moderation" og "Bekvemmelighed". 

![Rapportside](media/end-user-interactions/power-bi-interactions-before.png)

1. Lad os se, hvad der sker, når vi vælger **Moderation**.

    ![Rapportside efter segmentet Moderation i kransediagrammet er valgt](media/end-user-interactions/power-bi-interactions-after.png)

2. Med **krydsfiltrering** fjernes data, der ikke er gældende. Hvis du vælger **Moderation** i kransediagrammet, så krydsfiltreres kurvediagrammet. Der vises nu kun datapunkter for segmentet Moderation i kurvediagrammet. 

3. Med **krydsfremhævning** bevares alle oprindelige datapunkter, men den del, der ikke gælder for dit valg, nedtones. Hvis du vælger **Moderation** i kransediagrammet, så krydsfremhæves søjlediagrammet. Alle data, der gælder for segmentet Bekvemmelighed, nedtones i søjlediagrammet, og alle data, der gælder for segmentet Moderation, fremhæves. 


## <a name="considerations-and-troubleshooting"></a>Overvejelser og fejlfinding
- Hvis din rapport har en visualisering, der understøtter [detailudledning](end-user-drill.md), har det som standard ingen indvirkning på andre visualiseringer på rapportsiden, hvis du foretager detailudledning i én visualisering. Men *rapportdesigneren* kan ændre denne funktionsmåde, så kontrollér de visualiseringer, der kan zoomes i, for at se, **om zooming filtrerer andre visualiseringer** er blevet aktiveret af *rapportdesigneren*.
    
- Filtre på visualiseringsniveau bevares, når andre visualiseringer på rapportsiden krydsfiltreres og krydsfremhæves. Så hvis du eller rapportdesigneren har anvendt filtre på visualiseringsniveau i Visualisering A, og du bruger Visualisering A til at interagere med Visualisering B, så anvendes filtrene på visualiseringsniveau fra Visualisering A på Visualisering B.

    ![Rapportside, der viser filtre, der allerede er angivet](media/end-user-interactions/power-bi-visual-filters.png)

## <a name="next-steps"></a>Næste trin
[Sådan bruger du rapportfiltre](../consumer/end-user-report-filter.md)


[Om filtrering og fremhævning](end-user-report-filter.md).
