---
title: Brug af gruppering i Power BI Desktop
description: Få mere at vide om, hvordan du grupperer visualiseringer i Power BI Desktop
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 05/26/2020
LocalizationGroup: Create reports
ms.openlocfilehash: b74e06c076cd25132a6e3bfb8a12775d50b7263f
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96412891"
---
# <a name="group-visuals-in-power-bi-desktop-reports"></a>Gruppér visualiseringer i Power BI Desktop-rapporter
Med **gruppering** kan du i **Power BI Desktop** gruppere visuelle elementer i din rapport, f.eks. knapper, tekstfelter, figurbilleder og alle visuelle elementer, som du opretter, på samme måde som du grupperer elementer i PowerPoint. Når du grupperer visuelle elementer i en rapport, kan du behandle gruppen som et enkelt objekt, så det bliver nemmere, hurtigere og mere intuitivt at flytte, tilpasse størrelsen og arbejde med lag i din rapport.

![Brug af gruppering](media/desktop-grouping-visuals/grouping-visuals-01.png)


## <a name="creating-groups"></a>Oprettelse af grupper

Hvis du vil oprette en gruppe visuelle elementer i Power BI Desktop, skal du vælge det første visuelle element på lærredet og derefter holde Ctrl-tasten nede, klikke på en eller flere visuelle elementer, som du vil have med i gruppen, og derefter højreklikke på samlingen af visuelle elementer og vælge **Gruppér** i den menu, der vises.

![vælg to eller flere elementer, der skal grupperes](media/desktop-grouping-visuals/grouping-visuals-02.png)

Grupper vises i ruden **Valg**. Du kan have lige så mange grupper af visualiseringer, som du har brug for i dine rapporter, og du kan også indlejre grupper af visuelle elementer. På følgende billede er gruppen *Australien* indlejret i gruppen *Kort*. Du kan udvide en gruppe ved at vælge indsætningspunktet ud for gruppenavnet og skjule den ved at vælge indsætningspunktet igen. 

![indlejrede grupper](media/desktop-grouping-visuals/grouping-visuals-03.png)

Du kan også trække og slippe individuelle visuelle elementer i ruden **Valg** for at inkludere dem i en gruppe, fjerne dem fra en gruppe, indlejre en gruppe eller fjerne en gruppe eller et individuelt visuelt element fra en indlejring. Du skal blot trække det visuelle element, du vil justere, og placere det på det ønskede sted. Lagdelingen af visuelle elementer, hvis de overlapper hinanden, bestemmes af deres rækkefølge på *Rækkefølge for lag*.

Det er nemt at omdøbe en gruppe: du dobbeltklikker bare på gruppenavnet i ruden **Markering** og indtaster derefter det nye navn på din gruppe.

![træk og slip grupper](media/desktop-grouping-visuals/grouping-visuals-04.png)

Hvis du kun vil opdele gruppen, skal du markere gruppen, højreklikke og vælge **Opdel gruppe** i den menu, der vises.

## <a name="hide-and-show-visuals-or-groups"></a>Skjul og vis visuelle elementer eller grupper

Du kan nemt skjule eller få vist grupper ved hjælp af ruden **Valg**. Hvis du vil skjule en gruppe, skal du vælge knappen med øjet ud for gruppenavnet (eller et enkelt visuelt element) for at skifte mellem, om det visuelle element eller gruppen er skjult eller vist. På følgende billede er gruppen *Australien* skjult, og resten af grupperne, der er indlejret i gruppen *Kort*, vises.


![skjul og vis grupper](media/desktop-grouping-visuals/grouping-visuals-05.png)

Når du skjuler en gruppe, skjules alle visuelle elementer i den pågældende gruppe, hvilket vises, ved at knappen med øjet nedtones (ikke muligt at slå til og fra, da hele gruppen er skjult). Hvis du kun vil skjule bestemte visuelle elementer i en gruppe, skal du bare slå knappen med øjet ud for det visuelle element fra, hvorefter det kun er det visuelle element i gruppen, der er skjult.

## <a name="selecting-visuals-within-a-group"></a>Valg af visuelle elementer i en gruppe

Der er et par måder at navigere på og vælge elementer i en gruppe visuelle elementer. På følgende liste beskrives funktionsmåden:

* Hvis du klikker på et tomt område i en gruppe (f.eks. et tomt område mellem visuelle elementer), markeres der ikke noget.
* Hvis du klikker på et visuelt element i en gruppe, vælges hele gruppen. Hvis du klikker endnu en gang, markeres det enkelte visuelle element.
* Når du markerer en gruppe og derefter et andet objekt på rapportlærredet, oprettes en indlejret gruppe, hvis du vælger **Gruppér** i menuen, når du højreklikker.
* Når du vælger to grupper, vises der en mulighed for at flette de valgte grupper i stedet for at indlejre dem, når du højreklikker

## <a name="apply-background-color"></a>Anvend baggrundsfarve

Du kan også anvende en baggrundsfarve for en gruppe ved hjælp afsnittet **Formatering** i ruden **Visualiseringer**, som vist på følgende billede. 

![baggrundsfarve for grupper](media/desktop-grouping-visuals/grouping-visuals-06.png)

Når du har anvendt en baggrundsfarve, markerer du gruppen ved at klikke på området mellem de visuelle elementer i gruppen (sammenlign dette med at klikke på det tomme område mellem visuelle elementer i en gruppe, hvilket ikke markerer gruppen). 


## <a name="next-steps"></a>Næste trin
Du kan få flere oplysninger om gruppering ved at se følgende video:

* [Gruppering i Power BI Desktop – video](https://youtu.be/sf4n7VXoQHY?t=10)

Du vil måske også være interesseret i følgende artikler:

* [Brug tværgående detaljeadgang i rapport i Power BI Desktop](desktop-cross-report-drill-through.md)
* [Brug af udsnitsværktøjer i Power BI Desktop](../visuals/power-bi-visualization-slicers.md)
