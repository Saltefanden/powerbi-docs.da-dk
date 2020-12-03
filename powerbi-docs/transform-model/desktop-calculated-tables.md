---
title: Brug af beregnede tabeller i Power BI Desktop
description: Beregnede tabeller i Power BI Desktop
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-transform-model
ms.topic: how-to
ms.date: 05/06/2020
LocalizationGroup: Model your data
ms.openlocfilehash: de919d5dc72ec4c9f1939d844a1cd287728f1ac8
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96415904"
---
# <a name="create-calculated-tables-in-power-bi-desktop"></a>Opret beregnede tabeller i Power BI Desktop
I de fleste tilfælde opretter du tabeller ved at importere data til din model fra en ekstern datakilde. Men med *beregnede tabeller* kan du tilføje nye tabeller, der er baseret på data, du allerede har indlæst i modellen. I stedet for at forespørge efter og indlæse værdier i din nye tabels kolonner fra en datakilde kan du oprette en [DAX-formel (Data Analysis Expressions)](/dax/index), der definerer værdierne i tabellen.

DAX er et formelsprog, der bruges til at arbejde med relationsdata, som i Power BI Desktop. DAX inkluderer et bibliotek med mere end 200 funktioner, operatorer og konstruktioner, hvilket giver stor fleksibilitet, når du opretter formler til beregning af resultater for stort set alle dataanalyser. Beregnede tabeller er bedst til mellemliggende beregninger og data, der skal gemmes som en del af modellen, i stedet for løbende beregninger eller som forespørgselsresultater. Det kan f.eks. være, at du vil *forene* eller *sammenføje* to eksisterende tabeller på tværs.

Beregnede tabeller kan have relationer til andre tabeller på samme måde som andre Power BI Desktop-tabeller. Beregnede tabelkolonner indeholder datatyper og formatering og kan tilhøre en datakategori. Du kan navngive kolonnerne, som du vil, og føje dem til rapportvisualiseringer på samme måde som alle andre felter. Beregnede tabeller genberegnes, hvis nogen af de tabeller, de henter data fra, opdateres, medmindre tabellen bruger data fra en tabel, der bruger DirectQuery. Hvis det er tilfældet, vil tabellen kun afspejle ændringerne, når datasættet er blevet opdateret. Hvis en tabel skal bruge DirectQuery, er det bedst også at have den beregnede tabel i DirectQuery.

## <a name="create-a-calculated-table"></a>Opret en beregnet tabel

Du opretter beregnede tabeller ved hjælp af funktionen **Ny tabel** i Rapportvisning eller Datavisning i Power BI Desktop.

Forestil dig f.eks., at du er personalechef, der har en tabel med **Northwest Employees** og en anden tabel med **Southwest Employees**. Du vil kombinere de to tabeller i en enkelt tabel, der kaldes **Western Region Employees**.

**Northwest Employees**

 ![Skærmbillede af Power B I Desktop, der viser tabeldata for Northwest Employees.](media/desktop-calculated-tables/calctables_nwempl.png)

**Southwest Employees**

 ![Skærmbillede af Power B I Desktop, der viser tabeldata for Northwest Employees.](media/desktop-calculated-tables/calctables_swempl.png)

I Rapportvisning eller Datavisning i Power BI Desktop skal du i gruppen **Beregninger** under fanen **Udformning** vælge **Ny tabel**. Det er lidt nemmere at gøre i Datavisning, da du straks kan se den nye beregnede tabel.

 ![Ny tabel i Datavisning](media/desktop-calculated-tables/calctables_formulabarempty.png)

Indtast følgende formel på formellinjen:

```dax
Western Region Employees = UNION('Northwest Employees', 'Southwest Employees')
```

Der oprettes en ny tabel med navnet **Western Region Employees**, og den vises på samme måde som en hvilken som helst anden tabel på ruden **Felter**. Du kan oprette relationer til andre tabeller, tilføje målinger og beregnede kolonner samt føje felterne til rapporter på samme måde som en hvilken som helst anden tabel.

 ![Ny beregnet tabel](media/desktop-calculated-tables/calctables_westregionempl.png)

 ![Ny tabel i ruden Felter](media/desktop-calculated-tables/calctables_fieldlist.png)

## <a name="functions-for-calculated-tables"></a>Funktioner i forbindelse med beregnede tabeller

Du kan definere en beregnet tabel af et DAX-udtryk, der returnerer en tabel, herunder en enkelt reference til en anden tabel. Eksempel:

```dax
New Western Region Employees = 'Western Region Employees'
```

I denne artikel får du kun en hurtig introduktion til beregnede tabeller. Du kan bruge beregnede tabeller med DAX for at løse mange analyseproblemer. Her er nogle af de mest almindelige DAX-tabelfunktioner, som du kan bruge:

* DISTINCT
* VÆRDIER
* CROSSJOIN
* UNION
* NATURALINNERJOIN
* NATURALLEFTOUTERJOIN
* INTERSECT
* CALENDAR
* CALENDARAUTO

Du kan se disse og andre DAX-funktioner, der returnerer en tabel, under [Reference til DAX-funktioner](/dax/dax-function-reference).

