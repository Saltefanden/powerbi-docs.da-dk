---
title: Introduktion til brug af testhjælpeprogrammer i Power BI-visualiseringer i en integreret Power BI-analyse for at få bedre integreret BI-indsigt
description: I denne artikel beskrives det, hvordan du bruger testværktøjer til at forenkle modeller og specifikke metoder i forbindelse med enhedstest af Power BI-visualiseringer. Aktivér bedre integreret BI-indsigt ved hjælp af Power BI-integreret analyse.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 02/14/2020
ms.openlocfilehash: 4b2a846f4905c4cb28fe92043cf3c71750b40f11
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 01/05/2021
ms.locfileid: "97888046"
---
# <a name="power-bi-visuals-test-utils"></a>Testværktøjer til Power BI-visualiseringer

I denne artikel kan du få hjælp til at installere, importere og bruge testværktøjer til Power BI-visualiseringer. Disse testværktøjer kan bruges til at teste enheder og indeholder modeller og metoder til elementer som f.eks. datavisninger, valg og farveskemaer.

## <a name="requirements"></a>Krav

Hvis du vil bruge denne pakke, skal du installere følgende:

* [node. js](https://nodejs.org) – det anbefales at bruge LTS-versionen
* [npm](https://www.npmjs.com/) – version 3.0.0 eller nyere
* Pakken [PowerBI-visuals-tools](https://github.com/Microsoft/PowerBI-visuals-tools)

## <a name="installation"></a>Installation

Hvis du vil installere testværktøjer og føje de tilhørende afhængigheder til *package.json*, skal du køre følgende kommando fra mappen med Power BI-visualiseringer:

```bash
npm install powerbi-visuals-utils-testutils --save
```

Følgende indeholder beskrivelser og eksempler på den offentlige API til testværktøjer.

## <a name="visualbuilderbase"></a>VisualBuilderBase

Benyttes af **VisualBuilder** i enhedstest med de hyppigst anvendte metoder `build`, `update`og `updateRenderTimeout`. 

Metoden `build` returnerer en oprettet forekomst af visualiseringen.

Metoderne `enumerateObjectInstances` og `updateEnumerateObjectInstancesRenderTimeout` er påkrævet for at kontrollere ændringer af indstillingerne for filsæt og formatering.

```typescript
abstract class VisualBuilderBase<T extends IVisual> {
    element: JQuery;
    viewport: IViewport;
    visualHost: IVisualHost;
    protected visual: T;
    constructor(width?: number, height?: number, guid?: string, element?: JQuery);
    protected abstract build(options: VisualConstructorOptions): T;
     nit(): void;
    destroy(): void;
    update(dataView: DataView[] | DataView): void;
    updateRenderTimeout(dataViews: DataView[] | DataView, fn: Function, timeout?: number): number;
    updateEnumerateObjectInstancesRenderTimeout(dataViews: DataView[] | DataView, options: EnumerateVisualObjectInstancesOptions, fn: (enumeration: VisualObjectInstance[]) => void, timeout?: number): number;
    updateFlushAllD3Transitions(dataViews: DataView[] | DataView): void;
    updateflushAllD3TransitionsRenderTimeout(dataViews: DataView[] | DataView, fn: Function, timeout?: number): number;
    enumerateObjectInstances(options: EnumerateVisualObjectInstancesOptions): VisualObjectInstance[];
}
```

> [!NOTE]
> Hvis du vil have flere eksempler, skal du se [skrivning af VisualBuilderBase-enhedstest](./unit-tests-introduction.md#create-a-visual-instance-builder) og et [VisualBuilderBase-scenarie i realtid](https://github.com/microsoft/powerbi-visuals-gantt/blob/master/test/visualBuilder.ts).

## <a name="dataviewbuilder"></a>DataViewBuilder

Dette modul, der bruges af **TestDataViewBuilder**, indeholder en **CategoricalDataViewBuilder**-klasse, der bruges i metoden `createCategoricalDataViewBuilder`. Det angiver også de grænseflader og metoder, der kræves for at arbejde med modellen **DataView** i enhedstest.

* `withValues` tilføjer kolonner for statiske serier, og `withGroupedValues` tilføjer kolonner for dynamiske serier

  Undgå at anvende både dynamiske serier og statiske serier i en visuel **DataViewCategorical**. Du kan kun bruge dem begge i forespørgslen **DataViewCategorical**, hvor **DataViewTransform** forventes at opdele dem i separate **DataViewCategorical**-visualiseringsobjekter.

* `build` returnerer DataView med metadata og DataViewCategorical

  `build` returnerer **Undefined**, hvis kombinationen af parametre er ugyldig, f.eks. både dynamiske og statiske serier, når du bygger visualiseringen **DataView**.

```typescript
class CategoricalDataViewBuilder implements IDataViewBuilderCategorical {
    withCategory(options: DataViewBuilderCategoryColumnOptions): IDataViewBuilderCategorical;
    withCategories(categories: DataViewCategoryColumn[]): IDataViewBuilderCategorical;
    withValues(options: DataViewBuilderValuesOptions): IDataViewBuilderCategorical;
    withGroupedValues(options: DataViewBuilderGroupedValuesOptions): IDataViewBuilderCategorical;
    build(): DataView;
}

function createCategoricalDataViewBuilder(): IDataViewBuilderCategorical;
```

## <a name="testdataviewbuilder"></a>TestDataViewBuilder

Bruges til oprettelse af **VisualData** i enhedstest. Når data placeres i datafelt-buckets, producerer Power BI et kategorisk **DataView**-objekt, der er baseret på dataene. **TestDataViewBuilder** kan hjælpe med at simulere oprettelsen af en kategorisk **DataView**.

```typescript
abstract class TestDataViewBuilder {
    static DataViewName: string;
    private aggregateFunction;
    static setDefaultQueryName(source: DataViewMetadataColumn): DataViewMetadataColumn;
    static getDataViewBuilderColumnIdentitySources(options: TestDataViewBuilderColumnOptions[] | TestDataViewBuilderColumnOptions): DataViewBuilderColumnIdentitySource[];
    static getValuesTable(categories?: DataViewCategoryColumn[], values?: DataViewValueColumn[]): any[][];
    static createDataViewBuilderColumnOptions(categoriesColumns: (TestDataViewBuilderCategoryColumnOptions | TestDataViewBuilderCategoryColumnOptions[])[], valuesColumns: (DataViewBuilderValuesColumnOptions | DataViewBuilderValuesColumnOptions[])[], filter?: (options: TestDataViewBuilderColumnOptions) => boolean, customizeColumns?: CustomizeColumnFn): DataViewBuilderAllColumnOptions;
    static setUpDataViewBuilderColumnOptions(options: DataViewBuilderAllColumnOptions, aggregateFunction: (array: number[]) => number): DataViewBuilderAllColumnOptions;
    static setUpDataView(dataView: DataView, options: DataViewBuilderAllColumnOptions): DataView;
    protected createCategoricalDataViewBuilder(categoriesColumns: (TestDataViewBuilderCategoryColumnOptions | TestDataViewBuilderCategoryColumnOptions[])[], valuesColumns: (DataViewBuilderValuesColumnOptions | DataViewBuilderValuesColumnOptions[])[], columnNames: string[], customizeColumns?: CustomizeColumnFn): IDataViewBuilderCategorical;
    abstract getDataView(columnNames?: string[]): DataView;
}
```

  På følgende liste vises de grænseflader, der oftest bruges, når du opretter en `testDataView`:

  ```typescript
  interface TestDataViewBuilderColumnOptions extends DataViewBuilderColumnOptions {
      values: any[];
  }

  interface TestDataViewBuilderCategoryColumnOptions extends TestDataViewBuilderColumnOptions {
      objects?: DataViewObjects[];
      isGroup?: boolean;
  }

  interface DataViewBuilderColumnOptions {
      source: DataViewMetadataColumn;
  }

  interface DataViewBuilderSeriesData {
      values: PrimitiveValue[];
      highlights?: PrimitiveValue[];
      /** Client-computed maximum value for a column. */
      maxLocal?: any;
      /** Client-computed maximum value for a column. */
      minLocal?: any;
  }

  interface DataViewBuilderColumnIdentitySource {
      fields: any[];
      identities?: CustomVisualOpaqueIdentity[];
  }
  ```
   
> [!NOTE]
> Hvis du vil have flere eksempler, skal du se [skrivning af TestDataViewBuilder-enhedstest](./unit-tests-introduction.md#how-to-add-static-data-for-unit-tests) og et [TestDataViewBuilder-scenarie i realtid](https://github.com/microsoft/powerbi-visuals-gantt/blob/master/test/visualData.ts).

## <a name="mocks"></a>Modeller

### <a name="mockivisualhost"></a>MockIVisualHost

Implementerer **IVisualHost** for at teste Power BI-visualiseringer uden eksterne afhængigheder, f.eks. Power BI-strukturen.

Nyttige metoder omfatter egenskaber for `createSelectionIdBuilder`, `createSelectionManager`, `createLocalizationManager` og hentningsfunktioner.

```typescript
import powerbi from "powerbi-visuals-api";

import VisualObjectInstancesToPersist = powerbi.VisualObjectInstancesToPersist;
import ISelectionIdBuilder = powerbi.visuals.ISelectionIdBuilder;
import ISelectionManager = powerbi.extensibility.ISelectionManager;
import IColorPalette = powerbi.extensibility.IColorPalette;
import IVisualEventService = powerbi.extensibility.IVisualEventService;
import ITooltipService = powerbi.extensibility.ITooltipService;
import IVisualHost = powerbi.extensibility.visual.IVisualHost;

class MockIVisualHost implements IVisualHost {
      constructor(
          colorPalette?: IColorPalette,
          selectionManager?: ISelectionManager,
          tooltipServiceInstance?: ITooltipService,
          localeInstance?: MockILocale,
          allowInteractionsInstance?: MockIAllowInteractions,
          localizationManager?: powerbi.extensibility.ILocalizationManager,
          telemetryService?: powerbi.extensibility.ITelemetryService,
          authService?: powerbi.extensibility.IAuthenticationService,
          storageService?: ILocalVisualStorageService,
          eventService?: IVisualEventService);
      createSelectionIdBuilder(): ISelectionIdBuilder;
      createSelectionManager(): ISelectionManager;
      createLocalizationManager(): ILocalizationManager;
      colorPalette: IColorPalette;
      locale: string;
      telemetry: ITelemetryService;
      tooltipService: ITooltipService;
      allowInteractios: boolean;
      storageService: ILocalVisualStorageService;
      eventService: IVisualEventService;
      persistProperties(changes: VisualObjectInstancesToPersist): void;
}
```
   
- `createVisualHost` opretter og returnerer en forekomst af **IVisualHost**, dvs. **MockIVisualHost**
  ```typescript
  function createVisualHost(locale?: Object, allowInteractions?: boolean, colors?: IColorInfo[], isEnabled?: boolean, displayNames?: any, token?: string): IVisualHost;
  ```

    Eksempel
    ```typescript
    import { createVisualHost } from "powerbi-visuals-utils-testutils"

    let host: IVisualHost = createVisualHost();
    ```

> [!IMPORTANT]
> **MockIVisualHost** er en falsk implementering af **IVisualHost** og bør kun bruges sammen med enhedstest.

### <a name="mockicolorpalette"></a>MockIColorPalette

Implementerer **IColorPalette** for at teste Power BI-visualiseringer uden eksterne afhængigheder, f.eks. Power BI-strukturen.

**MockIColorPalette** indeholder nyttige egenskaber til at kontrollere farveskema eller tilstand med høj kontrast i enhedstest.

  ```typescript
  import powerbi from "powerbi-visuals-api";
  import IColorPalette = powerbi.extensibility.ISandboxExtendedColorPalette;
  import IColorInfo = powerbi.IColorInfo;

  class MockIColorPalette implements IColorPalette {
      constructor(colors?: IColorInfo[]);
      getColor(key: string): IColorInfo;
      reset(): IColorPalette;
      isHighContrastMode: boolean;
      foreground: {value: string};
      foregroundLight: {value: string};
      ...
      background: {value: string};
      backgroundLight: {value: string};
      ...
      shapeStroke: {value: string};
  }
  ```
  - `createColorPalette` opretter og returnerer en forekomst af **IColorPalette**, dvs. **MockIColorPalette**
    ```typescript
    function createColorPalette(colors?: IColorInfo[]): IColorPalette;
    ```

    Eksempel
    ```typescript
    import { createColorPalette } from "powerbi-visuals-utils-testutils"

    let colorPalette: IColorPalette = createColorPalette();
    ```
    
> [!IMPORTANT]
> **MockIColorPalette** er en falsk implementering af **IColorPalette** og bør kun bruges sammen med enhedstest.

### <a name="mockiselectionid"></a>MockISelectionId

Implementerer **ISelectionId** for at teste Power BI-visualiseringer uden eksterne afhængigheder, f.eks. Power BI-strukturen.

  ```typescript
  import powerbi from "powerbi-visuals-api";
  import Selector = powerbi.data.Selector;
  import ISelectionId = powerbi.visuals.ISelectionId;

  class MockISelectionId implements ISelectionId {
      constructor(key: string);
      equals(other: ISelectionId): boolean;
      includes(other: ISelectionId, ignoreHighlight?: boolean): boolean;
      getKey(): string;
      getSelector(): Selector;
      getSelectorsByColumn(): Selector;
      hasIdentity(): boolean;
  }
  ```

  - `createSelectionId` opretter og returnerer en forekomst af **ISelectionId**, dvs. **MockISelectionId**
    ```typescript
    function createSelectionId(key?: string): ISelectionId;
    ```

    Eksempel
    ```typescript
    import { createColorPalette } from "powerbi-visuals-utils-testutils"

    let selectionId: ISelectionId = createSelectionId();
    ```
    
> [!NOTE]
> **MockISelectionId** er en falsk implementering af **ISelectionId** og bør kun bruges sammen med enhedstest.

### <a name="mockiselectionidbuilder"></a>MockISelectionIdBuilder

Implementerer **ISelectionIdBuilder** for at teste Power BI-visualiseringer uden eksterne afhængigheder, f.eks. Power BI-strukturen. 

  ```typescript
  import DataViewCategoryColumn = powerbi.DataViewCategoryColumn;
  import DataViewValueColumn = powerbi.DataViewValueColumn;
  import DataViewValueColumnGroup = powerbi.DataViewValueColumnGroup;
  import DataViewValueColumns = powerbi.DataViewValueColumns;
  import ISelectionIdBuilder = powerbi.visuals.ISelectionIdBuilder;
  import ISelectionId = powerbi.visuals.ISelectionId;

  class MockISelectionIdBuilder implements ISelectionIdBuilder {
      withCategory(categoryColumn: DataViewCategoryColumn, index: number): this;
      withSeries(seriesColumn: DataViewValueColumns, valueColumn: DataViewValueColumn | DataViewValueColumnGroup): this;
      withMeasure(measureId: string): this;
      createSelectionId(): ISelectionId;
      withMatrixNode(matrixNode: DataViewMatrixNode, levels: DataViewHierarchyLevel[]): this;
      withTable(table: DataViewTable, rowIndex: number): this;
  }
  ```

  - `createSelectionIdBuilder` opretter og returnerer en forekomst af **ISelectionIdBuilder**, dvs. **MockISelectionIdBuilder**
    ```typescript
    function createSelectionIdBuilder(): ISelectionIdBuilder;
    ```

    Eksempel
    ```typescript
    import { selectionIdBuilder } from "powerbi-visuals-utils-testutils";

    let selectionIdBuilder = createSelectionIdBuilder();
    ```

> [!NOTE]
> **MockISelectionIdBuilder** er en falsk implementering af **ISelectionIdBuilder** og bør kun bruges sammen med enhedstest.

### <a name="mockiselectionmanager"></a>MockISelectionManager

Implementerer **ISelectionManager** for at teste Power BI-visualiseringer uden eksterne afhængigheder, f.eks. Power BI-strukturen. 

  ```typescript
  import powerbi from "powerbi-visuals-api";
  import IPromise = powerbi.IPromise;
  import ISelectionId = powerbi.visuals.ISelectionId;
  import ISelectionManager = powerbi.extensibility.ISelectionManager;

  class MockISelectionManager implements ISelectionManager {
      select(selectionId: ISelectionId | ISelectionId[], multiSelect?: boolean): IPromise<ISelectionId[]>;
      hasSelection(): boolean;
      clear(): IPromise<{}>;
      getSelectionIds(): ISelectionId[];
      containsSelection(id: ISelectionId): boolean;
      showContextMenu(selectionId: ISelectionId, position: IPoint): IPromise<{}>;
      registerOnSelectCallback(callback: (ids: ISelectionId[]) => void): void;
      simutateSelection(selections: ISelectionId[]): void;
  }
  ```

  - `createSelectionManager` opretter og returnerer en forekomst af **ISelectionManager**, dvs. **MockISelectionManager**
    ```typescript
    function createSelectionManager(): ISelectionManager
    ```

    Eksempel
    ```typescript
    import { createSelectionManager } from "powerbi-visuals-utils-testutils";

    let selectionManager: ISelectionManager = createSelectionManager();
    ```

> [!NOTE]
> **MockISelectionManager** er en falsk implementering af **ISelectionManager** og bør kun bruges sammen med enhedstest.

### <a name="mockilocale"></a>MockILocale

  Indstiller landestandarden og ændrer den til dine behov under en enhedstestproces.
  ```typescript
  class MockILocale {
      constructor(locales?: Object): void; // Default locales are en-US and ru-RU 
      locale(key: string): void;// setter property
      locale(): string; // getter property
  }
  ```
  - `createLocale` opretter og returnerer en forekomst af **MockILocale**
    ```typescript
    funciton createLocale(locales?: Object): MockILocale;
    ```

### <a name="mockitooltipservice"></a><a id="mockitooltipservice"></a> MockITooltipService
Simulerer `TooltipService` og kalder den i henhold til dine behov under en enhedstestproces.
  ```typescript
  class MockITooltipService implements ITooltipService {
      constructor(isEnabled: boolean = true);
      enabled(): boolean;
      show(options: TooltipShowOptions): void;
      move(options: TooltipMoveOptions): void;
      hide(options: TooltipHideOptions): void;
  }
  ```
  - `createTooltipService` opretter og returnerer en forekomst af **MockITooltipService**
    ```typescript
    function createTooltipService(isEnabled?: boolean): ITooltipService;
    ```

### <a name="mockiallowinteractions"></a>MockIAllowInteractions

```typescript
export class MockIAllowInteractions {
    constructor(public isEnabled?: boolean); // false by default
}
```
  - `createAllowInteractions` opretter og returnerer en forekomst af **MockIAllowInteractions**
    ```typescript
    function createAllowInteractions(isEnabled?: boolean): MockIAllowInteractions;
    ```

### <a name="mockilocalizationmanager"></a><a id="mockilocalizationmanager"></a> MockILocalizationManager
Leverer grundlæggende muligheder for **LocalizationManager**, der er nødvendige til enhedstest.
```typescript
class MockILocalizationManager implements ILocalizationManager {
    constructor(displayNames: {[key: string]: string});
    getDisplayName(key: string): string; // returns default or setted displayNames for localized elements
}
```
  - `createLocalizationManager` opretter og returnerer en forekomst af **ILocalizationManager**, dvs. **MockILocalizationManager**
    ```typescript
    function createLocalizationManager(displayNames?: any): ILocalizationManager;
    ```

    Eksempel
    ```typescript
    import { createLocalizationManager } from "powerbi-visuals-utils-testutils";
    let localizationManagerMock: ILocalizationManager = createLocalizationManager();
    ```

### <a name="mockitelemetryservice"></a>MockITelemetryService
Simulerer brug af **TelemetryService**.
```typescript
class MockITelemetryService implements ITelemetryService {
    instanceId: string;
    trace(veType: powerbi.VisualEventType, payload?: string) {
    }
}
```
  Oprettelse af `MockITelemetryService`
    ```typescript
    function createTelemetryService(): ITelemetryService;
    ```
### <a name="mockiauthenticationservice"></a>MockIAuthenticationService
Simulerer arbejdet med **AuthenticationService** ved at sende et AAD-modeltoken.
```typescript
class MockIAuthenticationService implements IAuthenticationService  {
    constructor(token: string);
    getAADToken(visualId?: string): powerbi.IPromise<string>
}
```
  - `createAuthenticationService` opretter og returnerer en forekomst af **IAuthenticationService**, dvs. **MockIAuthenticationService**
    ```typescript
    function createAuthenticationService(token?: string): IAuthenticationService;
    ```

### <a name="mockistorageservice"></a>MockIStorageService
Giver dig mulighed for at bruge **ILocalVisualStorageService** med samme funktionsmåde som **LocalStorage**.
```typescript
class MockIStorageService implements ILocalVisualStorageService {
  get(key: string): IPromise<string>;
  set(key: string, data: string): IPromise<number>;
  remove(key: string): void;
}
```
  - `createStorageService` opretter og returnerer en forekomst af **ILocalVisualStorageService**, dvs. **MockIStorageService**
    ```typescript
    function createStorageService(): ILocalVisualStorageService;
    ```

### <a name="mockieventservice"></a>MockIEventService
```typescript
import powerbi from "powerbi-visuals-api";
import IVisualEventService = powerbi.extensibility.IVisualEventService;
import VisualUpdateOptions = powerbi.extensibility.VisualUpdateOptions;

class MockIEventService implements IVisualEventService {
      renderingStarted(options: VisualUpdateOptions): void;
      renderingFinished(options: VisualUpdateOptions): void;
      renderingFailed(options: VisualUpdateOptions, reason?: string): void;
}
```
  - `createEventService` opretter og returnerer en forekomst af **IVisualEventService**, dvs. **MockIEventService**
    ```typescript
    function createEventService(): IVisualEventService;
    ```

## <a name="utils"></a>Utils

Utils omfatter hjælpemetoder til enhedstest af Power BI-visualiseringer, herunder hjælpefunktioner, der er relateret til farver, tal og hændelser.

- `renderTimeout` returnerer timeout
  ```typescript
  function renderTimeout(fn: Function, timeout: number = DefaultWaitForRender): number
  ```

- `testDom` hjælper med at angive et fast punkt i enhedstest
  ```typescript
  function testDom(height: number | string, width: number | string): JQuery
  ```
  Eksempel
  ```typescript
  import { testDom }  from "powerbi-visuals-utils-testutils";
  describe("testDom", () => {
      it("should return an element", () => {
          let element: JQuery = testDom(500, 500);
          expect(element.get(0)).toBeDefined();
      });
  });
  ```

### <a name="color-related-helper-methods"></a>Farverelaterede hjælpemetoder

- `getSolidColorStructuralObject`
  ```typescript
  function getSolidColorStructuralObject(color: string): any
  ```
  Returnerer følgende struktur:

  ```json
  { solid: { color: color } }
  ```

- `assertColorsMatch` sammenligner **RgbColor**-objekter, der er fortolket fra inputstrenge
  ```typescript
  function assertColorsMatch(actual: string, expected: string, invert: boolean = false): boolean
  ```

- `parseColorString` fortolker farven fra inputstrengen og returnerer den i den angivne grænseflade **RgbColor**
  ```typescript
  function parseColorString(color: string): RgbColor
  ```

### <a name="number-related-helper-methods"></a>Nummerrelaterede hjælpemetoder

- `getRandomNumbers` genererer et tilfældigt tal med minimum- og maksimumværdier. Du kan angive `exceptionList` og få en funktion til ændring af resultatet.
  ```typescript
  function getRandomNumber(
      min: number,
      max: number,
      exceptionList?: number[],
      changeResult: (value: any) => number = x => x): number
  ```

- `getRandomNumbers` indeholder en matrix af tilfældige tal, der genereres af `getRandomNumber`-metoden med angivne minimum- og maksimumværdier
  ```typescript
  function getRandomNumbers(count: number, min: number = 0, max: number = 1): number[]
  ```

### <a name="event-related-helper-methods"></a>Hændelsesrelaterede hjælpemetoder
Følgende metoder er skrevet til simulering af hændelser på websider i enhedstest.

- `clickElement` simulerer et klik på det angivne element
  ```typescript
  function clickElement(element: JQuery, ctrlKey: boolean = false): void
  ```

- `createTouch` returnerer et **Touch**-objekt for at hjælpe med at simulere en berøringshændelse
  ```typescript
  function createTouch(x: number, y: number, element: JQuery, id: number = 0): Touch
  ```

- `createTouchesList` returnerer en liste over simulerede **Touch-** hændelser
  ```typescript
  function createTouchesList(touches: Touch[]): TouchList
  ```

- `createContextMenuEvent` returnerer **MouseEvent**
  ```typescript
  function createContextMenuEvent(x: number, y: number): MouseEvent
  ```

- `createMouseEvent` opretter og returnerer **MouseEvent**
  ```typescript
  function createMouseEvent(
      mouseEventType: MouseEventType,
      eventType: ClickEventType,
      x: number,
      y: number,
      button: number = 0): MouseEvent
  ```

- `createTouchEndEvent`
  ```typescript
  function createTouchEndEvent(touchList?: TouchList): UIEvent
  ```

- `createTouchMoveEvent`
  ```typescript
  function createTouchMoveEvent(touchList?: TouchList): UIEvent
  ```

- `createTouchStartEvent`
  ```typescript
  function createTouchStartEvent(touchList?: TouchList): UIEvent
  ```

### <a name="d3-event-related-helper-methods"></a>D3-hændelsesrelaterede hjælpemetoder

Følgende metoder bruges til at simulere D3-hændelser i enhedstest.

- `flushAllD3Transitions` tvinger alle D3-overgange til at blive fuldført

  ```typescript
  function flushAllD3Transitions()
  ```
  
  > [!NOTE]
  > Normalt udføres overgange med nul forsinkelse efter en øjeblikkelig forsinkelse (< 10 MS), men det kan medføre kortvarig flimren, hvis browseren gengiver siden to gange. Én gang i slutningen af den første hændelsesløkke og derefter igen straks efter tilbagekald af den første timer.
  >
  > Denne flimren er tydeligere i IE og med et stort antal webvisninger og anbefales ikke til iOS.
  > 
  > Hvis du rydder timerkøen ved slutningen af den første hændelsesløkke, kan du køre enhver overgang uden forsinkelse og undgå, at det flimrer.

Følgende metoder er også inkluderet:
```typescript
function d3Click(element: JQuery, x: number, y: number, eventType?: ClickEventType, button?: number): void
function d3MouseUp(element: JQuery, x: number, y: number, eventType?: ClickEventType, button?: number): void
function d3MouseDown(element: JQuery, x: number, y: number, eventType?: ClickEventType, button?: number): void
function d3MouseOver(element: JQuery, x: number, y: number, eventType?: ClickEventType, button?: number): void
function d3MouseMove(element: JQuery, x: number, y: number, eventType?: ClickEventType, button?: number): void
function d3MouseOut(element: JQuery, x: number, y: number, eventType?: ClickEventType, button?: number): void
function d3KeyEvent(element: JQuery, typeArg: string, keyArg: string, keyCode: number): void
function d3TouchStart(element: JQuery, touchList?: TouchList): void
function d3TouchMove(element: JQuery, touchList?: TouchList): void
function d3TouchEnd(element: JQuery, touchList?: TouchList): void
function d3ContextMenu(element: JQuery, x: number, y: number): void
```

### <a name="helper-interfaces"></a>Hjælpegrænseflader
Følgende grænseflade og optællinger bruges i hjælpefunktionen.

```typescript
interface RgbColor {
    R: number;
    G: number;
    B: number;
    A?: number; 
}

enum ClickEventType {
    Default = 0,
    CtrlKey = 1,
    AltKey = 2,
    ShiftKey = 4,
    MetaKey = 8,
}

enum MouseEventType {
    click,
    mousedown,
    mouseup,
    mouseover,
    mousemove,
    mouseout,
}
```

## <a name="next-steps"></a>Næste trin

Hvis du vil skrive enhedstest for webpakkebaserede Power BI-visualiseringer og enhedstest med `karma` og `jasmine`, kan du f.eks. se [Selvstudium: Tilføj enhedstest i visuelle projekter i Power BI](./unit-tests-introduction.md).
