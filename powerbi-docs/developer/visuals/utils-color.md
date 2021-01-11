---
title: Introduktion til brug af farvehjælpeprogrammer i Power BI-visualiseringer i en integreret Power BI-analyse for at opnå bedre integreret BI-indsigt
description: I denne artikel beskrives det, hvordan brugen af farvehjælpeprogrammer forenkler anvendelsen af temaer og paletter for visualiseringens datapunkter i Power BI-visualiseringer. Aktivér bedre integreret BI-indsigt ved hjælp af Power BI-integreret analyse.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 02/14/2020
ms.openlocfilehash: cc75188d806d653766860b2fada9028477a75f71
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 01/05/2021
ms.locfileid: "97887839"
---
# <a name="color-utils"></a>Hjælpeprogrammer til farver
Denne artikel kan hjælpe dig med at installere, importere og bruge hjælpeprogrammer til farver. I denne artikel beskrives det, hvordan brugen af farvehjælpeprogrammer forenkler anvendelsen af temaer og paletter for visualiseringens datapunkter i Power BI-visualiseringer.

## <a name="requirements"></a>Krav
Hvis du vil bruge pakken, skal du have følgende:
* [node.js](https://nodejs.org) (den nyeste LTS-version anbefales)
* [npm](https://www.npmjs.com/) (som minimum understøttes version 3.0.0)
* Den brugerdefinerede visualisering, der er oprettet af [PowerBI-visuals-tools](https://www.npmjs.com/package/powerbi-visuals-tools)

## <a name="installation"></a>Installation

Hvis du vil installere pakken, skal du køre følgende kommando i mappen med din aktuelle visual:

```bash
npm install powerbi-visuals-utils-colorutils --save
```
Med denne kommando installeres pakken, og der tilføjes en pakke som en afhængighed af din ```package.json```

## <a name="usage"></a>Brug

For at bruge interaktivitetsutils skal du importere den påkrævede komponent i visual'ets kildekode.
```typescript
import { ColorHelper } from "powerbi-visuals-utils-colorutils";
```

Få mere at vide om, hvordan du installerer og bruger ColorUtils i dine Power BI-visuals:

* [Usage Guide] Brugervejledningen indeholder en beskrivelse af en offentlig API til pakken. Du kan finde en beskrivelse og et par eksempler til hver offentlige grænseflade for pakken.

Denne pakke indeholder følgende klasser og moduler:
* [ColorHelper](#colorhelper) – hjælper med at generere forskellige farver til dine diagramværdier
* [colorUtils](#colorutils) – hjælper med at konvertere farveformater

## `ColorHelper`
Klassen `ColorHelper` omfatter følgende funktioner og metoder:

### `getColorForSeriesValue` 
Denne metode henter farven for den angivne serieværdi. Hvis der ikke er angivet nogen eksplicit farve eller standardfarve, tildeles farven fra farveskalaen for denne serie.
```typescript
getColorForSeriesValue(objects: IDataViewObjects, value: PrimitiveValue, themeColorName?: ThemeColorName): string;
```
#### <a name="example"></a>Eksempel
```typescript
import powerbi from "powerbi-visuals-api";
import { ColorHelper } from "powerbi-visuals-utils-colorutils";

import DataViewObjects = powerbi.DataViewObjects;

import DataViewValueColumns = powerbi.DataViewValueColumns;
import DataViewValueColumnGroup = powerbi.DataViewValueColumnGroup;
import DataViewObjectPropertyIdentifier = powerbi.DataViewObjectPropertyIdentifier;

import IVisual = powerbi.extensibility.visual.IVisual;
import IColorPalette = powerbi.extensibility.IColorPalette;
import VisualUpdateOptions = powerbi.extensibility.visual.VisualUpdateOptions;
import VisualConstructorOptions = powerbi.extensibility.visual.VisualConstructorOptions;

export class YourVisual implements IVisual {
    // Implementation of IVisual

    private colorPalette: IColorPalette;

    constructor(options: VisualConstructorOptions) {
        this.colorPalette = options.host.colorPalette;
    }

    public update(visualUpdateOptions: VisualUpdateOptions): void {
        const valueColumns: DataViewValueColumns = visualUpdateOptions.dataViews[0].categorical.values,
            grouped: DataViewValueColumnGroup[] = valueColumns.grouped(),
            defaultDataPointColor: string = "green",
            fillProp: DataViewObjectPropertyIdentifier = {
                objectName: "objectName",
                propertyName: "propertyName"
            };

        let colorHelper: ColorHelper = new ColorHelper(
            this.colorPalette,
            fillProp,
            defaultDataPointColor);

        for (let i = 0; i < grouped.length; i++) {
            let grouping: DataViewValueColumnGroup = grouped[i];

            let color = colorHelper.getColorForSeriesValue(grouping.objects, grouping.name); // returns a color of the series
        }
    }
}
```

### `getColorForMeasure`
Denne metode henter farven for den angivne måling.
```typescript
 getColorForMeasure(objects: IDataViewObjects, measureKey: any, themeColorName?: ThemeColorName): string;
```
#### <a name="example"></a>Eksempel
```typescript
import powerbi from "powerbi-visuals-api";
import { ColorHelper } from "powerbi-visuals-utils-colorutils";

import DataViewObjects = powerbi.DataViewObjects;
import IVisual = powerbi.extensibility.visual.IVisual;
import IColorPalette = powerbi.extensibility.IColorPalette;
import VisualUpdateOptions = powerbi.extensibility.visual.VisualUpdateOptions;
import DataViewObjectPropertyIdentifier = powerbi.DataViewObjectPropertyIdentifier;
import VisualConstructorOptions = powerbi.extensibility.visual.VisualConstructorOptions;

export class YourVisual implements IVisual {
    // Implementation of IVisual

    private colorPalette: IColorPalette;

    constructor(options: VisualConstructorOptions) {
        this.colorPalette = options.host.colorPalette;
    }

    public update(visualUpdateOptions: VisualUpdateOptions): void {
        const objects: DataViewObjects = visualUpdateOptions.dataViews[0].categorical.categories[0].objects[0],
            defaultDataPointColor: string = "green",
            fillProp: DataViewObjectPropertyIdentifier = {
                objectName: "objectName",
                propertyName: "propertyName"
            };

        let colorHelper: ColorHelper = new ColorHelper(
            this.colorPalette,
            fillProp,
            defaultDataPointColor);

        let color = colorHelper.getColorForMeasure(objects, ""); // returns a color
    }
}
```

### <a name="static-normalizeselector"></a>statisk `normalizeSelector`
Denne metode returnerer den normaliserede vælger
```typescript
static normalizeSelector(selector: Selector, isSingleSeries?: boolean): Selector;
```
#### <a name="example"></a>Eksempel
```typescript
import ISelectionId = powerbi.visuals.ISelectionId;
import { ColorHelper } from "powerbi-visuals-utils-colorutils";

let selectionId: ISelectionId = ...;
let selector = ColorHelper.normalizeSelector(selectionId.getSelector(), false);
```

Metoden `getThemeColor` og `getHighContrastColor` er begge relateret til farvetemafarver.
`ColorHelper` har også egenskaben `isHighContrast`, der er nyttig til kontrol.

### `getThemeColor`
Denne metode returnerer en temafarve
```typescript
 getThemeColor(themeColorName?: ThemeColorName): string;
```
### `getHighContrastColor`
 Denne metode returnerer en farve for højkontrasttilstanden
```typescript
getHighContrastColor(themeColorName?: ThemeColorName, defaultColor?: string): string;
```
#### <a name="example-related-to-high-contrast-mode-usage"></a>Eksempel relateret til højkontrasttilstand:
```typescript

import { ColorHelper } from "powerbi-visuals-utils-colorutils";

export class MyVisual implements IVisual {
        private colorHelper: ColorHelper;

        private init(options: VisualConstructorOptions): void {
            this.colors = options.host.colorPalette;
            this.colorHelper = new ColorHelper(this.colors);
        } 

            private createViewport(element: HTMLElement): void {
                const fontColor: string = "#131aea";
                const axisBackgroundColor: string = this.colorHelper.getThemeColor();
                
                // some d3 code before
                d3ElementName.attr("fill", colorHelper.getHighContrastColor("foreground", fontColor);
            }
                
            public static parseSettings(dataView: DataView, colorHelper: ColorHelper): VisualSettings {
                // some code that should be applied on formatting settings
                if (colorHelper.isHighContrast) {
                        this.settings.fontColor = colorHelper.getHighContrastColor("foreground", this.settings.fontColor);
                    }
            }
}
```


## `ColorUtils`
 Modulet indeholder følgende funktioner:

* [hexToRGBString](#hextorgbstring)
* [rotate](#rotate)
* [parseColorString](#parsecolorstring)
* [calculateHighlightColor](#calculatehighlightcolor)
* [createLinearColorScale](#createlinearcolorscale)
* [shadeColor](#shadecolor)
* [rgbBlend](#rgbblend)
* [channelBlend](#channelblend)
* [hexBlend](#hexblend)

### <a name="hextorgbstring"></a>hexToRGBString
Konverterer hex-farve til RGB-streng.

```typescript
function hexToRGBString(hex: string, transparency?: number): string
```

#### <a name="example"></a>Eksempel

```typescript
import  { hexToRGBString } from "powerbi-visuals-utils-colorutils";

hexToRGBString('#112233');

// returns: "rgb(17,34,51)"
```

### <a name="rotate"></a>rotate
Roterer RGB-farve.

```typescript
function rotate(rgbString: string, rotateFactor: number): string
```

#### <a name="example"></a>Eksempel

```typescript
import { rotate } from "powerbi-visuals-utils-colorutils";

rotate("#CC0000", 0.25); // returns: #66CC00
```

### <a name="parsecolorstring"></a>parseColorString
Fortolker en vilkårlig farvestreng til RGB-format.

```typescript
function parseColorString(color: string): RgbColor
```

#### <a name="example"></a>Eksempel

```typescript
import { parseColorString } from "powerbi-visuals-utils-colorutils";

parseColorString('#09f');
// returns: {R: 0, G: 153, B: 255 }

parseColorString('rgba(1, 2, 3, 1.0)');
// returns: {R: 1, G: 2, B: 3, A: 1.0 }
```

### <a name="calculatehighlightcolor"></a>calculateHighlightColor
Beregner fremhævningsfarven fra rgbColor baseret på lumianceThreshold og delta.

```typescript
function calculateHighlightColor(rgbColor: RgbColor, lumianceThreshold: number, delta: number): string
```

#### <a name="example"></a>Eksempel

```typescript
import { calculateHighlightColor } from "powerbi-visuals-utils-colorutils";

let yellow = "#FFFF00",
    yellowRGB = parseColorString(yellow);

calculateHighlightColor(yellowRGB, 0.8, 0.2);

// returns: '#CCCC00'
```

### <a name="createlinearcolorscale"></a>createLinearColorScale
Returnerer en lineær farveskala for et bestemt domæne af tal.

```typescript
function createLinearColorScale(domain: number[], range: string[], clamp: boolean): LinearColorScale
```

#### <a name="example"></a>Eksempel

```typescript
import { createLinearColorScale } from "powerbi-visuals-utils-colorutils";

let scale = ColorUtility.createLinearColorScale(
    [0, 1, 2, 3, 4],
    ["red", "green", "blue", "black", "yellow"],
    true);

scale(1); // returns: green
scale(10); // returns: yellow
```

### <a name="shadecolor"></a>shadeColor
Konverterer streng-hex-udtryk til tal, beregner procentdel samt R-, G- og B-kanaler.
Anvender procent for hver kanal og returnerer en hexadecimalværdi som streng med pundtegn.

```typescript
function shadeColor(color: string, percent: number): string
```

#### <a name="example"></a>Eksempel

```typescript
import { shadeColor } from "powerbi-visuals-utils-colorutils";

shadeColor('#000000', 0.1); // returns '#1a1a1a'
shadeColor('#FFFFFF', -0.5); // returns '#808080'
shadeColor('#00B8AA', -0.25); // returns '#008a80'
shadeColor('#00B8AA', 0); // returns '#00b8aa'
```

### <a name="rgbblend"></a>rgbBlend
Overlejrer en farve med uigennemsigtighed over en baggrundsfarve. En alfakanal ignoreres.

```typescript
function rgbBlend(foreColor: RgbColor, opacity: number, backColor: RgbColor): RgbColor
```

#### <a name="example"></a>Eksempel

```typescript
import { rgbBlend} from "powerbi-visuals-utils-colorutils";

rgbBlend({R: 100, G: 100, B: 100}, 0.5, {R: 200, G: 200, B: 200});

// returns: {R: 150, G: 150, B: 150}
```

### <a name="channelblend"></a>channelBlend
Blander en enkelt kanal til to farver.

```typescript
function channelBlend(foreChannel: number, opacity: number, backChannel: number): number
```

#### <a name="example"></a>Eksempel

```typescript
import { channelBlend} from "powerbi-visuals-utils-colorutils";

channelBlend(0, 1, 255); // returns: 0
channelBlend(128, 1, 255); // returns: 128
channelBlend(255, 0, 0); // returns: 0
channelBlend(88, 0, 88); // returns: 88
```

### <a name="hexblend"></a>hexBlend
Overlejrer en farve med uigennemsigtighed over en baggrundsfarve.

```typescript
function hexBlend(foreColor: string, opacity: number, backColor: string): string
```

#### <a name="example"></a>Eksempel

```typescript
import { hexBlend} from "powerbi-visuals-utils-colorutils";

let yellow = "#FFFF00",
    black = "#000000",
    white = "#FFFFFF";

hexBlend(yellow, 0.5, white); // returns: "#FFFF80"
hexBlend(white, 0.5, yellow); // returns: "#FFFF80"

hexBlend(yellow, 0.5, black); // returns: "#808000"
hexBlend(black, 0.5, yellow); // returns: "#808000"
```