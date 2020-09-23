---
title: Brug det forbedrede beregningsprogram med dataflows
description: Få mere at vide om, hvordan du bruger det forbedrede beregningsprogram i Power BI Premium med dataflows
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 06/01/2020
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: 7623be9f4eea3bd4d1a8c6fa7b4d1add3d41c783
ms.sourcegitcommit: 9350f994b7f18b0a52a2e9f8f8f8e472c342ea42
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 09/22/2020
ms.locfileid: "90861515"
---
# <a name="the-enhanced-compute-engine"></a>Det forbedrede beregningsprogram

Det forbedrede beregningsprogram i Power BI gør det muligt for Power BI Premium-abonnenter at bruge deres kapacitet til at optimere brugen af dataflows. Hvis du bruger det forbedrede beregningsprogram, får du følgende fordele:

* Reducerer betydeligt den opdateringstid, der er krævet i forbindelse med langvarige ETL-trin, i forhold til beregnede enheder, som f.eks. udførelse af *joinforbindelser*, *distinct*, *filtre* og *gruppér efter*
* Udfør DirectQuery-forespørgsler over enheder (i februar 2020)

I følgende afsnit beskrives det, hvordan du aktiverer det forbedrede beregningsprogram, og almindelige spørgsmål besvares.


## <a name="using-the-enhanced-compute-engine"></a>Brug af det forbedrede beregningsprogram

Det forbedrede beregningsprogram aktiveres fra siden **Kapacitetsindstillinger** i Power BI-tjenesten i afsnittet **Dataflows**. Det forbedrede beregningsprogram er som standard slået **Fra**. Hvis du vil slå det til, skal du skifte til **Til** som vist på følgende billede og gemme dine indstillinger. 

![Slå det forbedrede beregningsprogram til](media/service-dataflows-enhanced-compute-engine/enhanced-compute-engine-01.png)

> [!IMPORTANT]
> Det udvidede beregningsprogram fungerer kun for Power BI-kapaciteter på A3 og derover.

Når du har slået det forbedrede beregningsprogram til, kan du vende tilbage til dataflows og se en forbedring af ydeevnen i alle beregnede enheder, der udfører komplekse handlinger, f.eks. handlinger som *joinforbindelser* eller *gruppér efter* for dataflows, der er oprettet ud fra eksisterende sammenkædede enheder på samme kapacitet. 

Hvis du vil udnytte beregningsprogrammet optimalt, skal du opdele ETL-fasen i to separate dataflows på følgende måde:

* **Dataflow 1** – dette dataflow bør kun overføre det, der kræves af en datakilde, og placere det i dataflow 2.
* **Dataflow 2** – Udfør alle ETL-handlinger i dette andet dataflow, men sørg for, at du refererer til dataflow 1, som skal være på samme kapacitet. Sørg også for, at du udfører handlinger, der kan foldes (filtrere, gruppere efter, distinct, joinforbindelse), først før en anden handling for at sikre, at beregningsprogrammet anvendes.

## <a name="common-questions-and-answers"></a>Almindelige spørgsmål og svar

**Spørgsmål:** Jeg har aktiveret det forbedrede beregningsprogram, men mine opdateringer er langsommere. Hvorfor?

**Svar:** Hvis du aktiverer det forbedrede beregningsprogram, er der to mulige forklaringer, der kan føre til langsommere opdateringstider:

 - Når det forbedrede beregningsprogram er aktiveret, kræver det noget hukommelse for at fungere korrekt. Derfor reduceres den hukommelse, der er tilgængelig til at udføre en opdatering, og derfor øges sandsynligheden for, at opdateringerne sættes i kø, hvilket reducerer antallet af dataflows, der kan opdateres samtidig. Hvis du vil løse dette, skal du øge den hukommelse, der er tildelt til dataflows, når du aktiverer udvidet beregning, for at sikre, at den hukommelse, der er tilgængelig for samtidige dataflow-opdateringer, forbliver den samme.

 - En anden årsag til, at du oplever langsommere opdateringer er, at beregningsprogrammet kun fungerer oven på eksisterende enheder, hvis dit dataflow refererer til en datakilde, der ikke er et dataflow, og så oplever du ikke en forbedring. Der vil ikke være nogen forbedring af ydeevnen, da den indledende indlæsning fra en datakilde vil være langsommere i visse større datascenarier, da dataene skal overføres til det forbedrede beregningsprogram.  

**Spørgsmål:** Jeg kan ikke se, at det forbedrede beregningsprogram skifter indstilling. Hvorfor?

**Svar:** Det forbedrede beregningsprogram udgives i etaper til områder i hele verden. Vi forventer, at alle områder understøttes i slutningen af 2020.

**Spørgsmål:** Hvilke datatyper understøttes af beregningsprogrammet?

**Svar:** Det forbedrede beregningsprogram og dataflows understøtter i øjeblikket følgende datatyper. Hvis dit dataflow ikke bruger en af følgende datatyper, opstår der en fejl under opdateringen:

* Dato/klokkeslæt
* Decimaltal
* Tekst
* Heltal
* Dato/klokkeslæt/zone
* Sand/falsk
* Dato
* Klokkeslæt

## <a name="next-steps"></a>Næste trin

Denne artikel indeholdt oplysninger om brug af det forbedrede beregningsprogram til dataflows. Følgende artikler kan også være nyttige:

* [Selvbetjent dataforberedelse med dataflow](service-dataflows-overview.md)
* [Opret og brug dataflow i Power BI](service-dataflows-create-use.md)
* [Brug af beregnede objekter i Power BI Premium](service-dataflows-computed-entities-premium.md)
* [Udviklerressourcer til Power BI-dataflow](service-dataflows-developer-resources.md)

Du kan finde flere oplysninger om Power-forespørgsel og planlagt opdatering i disse artikler:
* [Oversigt over forespørgsler i Power BI Desktop](desktop-query-overview.md)
* [Konfiguration af planlagt opdatering](../connect-data/refresh-scheduled-refresh.md)

Du kan finde flere oplysninger om Common Data Model i denne oversigtsartikel:
* [Common Data Model – oversigt](/powerapps/common-data-model/overview)