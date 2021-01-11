---
title: Introduktion til brug af hjælpeprogrammer til datavisning i Power BI-visualiseringer i en integreret Power BI-analyse, der giver bedre integreret BI-indsigt
description: I denne artikel beskrives det, hvordan du bruger SVG-hjælpeprogrammer til at forenkle fortolkningen af DataView-objektet for Power BI-visualiseringer. Aktivér bedre integreret BI-indsigt ved hjælp af Power BI-integreret analyse.
author: KesemSharabi
ms.author: kesharab
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 06/18/2019
ms.openlocfilehash: 3c54333c35809ab272c065973d4d948e1ac37a8b
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 01/05/2021
ms.locfileid: "97887816"
---
# <a name="dataviewutils"></a>DataViewUtils

`DataViewUtils` er en række funktioner og klasser til forenkling af fortolkning af DataView-objektet for Power BI-visuals

## <a name="installation"></a>Installation

Hvis du vil installere pakken, skal du køre følgende kommando i mappen med din aktuelle brugerdefinerede visual:

npm install powerbi-visuals-utils-dataviewutils --save Denne kommando installerer pakken og føjer en pakke til package.json som en afhængighed

## <a name="dataviewwildcard"></a>DataViewWildcard

`DataViewWildcard` leverer funktionen `createDataViewWildcardSelector` for at understøtte en egenskabs [betinget formatering](conditional-format.md#define-how-conditional-formatting-behaves).

`createDataViewWildcardSelector` returnerer en vælger, der er påkrævet for at definere, hvordan posten for betinget formatering i formateringsruden skal anvendes, baseret på `dataviewWildcardMatchingOption (InstancesAndTotals (default), InstancesOnly, TotalsOnly)`.

Eksempel:

 ```typescript
import { dataViewWildcard } from "powerbi-visuals-utils-dataviewutils";

let selector = dataViewWildcard.createDataViewWildcardSelector(dataViewWildcard.DataViewWildcardMatchingOption.InstancesAndTotals);
// returns {data: [{dataViewWildcard:{matchingOption: 0}}]};

```

## <a name="datarolehelper"></a>DataRoleHelper

`DataRoleHelper` indeholder funktioner til kontrol af roller i et objektet dataView.

Modulet indeholder følgende funktioner:

### <a name="getmeasureindexofrole"></a>getMeasureIndexOfRole

Denne funktion finder målingen efter rollenavn og returnerer dens indeks.

```typescript
function getMeasureIndexOfRole(grouped: DataViewValueColumnGroup[], roleName: string): number;
```

Eksempel:

```typescript
import powerbi from "powerbi-visuals-api";
import DataViewValueColumnGroup = powerbi.DataViewValueColumnGroup;
import { dataRoleHelper } from "powerbi-visuals-utils-dataviewutils";
// ...

// This object is actually a part of the dataView object.
let columnGroup: DataViewValueColumnGroup[] = [{
    values: [
        {
            source: {
                displayName: "Microsoft",
                roles: {
                    "company": true
                }
            },
            values: []
        },
        {
            source: {
                displayName: "Power BI",
                roles: {
                    "product": true
                }
            },
            values: []
        }
    ]
}];

dataRoleHelper.getMeasureIndexOfRole(columnGroup, "product");

// returns: 1
```

### <a name="getcategoryindexofrole"></a>getCategoryIndexOfRole

Denne funktion finder kategorien efter rollenavn og returnerer dens indeks.

```typescript
function getCategoryIndexOfRole(categories: DataViewCategoryColumn[], roleName: string): number;
```

Eksempel:

```typescript
import powerbi from "powerbi-visuals-api";
import DataViewCategoryColumn = powerbi.DataViewCategoryColumn;
import { dataRoleHelper } from "powerbi-visuals-utils-dataviewutils";
// ...

// This object is actually a part of the dataView object.
let categoryGroup: DataViewCategoryColumn[] = [
    {
        source: {
            displayName: "Microsoft",
            roles: {
                "company": true
            }
        },
        values: []
    },
    {
        source: {
            displayName: "Power BI",
            roles: {
                "product": true
            }
        },
        values: []
    }
];

dataRoleHelper.getCategoryIndexOfRole(categoryGroup, "product");

// returns: 1
```

### <a name="hasrole"></a>hasRole

Denne funktion kontrollerer, om den angivne rolle er defineret i metadataene.

```typescript
function hasRole(column: DataViewMetadataColumn, name: string): boolean;
```

Eksempel:

```typescript
import powerbi from "powerbi-visuals-api";
import DataViewMetadataColumn = powerbi.DataViewMetadataColumn;
import { dataRoleHelper } from "powerbi-visuals-utils-dataviewutils";

// This object is actually a part of the dataView object.
let metadata: DataViewMetadataColumn = {
    displayName: "Microsoft",
    roles: {
        "company": true
    }
};

DataRoleHelper.hasRole(metadata, "company");

// returns: true
```

### <a name="hasroleindataview"></a>hasRoleInDataView

Denne funktion kontrollerer, om den angivne rolle er defineret i dataView.

```typescript
function hasRoleInDataView(dataView: DataView, name: string): boolean;
```

Eksempel:

```typescript
import powerbi from "powerbi-visuals-api";
import DataView = powerbi.DataView;
import { dataRoleHelper } from "powerbi-visuals-utils-dataviewutils";

// This object is actually a part of the dataView object.
let dataView: DataView = {
    metadata: {
        columns: [
            {
                displayName: "Microsoft",
                roles: {
                    "company": true
                }
            },
            {
                displayName: "Power BI",
                roles: {
                    "product": true
                }
            }
        ]
    }
};

DataRoleHelper.hasRoleInDataView(dataView, "product");

// returns: true
```

### <a name="hasroleinvaluecolumn"></a>hasRoleInValueColumn

Denne funktion kontrollerer, om den angivne rolle er defineret i værdikolonnen.

```typescript
function hasRoleInValueColumn(valueColumn: DataViewValueColumn, name: string): boolean;
```

Eksempel:

```typescript
import powerbi from "powerbi-visuals-api";
import DataViewValueColumn = powerbi.DataViewValueColumn;
import { dataRoleHelper } from "powerbi-visuals-utils-dataviewutils";

// This object is actually a part of the dataView object.
let valueColumn: DataViewValueColumn = {
    source: {
        displayName: "Microsoft",
        roles: {
            "company": true
        }
    },
    values: []
};

dataRoleHelper.hasRoleInValueColumn(valueColumn, "company");

// returns: true
```

## <a name="dataviewobjects"></a>DataViewObjects

`DataViewObjects` indeholder funktioner til udtrækning af objekternes værdier.

Modulet indeholder følgende funktioner:

### <a name="getvalue"></a>getValue

Denne funktion returnerer det angivne objekts værdi.

```typescript
function getValue<T>(objects: DataViewObjects, propertyId: DataViewObjectPropertyIdentifier, defaultValue?: T): T;
```

Eksempel:

```typescript
import powerbi from "powerbi-visuals-api";
import DataViewObjectPropertyIdentifier = powerbi.DataViewObjectPropertyIdentifier;
import { dataViewObjects } from "powerbi-visuals-utils-dataviewutils";

let property: DataViewObjectPropertyIdentifier = {
    objectName: "microsoft",
    propertyName: "bi"
};

// This object is actually a part of the dataView object.
let objects: powerbi.DataViewObjects = {
    "microsoft": {
        "windows": 5,
        "bi": "Power"
    }
};

dataViewObjects.getValue(objects, property);

// returns: Power
```

### <a name="getobject"></a>getObject

Denne funktion returnerer et objekt for det angivne objekt.

```typescript
function getObject(objects: DataViewObjects, objectName: string, defaultValue?: IDataViewObject): IDataViewObject;
```

Eksempel:

```typescript
import { dataViewObjects } from "powerbi-visuals-utils-dataviewutils";

// This object is actually a part of the dataView object.
let objects: powerbi.DataViewObjects = {
    "microsoft": {
        "windows": 5,
        "bi": "Power"
    }
};

dataViewObjects.getObject(objects, "microsoft");

/* returns: {
    "bi": "Power",
    "windows": 5

}*/
```

### <a name="getfillcolor"></a>getFillColor

Denne funktion returnerer en uigennemsigtig farve for objekterne.

```typescript
function getFillColor(objects: DataViewObjects, propertyId: DataViewObjectPropertyIdentifier, defaultColor?: string): string;
```

Eksempel:

```typescript
import powerbi from "powerbi-visuals-api";
import DataViewObjectPropertyIdentifier = powerbi.DataViewObjectPropertyIdentifier;
import { dataViewObjects } from "powerbi-visuals-utils-dataviewutils";

let property: DataViewObjectPropertyIdentifier = {
    objectName: "power",
    propertyName: "fillColor"
};

// This object is actually part of the dataView object.
let objects: powerbi.DataViewObjects = {
    "power": {
        "fillColor": {
            "solid": {
                "color": "yellow"
            }
        },
        "bi": "Power"
    }
};

dataViewObjects.getFillColor(objects, property);

// returns: yellow
```

### <a name="getcommonvalue"></a>getCommonValue

Denne funktion er en universel funktion til hentning af farven på eller værdien af et givent objekt.

```typescript
function getCommonValue(objects: DataViewObjects, propertyId: DataViewObjectPropertyIdentifier, defaultValue?: any): any;
```

Eksempel:

```typescript
import powerbi from "powerbi-visuals-api";
import DataViewObjectPropertyIdentifier = powerbi.DataViewObjectPropertyIdentifier;
import { dataViewObjects } from "powerbi-visuals-utils-dataviewutils";

let colorProperty: DataViewObjectPropertyIdentifier = {
    objectName: "power",
    propertyName: "fillColor"
};

let biProperty: DataViewObjectPropertyIdentifier = {
    objectName: "power",
    propertyName: "bi"
};

// This object is actually part of the dataView object.
let objects: powerbi.DataViewObjects = {
    "power": {
        "fillColor": {
            "solid": {
                "color": "yellow"
            }
        },
        "bi": "Power"
    }
};

dataViewObjects.getCommonValue(objects, colorProperty); // returns: yellow
dataViewObjects.getCommonValue(objects, biProperty); // returns: Power
```

## <a name="dataviewobject"></a>DataViewObject

`DataViewObject` indeholder funktioner til udtrækning af objektets værdi.

Modulet indeholder følgende funktioner:

### <a name="getvalue"></a>getValue

Denne funktion returnerer en værdi for objektet efter egenskabsnavn.

```typescript
function getValue<T>(object: IDataViewObject, propertyName: string, defaultValue?: T): T;
```

Eksempel:

```typescript
import { dataViewObject } from "powerbi-visuals-utils-dataviewutils";

// This object is actually a part of the dataView object.
let object: powerbi.DataViewObject = {
    "windows": 5,
    "microsoft": "Power BI"
};

dataViewObject.getValue(object, "microsoft");

// returns: Power BI
```

### <a name="getfillcolorbypropertyname"></a>getFillColorByPropertyName

Denne funktion returnerer en uigennemsigtig farve for objektet efter egenskabsnavn.

```typescript
function getFillColorByPropertyName(object: IDataViewObject, propertyName: string, defaultColor?: string): string;
```

Eksempel:

```typescript
import { dataViewObject } from "powerbi-visuals-utils-dataviewutils";

// This object is actually a part of the dataView object.
let object: powerbi.DataViewObject = {
    "windows": 5,
    "fillColor": {
        "solid": {
            "color": "green"
        }
    }
};

dataViewObject.getFillColorByPropertyName(object, "fillColor");

// returns: green
```

### <a name="converterhelper"></a>converterHelper

`converterHelper` indeholder funktioner til kontrol af egenskaber for dataView.

Modulet indeholder følgende funktioner:

### <a name="categoryisalsoseriesrole"></a>categoryIsAlsoSeriesRole

Denne funktion kontrollerer, om kategorien også er en serie.

```typescript
function categoryIsAlsoSeriesRole(dataView: DataViewCategorical, seriesRoleName: string, categoryRoleName: string): boolean;
```

Eksempel:

```typescript
import powerbi from "powerbi-visuals-api";
import DataViewCategorical = powerbi.DataViewCategorical;
import { converterHelper } from "powerbi-visuals-utils-dataviewutils";
// ...


// This object is actually part of the dataView object.
let categorical: DataViewCategorical = {
    categories: [{
        source: {
            displayName: "Microsoft",
            roles: {
                "power": true,
                "bi": true
            }
        },
        values: []
    }]
};

converterHelper.categoryIsAlsoSeriesRole(categorical, "power", "bi");

// returns: true
```

### <a name="getseriesname"></a>getSeriesName

Denne funktion returnerer seriens navn.

```typescript
function getSeriesName(source: DataViewMetadataColumn): PrimitiveValue;
```

Eksempel:

```typescript
import powerbi from "powerbi-visuals-api";
import DataViewMetadataColumn = powerbi.DataViewMetadataColumn;
import { converterHelper } from "powerbi-visuals-utils-dataviewutils";

// This object is actually a part of the dataView object.
let metadata: DataViewMetadataColumn = {
    displayName: "Microsoft",
    roles: {
        "power": true,
        "bi": true
    },
    groupName: "Power BI"
};

converterHelper.getSeriesName(metadata);

// returns: Power BI
```

### <a name="isimageurlcolumn"></a>isImageUrlColumn

Denne funktion kontrollerer, om kolonnen indeholder en URL-adresse til et billede.

```typescript
function isImageUrlColumn(column: DataViewMetadataColumn): boolean;
```

Eksempel:

```typescript
import powerbi from "powerbi-visuals-api";
import DataViewMetadataColumn = powerbi.DataViewMetadataColumn;
import { converterHelper } from "powerbi-visuals-utils-dataviewutils";

// This object is actually a part of the dataView object.
let metadata: DataViewMetadataColumn = {
    displayName: "Microsoft",
    type: {
        misc: {
            imageUrl: true
        }
    }
};

converterHelper.isImageUrlColumn(metadata);

// returns: true
```

### <a name="isweburlcolumn"></a>isWebUrlColumn

Denne funktion kontrollerer, om kolonnen indeholder en URL-adresse til et websted.

```typescript
function isWebUrlColumn(column: DataViewMetadataColumn): boolean;
```

Eksempel:

```typescript
import powerbi from "powerbi-visuals-api";
import DataViewMetadataColumn = powerbi.DataViewMetadataColumn;
import { converterHelper } from "powerbi-visuals-utils-dataviewutils";

// This object is actually a part of the dataView object.
let metadata: DataViewMetadataColumn = {
    displayName: "Microsoft",
    type: {
        misc: {
            webUrl: true
        }
    }
};

converterHelper.isWebUrlColumn(metadata);

// returns: true
```

### <a name="hasimageurlcolumn"></a>hasImageUrlColumn

Denne funktion kontrollerer, om dataView har en kolonne med en URL-adresse til et billede.

```typescript
function hasImageUrlColumn(dataView: DataView): boolean;
```

Eksempel:

```typescript
import DataView = powerbi.DataView;
import converterHelper = powerbi.extensibility.utils.dataview.converterHelper;

// This object is actually part of the dataView object.
let dataView: DataView = {
    metadata: {
        columns: [
            {
                displayName: "Microsoft"
            },
            {
                displayName: "Power BI",
                type: {
                    misc: {
                        imageUrl: true
                    }
                }
            }
        ]
    }
};

converterHelper.hasImageUrlColumn(dataView);

// returns: true
```

## <a name="dataviewobjectsparser"></a>DataViewObjectsParser

`DataViewObjectsParser` er den nemmeste måde at fortolke egenskaber for formateringspanelet på.

Klassen omfatter følgende metoder:

### <a name="getdefault"></a>getDefault

Denne statiske metode returnerer en forekomst af DataViewObjectsParser.

```typescript
static getDefault(): DataViewObjectsParser;
```

Eksempel:

```typescript
import { dataViewObjectsParser } from "powerbi-visuals-utils-dataviewutils";
// ...

dataViewObjectsParser.getDefault();

// returns: an instance of the DataViewObjectsParser
```

### <a name="parse"></a>parse

Denne metode fortolker egenskaber for formateringspanelet og returnerer en forekomst af `DataViewObjectsParser`.

```typescript
static parse<T extends DataViewObjectsParser>(dataView: DataView): T;
```

Eksempel:

```typescript
import powerbi from "powerbi-visuals-api";
import IVisual = powerbi.extensibility.IVisual;
import VisualUpdateOptions = powerbi.extensibility.visual.VisualUpdateOptions;
import { dataViewObjectsParser } from "powerbi-visuals-utils-dataviewutils";

/**
 * This class describes formatting panel properties.
 * Name of the property should match its name described in the capabilities.
 */
class DataPointProperties {
    public fillColor: string = "red"; // This value is a default value of the property.
}

class PropertiesParser extends dataViewObjectsParser.DataViewObjectsParser {
    /**
     * This property describes a group of properties.
     */
    public dataPoint: DataPointProperties = new DataPointProperties();
}

export class YourVisual extends IVisual {
    // implementation of the IVisual.

    private propertiesParser: PropertiesParser;

    public update(options: VisualUpdateOptions): void {
        // Parses properties.
        this.propertiesParser = PropertiesParser.parse<PropertiesParser>(options.dataViews[0]);

        // You can use the properties after parsing
        console.log(this.propertiesParser.dataPoint.fillColor); // returns "red" as default value, it will be updated automatically after any change of the formatting panel.
    }
}
```

## <a name="enumerateobjectinstances"></a>enumerateObjectInstances

Denne statiske metode optæller egenskaber og returnerer en forekomst af `VisualObjectInstanceEnumeration`.

Udfør den i metoden `enumerateObjectInstances` for visual'et.

```typescript
static enumerateObjectInstances(dataViewObjectParser: dataViewObjectsParser.DataViewObjectsParser, options: EnumerateVisualObjectInstancesOptions): VisualObjectInstanceEnumeration;
```

Eksempel:

```typescript
import powerbi from "powerbi-visuals-api";
import IVisual = powerbi.extensibility.IVisual;
import EnumerateVisualObjectInstancesOptions = powerbi.EnumerateVisualObjectInstancesOptions;
import VisualObjectInstanceEnumeration = powerbi.VisualObjectInstanceEnumeration;
import VisualUpdateOptions = powerbi.extensibility.visual.VisualUpdateOptions;
import { dataViewObjectsParser } from "powerbi-visuals-utils-dataviewutils";

/**
 * This class describes formatting panel properties.
 * Name of the property should match its name described in the capabilities.
 */
class DataPointProperties {
    public fillColor: string = "red";
}

class PropertiesParser extends dataViewObjectsParser.DataViewObjectsParser {
    /**
     * This property describes a group of properties.
     */
    public dataPoint: DataPointProperties = new DataPointProperties();
}

export class YourVisual extends IVisual {
    // implementation of the IVisual.

    private propertiesParser: PropertiesParser;

    public update(options: VisualUpdateOptions): void {
        // Parses properties.
        this.propertiesParser = PropertiesParser.parse<PropertiesParser>(options.dataViews[0]);
    }

    /**
     * This method will be executed only if the formatting panel is open.
     */
    public enumerateObjectInstances(options: EnumerateVisualObjectInstancesOptions): VisualObjectInstanceEnumeration {
        return PropertiesParser.enumerateObjectInstances(this.propertiesParser, options);
    }
}
```
