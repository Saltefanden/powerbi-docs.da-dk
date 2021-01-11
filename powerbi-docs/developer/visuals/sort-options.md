---
title: Sorteringsindstillinger til Power BI-visualiseringer i en integreret Power BI-analyse for at få bedre integreret BI-indsigt
description: I denne artikel beskrives standardsorteringen af visualiseringer i Power BI. Aktivér bedre integreret BI-indsigt ved hjælp af Power BI-integreret analyse.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 06/18/2019
ms.openlocfilehash: 0d24719b486608c283ec73f0188092a1ece3155e
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 01/05/2021
ms.locfileid: "97889242"
---
# <a name="sorting-options-for-power-bi-visuals"></a>Sorteringsmuligheder for Power BI-visualiseringer

I denne artikel beskrives det, hvordan *sorteringsindstillinger* angiver sorteringen af visualiseringer i Power BI. 

Sorteringsfunktionen kræver en af følgende parametre.

## <a name="default-sorting"></a>Standardsortering

Indstillingen `default` er den enkleste form. Den muliggør sortering af de data, der præsenteres i afsnittet "DataMappings". Denne indstilling gør det muligt for brugeren at sortere datatilknytninger og angiver sorteringsretningen.

```json
    "sorting": {
        "default": {   }
    }
```

![Sorteringsindstillinger i genvejsmenuen](media/sort-options/sorting.png)

## <a name="implicit-sorting"></a>Implicit sortering

Implicit sortering sorterer med en matrixparameteren `clauses`, der beskriver, hvordan der sorteres efter hver datarolle. `implicit` betyder, at visualiseringens bruger ikke kan ændre sorteringsrækkefølgen. Der vises ikke sorteringsindstillinger i visualiseringens menu i Power BI. Men Power BI sorterer data i henhold til de angivne indstillinger.

Parametrene `clauses` kan indeholde flere objekter med to parametre:

- `role`: Bestemmer `DataMapping` for sortering
- `direction`: Bestemmer sorteringsretningen (1 = stigende, 2 = faldende)

```json
    "sorting": {
        "implicit": {
            "clauses": [
                {
                    "role": "category",
                    "direction": 1
                },
                {
                    "role": "measure",
                    "direction": 2
                }
            ]
        }
    }
```

## <a name="custom-sorting"></a>Brugerdefineret sortering

Brugerdefineret sortering betyder, at sorteringen administreres af udvikleren i visualiseringens kode.
