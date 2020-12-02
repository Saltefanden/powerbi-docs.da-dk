---
title: Objekter og egenskaber for visualiseringer i Power BI
description: I denne artikel beskrives egenskaber, der kan brugertilpasses, for visualiseringer i Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: ae548abd0d579414a69b0d970213ff9d69ff2f08
ms.sourcegitcommit: 9d033abd9c01a01bba132972497dda428d7d5c12
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 11/25/2020
ms.locfileid: "96120207"
---
# <a name="objects-and-properties-of-power-bi-visuals"></a>Objekter og egenskaber for visualiseringer i Power BI

Objekter beskriver de egenskaber, der kan tilpasses, og som er knyttet til en visualisering. Et objekt kan have flere egenskaber, og hver egenskab har en tilknyttet type, der beskriver, hvad egenskaben skal være. Denne artikel indeholder oplysninger om objekter og egenskabstyper.

`myCustomObject` er det interne navn, der bruges til at referere objektet i `dataView` og `enumerateObjectInstances`.

```json
"objects": {
    "myCustomObject": {
        "displayName": "My Object Name",
        "properties": { ... }
    }
}
```

## <a name="display-name"></a>Vist navn

`displayName` er det navn, der bliver vist i egenskabsruden.

## <a name="properties"></a>Egenskaber

`properties` er en afbildning af egenskaber, der er defineret af udvikleren.

```json
"properties": {
    "myFirstProperty": {
        "displayName": "firstPropertyName",
        "type": ValueTypeDescriptor | StructuralTypeDescriptor
    }
}
```

> [!NOTE]
> `show` er en speciel egenskab, der gør det muligt for en switch at skifte objekt.

Eksempel:

```json
"properties": {
    "show": {
        "displayName": "My Property Switch",
        "type": {"bool": true}
    }
}
```

### <a name="property-types"></a>Egenskabstyper

Der findes to egenskabstyper: `ValueTypeDescriptor` og `StructuralTypeDescriptor`.

#### <a name="value-type-descriptor"></a>Beskrivelse af værditype

`ValueTypeDescriptor`-typer er hovedsageligt primitive og bruges normalt som et statisk objekt.

Her er nogle af de mest almindelige `ValueTypeDescriptor`-elementer:

```typescript
export interface ValueTypeDescriptor {
    text?: boolean;
    numeric?: boolean;
    integer?: boolean;
    bool?: boolean;
}
```

#### <a name="structural-type-descriptor"></a>Beskrivelse af strukturel type

`StructuralTypeDescriptor`-typer bruges hovedsageligt til databundne objekter.
Den mest almindelige `StructuralTypeDescriptor`-type er *udfyldning*.

```typescript
export interface StructuralTypeDescriptor {
    fill?: FillTypeDescriptor;
}
```

## <a name="gradient-property"></a>Egenskaben Graduering

Egenskaben Graduering er en egenskab, der ikke kan angives som en standardegenskab. I stedet skal du angive en regel for erstatning af egenskaben Farvevælger (*udfyldningstype*).

Et eksempel vises i følgende kode:

```json
"properties": {
    "showAllDataPoints": {
        "displayName": "Show all",
        "displayNameKey": "Visual_DataPoint_Show_All",
        "type": {
            "bool": true
        }
    },
    "fill": {
        "displayName": "Fill",
        "displayNameKey": "Visual_Fill",
        "type": {
            "fill": {
                "solid": {
                    "color": true
                }
            }
        }
    },
    "fillRule": {
        "displayName": "Color saturation",
        "displayNameKey": "Visual_ColorSaturation",
        "type": {
            "fillRule": {}
        },
        "rule": {
            "inputRole": "Gradient",
            "output": {
                "property": "fill",
                    "selector": [
                        "Category"
                    ]
            }
        }
    }
}
```

Vær opmærksom på egenskaberne *udfyldning* og *fillRule*. Den første er farvevælgeren, den anden er erstatningsreglen for graduering, der erstatter *udfyldningsegenskaben*, `visually`, når regelbetingelserne er opfyldt.

