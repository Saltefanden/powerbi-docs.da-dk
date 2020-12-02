---
title: Brug et udsnit eller filter for relativ tid i Power BI
description: Få mere at vide om, hvordan du bruger et udsnit eller et filter til at begrænse relative tidsintervaller i Power BI.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 07/06/2020
LocalizationGroup: Create reports
ms.openlocfilehash: 4b12760584df2471bf02029be0fb428d1ab21e4c
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96387545"
---
# <a name="use-a-relative-time-slicer-and-filter-in-power-bi"></a>Brug et udsnit og filter for relativ tid i Power BI

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-desktop](../includes/yes-desktop.md)] [!INCLUDE [yes-service](../includes/yes-service.md)]

I forbindelse med scenarier med hurtige opdateringer kan filtrering til et mindre tidsrum være nyttigt. Ved hjælp af udsnittet eller filteret for relativ tid kan du anvende tidsbaserede filtre på en hvilken som helst dato- eller tidskolonne i din datamodel. Du kan f.eks. bruge udsnittet for relativ tid til kun at vise videovisninger inden for det sidste minut eller den sidste time. 

:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time.gif" alt-text="Skærmbillede af eksempel på relativ tid.":::

Du behøver ikke at bruge denne funktion sammen med funktionen til [automatisk opdatering af side](../create-reports/desktop-automatic-page-refresh.md). Men mange scenarier med relativ tid passer dog godt sammen med funktionen til automatisk opdatering af siden.  

> [!NOTE]
> Når du anvender et filter eller et udsnit for relativ tid på side- eller rapportniveau, filtreres alle visualiseringer på denne side eller i denne rapport til nøjagtigt det samme tidsinterval ved hjælp af en delt *ankertid*. Da visualiseringer kan have en smule forskellige udførelsestider, sikrer denne ankertid, at visualiseringerne synkroniseres på tværs af din side eller på tværs af din rapport. Læs mere om [ankertider](#understanding-anchor-time) i denne artikel.

## <a name="create-a-relative-time-slicer-or-filter"></a>Opret et udsnit eller et filter for relativ tid

Efter du har aktiveret funktionen, skal du trække og slippe dato- eller tidsfeltet til feltbrønden i et udsnit eller til slipzonen i ruden Filtre. 

### <a name="create-a-slicer"></a>Opret et udsnit

1. Træk et dato- eller tidsfelt til lærredet.

2. Vælg visualiseringstypen **Udsnit**.

    :::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-create-slicer.png" alt-text="Skærmbillede af oprettelse af et tidsudsnit.":::

### <a name="create-a-filter"></a>Opret et filter
 
- Træk et dato- eller tidsfelt til ruden Filtre for **denne visualisering**, **denne side** eller **alle sider**.

### <a name="set-relative-time"></a>Angiv relativ tid 

Derefter skal du ændre filtertypen til **Relativ tid**.

:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-set.png" alt-text="Skærmbillede af skift til relativ tid.":::
 
Sådan ser det ud i et udsnit:

:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-slicer.png" alt-text="Skærmbillede af relativ tid i et udsnit.":::

Sådan ser det ud på et filterkort: 

:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-filter.png" alt-text="Skærmbillede af relativ tid i et filter.":::
 
Med denne nye filtertype kan du filtrere baseret på **Sidste**, **Næste** eller **Denne tidsperiode**: 

:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-last-next.png" alt-text="Skærmbillede af valg af Sidste, Næste eller Denne tidsperiode.":::
 
Du kan angive tidsvinduet ved hjælp af et heltal og en tidsenhed: **Minutter** eller **Timer**.
 
:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-minutes-hours.png" alt-text="Skærmbillede af valg af minutter eller timer.":::

Hvis du har brug for at spare plads på lærredet, kan du også oprette filteret for relativ tid som et filterkort i ruden Filtre.

:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-set-filter.png" alt-text="Skærmbillede af angivelse af relativ tid i et filter i stedet.":::
 
## <a name="understanding-anchor-time"></a>Om ankertid

Når der anvendes et filter på side- eller rapportniveau, synkroniseres alle visualiseringer på denne side eller i denne rapport til nøjagtigt det samme tidsinterval. Disse forespørgsler udstedes alle relativt til et tidspunkt kaldet *ankertid*. Ankertiden opdateres automatisk i følgende situationer:

- Ved indledende indlæsning af siden.
- Ved manuel opdatering.
- Automatisk opdatering af siden eller opdatering i forbindelse med registrering af ændringer.
- Ved ændring af modellen.

### <a name="anchor-time-exceptions"></a>Undtagelser for ankertid

- Filtrering efter relativ tid ved hjælp af visualiseringen Spørgsmål og svar er ikke relativ til denne ankertid, før du konverterer visualiseringen Spørgsmål og svar til en standardvisualisering. De andre visualiseringer med kunstig intelligens, f.eks. vigtige influencere og opdelingstræ, synkroniseres med ankertiden. 
- Derudover er filtre og udsnit for relativ tid ikke relative til ankertiden, medmindre der er filtre for relativ tid til stede. Hvis der filtre for relativ dato og relativ tid på den samme side, respekterer filteret for relativ tid ankertiden.

## <a name="limitations-and-considerations"></a>Begrænsninger og overvejelser

Følgende begrænsninger og overvejelser gælder i øjeblikket for udsnittet og filteret for relativ tid.

- **Overvejelser i forbindelse med tidszone**: Datamodeller i Power BI indeholder ikke oplysninger om tidszone. Modeller kan gemme tider, men der er ingen angivelse af den tidszone, de er i. Udsnittet og filteret er altid baseret på tidspunktet i UTC-tid. Hvis du konfigurerer et filter i en rapport og sender det til en kollega i en anden tidszone, ser I begge de samme data. Medmindre I befinder jer i UTC-tidszonen, skal I begge tage højde for den tidsforskydning, der gælder for jer. Brug Forespørgselseditoren til at konvertere data, der registreres i en lokal tidszone, til UTC.
- Denne nye filtertype understøttes i Power BI Desktop, Power BI-tjenesten, Power BI Embedded og Power BI-mobilapps. Den understøttes imidlertid ikke for Publicer på internettet.

- **Cachelagring af forespørgsel**: Vi bruger klientcachen. Lad os sige, at du angiver "sidste 1 minut", derefter "sidste 5 minutter" og derefter går tilbage til "sidste 1 minut". På dette tidspunkt ser du de samme resultater, som da den kørte første gang, medmindre du opdaterer siden, eller siden opdateres automatisk.

## <a name="next-steps"></a>Næste trin

- [Brug et udsnit og et filter for relativ dato i Power BI](../visuals/desktop-slicer-filter-date-range.md)
- [Udsnitsværktøjer i Power BI](../visuals/power-bi-visualization-slicers.md)
