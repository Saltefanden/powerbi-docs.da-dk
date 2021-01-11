---
title: Introduktion til brug af SVG-hjælpeprogrammer i Power BI-visualiseringer i en integreret Power BI-analyse for at opnå bedre integreret BI-indsigt
description: I denne artikel beskrives det, hvordan du bruger SVG-hjælpeprogrammer til at forenkle SVG-manipulationer for Power BI-visualiseringer. Aktivér bedre integreret BI-indsigt ved hjælp af Power BI-integreret analyse.
author: KesemSharabi
ms.author: kesharab
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 06/18/2019
ms.openlocfilehash: cf798ae13d874e354f6941d50982bfe26d73424d
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 01/05/2021
ms.locfileid: "97887747"
---
# <a name="svg-utils"></a>SVG-hjælpeprogrammer

SVG-hjælpeprogrammer er en række funktioner og klasser til forenkling af SVG-manipulationer for Power BI-visuals

## <a name="installation"></a>Installation

Hvis du vil installere pakken, skal du køre følgende kommando i mappen med din aktuelle visual:

```bash
npm install powerbi-visuals-utils-svgutils --save
```

## <a name="cssconstants"></a>CssConstants

Modulet `CssConstants` omfatter den specielle funktion og grænseflade til arbejde med klassevælgere.

Modulet `powerbi.extensibility.utils.svg.CssConstants` indeholder følgende funktion og grænseflade:

## <a name="classandselector"></a>ClassAndSelector

Denne grænseflade beskriver almindelige egenskaber for klassevælgeren.

```typescript
interface ClassAndSelector {
  class: string;
  selector: string;
}
```

### <a name="createclassandselector"></a>createClassAndSelector

Denne funktion opretter en forekomst af ClassAndSelector med det angivne navn for klassen.

```typescript
function createClassAndSelector(className: string): ClassAndSelector;
```

Eksempel:

```typescript
import { CssConstants } from "powerbi-visuals-utils-svgutils";
import createClassAndSelector = CssConstants.createClassAndSelector;
import ClassAndSelector = CssConstants.ClassAndSelector;

let divSelector: ClassAndSelector = createClassAndSelector("sample-block");

divSelector.selector === ".sample-block"; // returns: true
divSelector.class === "sample-block"; // returns: true
```

## <a name="manipulation"></a>manipulation

`manipulation` indeholder nogle specielle funktioner til generering af strenge til brug sammen med SVG-transformationsegenskaben.

Modulet indeholder følgende funktioner:

### <a name="translate"></a>translate

Denne funktion opretter en translate-streng til brug sammen med SVG-transformationsegenskaben.

```typescript
function translate(x: number, y: number): string;
```

Eksempel:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.translate(100, 100);

// returns: translate(100,100)
```

### <a name="translatexwithpixels"></a>translateXWithPixels

Denne funktion opretter en translateX-streng til brug sammen med SVG-transformationsegenskaben.

```typescript
function translateXWithPixels(x: number): string;
```

Eksempel:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.translateXWithPixels(100);

// returns: translateX(100px)
```

### <a name="translatewithpixels"></a>translateWithPixels

Denne funktion opretter en translate-streng til brug sammen med SVG-transformationsegenskaben.

```typescript
function translateWithPixels(x: number, y: number): string;
```

Eksempel:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.translateWithPixels(100, 100);

// returns: translate(100px,100px)
```

### <a name="translateandrotate"></a>translateAndRotate

Denne funktion opretter en translate-rotate-streng til brug sammen med SVG-transformationsegenskaben.

```typescript
function translateAndRotate(
  x: number,
  y: number,
  px: number,
  py: number,
  angle: number
): string;
```

Eksempel:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.translateAndRotate(100, 100, 50, 50, 35);

// returns: translate(100,100) rotate(35,50,50)
```

### <a name="scale"></a>scale

Denne funktion opretter en scale-streng til brug sammen med en CSS-transformationsegenskab.

```typescript
function scale(scale: number): string;
```

Eksempel:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.scale(50);

// returns: scale(50)
```

### <a name="transformorigin"></a>transformOrigin

Denne funktion opretter en transform-origin-streng til brug sammen med en CSS-transformationsegenskab.

```typescript
function transformOrigin(xOffset: string, yOffset: string): string;
```

Eksempel:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.transformOrigin(5, 5);

// returns: 5 5
```

### <a name="flushalld3transitions"></a>flushAllD3Transitions

Denne funktion tvinger alle D3-overgange til at blive fuldført.

```typescript
function flushAllD3Transitions(): void;
```

Eksempel:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.flushAllD3Transitions();

