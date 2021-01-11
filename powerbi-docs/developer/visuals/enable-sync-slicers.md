---
title: Aktivér funktionen Synkroniser udsnit i Power BI-visualiseringer i en integreret Power BI-analyse for at få bedre integreret BI-indsigt
description: I denne artikel beskrives det, hvordan du føjer funktionen Synkroniser udsnitsværktøjer til visualiseringer i Power BI. Aktivér bedre integreret BI-indsigt ved hjælp af Power BI-integreret analyse.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 06/18/2019
ms.openlocfilehash: bd69e05bba3e9449f9fb6f07bd9625dfb1ea0c08
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 01/05/2021
ms.locfileid: "97885263"
---
# <a name="sync-slicers-in-power-bi-visuals"></a>Synkroniser udsnitsværktøjer i visualiseringer i Power BI

For at understøtte funktionen [Synkroniser udsnitsværktøjer](../../visuals/power-bi-visualization-slicers.md) skal dit brugerdefinerede visuelle udsnit bruge API-version 1.13.0 eller nyere.

Derudover skal du aktivere indstillingen i filen *capabilities.json* som vist i følgende kode:

```json
{
    ...
    "supportsHighlight": true,
    "suppressDefaultTitle": true,
    "supportsSynchronizingFilterState": true,
    "sorting": {
        "default": {}
    }
}
```

Når du har opdateret filen *capabilities.json*, kan du få vist ruden med indstillinger for **Synkroniser udsnitsværktøjer**, når du vælger det brugerdefinerede visuelle udsnit.

> [!NOTE]
> Funktionen Synkroniser udsnitsværktøjer understøtter ikke mere end ét felt. Hvis udsnittet har mere end ét felt (**kategori** eller **måling**), er funktionen deaktiveret.

![Ruden "Synkroniser udsnit"](media/enable-sync-slicers/sync-slicers-panel.png)

I ruden **Synkroniser udsnit** kan du se, at synligheden af og filtreringen med dit udsnit muligvis er anvendt på flere rapportsider.