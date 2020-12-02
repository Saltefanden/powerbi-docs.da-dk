---
title: Brug gitterlinjer og fastgørelse til gitter i Power BI Desktop-rapporter
description: Brug gitterlinjer, fastgørelse til gitter, z-rækkefølge, justering og fordeling i Power BI Desktop-rapporter
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 05/08/2019
LocalizationGroup: Create reports
ms.openlocfilehash: 745b89efc76c179c0393e4dccd29d5bee6910676
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96412937"
---
# <a name="use-gridlines-and-snap-to-grid-in-power-bi-desktop-reports"></a>Brug gitterlinjer og fastgørelse til gitter i Power BI Desktop-rapporter
**Power BI Desktop**-rapportlærredet indeholder gitterlinjer, som du kan bruge til at justere visuelle elementer på en rapportside, så det ser pænt ud, og bruge funktionen for fastgørelse til gitter, så de visuelle elementer i dine rapporter ser jævne ud, er justeret og har lige stor afstand.

I **Power BI Desktop** kan du også tilpasse z-rækkefølgen for objekter i en rapport (flytte dem fremad eller bagud) og justere eller fordele de markerede visuelle elementer jævnt på lærredet.

![Skærmbillede af rapportlærredet, der viser, hvordan gitterlinjer og fastgørelsesgitre anvendes i Power BI Desktop-rapporter.](media/desktop-gridlines-snap-to-grid/snap-to-grid_0.png)

## <a name="enabling-gridlines-and-snap-to-grid"></a>Aktivér gitterlinjer og fastgørelse til gitter
Hvis du vil aktivere gitterlinjer og fastgørelse til gitter, skal du vælge båndet **Vis** og derefter markere afkrydsningsfeltet for **Vis gitterlinjer** og **Fastgør objekter til gitter**. Du kan vælge begge indstillinger. De fungerer uafhængigt af hinanden.

![Skærmbillede af rapportlærredet, der viser, hvordan gitterlinjer og fastgørelsesgitre aktiveres i Power BI Desktop-rapporter.](media/desktop-gridlines-snap-to-grid/snap-to-grid_1.png)

> [!NOTE]
> Hvis **Vis gitterlinjer** og **Fastgør objekter til gitter** er deaktiveret, kan du oprette forbindelse til en datakilde for at aktivere dem.

## <a name="using-gridlines"></a>Brug af gitterlinjer
Gitterlinjer er synlige vejledninger, der hjælper dig med at justere dine visuelle elementer. Når du forsøger at se, om to (eller flere) visuelle elementer står korrekt vandret eller lodret, kan du bruge gitterlinjerne til at se, om kanterne flugter med hinanden.

Brug Ctrl + klik til at markere mere end ét visuelt element ad gangen. Herved vises kanterne for alle de markerede visuelle elementer, så du kan se, om de flugter med hinanden.

![Skærmbillede af rapportlærredet, der viser, hvordan du justerer dine visuelle elementer ved hjælp af gitterlinjer.](media/desktop-gridlines-snap-to-grid/snap-to-grid_2.png)

### <a name="using-gridlines-inside-visuals"></a>Brug af gitterlinjer i visuelle elementer
I Power BI er der også gitterlinjer inden i de visuelle elementer. De fungerer som synlige hjælpelinjer ved sammenligning af datapunkter og værdier. Fra og med versionen af **Power BI Desktop** fra september 2017 kan du nu administrere gitterlinjerne i visuelle elementer ved hjælp af kortet **X-akse** eller **Y-akse** (afhængigt af typen af visuelt element), der findes i sektionen **Format** i ruden **Visualiseringer**. Du kan administrere følgende gitterlinjeelementer i et visuelt element:

* Slå gitterlinjer til eller fra
* Skift farve på gitterlinjer
* Juster stregen (tykkelsen) i gitterlinjer
* Vælg stregtypen for gitterlinjerne i det visuelle element, f.eks. udfyldt, stiplet eller prikket

