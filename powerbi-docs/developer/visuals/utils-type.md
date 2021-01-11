---
title: Introduktion til brug af typehjælpeprogrammer i Power BI-visualiseringer i en integreret Power BI-analyse for at opnå bedre integreret BI-indsigt
description: I denne artikel beskrives det, hvordan du bruger SVG-hjælpeprogrammer til udvidelse af basistyperne for Power BI-visualiseringer. Aktivér bedre integreret BI-indsigt ved hjælp af Power BI-integreret analyse.
author: KesemSharabi
ms.author: kesharab
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 06/18/2019
ms.openlocfilehash: 4f81f55f8d5cfc54020b3b4e02e8be55fb65b0d1
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 01/05/2021
ms.locfileid: "97888115"
---
# <a name="type-utils"></a>Hjælpeprogrammer til typer

Typehjælpeprogrammer er en række funktioner og klasser, der udvider basistyperne for Power BI-visuals.

## <a name="installation"></a>Installation

Hvis du vil installere pakken, skal du køre følgende kommando i mappen med din aktuelle brugerdefinerede visual:

npm install powerbi-visuals-utils-typeutils --save Denne kommando installerer pakken og føjer en pakke til package.json som en afhængighed

## <a name="double"></a>Double

`Double` giver mulighed for at ændre tallenes præcision.

Modulet indeholder følgende funktioner:

### <a name="pow10"></a>pow10

Denne funktion returnerer potensen af 10.

```typescript
function pow10(exp: number): number;
```

Eksempel:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.pow10(25);

// returns: 1e+25
```

### <a name="log10"></a>log10

Denne funktion returnerer 10-basislogaritme for tallet.

```typescript
function log10(val: number): number;
```

Eksempel:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.log10(25);

// returns: 1
```

## <a name="getprecision"></a>getPrecision

Denne funktion returnerer potensen af 10, der repræsenterer tallets præcision.

```typescript
function getPrecision(x: number, decimalDigits?: number): number;
```

Eksempel:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.getPrecision(562344, 6);

// returns: 0.1
```

### <a name="equalwithprecision"></a>equalWithPrecision

Denne funktion kontrollerer, om en delta mellem to tal er mindre end den angivne præcision.

```typescript
function equalWithPrecision(x: number, y: number, precision?: number): boolean;
```

Eksempel:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.equalWithPrecision(1, 1.005, 0.01);

// returns: true
```

### <a name="lesswithprecision"></a>lessWithPrecision

Denne funktion kontrollerer, om den første værdi er mindre end den anden værdi.

```typescript
function lessWithPrecision(x: number, y: number, precision?: number): boolean;
```

Eksempel:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.lessWithPrecision(0.995, 1, 0.001);

// returns: true
```

### <a name="lessorequalwithprecision"></a>lessOrEqualWithPrecision

Denne funktion kontrollerer, om den første værdi er mindre end eller lig med den anden værdi.

```typescript
function lessOrEqualWithPrecision(x: number, y: number, precision?: number): boolean;
```

Eksempel:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.lessOrEqualWithPrecision(1.005, 1, 0.01);

// returns: true
```

### <a name="greaterwithprecision"></a>greaterWithPrecision

Denne funktion kontrollerer, om den første værdi er større end den anden værdi.

```typescript
function greaterWithPrecision(x: number, y: number, precision?: number): boolean;
```

Eksempel:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.greaterWithPrecision(1, 0.995, 0.01);

// returns: false
```

### <a name="greaterorequalwithprecision"></a>greaterOrEqualWithPrecision

Denne funktion kontrollerer, om den første værdi er større end eller lig med den anden værdi.

```typescript
function greaterOrEqualWithPrecision(x: number, y: number, precision?: number): boolean;
```

Eksempel:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.greaterOrEqualWithPrecision(1, 1.005, 0.01);

// returns: true
```

### <a name="floorwithprecision"></a>floorWithPrecision

Denne funktion nedrunder tallet med den angivne præcision.

```typescript
function floorWithPrecision(x: number, precision?: number): number;
```

Eksempel:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.floorWithPrecision(5.96, 0.001);

// returns: 5
```

### <a name="ceilwithprecision"></a>ceilWithPrecision

Denne funktion `ceils` tallet med den angivne præcision.

```typescript
function ceilWithPrecision(x: number, precision?: number): number;
```

Eksempel:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.ceilWithPrecision(5.06, 0.001);

// returns: 6
```

### <a name="floortoprecision"></a>floorToPrecision

Denne funktion nedrunder tallet til den angivne præcision.

```typescript
function floorToPrecision(x: number, precision?: number): number;
```

Eksempel:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.floorToPrecision(5.96, 0.1);

