---
title: Visualiserings-API i en integreret Power BI-analyse, der giver bedre integreret BI-indsigt
description: I denne artikel beskrives det, hvordan du bruger IVisual API i Power BI-visualiseringer. Aktivér bedre integreret BI-indsigt ved hjælp af Power BI-integreret analyse.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 03/19/2020
ms.openlocfilehash: 7b81ecfa1b97b202b6c1ff306cf858f2ea00acde
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 01/05/2021
ms.locfileid: "97888529"
---
# <a name="visual-api"></a>Visualiserings-API
Alle visualiseringer starter med en klasse, der implementerer grænsefladen `IVisual`. Du kan navngive klassen, så længe der er nøjagtig én klasse, der implementerer grænsefladen `IVisual`.

> [!NOTE]
> Klassenavnet på visualiseringen skal stemme overens med det, der er defineret i filen *pbiviz.json*.

Se eksemplet på visualiseringsklassen med følgende metoder, der skal implementeres:

* `constructor` – en standardkonstruktør til initialisering af visualiseringens tilstand
* `update` – til at opdatere visualiseringens data
* `enumerateObjectInstances` – hvis du vil returnere objekter til at udfylde egenskabsruden (formateringsindstillinger), hvor du kan ændre dem efter behov
* `destroy` – en standarddestruktør til oprydning

```typescript
class MyVisual implements IVisual {
    
    constructor(options: VisualConstructorOptions) {
        //one time setup code goes here (called once)
    }
    
    public update(options: VisualUpdateOptions): void {
        //code to update your visual goes here (called on all view or data changes)
    }

    public enumerateObjectInstances(options: EnumerateVisualObjectInstancesOptions): VisualObjectInstanceEnumeration {
        //returns objects to populate the property pane (called for each object defined in capabilities)
    }
    
    public destroy(): void {
        //one time cleanup code goes here (called once)
    }
}
```

## <a name="constructor"></a>konstruktør

Konstruktøren i den visuelle klasse kaldes, når visualiseringen er instantieret. Den kan bruges til alle de konfigurationshandlinger, der kræves af visualiseringen.

```typescript
constructor(options: VisualConstructorOptions)
```

**VisualConstructorOptions**

* `element: HTMLElement` – en reference til det DOM-element, der skal indeholde visualiseringen
* `host: IVisualHost` – en samling egenskaber og tjenester, der kan bruges til at interagere med den visuelle vært (Power BI)

   `IVisualHost` indeholder følgende tjenester:

   ```typescript
   export interface IVisualHost extends extensibility.IVisualHost {
       createSelectionIdBuilder: () => visuals.ISelectionIdBuilder;
       : () => ISelectionManager;
       colorPalette: ISandboxExtendedColorPalette;
       persistProperties: (changes: VisualObjectInstancesToPersist) => void;
       applyJsonFilter: (filter: IFilter[] | IFilter, objectName: string, propertyName: string, action: FilterAction) => void;
       tooltipService: ITooltipService;
       telemetry: ITelemetryService;
       authenticationService: IAuthenticationService;
       locale: string;
       allowInteractions: boolean;
       launchUrl: (url: string) => void;
       fetchMoreData: () => boolean;
       instanceId: string;
       refreshHostData: () => void;
       createLocalizationManager: () => ILocalizationManager;
       storageService: ILocalVisualStorageService;
       eventService: IVisualEventService;
       switchFocusModeState: (on: boolean) => void;
   }
   ```
   * `createSelectionIdBuilder` – genererer og lagrer metadata for elementer, der kan vælges, i visualiseringen
   * `createSelectionManager` – opretter den kommunikationsbro, der skal bruges til at give visualiseringens vært besked om ændringer i markeringstilstanden, se [API til valg](./selection-api.md).
   * `createLocalizationManager` – genererer en manager, der kan hjælpe med [lokalisering](./localization.md)
   * `allowInteractions: boolean` – et boolesk flag, der kan bruges til at få et indblik i, om visualiseringen skal være interaktiv
   * `applyJsonFilter` – anvender bestemte filtertyper, se [filter-API](./filter-api.md)
   * `persistProperties` – gør det muligt for brugerne at bevare egenskaber og gemme dem sammen med den visuelle definition, så de er tilgængelige ved næste genindlæsning
   * `eventService` – returnerer en [hændelsestjeneste](./event-service.md) til at understøtte hændelser til **gengivelse**
   * `storageService` – returnerer en tjeneste, der kan hjælpe med at bruge [lokal lagring](./local-storage.md) i visualiseringen
   * `authenticationService` – genererer en tjeneste, der hjælper med brugergodkendelse
   * `tooltipService` – returnerer en [værktøjstiptjeneste](./add-tooltips.md), der kan hjælpe med at bruge værktøjstip i visualiseringen
   * `launchUrl` – hjælper [med at starte URL](./launch-url.md) i den næste fane
   * `locale` – returnerer en landestandardstreng, se [lokalisering](./localization.md)
   * `instanceId` –returnerer en streng, der identificerer den aktuelle visuelle forekomst
   * `colorPalette` – returnerer den colorPalette, der er påkrævet for at anvende farver på dine data
   * `fetchMoreData` – understøtter brug af flere data end standardgrænsen (1.000 rækker)
   * `switchFocusModeState` – hjælper med at ændre tilstanden for fokustilstand

