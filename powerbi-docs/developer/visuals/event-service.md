---
title: Gengiv hændelser i Power BI-visualiseringer i en integreret Power BI-analyse for at få bedre integreret BI-indsigt
description: Power BI-visualiseringer kan give Power BI besked om, at de er klar til at blive eksporteret til Power Point eller PDF. Aktivér bedre integreret BI-indsigt ved hjælp af Power BI-integreret analyse.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 06/18/2019
ms.openlocfilehash: 77ed686b78a96717193e594e9f846d4204d8b5e8
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 01/05/2021
ms.locfileid: "97885079"
---
# <a name="render-events-in-power-bi-visuals"></a>Gengiv begivenheder i visualiseringer i Power BI

Den nye API består af tre metoder (`started`, `finished` eller `failed`), som skal kaldes under gengivelse.

Når gengivelsen starter, kalder Power BI-visualiseringskoden metoden `renderingStarted` for at angive, at gengivelsesprocessen er startet.

Hvis gengivelsen er fuldført, kalder visualiseringskoden i Power BI øjeblikkeligt metoden `renderingFinished`, hvilket giver lyttefunktionen (primært *eksportér til PDF* og *eksportér til PowerPoint*) besked om, at visualiseringens afbildning er klar til eksport.

Hvis der opstår et problem under processen, forhindres gengivelsen af det visuelle element i Power BI. Den brugerdefinerede Power BI-visualiseringskode bør kalde metoden `renderingFailed` for at give lytterne besked om, at gengivelsesprocessen ikke er fuldført. Denne metode indeholder også en valgfri streng, der giver en årsag til fejlen.

## <a name="usage"></a>Brug

```typescript
export interface IVisualHost extends extensibility.IVisualHost {
    eventService: IVisualEventService ;
}

/**
 * An interface for reporting rendering events
 */
export interface IVisualEventService {
    /**
     * Should be called just before the actual rendering starts, 
     * usually at the start of the update method
     *
     * @param options - the visual update options received as an update parameter
     */
    renderingStarted(options: VisualUpdateOptions): void;

    /**
     * Should be called immediately after rendering finishes successfully
     * 
     * @param options - the visual update options received as an update parameter
     */
    renderingFinished(options: VisualUpdateOptions): void;

    /**
     * Called when rendering fails, with an optional reason string
     * 
     * @param options - the visual update options received as an update parameter
     * @param reason - the optional failure reason string
     */
    renderingFailed(options: VisualUpdateOptions, reason?: string): void;
}
```

### <a name="sample-the-visual-displays-no-animations"></a>Eksempel: Visualiseringen viser ingen animationer

```typescript
    export class Visual implements IVisual {
        ...
        private events: IVisualEventService;
        ...

        constructor(options: VisualConstructorOptions) {
            ...
            this.events = options.host.eventService;
            ...
        }

        public update(options: VisualUpdateOptions) {
            this.events.renderingStarted(options);
            ...
            this.events.renderingFinished(options);
        }
```

### <a name="sample-the-visual-displays-animations"></a>Eksempel: Visualiseringen viser animationer

Hvis visualiseringen indeholder animationer eller asynkrone funktioner til gengivelse, skal metoden `renderingFinished` kaldes efter animationen eller inde i den asynkrone funktion.

```typescript
    export class Visual implements IVisual {
        ...
        private events: IVisualEventService;
        private element: HTMLElement;
        ...

        constructor(options: VisualConstructorOptions) {
            ...
            this.events = options.host.eventService;
            this.element = options.element;
            ...
        }

        public update(options: VisualUpdateOptions) {
            this.events.renderingStarted(options);
            ...
            // Learn more at https://github.com/d3/d3-transition/blob/master/README.md#transition_end
            d3.select(this.element).transition().duration(100).style("opacity","0").end().then(() => {
                // renderingFinished called after transition end
                this.events.renderingFinished(options);
            });
        }
```

## <a name="rendering-events-for-visual-certification"></a>Gengivelse af hændelser til visuel certificering

Et af kravene til certificering af visualiseringer er understøttelse af gengivelseshændelser fra visualiseringen. Du kan finde flere oplysninger i [certificeringskrav](power-bi-custom-visuals-certified.md#certification-requirements).