---
title: Opret små multipla i Power BI (eksempelvisning)
description: Små multipla eller trellising, Opdel en visualisering i flere versioner af sig selv, der vises side om side, med data partitioneret på tværs af disse versioner af en valgt dimension.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: mihart
ms.service: powerbi
ms.subservice: pbi-visuals
ms.topic: how-to
ms.date: 02/05/2021
LocalizationGroup: Visualizations
ms.openlocfilehash: bc1f890e588227f9d0dc30202474a8f77f93fc38
ms.sourcegitcommit: f17acb16018752c234db6bff1f51f5130be12c58
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/06/2021
ms.locfileid: "99617325"
---
# <a name="create-small-multiples-in-power-bi-preview"></a>Opret små multipla i Power BI (eksempelvisning)

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-desktop](../includes/yes-desktop.md)] [!INCLUDE [yes-service](../includes/yes-service.md)]

Små multipla eller trellising, opdeler en visualisering i flere forskellige versioner af sig selv. Versionerne vises side om side med data, der er delt på tværs af disse versioner, med en valgt dimension. Et lille multiplum kan f. eks. opdele kolonne diagrammet "salg efter kategori" på tværs af produktlinjer eller områder. I denne prøveversion indeholder små Multipla en lille mængde funktioner, hvor flere kommer i gang med senere versioner.

:::image type="content" source="media/power-bi-visualization-small-multiples/small-mulitple-sales-category-region.png" alt-text="Skærmbillede af små multipla for kategori og område.":::

## <a name="enable-the-preview-feature"></a>Aktiver prøveversionsfunktionen

I menuen **filer** skal du vælge **Indstillinger**  >  **for**  >  **prøveversion** og indstillinger og markere afkrydsningsfeltet **små multipla** .

:::image type="content" source="media/power-bi-visualization-small-multiples/small-multiple-enable-preview.png" alt-text="Aktivér prøveversionen for små multipla.":::

Genstart Power BI Desktop, og du er klar til at prøve små multipla.

## <a name="create-small-multiples"></a>Opret små multipla

I øjeblikket kan du oprette små multipla på søjle-, kolonne-, kurve-og områdediagrammer. 

For at komme i gang skal du oprette en af ovenstående visuelle elementer og vælge et felt, hvor du vil partitionere dataene. Træk dette felt til afsnittet **små multiplies** i sektionen felter i ruden visualiseringer. Diagrammet opdeler til et 2 × 2-gitter, hvor dataene er fordelt langs den valgte dimension. Gitteret udfylder med de små multipla-diagrammer. De er sorteret efter den valgte sorteringsrækkefølge, fra venstre mod højre og derefter fra top til bund.

:::image type="content" source="media/power-bi-visualization-small-multiples/small-multiple-two-by-two-grid.png" alt-text="Små multipla i et gitter med to efter to.":::

Du kan se, at akserne er synkroniseret. Der er én Y-akse til venstre for hver række og én X-akse nederst i hver kolonne.

Nu, hvor du har oprettet små multipla, kan du se, hvordan du [interagerer med små multipla i Power bi (prøveversion)](power-bi-visualization-small-multiples-interact.md).

## <a name="format-a-small-multiples-visual"></a>Formatér et lille visuelt element

Med nogle nye indstillinger i formaterings ruden kan du styre gitterets udseende og funktionalitet.

### <a name="change-the-grid-dimensions"></a>Rediger gitter dimensioner

Du kan ændre gitterets dimensioner på kortet gitter layout:

:::image type="content" source="media/power-bi-visualization-small-multiples/small-multiple-grid-layout-card.png" alt-text="Lille layout kort med flere gitre.":::

Standarden er 2 × 2 Grid af små multipla, men du kan justere antallet af rækker og kolonner til op til 6 × 6. Alle de multipla, der ikke passer til det pågældende gitter, indlæses, når du ruller ned.


### <a name="adjust-the-small-multiples-titles"></a>Juster små titler med flere titler

På samme måde som med andre visuelle titler kan du justere typografien og placeringen af små flere titler på det **lille afsnits** kort.

