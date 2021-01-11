---
title: Føj en kontekstmenu til en Power BI-visualisering i en integreret Power BI-analyse for at få bedre integreret BI-indsigt
description: Få mere at vide om, hvordan du føjer en genvejsmenu til en Power BI-visualisering. Aktivér bedre integreret BI-indsigt ved hjælp af Power BI-integreret analyse.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
manager: rkarlin
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 06/18/2019
ms.openlocfilehash: 1c19ba94588628e002cdb9e65f59bd4182020e1c
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 01/05/2021
ms.locfileid: "97888690"
---
# <a name="add-context-menu-to-power-bi-visual"></a>Føj en genvejsmenu til Power BI-visual

Du kan bruge `selectionManager.showContextMenu()` med parametre `selectionId` og en placering (som et `{x:, y:}`-objekt) for at få Power BI til at vise en genvejsmenu for dit visual.

> [!IMPORTANT]
> `selectionManager.showContextMenu()` blev introduceret i API 2.2.0 til visuals.

Den tilføjes typisk som en højreklikhændelse (eller langt tryk for touchenheder), og der blev tilføjet en genvejsmenu til eksempelsøjlediagrammet til reference:

```typescript
    public update(options: VisualUpdateOptions) {
        //...
        //handle context menu
        this.svg.on('contextmenu', () => {
            const mouseEvent: MouseEvent = d3.event as MouseEvent;
            const eventTarget: EventTarget = mouseEvent.target;
            let dataPoint = d3.select(eventTarget).datum();
            this.selectionManager.showContextMenu(dataPoint? dataPoint.selectionId : {}, {
                x: mouseEvent.clientX,
                y: mouseEvent.clientY
            });
            mouseEvent.preventDefault();
        });
```
