---
title: Introduktion til brug af hjælpeprogrammer til værktøjstip i Power BI-visualiseringer i en integreret Power BI-analyse for at få bedre integreret BI-indsigt
description: Denne artikel indeholder en beskrivelse af, hvordan du bruger hjælpeprogrammer til værktøjstip til at forenkle tilpasningen af værktøjstip for Power BI-visualiseringer. Aktivér bedre integreret BI-indsigt ved hjælp af Power BI-integreret analyse.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 02/14/2020
ms.openlocfilehash: b2ddc85d9ba2530dc394b4106d72b4af702bd9b4
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 01/05/2021
ms.locfileid: "97888644"
---
# <a name="tooltip-utils"></a>Hjælpeprogrammer til værktøjstip
Denne artikel kan hjælpe dig med at installere, importere og bruge hjælpeprogrammer til værktøjstip. Dette hjælpeprogram er nyttigt til en hvilken som helst tilpasning af værktøjstip i Power BI-visualiseringer.

## <a name="requirements"></a>Krav
Hvis du vil bruge pakken, skal du have følgende:
* [node.js](https://nodejs.org) (den nyeste LTS-version anbefales)
* [npm](https://www.npmjs.com/) (som minimum understøttes version 3.0.0)
* Den brugerdefinerede visualisering, der er oprettet af [PowerBI-visuals-tools](https://www.npmjs.com/package/powerbi-visuals-tools)

## <a name="installation"></a>Installation

Hvis du vil installere pakken, skal du køre følgende kommando i mappen med din aktuelle visual:

```bash
npm install powerbi-visuals-utils-tooltiputils --save
```
Med denne kommando installeres pakken, og der tilføjes en pakke som en afhængighed af din ```package.json```

## <a name="usage"></a>Brug

> Brugervejledningen indeholder en beskrivelse af en offentligt API til pakken. Du kan finde en beskrivelse og et par eksempler til hver offentlige grænseflade for pakken.

Denne pakke indeholder en metode til at oprette `TooltipServiceWrapper` og metoder, der kan hjælpe med at håndtere handlinger for værktøjstip. Den bruger grænseflader for værktøjstip – `ITooltipServiceWrapper`, `TooltipEventArgs`, `TooltipEnabledDataPoint`. 

Den indeholder også specifikke metoder (berøringshændelseshandlere) relateret til mobiludvikling: `touchEndEventName`, `touchStartEventName`, `usePointerEvents`.

`TooltipServiceWrapper` er den enkleste måde at manipulere værktøjstip på.

Dette modul indeholder følgende grænseflade og funktion:
* [ITooltipServiceWrapper](#itooltipservicewrapper)
  * [addTooltip](#itooltipservicewrapperaddtooltip)
  * [hide](#itooltipservicewrapperhide)

* [Grænseflader](#interfaces)
  * [TooltipEventArgs](#tooltipeventargs)
  * [TooltipEnabledDataPoint](#tooltipenableddatapoint)
  * [TooltipServiceWrapperOptions](#tooltipservicewrapperoptions)
* [Berøringshændelser](#touch-events)

### `createTooltipServiceWrapper`
Denne funktion opretter en instans af ITooltipServiceWrapper.

```typescript
function createTooltipServiceWrapper(tooltipService: ITooltipService, rootElement: Element, handleTouchDelay?: number,  getEventMethod?: () => MouseEvent): ITooltipServiceWrapper;
```

```ITooltipService``` er tilgængelig i [IVisualHost](https://github.com/microsoft/PowerBI-visuals-tools/blob/master/templates/visuals/.api/v2.6.0/PowerBI-visuals.d.ts#L1335).

**Eksempel**

```typescript
import { createTooltipServiceWrapper } from "powerbi-visuals-utils-tooltiputils";

export class YourVisual implements IVisual {
    // implementation of IVisual.

    constructor(options: VisualConstructorOptions) {
        createTooltipServiceWrapper(
            options.host.tooltipService,
            options.element);

        // returns: an instance of ITooltipServiceWrapper.
    }
}
```

Du kan se eksempelkoden til det brugerdefinerede visual [her](https://github.com/microsoft/powerbi-visuals-gantt/blob/master/src/gantt.ts#L391).

### `ITooltipServiceWrapper`
I denne grænseflade beskrives offentlige metoder til TooltipService.

```typescript
interface ITooltipServiceWrapper {
    addTooltip<T>(selection: d3.Selection<any, any, any, any>, getTooltipInfoDelegate: (args: TooltipEventArgs<T>) => powerbi.extensibility.VisualTooltipDataItem[], getDataPointIdentity?: (args: TooltipEventArgs<T>) => powerbi.visuals.ISelectionId, reloadTooltipDataOnMouseMove?: boolean): void;
    hide(): void;
}
```

#### `ITooltipServiceWrapper.addTooltip`

Med denne metode føjes der værktøjstip til det aktuelle valg.

```typescript
addTooltip<T>(selection: d3.Selection<any>, getTooltipInfoDelegate: (args: TooltipEventArgs<T>) => VisualTooltipDataItem[], getDataPointIdentity?: (args: TooltipEventArgs<T>) => ISelectionId, reloadTooltipDataOnMouseMove?: boolean): void;
```

**Eksempel**

```typescript
import { createTooltipServiceWrapper, TooltipEventArgs, ITooltipServiceWrapper, TooltipEnabledDataPoint } from "powerbi-visuals-utils-tooltiputils";

let bodyElement = d3.select("body");

let element = bodyElement
    .append("div")
    .style({
        "background-color": "green",
        "width": "150px",
        "height": "150px"
    })
    .classed("visual", true)
    .data([{
        tooltipInfo: [{
            displayName: "Power BI",
            value: 2016
        }]
    }]);

let tooltipServiceWrapper: ITooltipServiceWrapper = createTooltipServiceWrapper(tooltipService, bodyElement.get(0)); // tooltipService is from the IVisualHost.

tooltipServiceWrapper.addTooltip<TooltipEnabledDataPoint>(element, (eventArgs: TooltipEventArgs<TooltipEnabledDataPoint>) => {
    return eventArgs.data.tooltipInfo;
});

// You will see a tooltip if you mouseover the element.
```

Du kan se eksempelkoden til det brugerdefinerede visual [her](https://github.com/microsoft/powerbi-visuals-gantt/blob/master/src/gantt.ts#L2931).

Vær også opmærksom på følgende eksempel på tilpasning af værktøjstip i den brugerdefinerede Gantt-visualisering [her](https://github.com/microsoft/powerbi-visuals-gantt/blob/master/src/gantt.ts#L573-L648)

### `ITooltipServiceWrapper.hide`

Med denne metode skjules værktøjstippet.

```typescript
hide(): void;
```

**Eksempel**

```typescript
import {createTooltipServiceWrapper} from "powerbi-visuals-utils-tooltiputils";

let tooltipServiceWrapper = createTooltipServiceWrapper(options.host.tooltipService, options.element); // options are from the VisualConstructorOptions.

tooltipServiceWrapper.hide();
```
### `Interfaces`
Denne grænseflade bruges under oprettelse af TooltipServiceWrapper og brugen af den. De blev også nævnt i eksempler fra det forrige emne [her](#itooltipservicewrapperaddtooltip).

#### `TooltipEventArgs`
```typescript
interface TooltipEventArgs<TData> {
    data: TData;
    coordinates: number[];
    elementCoordinates: number[];
    context: HTMLElement;
    isTouchEvent: boolean;
}
```

#### `TooltipEnabledDataPoint`
```typescript
interface TooltipEnabledDataPoint {
    tooltipInfo?: powerbi.extensibility.VisualTooltipDataItem[];
}
```

#### `TooltipServiceWrapperOptions`
```typescript
interface TooltipServiceWrapperOptions {
    tooltipService: ITooltipService;
    rootElement: Element;
    handleTouchDelay: number;
    getEventMethod?: () => MouseEvent;
```

### `Touch events`

Hjælpeprogrammer til værktøjstip kan nu håndtere adskillige berøringshændelser, som er nyttige i forbindelse med mobiludvikling.

#### `touchStartEventName`
```typescript
function touchStartEventName(): string
```
Med denne metode returneres navnet på startberøringshændelsen.

#### `touchEndEventName`
```typescript
function touchEndEventName(): string
```
Med denne metode returneres navnet på startberøringshændelsen.

#### `usePointerEvents`
```typescript
function usePointerEvents(): boolean
```
Med denne metode returneres den aktuelle startberøringshændelse, som er relateret til markør eller ej.
