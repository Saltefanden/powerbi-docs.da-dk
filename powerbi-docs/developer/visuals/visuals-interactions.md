---
title: Visuelle interaktioner i Power BI-visualiseringer i en integreret Power BI-analyse for at få bedre integreret BI-indsigt
description: I denne artikel beskrives det, hvordan du kontrollerer, om visualiseringer i Power BI tillader visuelle interaktioner. Aktivér bedre integreret BI-indsigt ved hjælp af Power BI-integreret analyse.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 06/18/2019
ms.openlocfilehash: a5b46e901b5e8cabc00d48e4ef307b2ae98de2b6
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 01/05/2021
ms.locfileid: "97888506"
---
# <a name="visual-interactions-in-power-bi-visuals"></a>Interaktioner mellem visualiseringer i Power BI

Visualiseringer kan forespørge om værdien af flaget `allowInteractions`, som angiver, om visualiseringen skal tillade visuelle interaktioner. Visualiseringer er f.eks. interaktive i forbindelse med visning eller redigering af en rapport, men ikke når de vises på et dashboard. Disse interaktioner er *klik*, *panorering*, *zoom*, *markeringer* m. fl. 

> [!NOTE]
> Du skal aktivere værktøjstip i alle scenarier, uanset hvilket flag der er angivet.

Flaget `allowInteractions` overføres som en boolesk værdi under initialiseringen af en visualisering som et medlem af grænsefladen IVisualHost.

I ethvert Power BI-scenarie, der kræver, at visualiseringer ikke er interaktive (f.eks. ved dashboardfelter), angives flaget `allowInteractions` som `false`. Ellers angives `allowInteractions` til `true` (f.eks. Rapport).

Du kan finde flere oplysninger i [lageret med SampleBarChart-visualiseringen](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/59a47935d8f5272ce145fe804193599ddb7e2001).

```typescript
   ...
   let allowInteractions = options.host.allowInteractions;
   bars.on('click', function(d) {
       if (allowInteractions) {
           selectionManager.select(d.selectionId);
           ...
       }
   });
```
