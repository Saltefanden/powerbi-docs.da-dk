---
title: Funktionen supportsMultiVisualSelection
description: I denne artikel beskrives det, hvordan du bruger funktionen supportsMultiVisualSelection i Power BI-visualiseringer, og de tilhørende krav.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 04/30/2020
ms.openlocfilehash: 091bdeb4eeb4c979ccf0e79476eb081895fae2e1
ms.sourcegitcommit: 50b21718a167c2b131313b4135c8034c6f027597
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 10/14/2020
ms.locfileid: "92049401"
---
# <a name="use-the-supportsmultivisualselection-feature"></a>Brug af funktionen supportsMultiVisualSelection

Funktionen `supportsMultiVisualSelection` gør det muligt for dig at bruge markering i flere visualiseringer i en rapport.

## <a name="example"></a>Eksempel

I en rapport med mere end én visualisering skal du vælge to værdier for at få disse værdier til at gælde for andre visualiseringer. I [eksemplet på en detailhandelsanalyse](../../create-reports/sample-retail-analysis.md) kan du f.eks. vælge **Fashions Direct** i én visualisering. Vælg Ctrl og **Jan** i en anden visualisering. I rapporten gælder dine valg for de andre visualiseringer, der understøtter brug af denne funktion. Andre visualiseringer fokuserer nu på **Fashions Direct** og **Jan**.

## <a name="requirements"></a>Krav

Denne funktion kræver API v 3.2.0 eller nyere.

Du kan ikke anvende denne funktion på billedvisualiseringer. Der er visse avancerede visualiseringer, du ikke kan anvende den for, f.eks. nøgleperson, opdelingstræ, Spørgsmål og svar-visualiseringer, tekstfelt og målerdiagrammer.

## <a name="usage"></a>Forbrug

Hvis du vil bruge funktionen `supportsMultiVisualSelection`, skal du føje følgende kode til filen `capabilities.json` i visualiseringen.

```json
    {   
            ...
        "supportsMultiVisualSelection": true
            ...
    }
```

## <a name="next-steps"></a>Næste trin

Du kan få mere at vide om Power BI-koncepter i [Visualiseringer i Power BI](power-bi-visuals-concept.md).

Hvis du vil prøve Power BI-udvikling, kan du se [Udvikling af et Power BI-cirkelkort](develop-circle-card.md).