Dette link mellem *udfyldningsegenskaben* og erstatningsreglen angives i afsnittet `"rule"`>`"output"` for egenskaben *fillRule*.

Egenskaben `"Rule"`>`"InputRole"` angiver, hvilken datarolle der udløser reglen (betingelsen). Hvis datarollen `"Gradient"` indeholder data i dette eksempel, anvendes reglen for egenskaben `"fill"`.

Følgende kode viser et eksempel på den datarolle, der udløser udfyldningsreglen (`the last item`):

```json
{
    "dataRoles": [
            {
                "name": "Category",
                "kind": "Grouping",
                "displayName": "Details",
                "displayNameKey": "Role_DisplayName_Details"
            },
            {
                "name": "Series",
                "kind": "Grouping",
                "displayName": "Legend",
                "displayNameKey": "Role_DisplayName_Legend"
            },
            {
                "name": "Gradient",
                "kind": "Measure",
                "displayName": "Color saturation",
                "displayNameKey": "Role_DisplayName_Gradient"
            }
    ]
}
```

## <a name="the-enumerateobjectinstances-method"></a>Metoden enumerateObjectInstances

Hvis du vil bruge objekter effektivt, skal du bruge en funktion i din brugerdefinerede visualisering, der hedder `enumerateObjectInstances`. Denne funktion udfylder egenskabsruden med objekter og bestemmer også, hvor objekterne skal bindes i datavisningen.  

Sådan ser en typisk opsætning ud:

```typescript
public enumerateObjectInstances(options: EnumerateVisualObjectInstancesOptions): VisualObjectInstanceEnumeration {
    let objectName: string = options.objectName;
    let objectEnumeration: VisualObjectInstance[] = [];

    switch( objectName ) {
        case 'myCustomObject':
            objectEnumeration.push({
                objectName: objectName,
                properties: { ... },
                selector: { ... }
            });
            break;
    };

    return objectEnumeration;
}
```

### <a name="properties"></a>Egenskaber

Egenskaberne i `enumerateObjectInstances` afspejler de egenskaber, du har defineret i dine funktioner. Du kan finde et eksempel ved at gå til slutningen af denne artikel.

### <a name="objects-selector"></a>Objektvælger

Vælgeren `enumerateObjectInstances` angiver, hvor hvert objekt skal bindes i datavisningen. Der er fire forskellige muligheder.

#### <a name="static"></a>statisk

Dette objekt er bundet til metadata `dataviews[index].metadata.objects` som vist her.

```typescript
selector: null
```

#### <a name="columns"></a>kolonner

Dette objekt bindes til kolonner med det tilsvarende `QueryName`.

```typescript
selector: {
    metadata: 'QueryName'
}
```

#### <a name="selector"></a>vælger

Dette objekt bindes til det element, som du har oprettet et `selectionID` for. I dette eksempel antager vi, at vi har oprettet `selectionID`'er for nogle datapunkter, og at vi looper gennem dem.

```typescript
for (let dataPoint in dataPoints) {
    ...
    selector: dataPoint.selectionID.getSelector()
}
```

#### <a name="scope-identity"></a>Område-id

Dette objekt bindes til bestemte værdier ved gruppernes skæringspunkt. Hvis du f.eks. har kategorierne `["Jan", "Feb", "March", ...]` og serien `["Small", "Medium", "Large"]`, kan det være en fordel at have et objekt på skæringspunktet for værdier, der stemmer overens med `Feb` og `Large`. Det kan du gøre ved at hente `DataViewScopeIdentity` for begge kolonner, skubbe dem til variablen `identities` og benytte denne syntaks sammen med vælgeren.

```typescript
selector: {
    data: <DataViewScopeIdentity[]>identities
}
```

##### <a name="example"></a>Eksempel

Det følgende eksempel viser, hvordan en objectEnumeration ville se ud for et customColor-objekt med egenskaben *udfyldning*. Dette objekt skal bindes statisk til `dataViews[index].metadata.objects` som vist:

```typescript
objectEnumeration.push({
    objectName: "customColor",
    displayName: "Custom Color",
    properties: {
        fill: {
            solid: {
                color: dataPoint.color
            }
        }
    },
    selector: null
});
```
