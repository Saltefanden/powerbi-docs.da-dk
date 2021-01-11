---
title: Føj eksterne biblioteker til dine Power BI-visualiseringer i en integreret Power BI-analyse for at få bedre integreret BI-indsigt
description: I denne artikel beskrives det, hvordan du bruger eksterne biblioteker i Power BI-visualiseringer. Aktivér bedre integreret BI-indsigt ved hjælp af Power BI-integreret analyse.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 02/24/2020
ms.openlocfilehash: b9a443040384e4d38bd7440eae0a5582cc422836
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 01/05/2021
ms.locfileid: "97889173"
---
# <a name="adding-external-libraries"></a>Tilføjelse af eksterne biblioteker

I denne artikel beskrives det, hvordan du bruger eksterne biblioteker i Power BI-visualiseringer. Den indeholder oplysninger om, hvordan du installerer, importerer og kalder eksterne biblioteker fra Power BI-visualiseringens kode.

## <a name="javascript-libraries"></a>JavaScript-biblioteker

1. Installér et eksternt JavaScript-bibliotek ved hjælp af en pakkeadministrator, f.eks. *npm* eller *yarn*.
2. Importér de nødvendige moduler til kildefilerne ved hjælp af det eksterne bibliotek.

>[!NOTE]
>Hvis du vil tilføje indtastninger i JavaScript-biblioteket og have mulighed for at bruge IntelliSense og kompileringssikkerhed, skal du sørge for at installere den relevante pakke.

### <a name="installing-the-d3-library"></a>Installation af d3-biblioteket

Dette er et eksempel på installation af [d3-biblioteket](https://www.npmjs.com/package/d3) og [@types/d3](https://www.npmjs.com/package/@types/d3)-pakken ved hjælp af [npm](https://www.npmjs.com/).

Hvis du vil se et komplet eksempel, kan du se koden til [Power BI-visualiseringer](https://github.com/microsoft/powerbi-visuals-gantt/blob/master/src/gantt.ts#L29).

1. Installer *d3-pakken* og *d3-typepakken*.

    ```powershell
    npm install d3@5 --save
    npm install @types/d3@5 --save
    ```

2. Importér *d3*-biblioteket i de filer, der bruger biblioteket, f.eks. `visual.ts`.

    ```typescript
    import * as d3 from "d3";
    ```

## <a name="css-framework"></a>CSS-struktur

1. Installér en ekstern CSS-struktur ved hjælp af en pakkeadministrator, f.eks. *npm* eller *yarn*.
2. I filen `.less` for visualiseringen skal du medtage `import`-sætningen.

### <a name="installing-bootstrap"></a>Installation af bootstrap

Dette er et eksempel på installation af [bootstrap](https://www.npmjs.com/package/bootstrap) ved hjælp af [npm](https://www.npmjs.com/).

Hvis du vil se et komplet eksempel, kan du se koden til [Power BI-visualiseringer](https://github.com/Microsoft/powerbi-visuals-sankey/blob/c8200da56913cd8b253be949a35fad0f4472b6de/style/visual.less#L32).

1. Installér *bootstrap-pakken*.

    ```powershell
    npm install bootstrap --save
    ```

2. Medtag sætningen `import` i `visual.less`.

    ```less
    @import (less) "node_modules/bootstrap/dist/css/bootstrap.css";
    ```
