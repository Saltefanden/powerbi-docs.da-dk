---
title: Føj en genvejsmenu til Power BI-visual
description: Få mere at vide om, hvordan du føjer en genvejsmenu til en Power BI-visualisering.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
manager: rkarlin
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 06/18/2019
ms.openlocfilehash: 9e63a1196ddc7557fcf8b2fceb424415a63d4df9
ms.sourcegitcommit: 6bc66f9c0fac132e004d096cfdcc191a04549683
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2020
ms.locfileid: "91748074"
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