// returns: 5.9
```

### <a name="ceiltoprecision"></a>ceilToPrecision

Denne funktion `ceils` tallet til den angivne præcision.

```typescript
function ceilToPrecision(x: number, precision?: number): number;
```

Eksempel:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.ceilToPrecision(-506, 10);

// returns: -500
```

### <a name="roundtoprecision"></a>roundToPrecision

Denne funktion afrunder tallet til den angivne præcision.

```typescript
function roundToPrecision(x: number, precision?: number): number;
```

Eksempel:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.roundToPrecision(596, 10);

// returns: 600
```

### <a name="ensureinrange"></a>ensureInRange

Denne funktion returnerer et tal, der er mellem min. og maks.

```typescript
function ensureInRange(x: number, min: number, max: number): number;
```

Eksempel:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.ensureInRange(-27.2, -10, -5);

// returns: -10
```

### <a name="round"></a>round

Denne funktion afrunder tallet.

```typescript
function round(x: number): number;
```

Eksempel:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.round(27.45);

// returns: 27
```

### <a name="removedecimalnoise"></a>removeDecimalNoise

Denne funktion fjerner decimalstøj.

```typescript
function removeDecimalNoise(value: number): number;
```

Eksempel:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.removeDecimalNoise(21.493000000000002);

// returns: 21.493
```

### <a name="isinteger"></a>isInteger

Denne funktion kontrollerer, om tallet er et heltal.

```typescript
function isInteger(value: number): boolean;
```

Eksempel:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.isInteger(21.493000000000002);

// returns: false
```

### <a name="toincrement"></a>toIncrement

Denne funktion øger tallet gradvist med det angivne tal og returnerer det afrundede tal.

```typescript
function toIncrement(value: number, increment: number): number;
```

Eksempel:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.toIncrement(0.6383723, 0.05);

// returns: 0.65
```

## <a name="prototype"></a>Prototype

`Prototype` giver mulighed for at nedarve objekter.

Modulet indeholder følgende funktioner:

## <a name="inherit"></a>inherit

Denne funktion returnerer et nyt objekt med det angivne objekt som prototypen.

```typescript
function inherit<T>(obj: T, extension?: (inherited: T) => void): T;
```

Eksempel:

```typescript
import { prototype } from "powerbi-visuals-utils-typeutils";
// ...

let base = { Microsoft: "Power BI" };

prototype.inherit(base);

/* returns: {
    __proto__: {
        Microsoft: "Power BI"
    }
}*/
```

## <a name="inheritsingle"></a>inheritSingle

Denne funktion returnerer et nyt objekt med det angivne objekt som prototype, hvis, og kun hvis, prototypen ikke er angivet.

```typescript
function inheritSingle<T>(obj: T): T;
```

Eksempel:

```typescript
import { prototype } from "powerbi-visuals-utils-typeutils";
// ...

let base = { Microsoft: "Power BI" };

prototype.inheritSingle(base);

/* returns: {
    __proto__: {
        Microsoft: "Power BI"
    }
}*/
```

## <a name="pixelconverter"></a>PixelConverter

`PixelConverter` gør det muligt at konvertere pixel til punkter og punkter til pixel.

Modulet indeholder følgende funktioner:

## <a name="tostring"></a>toString

Denne funktion konverterer pixelværdien til en streng.

```typescript
function toString(px: number): string;
```

Eksempel:

```typescript
import { pixelConverter } from "powerbi-visuals-utils-typeutils";
// ...

pixelConverter.toString(25);

// returns: 25px
```

## <a name="frompoint"></a>fromPoint

Denne funktion konverterer den angivne punkt værdi til pixelværdien og returnerer strengfortolkningen.

```typescript
function fromPoint(pt: number): string;
```

Eksempel:

```typescript
import { pixelConverter } from "powerbi-visuals-utils-typeutils";
// ...

pixelConverter.fromPoint(8);

// returns: 33.33333333333333px
```

## <a name="frompointtopixel"></a>fromPointToPixel

Denne funktion konverterer den angivne punkt værdi til pixelværdien.

```typescript
function fromPointToPixel(pt: number): number;
```

Eksempel:

```typescript
import { pixelConverter } from "powerbi-visuals-utils-typeutils";
// ...

pixelConverter.fromPointToPixel(8);

// returns: 10.666666666666666
```

## <a name="topoint"></a>toPoint

Denne funktion konverterer pixelværdien til punktværdien.

```typescript
function toPoint(px: number): number;
```

Eksempel:

```typescript
import { pixelConverter } from "powerbi-visuals-utils-typeutils";
// ...

pixelConverter.toPoint(8);

// returns: 6
```
