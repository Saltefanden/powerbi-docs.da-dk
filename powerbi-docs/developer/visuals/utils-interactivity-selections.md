---
title: Hjælpeprogrammer til interaktivitet mellem Power BI-visualiseringer i en integreret Power BI-analyse for at få bedre integreret BI-indsigt
description: I artikIen beskrives det, hvordan du føjer valg til Power BI-visualiseringer ved hjælp af hjælpeprogrammer til interaktivitet. Aktivér bedre integreret BI-indsigt ved hjælp af Power BI-integreret analyse.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
manager: rkarlin
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 02/24/2020
ms.openlocfilehash: 533cf90ed9192a8d9e595cdea6320207b841b559
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 01/05/2021
ms.locfileid: "97887770"
---
# <a name="power-bi-visuals-interactivity-utils"></a>Interaktivitetsutils til Power BI-visuals

Interaktivitetshjælpeprogrammer (`InteractivityUtils`) er en række funktioner og klasser, der forenkler implementeringen af krydsvalg og krydsfiltrering.

> [!NOTE]
> De nye opdateringer af interaktivitetshjælpeprogrammer understøtter kun den nyeste version af Tools (3.x.x og derover).

## <a name="installation"></a>Installation

1. Hvis du vil installere pakken, skal du køre følgende kommando i mappen med din aktuelle Power BI-visualisering.

    ```bash
    npm install powerbi-visuals-utils-interactivityutils --save
    ```

2. Hvis du bruger version 3.0 eller nyere eller værktøjet, skal du installere `powerbi-models` for at løse afhængigheder.

    ```bash
    npm install powerbi-models --save
    ```

3. Hvis du vil bruge interaktivitetshjælpeprogrammer, skal du importere den påkrævede komponent i Power BI-visualiseringens kildekode.

    ```typescript
    import { interactivitySelectionService } from "powerbi-visuals-utils-interactivityutils";
    ```

### <a name="including-the-css-files"></a>Medtagning af CSS-filerne

Hvis du vil bruge pakken sammen med dine brugerdefinerede Power BI-visualiseringer, skal du importere følgende CSS-fil til filen `.less`.

`node_modules/powerbi-visuals-utils-interactivityutils/lib/index.css`

Importér CSS-filen som en `.less`-fil, fordi Power BI-visualiseringsværktøjet ombryder eksterne CSS-regler.

```less
@import (less) "node_modules/powerbi-visuals-utils-interactivityutils/lib/index.css";
```

## <a name="selectabledatapoint-properties"></a>Egenskaber for SelectableDataPoint

Datapunkter indeholder normalt valg og værdier. Grænsefladen udvider `SelectableDataPoint`-grænsefladen.

`SelectableDataPoint` indeholder allerede egenskaber som beskrevet nedenfor.

```typescript
  /** Flag for identifying that a data point was selected */
  selected: boolean;

  /** Identity for identifying the selectable data point for selection purposes */
  identity: powerbi.extensibility.ISelectionId;

  /*
   * A specific identity for when data points exist at a finer granularity than
   * selection is performed.  For example, if your data points select based
   * only on series, even if they exist as category/series intersections.
   */

  specificIdentity?: powerbi.extensibility.ISelectionId;
```

## <a name="defining-an-interface-for-data-points"></a>Definition af grænsefladen for datapunkter

1. Opret en forekomst af interaktivitetshjælpeværktøjer, og gem objektet som en egenskab i visualiseringen

    ```typescript
    export class Visual implements IVisual {
      // ...
      private interactivity: interactivityBaseService.IInteractivityService<VisualDataPoint>;
      // ...
      constructor(options: VisualConstructorOptions) {
          // ...
          this.interactivity = interactivitySelectionService.createInteractivitySelectionService(this.host);
          // ...
      }
    }
    ```

    ```typescript
    import { interactivitySelectionService } from "powerbi-visuals-utils-interactivityutils";

    export interface VisualDataPoint extends interactivitySelectionService.SelectableDataPoint {
        value: powerbi.PrimitiveValue;
    }
    ```

