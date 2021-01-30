---
title: Opret datotabeller i Power BI Desktop
description: Teknikker og vejledning til oprettelse af datotabeller i Power BI Desktop.
author: peter-myers
ms.author: kfollis
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 06/24/2020
ms.openlocfilehash: ede11b592084c83e6306f21b96e8fe1ecb38dd61
ms.sourcegitcommit: fb529c4532fbbdfde7ce28e2b4b35f990e8f21d9
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/30/2021
ms.locfileid: "99086941"
---
# <a name="create-date-tables-in-power-bi-desktop"></a>Opret datotabeller i Power BI Desktop

Denne artikel henvender sig til designere af datamodeller, der arbejder med Power BI Desktop. I artiklen beskrives god designpraksis i forbindelse med oprettelse af datotabeller i dine datamodeller.

Hvis du vil arbejde med DAX-[funktioner for tidsintelligens](/dax/time-intelligence-functions-dax) (Data Analysis Expressions), er der følgende krav til modellen: Du skal have mindst én _datotabel_ i din model. En datotabel er en tabel, der overholder følgende krav:

> [!div class="checklist"]
> - Den skal have en kolonne med datatypen **dato** (eller **dato/klokkeslæt**) – også kaldet en _datokolonne_.
> - Datokolonnen må kun indeholde entydige værdier.
> - Datokolonnen må ikke indeholde TOMME værdier.
> - Datokolonnen må ikke have nogen manglende datoer.
> - Datokolonnen skal strække sig over hele år. Et år er ikke nødvendigvis et kalenderår (januar-december).
> - Dato tabellen skal være [markeret som en datotabel](../transform-model/desktop-date-tables.md#setting-your-own-date-table).

Du kan bruge en af flere teknikker til at føje en datotabel til din model:

- Indstillingen Automatisk dato/klokkeslæt
- Power Query til oprettelse af forbindelse til en datodimensionstabel
- Power Query til oprettelse af en datotabel
- DAX til oprettelse af en datotabel
- DAX til kloning af en eksisterende datotabel

> [!TIP]
> En datotabel er muligvis den mest konsistente funktion, du kan føje til dine modeller. Derudover skal en datotabel i en organisation være defineret på en konsistent måde. Så uanset hvilken teknik du beslutter dig for at bruge, anbefaler vi, at du opretter en [Power BI Desktop-skabelon](../create-reports/desktop-templates.md), der omfatter en fuldt konfigureret datotabel. Del skabelonen med alle modeller i din organisation. Det betyder, at når nogen udvikler en ny model, kan de begynde med en datotabel, der er defineret på en konsistent måde.

## <a name="use-auto-datetime"></a>Brug Automatisk dato/klokkeslæt

Med indstillingen [Automatisk dato/klokkeslæt](../transform-model/desktop-auto-date-time.md) får du praktisk, hurtig og brugervenlig time intelligence. Rapportforfattere kan arbejde med time intelligence, når de filtrerer, grupperer og zoomer ind på detaljeniveauet gennem tidsperioder i kalendere.

Det anbefales, at du bevarer indstillingen Automatisk dato/klokkeslæt aktiveret, når du arbejder med tidsperioder i kalendere, og når du har forenklede modelkrav i forhold til tid. Det kan også være praktisk at bruge denne indstilling, når du opretter ad hoc-modeller eller udfører dataudforskning eller -profilering. Denne fremgangsmåde understøtter dog ikke et enkelt datotabel design, der kan overføre filtre til flere tabeller. Du kan finde flere oplysninger under [Vejledning til automatisk dato/klokkeslæt i Power BI Desktop](auto-date-time.md).

## <a name="connect-with-power-query"></a>Opret forbindelse til Power Query

Hvis din datakilde allerede har en datotabel, anbefaler vi, at du bruger den som kilden til din modeldatotabel. Det er normalt tilfældet, når du opretter forbindelse til et data warehouse, da det har en datodimensionstabel. På denne måde bruger din model en enkelt kilde til sandhed til datoerne i din organisation.

Hvis du udvikler en DirectQuery-model, og din datakilde ikke omfatter en datotabel, anbefaler vi på det kraftigste, at du føjer en datotabel til datakilden. Den skal opfylde alle modelleringskrav til en datotabel. Du kan derefter bruge Power Query til at oprette forbindelse til datotabellen. På denne måde kan dine modelberegninger udnytte DAX-funktionerne til tidsintelligens.

## <a name="generate-with-power-query"></a>Opret med Power Query

Du kan oprette en datotabel ved hjælp af Power Query. Du kan finde flere oplysninger i Chris Webbs blogindlæg [Generating A Date Dimension Table In Power Query](https://blog.crossjoin.co.uk/2013/11/19/generating-a-date-dimension-table-in-power-query/).

> [!TIP]
> Hvis du ikke har et data warehouse eller en anden konsistent definition af tiden i din organisation, kan du overveje at bruge Power Query til at publicere et [dataflow](../transform-model/dataflows/dataflows-introduction-self-service.md). Derefter kan alle udviklere af datamodeller oprette forbindelse til dataflowet for at føje datotabeller til deres modeller. Dataflowet bliver den eneste På denne måde bruger din model en enkelt kilde til sandhed til datoerne i din organisation.

Hvis du har brug for at oprette en datotabel, kan du overveje at gøre det med DAX. Det kan være nemmere. Derudover er det sandsynligt, at det vil være mere praktisk, da DAX omfatter indbygget intelligens, der forenkler oprettelse og administration af datotabeller.

## <a name="generate-with-dax"></a>Opret med DAX

Du kan oprette en datotabel i din model ved at oprette en beregnet tabel ved hjælp af DAX-funktionerne [CALENDAR](/dax/calendar-function-dax) eller [CALENDARAUTO](/dax/calendarauto-function-dax). Hver funktion returnerer en tabel med en enkelt kolonne med datoer. Du kan derefter udvide den beregnede tabel med beregnede kolonner for at understøtte kravene til filtrering og gruppering af datointervaller.

- Brug funktionen **CALENDAR**, når du vil definere et datointerval. Du overfører to værdier: startdatoen og slutdatoen. Disse værdier kan defineres af andre DAX-funktioner, f. eks. `MIN(Sales[OrderDate])` eller `MAX(Sales[OrderDate])`.
- Brug funktionen **CALENDARAUTO**, når datointervallet automatisk skal omfatte alle de datoer, der er gemt i modellen. Du kan overføre en enkelt valgfri parameter, som er årets slutmåned (hvis dit år er et kalenderår, der slutter i december, behøver du ikke at overføre en værdi). Det er en nyttig funktion, da den sikrer, at der returneres datoer for komplette år, hvilket er et krav til en markeret datotabel. Derudover behøver ikke at administrere forlængelsen af tabellen til fremtidige år: Når en dataopdatering er fuldført, udløser den genberegningen af tabellen. En genberegning udvider automatisk tabellens datointerval, når datoer for et nyt år indlæses i modellen.

## <a name="clone-with-dax"></a>Klon med DAX

Når modellen allerede har en datotabel, og du har brug for en ekstra datotabel, kan du nemt klone den eksisterende datotabel. Det er tilfældet, når datoen er en [dimension med forskellige roller](star-schema.md#role-playing-dimensions). Du kan klone en tabel ved at oprette en beregnet tabel. Det beregnede tabeludtryk er blot navnet på den eksisterende datotabel.

## <a name="next-steps"></a>Næste trin

Du kan finde flere oplysninger, der er relateret til denne artikel, i følgende ressourcer:

- [Automatisk dato/klokkeslæt i Power BI Desktop](../transform-model/desktop-auto-date-time.md)
- [Vejledning til automatisk dato/klokkeslæt i Power BI Desktop](auto-date-time.md)
- [Angiv og brug datotabeller i Power BI Desktop](../transform-model/desktop-date-tables.md)
- [Selvbetjent dataforberedelse i Power BI](../transform-model/dataflows/dataflows-introduction-self-service.md)
- [Funktionen CALENDAR (DAX)](/dax/calendar-function-dax)
- [Funktionen CALENDARAUTO (DAX)](/dax/calendarauto-function-dax)
- Har du spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
- Forslag? [Få ideer til at forbedre Power BI](https://ideas.powerbi.com/)