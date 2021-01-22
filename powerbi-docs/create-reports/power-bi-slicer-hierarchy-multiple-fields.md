---
title: Føj flere felter til et hierarki-udsnitsværktøj
description: Få mere at vide om, hvordan du opretter et hierarkiudsnitsværktøj, der indeholder flere felter i et hierarki.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 01/19/2021
LocalizationGroup: Create reports
ms.openlocfilehash: abed7e9f6da352d5461868e6371ffefb814eb3ff
ms.sourcegitcommit: 96080432af4c8e3fe46c23274478ccffa0970efb
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 01/20/2021
ms.locfileid: "98597643"
---
# <a name="add-multiple-fields-to-a-hierarchy-slicer"></a>Føj flere felter til et hierarki-udsnitsværktøj

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-desktop](../includes/yes-desktop.md)] [!INCLUDE [yes-service](../includes/yes-service.md)]

Hvis du vil filtrere flere relaterede felter i et enkelt udsnitsværktøj, kan du gøre det ved at opbygge det, der kaldes et *hierarki-udsnitsværktøj*. Du kan oprette disse udsnitsværktøjer i enten Power BI Desktop eller i Power BI-tjenesten.

:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy.png" alt-text="Skærmbillede af hierarki-udsnitsværktøjet i Power BI.":::

Når du føjer flere felter til udsnittet, vises der som standard en pil eller *vinkel* ud for de elementer, der kan udvides, for at få elementerne på næste niveau vist.

:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy-arrow.png" alt-text="Skærmbillede af rullelisten til hierarki-udsnitsværktøjet i Power BI.":::
 
 
Når du vælger et eller flere underordnede til et element, kan du se en delvist markeret cirkel for elementet på øverste niveau.
 
:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy-semi-selected.png" alt-text="Skærmbillede af enkeltmarkeringstilstand for hierarki-udsnitsværktøjet i Power BI.":::

## <a name="format-the-slicer"></a>Formatér udsnittet

Funktionsmåden for udsnittet er ikke blevet ændret. Du kan også indstille dit udsnitsværktøj, som du vil. Du kan f.eks. angive det til enkeltmarkeringstilstand. Eller du kan skifte mellem en liste og en rullemenu. 

:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy-dropdown.png" alt-text="Skærmbillede af hierarki-udsnitsværktøjet, der er formateret som et rullelisteudsnitsværktøj.":::

Du kan også foretage følgende formateringsændringer.

### <a name="change-the-title"></a>Rediger titlen

Du kan redigere titlen på ethvert udsnitsværktøj, men det er især nyttigt til hierarki-udsnitsværktøjer. Navnet på et hierarki-udsnitsværktøj er som standard en liste over feltnavne i hierarkiet.

I dette eksempel viser titlen på udsnitsværktøjet de tre felter i hierarkiet: Type, Platform og Navn.

:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-title.png" alt-text="Skærmbillede af hierarki-udsnitsværktøjet med felterne Type, Platform og Navn.":::

Hvis du vil ændre navnet, skal du markere udsnitsværktøjet og derefter vælge ruden **Formatér**. Under **Header for udsnitsværktøj** kan du se det aktuelle navn på udsnitsværktøjet i feltet **Titeltekst**.

:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-edit-title.png" alt-text="Skærmbillede af ruden Formatér med den aktuelle titel.":::

Vælg teksten, og tilføj et nyt navn.

:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-new-title.png" alt-text="Skærmbillede af ny titel til hierarki-udsnitsværktøjet.":::


### <a name="change-the-expandcollapse-icon"></a>Rediger ikonet Udvid/skjul

Hierarki-udsnitsværktøjer har nogle andre formateringsindstillinger. Du kan ændre ikonet Udvid/skjul fra standard pilen til et plus-/minustegn eller en tekstmarkør.

1. Vælg udsnitsværktøjet, og vælg derefter **Format**.
1. Udvid **Elementer** og vælg **ikonet Udvid/skjul**.
1. Vælg mellem **Chevron**, **Plus/minus** og **Tekstmarkør**.
 
    :::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy-caret.png" alt-text="Skærmbillede af Vælg et udvid-/skjul-ikon til hierarki-udsnitsværktøjet.":::
 
### <a name="change-the-indentation"></a>Rediger indrykningen

Hvis der ikke er meget plads i din rapport, kan det være en god idé at reducere mængden, du rykker de underordnede elementer ind. Indrykningen er som standard 15 pixel, men du kan øge eller reducere værdien. 

1. Vælg udsnitsværktøjet, og vælg derefter **Format**.
1. Udvid **Elementer**, og træk **Trinvis layoutindrykning** mindre eller større. Du kan også blot angive et tal i feltet.

    :::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-indentation.png" alt-text="Angiv indrykningen for hierarki-udsnitsværktøjet.":::
    
## <a name="limitations-and-considerations"></a>Begrænsninger og overvejelser

- Til tabelmodeller kræver denne funktion SQL Server Analysis Services 2017 eller nyere.
- Til flerdimensionelle modeller kræver denne funktion SQL Server Analysis Services 2019 CU5 eller nyere med SuperDAXMD aktiveret. Læs mere om [SuperDAXMD](/analysis-services/multidimensional-models/dax-for-multidimensional-models#superdaxmd).

## <a name="next-steps"></a>Næste trin

- [Udsnitsværktøjer i Power BI](../visuals/power-bi-visualization-slicers.md)
- Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
