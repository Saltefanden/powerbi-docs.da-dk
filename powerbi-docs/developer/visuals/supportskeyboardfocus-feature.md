---
title: Funktionen supportsKeyboardFocus i en integreret Power BI-analyse, der giver bedre integreret BI-indsigt
description: I denne artikel beskrives det, hvordan du bruger funktionen supportsKeyboardFocus i Power BI-visualiseringer, og de tilhørende krav. Aktivér bedre integreret BI-indsigt ved hjælp af Power BI-integreret analyse.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 04/30/2020
ms.openlocfilehash: 5ba87db8118076de4bf13abc0280223f9f04f871
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 01/05/2021
ms.locfileid: "97887954"
---
# <a name="use-the-supportskeyboardfocus-feature"></a>Brug af funktionen supportsKeyboardFocus

I denne artikel beskrives det, hvordan du bruger funktionen `supportsKeyboardFocus` i Power BI-visualiseringer.
Funktionen `supportsKeyboardFocus` gør det muligt at navigere i datapunkterne i visualiseringen udelukkende ved hjælp af tastaturet.

Hvis du vil vide mere om tastaturnavigation til visualiseringer, kan du se [Tastaturnavigation](../../create-reports/desktop-accessibility-consuming-tools.md#keyboard-navigation).

## <a name="example"></a>Eksempel

Åbn en visualisering, der bruger funktionen `supportsKeyboardFocus`. Vælg et vilkårligt datapunkt i visualiseringen, og vælg tabulatoren. Fokus flyttes til det næste datapunkt, for hver gang du vælger tabulatoren. Vælg Enter for at markere det fremhævede datapunkt.

![Eksempel på fokus på understøttelse af tastatur](./media/supportskeyboardfocus-feature/supports-keyboard-focus-example.png)

## <a name="requirements"></a>Krav

Denne funktion kræver API v2.1.0 eller nyere.

Denne funktion kan anvendes på alle visualiseringer, undtagen billedvisualiseringer.

## <a name="usage"></a>Forbrug

Hvis du vil bruge funktionen `supportsKeyboardFocus`, skal du føje følgende kode til filen *capabilities.json* for visualiseringen.
Denne egenskab gør det muligt, at der fokuseres på visualiseringen gennem navigation på tastaturet.

```json
    {   
            ...
        "supportsKeyboardFocus": true
            ...
    }

```

## <a name="next-steps"></a>Næste trin

Du kan få mere at vide om tilgængelighedsfunktioner i [Design Power BI-rapporter om tilgængelighed](../../create-reports/desktop-accessibility-creating-reports.md).

Hvis du vil prøve Power BI-udvikling, kan du se [Udvikling af en Power BI-cirkelkortvisualisering](develop-circle-card.md).
