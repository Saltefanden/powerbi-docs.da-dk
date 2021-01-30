---
title: 'DAX: Passende brug af fejlfunktioner'
description: Vejledning til, hvornår du skal bruge DAX-fejlfunktioner.
author: peter-myers
ms.author: kfollis
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 09/26/2019
ms.openlocfilehash: c0766a989ea3dbfe42620fd53b4c49d6144b4c5f
ms.sourcegitcommit: fb529c4532fbbdfde7ce28e2b4b35f990e8f21d9
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/30/2021
ms.locfileid: "99088459"
---
# <a name="dax-appropriate-use-of-error-functions"></a>DAX: Passende brug af fejlfunktioner

Som dataudformer kan du overveje at bruge to nyttige DAX-funktioner, når du skriver et DAX-udtryk, som muligvis udløser en fejl af typen evalueringstid.

- Funktionen [ER.FEJL](/dax/iserror-function-dax), som kræver et enkelt udtryk og returnerer SAND, hvis det pågældende udtryk resulterer i en fejl.
- Funktionen [HVIS.FEJL](/dax/iferror-function-dax), som kræver to udtryk. Hvis det første udtryk resulterer i en fejl, returneres værdien for det andet udtryk. Det er faktisk en mere optimeret implementering af indlejring af funktionen ER.FEJL inde i en [HVIS](/dax/if-function-dax)-funktion.

Men selvom disse funktioner kan være nyttige og kan bidrage til at skrive udtryk, der er nemme at forstå, kan de også degradere ydeevnen af beregninger markant. Dette kan ske, fordi disse funktioner øger antallet af påkrævede scanninger af lagringsprogrammet.

De fleste fejl af typen evalueringstid skyldes uventede TOMME VÆRDIER eller nulværdier eller ugyldig konvertering af datatypen.

## <a name="recommendations"></a>Anbefalinger

Det er bedre at undgå at bruge funktionerne ER.FEJL og HVIS.FEJL. Anvend i stedet defensive strategier, når du udvikler modellen og skriver udtryk. Strategierne kan omfatte:

- **Sørg for, at kvalitetsdata indlæses i modellen:** Brug Power Query-transformationer til at fjerne eller erstatte ugyldige eller manglende værdier og til at angive korrekte datatyper. En Power Query-transformation kan også bruges til at filtrere rækker, når der opstår fejl, f.eks. ugyldig datakonvertering.

    Datakvaliteten kan også styres ved at angive egenskaben **Kan være nul** for kolonnen i modellen til Fra, hvorved dataopdateringen mislykkes, hvis der opleves TOMME VÆRDIER. Hvis denne fejl opstår, forbliver de data, der indlæses som følge af en vellykket opdatering, i tabellerne.
- **Brug af HVIS-funktionen:** Det logiske testudtryk med HVIS-funktionen kan afgøre, om der opstår et fejlresultat. Bemærk! Ligesom funktionerne ER.FEJL og HVIS.FEJL kan denne funktion resultere i yderligere scanninger af lagringsprogrammet, men den vil sandsynligvis have en bedre ydeevne end dem, da der ikke skal udløses nogen fejl.
- **Brug af fejltolerante funktioner:** Nogle DAX-funktioner tester og kompenserer for fejltilstande. Disse funktioner gør det muligt for dig at angive et alternativt resultat, som bliver returneret i stedet. Funktionen [DIVIDER](/dax/divide-function-dax) er præcist sådan et eksempel. Hvis du har brug for yderligere vejledning om denne funktion, kan du læse artiklen [DAX: DIVIDER-funktion vs. divisionsoperator (/)](dax-divide-function-operator.md).

## <a name="example"></a>Eksempel

Følgende målingsudtryk tester, om der skal udløses en fejl. Den returnerer TOMME VÆRDIER i denne forekomst (hvilket er tilfældet, når du ikke angiver funktionen HVIS med et udtryk af typen værdi-hvis-falsk).

```dax
Profit Margin
= IF(ISERROR([Profit] / [Sales]))
```

Denne næste version af målingsudtrykket er blevet forbedret ved hjælp af funktionen HVIS.FEJL i stedet for funktionerne HVIS og ER.FEJL.

```dax
Profit Margin
= IFERROR([Profit] / [Sales], BLANK())
```

Denne endelige version af målingsudtrykket opnår samme resultat, men på en mere effektiv og elegant måde.

```dax
Profit Margin
= DIVIDE([Profit], [Sales])
```

## <a name="next-steps"></a>Næste trin

Du kan finde flere oplysninger om denne artikel i følgende ressourcer:

- [Henvisning til DAX (Data Analysis Expressions)](/dax/)

- Læringsforløb: [Brug DAX i Power BI Desktop](/learn/paths/dax-power-bi/)
- Har du spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
- Forslag? [Få ideer til at forbedre Power BI](https://ideas.powerbi.com)