## <a name="update"></a>opdater

Alle visualiseringer skal implementere en offentlig opdateringsmetode, der kaldes, når der er en ændring i dataene eller værtsmiljøet.

```typescript
public update(options: VisualUpdateOptions): void
```

**VisualUpdateOptions**

* `viewport: IViewport` – billedets dimensioner, som visualiseringen skal gengives i
* `dataViews: DataView[]` – det DataView-objekt, der indeholder alle de data, der skal bruges for at gengive visualiseringen (visualiseringen vil typisk bruge kategoriegenskaben under DataView)
* `type: VisualUpdateType` – flag til at angive typen eller typerne af denne opdatering (**Data** | **Resize** | **ViewMode** | **Style** | **ResizeEnd**)
* `viewMode: ViewMode` – flag til at angive visningstilstanden for visualiseringen (**View** | **Edit** | **InFocusEdit**)
* `editMode: EditMode` – flag til at angive redigeringstilstanden for visualiseringen (**Standard** | **Advanced**) (hvis visualiseringen understøtter **AdvancedEditMode**, skal den kun gengive avancerede kontrolelementer til brugergrænsefladen, når **editMode** er indstillet til **Advanced** under [AdvancedEditMode](./advanced-edit-mode.md))
* `operationKind?: VisualDataChangeOperationKind` – flag til at angive typen af dataændring (**Create** | **Append**)
* `jsonFilters?: IFilter[]` – samling af anvendte JSON-filtre
* `isInFocus?: boolean` – flag til at angive, om visualiseringen er i fokustilstand eller ej
    
## <a name="enumerateobjectinstances-optional"></a>enumerateObjectInstances `optional`

Denne metode kaldes for alle de objekter, der er angivet i egenskaberne. Når du bruger disse indstillinger (i øjeblikket kun navnet) kan du returnere en `VisualObjectInstanceEnumeration` med oplysninger om, hvordan denne egenskab skal vises.

```typescript
enumerateObjectInstances(options:EnumerateVisualObjectInstancesOptions):VisualObjectInstanceEnumeration
```

**EnumerateVisualObjectInstancesOptions**

* `objectName: string` – navnet på objektet

## <a name="destroy-optional"></a>destroy `optional`

Destroy-funktionen kaldes, når visualiseringen er blevet fjernet og kan bruges til at rydde op i opgaver, f.eks. til at fjerne lyttefunktioner for hændelser.

``` typescript
public destroy(): void
```

> [!Note]
> Power BI kalder generelt ikke `destroy`, da det er hurtigere at fjerne hele den IFrame, der indeholder visualiseringen.