2. Udvid den grundlæggende funktionsmådeklasse.

    > [!NOTE]
    > `BaseBehavior` blev introduceret i [5.6. x-versionen af interaktivitetshjælpeprogrammer](https://www.npmjs.com/package/powerbi-visuals-utils-interactivityutils/v/5.6.0). Hvis du bruger en ældre version, skal du oprette funktionsmådeklassen fra eksemplet nedenfor.

3. Definer grænsefladen for indstillinger for funktionsmådeklassen.

    ```typescript
    import { SelectableDataPoint } from "./interactivitySelectionService";

    import {
        IBehaviorOptions,
        BaseDataPoint
    } from "./interactivityBaseService";

    export interface BaseBehaviorOptions<SelectableDataPointType extends BaseDataPoint> extends IBehaviorOptions<SelectableDataPointType> {

    /** d3 selection object of the main elements on the chart */
    elementsSelection: Selection<any, SelectableDataPoint, any, any>;

    /** d3 selection object of some elements on backgroup, to hadle click of reset selection */
    clearCatcherSelection: d3.Selection<any, any, any, any>;
    }
    ```

4. Definer en klasse for `visual behavior`. Du kan også udvide klassen `BaseBehavior`.

    **Definition af en klasse for `visual behavior`**

    Den klasse, der er ansvarlig for håndtering af musehændelserne `click` `contextmenu`.

    Når en bruger klikker på dataelementer, kalder visualiseringen valghandleren for at vælge datapunkter. Hvis brugeren klikker på baggrundselementet i visualiseringen, kalder den valghandleren for ryd.

    Klassen har følgende tilsvarende metoder:
    * `bindClick`
    * `bindClearCatcher`
    * `bindContextMenu`.

    ```typescript
    export class Behavior<SelectableDataPointType extends BaseDataPoint> implements IInteractiveBehavior {

        /** d3 selection object of main elements in the chart */
        protected options: BaseBehaviorOptions<SelectableDataPointType>;
        protected selectionHandler: ISelectionHandler;
    
        protected bindClick() {
          // ...
        }
    
        protected bindClearCatcher() {
          // ...
        }
    
        protected bindContextMenu() {
          // ...
        }
    
        public bindEvents(
            options: BaseBehaviorOptions<SelectableDataPointType>,
            selectionHandler: ISelectionHandler): void {
          // ...
        }
    
        public renderSelection(hasSelection: boolean): void {
          // ...
        }
    }
    ```

    **Udvidelse af klassen `BaseBehavior`**

    ```typescript
    import powerbi from "powerbi-visuals-api";
    import { interactivitySelectionService, baseBehavior } from "powerbi-visuals-utils-interactivityutils";

    export interface VisualDataPoint extends interactivitySelectionService.SelectableDataPoint {
        value: powerbi.PrimitiveValue;
    }

    export class Behavior extends baseBehavior.BaseBehavior<VisualDataPoint> {
      // ...
    }
    ```

5. Hvis du vil håndtere klik på elementer, skal du kalde *d3*-valgobjektet for metoden `on`. Dette gælder også for `elementsSelection` og `clearCatcherSelection`.

    ```typescript
    protected bindClick() {
      const {
          elementsSelection
      } = this.options;
    
      elementsSelection.on("click", (datum) => {
          const mouseEvent: MouseEvent = getEvent() as MouseEvent || window.event as MouseEvent;
          mouseEvent && this.selectionHandler.handleSelection(
              datum,
              mouseEvent.ctrlKey);
      });
    }
    ```

6. Tilføj en lignende handler, så hændelsen `contextmenu` kalder valgstyringsmetodens `showContextMenu`.

    ```typescript
    protected bindContextMenu() {
        const {
            elementsSelection
        } = this.options;
    
        elementsSelection.on("contextmenu", (datum) => {
            const event: MouseEvent = (getEvent() as MouseEvent) || window.event as MouseEvent;
            if (event) {
                this.selectionHandler.handleContextMenu(
                    datum,
                    {
                        x: event.clientX,
                        y: event.clientY
                    });
                event.preventDefault();
            }
        });
    }
    ```

7. Hvis du vil tildele funktioner til handlere, kalder interaktivitetshjælpeprogrammer metoden `bindEvents`. Føj følgende kald til metoden `bindEvents`:
    * `bindClick`
    * `bindClearCatcher`
    * `bindContextMenu`

    ```typescript
      public bindEvents(
          options: BaseBehaviorOptions<SelectableDataPointType>,
          selectionHandler: ISelectionHandler): void {

          this.options = options;
          this.selectionHandler = selectionHandler;

          this.bindClick();
          this.bindClearCatcher();
          this.bindContextMenu();
      }
    ```

8. Metoden `renderSelection` er ansvarlig for at opdatere elementers visualtilstand i diagrammet. Eksempel på implementeringen af `renderSelection`.

    ```typescript
    public renderSelection(hasSelection: boolean): void {
        this.options.elementsSelection.style("opacity", (category: any) => {
            if (category.selected) {
                return 0.5;
            } else {
                return 1;
            }
        });
    }
    ```

9. Det sidste trin er oprettelse af en forekomst af `visual behavior` og kald af metoden `bind` for forekomsten af interaktivitetshjælpeprogrammer.

    ```typescript
    this.interactivity.bind(<BaseBehaviorOptions<VisualDataPoint>>{
        behavior: this.behavior,
        dataPoints: this.categories,
        clearCatcherSelection: select(this.target),
        elementsSelection: selectionMerge
    });
    ```

    * `selectionMerge` er et *d3*-valgobjekt, som repræsenterer alle elementer, der kan vælges i visualiseringen.
    * `select(this.target)` er et *d3*-valgobjekt, som repræsenterer visualiseringens primære DOM-elementer.
    * `this.categories` er datapunkter med elementer, hvor grænsefladen er `VisualDataPoint` eller `categories: VisualDataPoint[];`.
    * `this.behavior` er en ny forekomst af `visual behavior`, der er oprettet i visualiseringskonstruktøren, som vist nedenfor.

      ```typescript
      export class Visual implements IVisual {
        // ...
        constructor(options: VisualConstructorOptions) {
            // ...
            this.behavior = new Behavior();
        }
        // ...
      }
      ```
## <a name="next-steps"></a>Næste trin

* [Læs om, hvordan du kan håndtere valg ved skift af bogmærker](bookmarks-support.md#visuals-with-selection)

* [Læs om, hvordan du tilføjer en genvejsmenu for visualdatapunkter](context-menu.md)

* [Læs om, hvordan du bruger valgstyringen til at føje valg til Power BI-visuals](selection-api.md)
