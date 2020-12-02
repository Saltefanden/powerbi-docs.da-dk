---
title: 'DAX: Brug variabler til at forbedre dine formler'
description: Vejledning til brug af variabler i DAX-udtryk.
author: peter-myers
ms.author: v-pemyer
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 11/23/2019
ms.openlocfilehash: 2448ac8b94465872e4224738162c6a252cafe56c
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96393594"
---
# <a name="dax-use-variables-to-improve-your-formulas"></a>DAX: Brug variabler til at forbedre dine formler

Det kan være udfordrende for dataudformere at skrive og foretage fejlfinding af visse DAX-beregninger. Det er almindeligt, at komplekse beregninger ofte kræver, at der skrives sammensatte eller komplekse udtryk. Sammensatte udtryk kan involvere brugen af mange indlejrede funktioner og muligvis genbrug af udtrykslogik.

Brug af variabler i DAX-formler hjælper dig, når du skal skrive komplekse og effektive beregninger. Variabler kan:

- [forbedre ydeevnen](#improve-performance)
- [forbedre læsbarheden](#improve-readability)
- [forenkle fejlfinding](#simplify-debugging)
- [reducer kompleksiteten](#reduce-complexity)

I denne artikel demonstrerer vi de første tre fordele ved hjælp af en eksempelmåling for salgsvæksten år-til-år. (Formlen for salgsvæksten år-til-år er: periodesalg _mindre salg i samme periode sidste år, _divideret med_ salg i samme periode sidste år.)

Lad os starte med følgende målingsdefinition.

```dax
Sales YoY Growth % =
DIVIDE(
    ([Sales] - CALCULATE([Sales], PARALLELPERIOD('Date'[Date], -12, MONTH))),
    CALCULATE([Sales], PARALLELPERIOD('Date'[Date], -12, MONTH))
)
```

Målingen giver det korrekte resultat, men lad os nu se, hvordan det kan forbedres.

## <a name="improve-performance"></a>Gør ydeevnen bedre

Bemærk, at formlen gentager det udtryk, der beregner "samme periode sidste år". Denne formel er ineffektiv, da den kræver, at Power BI skal evaluere det samme udtryk to gange. Målingsdefinitionen kan gøres mere effektiv ved brug af en variabel.

Følgende målingsdefinition repræsenterer en forbedring. Det bruger et udtryk til at tildele resultatet "samme periode sidste år" til en variabel, med navnet **SalesPriorYear**. Variablen bruges derefter to gange i RETURN-udtrykket.

```dax
Sales YoY Growth % =
VAR SalesPriorYear =
    CALCULATE([Sales], PARALLELPERIOD('Date'[Date], -12, MONTH))
RETURN
    DIVIDE(([Sales] - SalesPriorYear), SalesPriorYear)
```

Målingen fortsætter med at give det korrekte resultat, og det gør den i ca. halvdelen af forespørgselstiden.

## <a name="improve-readability"></a>Gør læsbarheden bedre

I den tidligere målingsdefinition kan du se, hvordan valget af variabelnavn gør det enklere at forstå udtrykket RETURN. Udtrykket er kort og selvbeskrivende.

## <a name="simplify-debugging"></a>Gør fejlfinding mere enkel

Variabler kan også hjælpe dig med at foretage fejlfinding af en formel. Hvis du vil teste et udtryk, der er knyttet til en variabel, skal du midlertidigt omskrive RETURN-udtrykket for at sende variablen til output.

Følgende målingsdefinition returnerer kun variablen **SalesPriorYear**. Bemærk, hvordan den markerer det påtænkte RETURN-udtryk som kommentar. Denne teknik giver dig mulighed for nemt at gendanne det, når fejlfindingen er fuldført.

```dax
Sales YoY Growth % =
VAR SalesPriorYear =
    CALCULATE([Sales], PARALLELPERIOD('Date'[Date], -12, MONTH))
RETURN
    --DIVIDE(([Sales] - SalesPriorYear), SalesPriorYear)
    SalesPriorYear
```

## <a name="reduce-complexity"></a>Reducer kompleksiteten

I tidligere versioner af DAX var variabler endnu ikke understøttet. Komplekse udtryk, der introducerede nye filterkontekster, skulle bruge DAX-funktionerne [EARLIER](/dax/earlier-function-dax) eller [EARLIEST](/dax/earliest-function-dax) til at referere til ydre filterkontekster. Desværre synes dataudformere, at disse funktioner er svære at forstå og bruge.

Variabler evalueres altid uden for de filtre, som RETURN-udtrykket gælder for. Derfor får en variabel samme resultat som funktionen EARLIEST, når du bruger den i en ændret filterkontekst. Brugen af funktionen EARLIER eller EARLIEST kan derfor undgås. Det betyder, at du nu kan skrive formler, der er mindre komplekse og nemmere at forstå.

Du kan se, at den følgende beregnede kolonnedefinition er føjet til tabellen **Subcategory**. Den evaluerer en rangordning af hver produktunderkategori baseret på værdierne i kolonnen **Subkategory Sales**.

```dax
Subcategory Sales Rank =
COUNTROWS(
    FILTER(
        Subcategory,
        EARLIER(Subcategory[Subcategory Sales]) < Subcategory[Subcategory Sales]
    )
) + 1
```

Funktionen EARLIER bruges til at henvise til kolonneværdien **Subcategory Sales**_i den aktuelle rækkekontekst_.

Den beregnede kolonnedefinition kan forbedres, ved at der bruges en variabel i stedet for funktionen EARLIER. Variablen **CurrentSubcategorySales** gemmer kolonneværdien for **Subcategory Sales**_i den aktuelle rækkekontekst_, og RETURN-udtrykket bruger den i en ændret filterkontekst.

```dax
Subcategory Sales Rank =
VAR CurrentSubcategorySales = Subcategory[Subcategory Sales]
RETURN
    COUNTROWS(
        FILTER(
            Subcategory,
            CurrentSubcategorySales < Subcategory[Subcategory Sales]
        )
    ) + 1
```

## <a name="next-steps"></a>Næste trin

Du kan finde flere oplysninger om denne artikel i følgende ressourcer:

- [Henvisning til DAX (Data Analysis Expressions)](/dax/)
- DAX-artiklen [VAR](/dax/var-dax)
- Læringsforløb: [Brug DAX i Power BI Desktop](/learn/paths/dax-power-bi/)
- Har du spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
- Forslag? [Få ideer til at forbedre Power BI](https://ideas.powerbi.com)