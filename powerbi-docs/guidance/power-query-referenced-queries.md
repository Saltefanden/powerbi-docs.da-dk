---
title: Henvisning til Power Query-forespørgsler
description: Vejledning i reference til Power Query-forespørgsler.
author: peter-myers
ms.author: kfollis
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 11/30/2019
ms.openlocfilehash: 59ba1454b1409e13587d1c1bae75e06025fa72ea
ms.sourcegitcommit: fb529c4532fbbdfde7ce28e2b4b35f990e8f21d9
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/30/2021
ms.locfileid: "99087401"
---
# <a name="referencing-power-query-queries"></a>Henvisning til Power Query-forespørgsler

Denne artikel henvender sig til designere af datamodeller, der arbejder med Power BI Desktop. Den indeholder en vejledning i, hvordan Power Query-forespørgsler, der refererer til andre forespørgsler, defineres.

Det betyder helt konkret: _Når en forespørgsel referer til en anden forespørgsel, er det som om, at trinnene i den anden forespørgsel kombineres med og kører før trinnene i den første forespørgsel._

Tænk på flere forespørgsler: **Forespørgsel1** henter data fra en webtjeneste, og dens indlæsning er deaktiveret. **Forespørgsel2**, **Forespørgsel3** og **Forespørgsel4** refererer alle til **Forespørgsel1**, og deres output indlæses i datamodellen.

![Diagram, der viser visningen Forespørgselsafhængigheder med forespørgsler, der er beskrevet i forrige afsnit.](media/power-query-referenced-queries/query-dependencies-web-service.png)

Når datamodellen opdateres, antages det ofte, at Power Query henter resultatet for **Forespørgsel1**, og at det genbruges i refererede forespørgsler. Denne antagelse er forkert. Faktisk udfører Power Query **Forespørgsel2**, **Forespørgsel3** og **Forespørgsel4** separat.

Du kan tænke på det, som at **Forespørgsel2** har trinnene fra **Forespørgsel1** integreret. Det er også tilfældet for **Forespørgsel3** og **Forespørgsel4**. I følgende diagram vises et tydeligere billede af, hvordan forespørgslerne udføres.

![Diagram, der viser en modificeret version af visningen Forespørgselsafhængigheder, der viser Forespørgsel 2, Forespørgsel 3 og Forespørgsel 4.](media/power-query-referenced-queries/query-dependencies-web-service-concept.png)

**Forespørgsel1** udføres tre gange. De enkelte udførelser kan resultere i langsom opdatering af data og påvirke datakilden negativt.

Brugen af funktionen [Table.Buffer](/powerquery-m/table-buffer) i **Forespørgsel1** udelukker ikke yderligere datahentning. Denne funktion gemmer en tabel i buffer i hukommelsen. Og tabellen, der er gemt i buffer, kan kun bruges i den samme udførelse af forespørgslen. Så hvis **Forespørgsel1** i eksemplet gemmes i buffer, når **Forespørgsel2** udføres, så kan de data, der er gemt i buffer, ikke bruges, når **Forespørgsel3** og **Forespørgsel4** udføres. Disse gemmer selv dataene i buffer to gange mere. (Dette resultat kan faktisk forværre den negative ydeevne, da tabellen gemmes i buffer af hver refererende forespørgsel).

> [!NOTE]
> Arkitekturen for cachelagring af Power Query er kompleks, og det er ikke denne artikels fokus. Power Query kan cachelagre data, der er hentet fra en datakilde. Men når den udfører en forespørgsel, henter den måske dataene fra datakilden mere end én gang.

## <a name="recommendations"></a>Anbefalinger

Generelt anbefales det, at du refererer til forespørgsler for at undgå duplikering af logik på tværs af dine forespørgsler. Men som beskrevet i denne artikel kan denne designmetode bidrage til langsomme dataopdateringer og overbelastede datakilder.

Det anbefales, at du i stedet opretter et [dataflow](../transform-model/dataflows/dataflows-introduction-self-service.md). Brug af et dataflow kan forbedre opdateringstiden for data og reducere indvirkningen på dine datakilder.

Du kan designe dataflow for at sammenfatte kildedataene og transformationerne. Da dataflow er et permanent lager med data i Power BI-tjenesten, sker datahentningen hurtigt. Så selv når reference til forespørgsler resulterer i flere anmodninger til dataflowet, kan opdateringstiden for data forbedres.

Hvis **Forespørgsel1** i eksemplet redesignes som en dataflowenhed, kan **Forespørgsel2**, **Forespørgsel3** og **Forespørgsel4** bruge den som en datakilde. Med dette design evalueres den enhed, der hentes af **Forespørgsel1**, kun én gang.

## <a name="next-steps"></a>Næste trin

Du kan finde flere oplysninger, der er relateret til denne artikel, i følgende ressourcer:

- [Selvbetjent dataforberedelse i Power BI](../transform-model/dataflows/dataflows-introduction-self-service.md)
- [Oprettelse og brug af dataflow i Power BI](../transform-model/dataflows/dataflows-create.md)
- Har du spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
- Forslag? [Få ideer til at forbedre Power BI](https://ideas.powerbi.com/)