// forces every transition of D3 to complete
```

### <a name="parsetranslatetransform"></a>parseTranslateTransform

Denne funktion fortolker transformationsstrengen med værdien "translate(x, y)".

```typescript
function parseTranslateTransform(input: string): { x: string; y: string };
```

Eksempel:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.parseTranslateTransform("translate(100px,100px)");

// returns: { "x":"100px", "y":"100px" }
```

### <a name="createarrow"></a>createArrow

Denne funktion opretter en pil.

```typescript
function createArrow(
  width: number,
  height: number,
  rotate: number
): { path: string; transform: string };
```

Eksempel:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.createArrow(10, 20, 5);

/* returns: {
    "path": "M0 0L0 20L10 10 Z",
    "transform": "rotate(5 5 10)"
}*/
```

## <a name="rect"></a>Rect

Modulet `Rect` indeholder nogle specielle funktioner, der kan bruges til manipulering af rektangler.

Modulet indeholder følgende funktioner:

### <a name="getoffset"></a>getOffset

Denne funktion returnerer en forskydning af rektanglet.

```typescript
function getOffset(rect: IRect): IPoint;
```

Eksempel:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.getOffset({ left: 25, top: 25, width: 100, height: 100 });

/* returns: {
    x: 25,
    y: 25
}*/
```

### <a name="getsize"></a>getSize

Denne funktion returnerer rektanglets størrelse.

```typescript
function getSize(rect: IRect): ISize;
```

Eksempel:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.getSize({ left: 25, top: 25, width: 100, height: 100 });

/* returns: {
    width: 100,
    height: 100
}*/
```

### <a name="setsize"></a>setSize

Denne funktion ændrer rektanglets størrelse.

```typescript
function setSize(rect: IRect, value: ISize): void;
```

Eksempel:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

let rectangle = { left: 25, top: 25, width: 100, height: 100 };

Rect.setSize(rectangle, { width: 250, height: 250 });

// rectangle === { left: 25, top: 25, width: 250, height: 250 }
```

### <a name="right"></a>right

Denne funktion returnerer en placering til højre af rektanglet.

```typescript
function right(rect: IRect): number;
```

Eksempel:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.right({ left: 25, top: 25, width: 100, height: 100 });

// returns: 125
```

### <a name="bottom"></a>bottom

Denne funktion returnerer en placering nederst af rektanglet.

```typescript
function bottom(rect: IRect): number;
```

Eksempel:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.bottom({ left: 25, top: 25, width: 100, height: 100 });

// returns: 125
```

### <a name="topleft"></a>topLeft

Denne funktion returnerer en placering øverst til venstre af rektanglet.

```typescript
function topLeft(rect: IRect): IPoint;
```

Eksempel:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.topLeft({ left: 25, top: 25, width: 100, height: 100 });

// returns: { x: 25, y: 25 }
```

### <a name="topright"></a>topRight

Denne funktion returnerer en placering øverst til højre af rektanglet.

```typescript
function topRight(rect: IRect): IPoint;
```

Eksempel:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.topRight({ left: 25, top: 25, width: 100, height: 100 });

// returns: { x: 125, y: 25 }
```

### <a name="bottomleft"></a>bottomLeft

Denne funktion returnerer en placering nederst til venstre af rektanglet.

```typescript
function bottomLeft(rect: IRect): IPoint;
```

Eksempel:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.bottomLeft({ left: 25, top: 25, width: 100, height: 100 });

// returns: { x: 25, y: 125 }
```

### <a name="bottomright"></a>bottomRight

Denne funktion returnerer en placering nederst til højre af rektanglet.

```typescript
function bottomRight(rect: IRect): IPoint;
```

### <a name="example"></a>Eksempel

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.bottomRight({ left: 25, top: 25, width: 100, height: 100 });

// returns: { x: 125, y: 125 }
```

### <a name="clone"></a>clone

Denne funktion opretter en kopi af rektanglet.

```typescript
function clone(rect: IRect): IRect;
```

Eksempel:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.clone({ left: 25, top: 25, width: 100, height: 100 });

/* returns: {
    left: 25, top: 25, width: 100, height: 100}
*/
```

### <a name="tostring"></a>toString

Denne funktion konverterer rektanglet til en streng.

```typescript
function toString(rect: IRect): string;
```

Eksempel:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.toString({ left: 25, top: 25, width: 100, height: 100 });

// returns: {left:25, top:25, width:100, height:100}
```

### <a name="offset"></a>offset

Denne funktion anvender en given forskydning på rektanglet.

```typescript
function offset(rect: IRect, offsetX: number, offsetY: number): IRect;
```

Eksempel:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.offset({ left: 25, top: 25, width: 100, height: 100 }, 50, 50);