## <a name="preview-limitations"></a>Prøve versions begrænsninger

Selvom funktionen findes i prøveversionen, arbejder vi hele tiden på at sikre, at den er en hjælp i resten af vores funktioner. Her er nogle aktuelle begrænsninger.

### <a name="fields-pane"></a>Ruden Felter

- Dato og andre fortløbende hierarkier: Lad os sige, at du har et visuelt element som et kurvediagram med et dato hierarki i X-aksen. Når du foretager små multipla af det, konverterer Power BI den pågældende akse fra en fortløbende til en kategori-akse.
- Vis elementer uden data: Indstillingen findes stadig, men funktionaliteten kan muligvis ikke justeres i forhold til dine forventninger.

### <a name="visual-interactions"></a>Interaktioner mellem visualiseringer

- Rul ned for at indlæse mere på kategori-aksen: i standard visualiseringer med mange kategorier på aksen, indlæser visuals flere kategorier, når du ruller til slutningen af aksen. I øjeblikket indlæser en lille Visual ikke flere kategorier.
- Sortér små multipla efter måling: sortering på små multipla er en ny funktionalitet. Du forventer muligvis at sortere dine små multipla efter en måling. I øjeblikket kan du kun sortere dine multipla efter feltets naturlige sorteringsrækkefølge.
- Højreklik/genvejsmenu – > Analysér: deaktiveret for øjeblikket.
- Genvejsmenuen Højreklik/genvej – > opsummere: deaktiveret for øjeblikket.
- Markering af flere datapunkter med rektangulær markering: deaktiveret for nu.
- Akse zoom: deaktiveret for nu.
- Hjælp til handicappede: du kan justere tastaturnavigation og skærm udlæsninger for bedre at understøtte det nye "gitter" lag, som små multipla fører til visualiseringer. Der mangler en funktionsmåde, f. eks. tastaturnavigation via rullepanelet kategori-akse.

### <a name="formatting-options"></a>Formateringsindstillinger

**Generelt**

- Tilpas til/fra: Indstillingen findes stadig, men funktionaliteten kan muligvis ikke justeres i forhold til dine forventninger. Da mange mobil tilpasninger er bundet til denne til/fra-knap, vil mobil oplevelser også vise den oplevelser, du finder i Power BI Desktop og Power BI-tjeneste.
- Stik prøvetagning med høj tæthed: for kurvediagrammer findes der stadig stik prøvetagning med høj tæthed, men det understøttes i øjeblikket ikke af små multipla.

**Akse**

- Sammenkædning af etiketter: deaktiveret for øjeblikket.

**Totalmærkater**

- Samlet antal etiketter til stablede diagrammer: deaktiveret for øjeblikket.

**Zoom skyder**

- Zoom skydere: deaktiveret for øjeblikket.

**Ruden Analytics** 

- Tendenslinjer: deaktiveret for øjeblikket.
- Prognose: deaktiveret for øjeblikket.

Dynamisk formatering til fremhævning af etiketter: understøttes ikke i øjeblikket.
Tilgængeligheden af tjenesten

## <a name="authoring-in-the-power-bi-service"></a>Oprettelse i Power BI-tjeneste

Oprettelse af små multipla på internettet understøttes ikke, når funktionen er tilgængelig som prøveversion. Du kan få vist en rapport med en lille visuel visualisering og endda formatere visualiseringen. Men du kan ikke konvertere en visualisering, der er standard, til et lille visuelle element i Power BI-tjeneste. En visualisering skal allerede have et felt i feltet små multipla, eller de små multipla vises ikke for det visuelle element.

## <a name="share-your-feedback"></a>Del din feedback

Giv os besked om det visuelle element med små multipla:

- [Power BI-community](https://community.powerbi.com/)
- [Siden Power BI idéer](https://ideas.powerbi.com/ideas/) 

## <a name="next-steps"></a>Næste trin

[Arbejd med små multipla i Power BI (eksempelvisning)](power-bi-visualization-small-multiples-interact.md)
