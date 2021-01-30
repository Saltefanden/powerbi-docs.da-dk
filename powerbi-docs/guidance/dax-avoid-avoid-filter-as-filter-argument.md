---
title: 'DAX: Undgå at bruge FILTER som et filterargument'
description: Vejledning til, hvordan du bruger funktionen FILTER som et filterargument.
author: peter-myers
ms.author: kfollis
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 12/30/2019
ms.openlocfilehash: 74ddac5a3ac2fa5e6e0fae9f3fdf5c7f79ba22d3
ms.sourcegitcommit: fb529c4532fbbdfde7ce28e2b4b35f990e8f21d9
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/30/2021
ms.locfileid: "99088574"
---
# <a name="dax-avoid-using-filter-as-a-filter-argument"></a>DAX: Undgå at bruge FILTER som et filterargument

Som dataudformer er det almindeligt at skrive DAX-udtryk, der skal evalueres i en ændret filterkontekst. Du kan f.eks. skrive en målingsdefinition for at beregne salg for "produkter med høj avance". Vi beskriver denne beregning senere i artiklen.

> [!NOTE]
> Denne artikel er især relevant for modelberegninger, der anvender filtre til import af tabeller.

DAX-funktionerne [CALCULATE](/dax/calculate-function-dax) og [CALCULATETABLE](/dax/calculatetable-function-dax) er vigtige og nyttige funktioner. De giver dig mulighed for at skrive beregninger, der fjerner eller tilføjer filtre eller ændrer relationsstier. Det gøres ved at overføre filterargumenter, der enten er booleske udtryk, tabeludtryk eller specielle filterfunktioner. Vi diskuterer kun booleske udtryk og tabeludtryk i denne artikel.

Overvej følgende målingsdefinition, som beregner røde produktsalg ved hjælp af et tabeludtryk. Det erstatter eventuelle filtre, der kan anvendes på tabellen **Product**.

```dax
Red Sales =
CALCULATE(
    [Sales],
    FILTER('Product', 'Product'[Color] = "Red")
)
```

Funktionen CALCULATE accepterer et tabeludtryk, der returneres af DAX-funktionen [FILTER](/dax/filter-function-dax), som evaluerer filterudtrykket for hver række i tabellen **Product**. Det finder det korrekte resultat – salgsresultatet for røde produkter. Det kan dog gøres meget mere effektivt ved hjælp af et boolesk udtryk.

Her er en forbedret målingsdefinition, som bruger et boolesk udtryk i stedet for tabeludtrykket. DAX-funktionen [KEEPFILTERS](/dax/keepfilters-function-dax) sikrer, at eventuelle eksisterende filtre, der er anvendt på kolonnen **Farve**, bevares og ikke overskrives.

```dax
Red Sales =
CALCULATE(
    [Sales],
    KEEPFILTERS('Product'[Color] = "Red")
)
```

Vi anbefaler, at du overfører filterargumenter som booleske udtryk, når det er muligt. Det skyldes, at tabeller af typen Importér model er gemte kolonnelagre. De er eksplicit optimeret til at filtrere kolonner på denne måde på en effektiv måde.

Der er dog begrænsninger, der gælder for booleske udtryk, når de bruges som filterargumenter. De:

- Kan ikke sammenlignes med andre kolonner
- Kan ikke referere til en måling
- Kan ikke bruge indlejrede funktioner af typen CALCULATE
- Kan ikke bruge funktioner, der scanner eller returnerer en tabel

Det betyder, at du skal bruge tabeludtryk til at få mere komplekse filterkrav.

Overvej nu en anden målingsdefinition.

```dax
High Margin Product Sales =
CALCULATE(
    [Sales],
    FILTER(
        'Product',
        'Product'[ListPrice] > 'Product'[StandardCost] * 2
    )
)
```

Definitionen af et _produkt med høj avance_ er et produkt, der har en listepris, der overskrider det dobbelte af standardomkostningerne. I dette eksempel skal funktionen Filter anvendes. Det skyldes, at filterudtrykket er for komplekst for et boolesk udtryk.

Her er et mere eksempel. Kravet denne gang er at beregne salg, men kun for måneder, der har opnået en fortjeneste.

```dax
Sales for Profitable Months =
CALCULATE(
    [Sales],
    FILTER(
        VALUES('Date'[Month]),
        [Profit] > 0)
    )
)
```

I dette eksempel skal funktionen FILTER også anvendes. Det skyldes, at den kræver vurdering af målingen **Profit** for at udelukke de måneder, hvor der ikke opnås en fortjeneste. Det er ikke muligt at bruge en måling i et boolesk udtryk, når den bruges som et filterargument.

## <a name="recommendations"></a>Anbefalinger

Vi anbefaler, at du bruger booleske udtryk som filterargumenter, når det er muligt, for at opnå den bedste ydeevne.

Derfor bør funktionen FILTER kun bruges, når det er nødvendigt. Du kan bruge den til at udføre filtrering af komplekse kolonnesammenligninger. Disse kolonnesammenligninger kan omfatte:

- Målinger
- Andre kolonner
- Brug af DAX-funktionen [OR](/dax/or-function-dax) eller den logiske operator OR (| |)

## <a name="next-steps"></a>Næste trin

Du kan finde flere oplysninger om denne artikel i følgende ressourcer:

- [Henvisning til DAX (Data Analysis Expressions)](/dax/)
- [Filterfunktioner (DAX)](/dax/filter-function-dax)
- Læringsforløb: [Brug DAX i Power BI Desktop](/learn/paths/dax-power-bi/)
- Har du spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
- Forslag? [Få ideer til at forbedre Power BI](https://ideas.powerbi.com)