Det kan især være en god ide at ændre bestemte elementer i gitterlinjer i rapporter, hvor der bruges en mørk baggrund til visuelle elementer. På følgende billede vises sektionen **Gitterlinjer** på kortet **Y-akse**.

![Skærmbillede af en visualisering, der viser afsnittet Gitterlinjer på Y-aksekortet.](media/desktop-gridlines-snap-to-grid/snap-to-grid_9.png)

## <a name="using-snap-to-grid"></a>Brug fastgørelse til gitter
Når du aktiverer **Fastgør objekter til gitter**, justeres alle visuelle elementer på lærredet i **Power BI Desktop**, som du flytter (eller ændrer størrelsen på), automatisk i forhold til den nærmeste akse i gitteret for at sikre, at to eller flere visuelle elementer justeres i forhold til den samme vandrette eller lodrette placering eller størrelse.

![Skærmbillede af lærredet, der viser, hvordan gitterlinjer og fastgørelsesgitter kan sikre, at de visuelle elementer i dine rapporter justeres pænt.](media/desktop-gridlines-snap-to-grid/snap-to-grid_3.png)

Og det er det eneste, du skal vide om at bruge **gitterlinjer** og **fastgørelse til gitter** for at sikre, at de visuelle elementer i dine rapporter er justeret, som de skal.

## <a name="using-z-order-align-and-distribute"></a>Brug z-rækkefølge, justering og fordeling
Du kan styre, hvilken rækkefølge de visuelle elementer i en rapport skal vises i fra forrest til bagest. Det kaldes ofte elementernes *z-rækkefølge*. Med denne funktion kan du overlappe visuelle elementer, som du ønsker det, og derefter justere rækkefølgen fra forreste til bageste element. Du kan angive rækkefølgen for de visuelle elementer med knapperne **Flyt fremad** og **Flyt bagud** i afsnittet **Arranger** af båndet **Formater**. Båndet **Formater** vises, når du har markeret et eller flere visuelle elementer på siden.

![Skærmbillede af rapportlærredet, der viser, hvordan du kan administrere rækkefølgen af visuelle elementer i en rapport.](media/desktop-gridlines-snap-to-grid/snap-to-grid_4.png)

Med båndet **Formater** kan du justere dine visuelle elementer på mange forskellige måder, så de vises på siden på den måde, der ser bedst ud og fungerer bedst.

![Skærmbillede af rapportlærredet, der viser, hvordan du kan justere dine visuelle elementer på mange forskellige måder.](media/desktop-gridlines-snap-to-grid/snap-to-grid_5.png)

Med knappen **Juster** justeres det markerede visuelle element til kanten (eller midten) af rapportlærredet som vist på følgende billede.

![Skærmbillede af rapportlærredet, der viser, hvordan du justerer et markeret visuelt element på kanten (eller i midten) af lærredet med knappen Juster.](media/desktop-gridlines-snap-to-grid/snap-to-grid_6.png)

Når to eller flere visuelle elementer er markeret, justeres de sammen og bruger den eksisterende justerede grænse for de visuelle elementer til justering. Hvis du for eksempel markerer to visuelle elementer og klikker på knappen **Venstrejuster**, justeres de visuelle elementer ud fra den grænse, der er længst til venstre for de valgte visuelle elementer.

![Skærmbillede af rapportlærredet, der viser, hvordan du justerer to visuelle elementer ved hjælp af indstillingen Juster til venstre.](media/desktop-gridlines-snap-to-grid/snap-to-grid_7.png)

Du kan også fordele dine visuelle elementer jævnt over hele rapportlærredet lodret eller vandret. Du skal bare bruge knappen **Fordel** på båndet **Format**.

![Skærmbillede af rapportlærredet, hvor du kan se, hvordan du fordeler dine visuelle elementer jævnt på tværs af lærredet ved hjælp af indstillingen Fordel.](media/desktop-gridlines-snap-to-grid/snap-to-grid_8.png)

Med bare et par indstillinger i disse værktøjer til gitterlinjer, justering og fordeling kommer dine rapporter til at se ud, som du ønsker det.

