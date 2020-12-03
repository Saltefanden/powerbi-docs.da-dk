---
title: Brug modelleringsvisning i Power BI Desktop
description: Brug Udformningsvisning til at se komplekse datasæt i en visualisering i Power BI Desktop
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-transform-model
ms.topic: conceptual
ms.date: 05/08/2019
LocalizationGroup: Transform and shape data
ms.openlocfilehash: a47bcba58a39f76a6e9e64778d2d06a75dc14132
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96413949"
---
# <a name="work-with-modeling-view-in-power-bi-desktop"></a>Arbejde med udformningsvisning i Power BI Desktop

Med **Udformningsvisning** i **Power BI Desktop** kan du få vist og arbejde med komplekse datasæt, der indeholder mange tabeller.


## <a name="using-modeling-view"></a>Brug af Udformningsvisning

Du tilgår Udformningsvisning ved at vælge ikonet Udformningsvisning, som du finder i venstre side af **Power BI Desktop**, som vist på følgende billede.

![Ikonet Udformningsvisning i Power BI Desktop](media/desktop-modeling-view/modeling-view_02.png)

## <a name="creating-separate-diagrams"></a>Oprettelse af separate diagrammer

Med Udformningsvisning kan du oprette diagrammer over din model, der kun indeholder et undersæt af tabellerne i modellen. Dette kan hjælpe med at give et tydeligere overblik over tabeller, du vil arbejde med, og gør det lettere at arbejde med komplekse datasæt. Hvis du vil oprette et nyt diagram kun med et undersæt af tabellerne, skal du klikke på tegnet **+** ud for fanen **Alle tabeller** i bunden af Power BI Desktop-vinduet.

![Opret et nyt diagram ved at klikke på plustegnet (+) i afsnittet faner](media/desktop-modeling-view/modeling-view_03.png)

Du kan derefter trække en tabel fra listen **Felter** til diagramoverfladen. Højreklik på tabellen, og vælg derefter **Tilføj relaterede tabeller** i den menu, der vises.

![Højreklik på en tabel, og vælg Tilføj relaterede tabeller](media/desktop-modeling-view/modeling-view_04.png)

Når du gør det, vises tabeller, der er relateret til den oprindelige tabel, i det nye diagram. På følgende billede kan du se, hvordan relaterede tabeller vises, når du har valgt menupunktet **Tilføj relaterede tabeller**.

![Viser relaterede tabeller](media/desktop-modeling-view/modeling-view_05.png)

## <a name="setting-common-properties"></a>Angivelse af fælles egenskaber

Du kan vælge flere objekter på én gang i Udformningsvisning ved at holde **CTRL**-tasten nede og klikke på flere tabeller. Når du vælger flere tabeller, fremhæves de i Udformningsvisning. Når flere tabeller er fremhævet, gælder ændringer, der er anvendt i ruden **Egenskaber**, for alle valgte tabeller.

Du kan f.eks. ændre [lagringstilstanden](desktop-storage-mode.md) for flere tabeller i diagramvisningen ved at holde **CTRL**-tasten nede, vælge tabeller og derefter ændre indstillingen for lagringstilstand i ruden **Egenskaber**.

![Vælg flere tabeller ved at holde CTRL nede, og angiv derefter fælles egenskaber på tværs af alle valgte tabeller](media/desktop-modeling-view/modeling-view_06.png)


## <a name="next-steps"></a>De næste trin

I følgende artikler beskrives flere detaljer om datamodeller og DirectQuery.

* [Sammenlægninger i Power BI Desktop (prøveversion)](desktop-aggregations.md)
* [Sammensatte modeller i Power BI Desktop](desktop-composite-models.md)
* [Lagringstilstand i Power BI Desktop (Preview)](desktop-storage-mode.md)
* [Mange til mange-relationer i Power BI Desktop](desktop-many-to-many-relationships.md)


Artikler om DirectQuery:

* [Brug af DirectQuery in Power BI](../connect-data/desktop-directquery-about.md)
* [Understøttede datakilder i forbindelse med DirectQuery i Power BI](../connect-data/power-bi-data-sources.md)
