---
title: 'DAX: Undgå at konvertere BLANKs til værdier'
description: Vejledning angående konvertering af BLANKs til værdier.
author: peter-myers
ms.author: kfollis
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 11/24/2019
ms.openlocfilehash: c7090b690f4b941068db91c4b47dad30373d0f16
ms.sourcegitcommit: fb529c4532fbbdfde7ce28e2b4b35f990e8f21d9
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/30/2021
ms.locfileid: "99088551"
---
# <a name="dax-avoid-converting-blanks-to-values"></a>DAX: Undgå at konvertere BLANKs til værdier

Som dataudformer kan du opleve situationer, hvor der ikke kan returneres en meningsfyldt værdi, når du skriver målingsudtryk. I disse tilfælde kan du blive fristet til at returnere en værdi – f. eks. nul – i stedet for. Det anbefales, at du tænker nøje over, om dette design er effektivt og praktisk.

Overvej følgende målingsdefinition, der udtrykkeligt konverterer BLANK-resultater til nul.

```dax
Sales (No Blank) =
IF(
    ISBLANK([Sales]),
    0,
    [Sales]
)
```

Overvej en anden målingsdefinition, der også konverterer BLANK-resultater til nul.

```dax
Profit Margin =
DIVIDE([Profit], [Sales], 0)
```

Funktionen [DIVIDE](/dax/divide-function-dax) dividerer målingen **Profit** med målingen **Sales**. Hvis resultatet skal være nul eller BLANK, returneres det tredje argument – det alternative resultat (som er valgfrit). I dette eksempel er det garanteret, at målingen returnerer en værdi, fordi nul overføres som det alternative resultat.

Disse målingsdesign er ineffektive og fører til dårlige rapportdesign.

Når de føjes til et rapportvisual, forsøger Power BI at hente alle grupperinger i filterkonteksten. Evalueringen og hentningen af store forespørgselsresultater medfører ofte en langsom gengivelse af rapporter. Hver eksempelmåling omdanner effektivt en sparse-beregning til en dense-beregning, hvilket tvinger Power BI til at bruge mere hukommelse, end det er nødvendigt.

Desuden virker for mange grupperinger ofte også overvældende på dine rapportbrugere.

Lad os se, hvad der sker, når målingen **Profit Margin** føjes til et tabelvisual med gruppering efter kunde.

![Skærmbillede af Power BI desktop, der viser et tabelvisual af data med én række pr. kunde. Salgsværdier er BLANK, og værdier i Profit Margin er nul %. ](media/dax-avoid-converting-blank/table-visual-poor.png)

I tabelvisual'et vises der et overvældende antal rækker. (Der er reelt 18.484 kunder i modellen, og der gøres forsøg på at vise dem alle i tabellen.) Bemærk, at kunderne i visningen ikke har opnået noget salg. Men de vises alligevel, fordi målingen **Profit Margin** altid returnerer en værdi.

> [!NOTE]
> Når der er for mange datapunkter at vise i et visual, bruges der muligvis strategier til datareduktion i Power BI for at fjerne eller opsummere store forespørgselsresultater. Du kan finde flere oplysninger i [Datapunktgrænser og -strategier efter visualtype](../visuals/power-bi-data-points.md).

Lad os se, hvad der sker, når definitionen af målingen **Profit Margin** forbedres. Der returneres nu kun en værdi, når målingen **Sales** ikke er BLANK (eller nul).

```dax
Profit Margin =
DIVIDE([Profit], [Sales])
```

I tabelvisual'et vises der nu kun de kunder, der har haft salg inden for den aktuelle filterkontekst. Den forbedrede måling resulterer i en mere effektiv og praktisk oplevelse for dine rapportbrugere.

![Skærmbillede af Power BI Desktop med tabelvisual af data, der har filtreret indhold.](media/dax-avoid-converting-blank/table-visual-good.png)

> [!TIP]
> Når det er nødvendigt, kan du konfigurere visualiseringen til at vise alle grupper (der returnerer værdier eller er BLANK) i filterkonteksten ved at aktivere indstillingen [Vis elementer uden data](../create-reports/desktop-show-items-no-data.md).

## <a name="recommendation"></a>Anbefaling

Det anbefales, at dine målinger returnerer BLANK, når der ikke kan returneres en meningsfyldt værdi.

Denne designmetode er effektiv og giver Power BI mulighed for at gengive rapporter hurtigere. Returnering af BLANK er desuden bedre, fordi rapportvisualiseringer som standard fjerner grupperinger, når opsummeringer er BLANK.

## <a name="next-steps"></a>Næste trin

Du kan finde flere oplysninger om denne artikel i følgende ressourcer:

- [Henvisning til DAX (Data Analysis Expressions)](/dax/)
- Læringsforløb: [Brug DAX i Power BI Desktop](/learn/paths/dax-power-bi/)
- Har du spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
- Forslag? [Få ideer til at forbedre Power BI](https://ideas.powerbi.com)