/* returns: {
    left: 75,
    top: 75,
    width: 100,
    height: 100
}*/
```

### <a name="add"></a>add

Denne funktion føjer det første rektangel til det andet rektangel.

```typescript
function add(rect: IRect, rect2: IRect): IRect;
```

Eksempel:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.add(
  { left: 25, top: 25, width: 100, height: 100 },
  { left: 50, top: 50, width: 75, height: 75 }
);

/* returns: {
    left: 75,
    top: 75,
    height: 175,
    width: 175
}*/
```

### <a name="getclosestpoint"></a>getClosestPoint

Denne funktion returnerer rektanglets nærmeste punkt til det angivne punkt.

```typescript
function getClosestPoint(rect: IRect, x: number, y: number): IPoint;
```

Eksempel:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.getClosestPoint({ left: 0, top: 0, width: 100, height: 100 }, 50, 50);

/* returns: {
    x: 50,
    y: 50
}*/
```

### <a name="equal"></a>equal

Denne funktion sammenligner rektangler og returnerer sand, hvis de er identiske.

```typescript
function equal(rect1: IRect, rect2: IRect): boolean;
```

Eksempel:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.equal(
  { left: 0, top: 0, width: 100, height: 100 },
  { left: 50, top: 50, width: 100, height: 100 }
);

// returns: false
```

### <a name="equalwithprecision"></a>equalWithPrecision

Denne funktion sammenligner rektangler ved hjælp af værdiernes nøjagtighed.

```typescript
function equalWithPrecision(rect1: IRect, rect2: IRect): boolean;
```

Eksempel:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.equalWithPrecision(
  { left: 0, top: 0, width: 100, height: 100 },
  { left: 50, top: 50, width: 100, height: 100 }
);

// returns: false
```

### <a name="isempty"></a>isEmpty

Denne funktion kontrollerer, om rektanglet er tomt.

```typescript
function isEmpty(rect: IRect): boolean;
```

Eksempel:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.isEmpty({ left: 0, top: 0, width: 0, height: 0 });

// returns: true
```

### <a name="containspoint"></a>containsPoint

Denne funktion kontrollerer, om rektanglet indeholder punktet.

```typescript
function containsPoint(rect: IRect, point: IPoint): boolean;
```

Eksempel:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.containsPoint(
  { left: 0, top: 0, width: 100, height: 100 },
  { x: 50, y: 50 }
);

// returns: true
```

### <a name="isintersecting"></a>isIntersecting

Denne funktion kontrollerer, om rektangler overlapper hinanden.

```typescript
function isIntersecting(rect1: IRect, rect2: IRect): boolean;
```

Eksempel:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.isIntersecting(
  { left: 0, top: 0, width: 100, height: 100 },
  { left: 0, top: 0, width: 50, height: 50 }
);

// returns: true
```

### <a name="intersect"></a>intersect

Denne funktion returnerer et skæringspunkt for rektangler.

```typescript
function intersect(rect1: IRect, rect2: IRect): IRect;
```

Eksempel:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.intersect(
  { left: 0, top: 0, width: 100, height: 100 },
  { left: 0, top: 0, width: 50, height: 50 }
);

/* returns: {
    left: 0,
    top: 0,
    width: 50,
    height: 50
}*/
```

### <a name="combine"></a>combine

Denne funktion kombinerer rektangler.

```typescript
function combine(rect1: IRect, rect2: IRect): IRect;
```

Eksempel:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.combine(
  { left: 0, top: 0, width: 100, height: 100 },
  { left: 0, top: 0, width: 50, height: 120 }
);

/* returns: {
    left: 0,
    top: 0,
    width: 100,
    height: 120
}*/
```

### <a name="getcentroid"></a>getCentroid

Denne funktion returnerer rektanglets midtpunkt.

```typescript
function getCentroid(rect: IRect): IPoint;
```

Eksempel:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.getCentroid({ left: 0, top: 0, width: 100, height: 100 });

/* returns: {
    x: 50,
    y: 50
}*/
```

## <a name="pointer"></a>pointer

Modulet `pointer` indeholder en specialfunktion til hentning af markørens position.

Modulet indeholder følgende funktion:

### <a name="getcoordinates"></a>getCoordinates

Denne funktion returnerer markørens position.

```typescript
function getCoordinates(rootNode: Element, isPointerEvent: boolean): number[];
```

Eksempel:

```typescript
import { pointer } from "powerbi-visuals-utils-svgutils";

let bodySelection = d3.select("body");

bodySelection
  .append("div")
  .style({
    width: "100px",
    height: "100px",
    "background-color": "green"
  })
  .on("click", () => {
    pointer.getCoordinates(bodySelection.node(), true);
  });

// click element, after that you will get position of the pointer
```
