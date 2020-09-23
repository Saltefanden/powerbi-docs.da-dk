---
title: 'DAX: Brug COUNTROWS i stedet for COUNT'
description: Vejledning til, hvornår du skal bruge COUNTROWS-fejlfunktioner.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/23/2019
ms.author: v-pemyer
ms.openlocfilehash: 1a49531c9c7e525371c3c92b7bf116bfa7e99fd3
ms.sourcegitcommit: cff93e604e2c5f24e0f03d6dbdcd10c2332aa487
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 09/22/2020
ms.locfileid: "90965534"
---
# <a name="dax-use-countrows-instead-of-count"></a>DAX: Brug COUNTROWS i stedet for COUNT

Dataudformere har nogle gange brug for at skrive et DAX-udtryk, der tæller tabelrækker. Tabellen kan være en modeltabel eller et udtryk, der returnerer en tabel.

Du kan få opfyldt dit krav på to måder. Du kan bruge funktionen [COUNT](/dax/count-function-dax) til at tælle kolonneværdier, eller du kan bruge funktionen [COUNTROWS](/dax/countrows-function-dax) til at tælle tabelrækker. Begge funktioner opnår samme resultat, forudsat, at den kolonne, hvor optællingen finder sted, ikke indeholder tomme værdier.

Der vises et eksempel i følgende målingsdefinition. Antallet af kolonneværdier for **Ordredato** beregnes.

```dax
Sales Orders =
COUNT(Sales[OrderDate])
```

Forudsat at kornetheden for tabellen **Sales** er én række pr. salgsordre, og at kolonnen **OrderDate** ikke indeholder BLANKs, returnerer målingen et korrekt resultat.

Følgende målingsdefinition er dog en bedre løsning.

```dax
Sales Orders =
COUNTROWS(Sales)
```

Der er tre årsager til, at den anden målingsdefinition er bedre:

- Den er mere effektiv og derfor nemmere at udføre.
- Den medtager ikke BLANKs i nogen af tabellens kolonner.
- Hensigten med formlen er tydeligere, hvilket vil sige, at den næsten er selvbeskrivende.

## <a name="recommendation"></a>Anbefaling

Når du vil tælle tabelrækker, anbefales det, at du altid bruger funktionen COUNTROWS.

## <a name="next-steps"></a>Næste trin

Du kan finde flere oplysninger om denne artikel i følgende ressourcer:

- [Henvisning til DAX (Data Analysis Expressions)](/dax/)
- Læringsforløb: [Brug DAX i Power BI Desktop](/learn/paths/dax-power-bi/)
- Har du spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
- Forslag? [Få ideer til at forbedre Power BI](https://ideas.powerbi.com)