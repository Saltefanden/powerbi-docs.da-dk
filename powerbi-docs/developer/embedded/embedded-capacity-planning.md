---
title: Kapacitetsplanlægning af integreret analyse i Power BI
description: Kapacitetsplanlægning af integreret analyse i Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 03/03/2020
ms.openlocfilehash: b172b48517ccc8c55821fa8e8217d5e2df398b2d
ms.sourcegitcommit: bbf7e9341a4e1cc96c969e24318c8605440282a5
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/11/2020
ms.locfileid: "97098346"
---
# <a name="capacity-planning-in-power-bi-embedded-analytics"></a>Kapacitetsplanlægning af integreret analyse i Power BI

Det kan være kompliceret at beregne, hvilken type kapacitet der kræves for en udrulning af integreret analyse i Power BI. Det skyldes, at denne beregning er baseret på flere parametre, hvoraf nogle af dem er vanskelige at forudsige.

Nogle af de ting, du skal tage højde for, når du planlægger din kapacitet, er:

* De datamodeller, du bruger.
* Antallet og kompleksiteten af de påkrævede forespørgsler.
* Timefordelingen af forbruget af dit program.
* Dataopdateringshastigheder.
* Yderligere forbrugsmønstre, der er vanskelige at forudsige.

Denne artikel har til formål at lette kapacitetsplanlægningen i forbindelse med integreret analyse i Power BI ved at introducere [værktøj til evaluering af arbejdsbelastning for kapaciteter i Power BI](https://github.com/microsoft/PowerBI-Tools-For-Capacities/tree/master/LoadTestingPowerShellTool/), der er udviklet til automatisering af belastningstest for kapaciteter til integreret analyse i Power BI (*A-*, *EM-* eller *P*-SKU'er).

## <a name="planning-tool"></a>Planlægningsværktøj

 [Værktøjet til evaluering af arbejdsbelastning for kapaciteter i Power BI](https://github.com/microsoft/PowerBI-Tools-For-Capacities/tree/master/LoadTestingPowerShellTool/) kan hjælpe dig med at forstå, hvor meget brugerbelastning din kapacitet kan håndtere. Værktøjet gør brug af PowerShell til at oprette automatiserede belastningstest i forhold til dine kapaciteter, og du kan vælge, hvilke rapporter der skal testes, og hvor mange samtidige brugere der skal simuleres.

Værktøjet opretter belastning på en kapacitet ved løbende at gengive hver rapport med nye filterværdier (for at forhindre en realistisk god ydeevne, der skyldes cachelagring af rapporten), indtil det token, der kræves for at godkende værktøjet i forhold til tjenesten, udløber.

### <a name="using-the-planning-tool"></a>Brug af planlægningsværktøjet

Når du kører værktøjet, skal du være opmærksom på den eksisterende belastning af dine kapaciteter og sikre, at du ikke kører belastningstest på spidsbelastningstidspunkter.

Her er nogle eksempler på, hvordan du kan bruge planlægningsværktøjet.

* Kapacitetsadministratorer kan få en bedre forståelse af, hvor mange brugere deres kapacitet kan håndtere i et bestemt tidsrum.
* Rapportudviklere kan få en forståelse af brugerbelastningseffekten, som måles med Power BI Desktops [Ydeevneanalyse](../../create-reports/desktop-performance-analyzer.md).
* Du kan se, at gengivelser sker i realtid i din browser.
* Du kan ved at bruge SQL Server Profiler [oprette forbindelse til XMLA-slutpunkterne](https://powerbi.microsoft.com/blog/power-bi-open-platform-connectivity-with-xmla-endpoints-public-preview/) for de kapaciteter, der måles, for at få vist de forespørgsler, der udføres.
* Belastningstesteffekterne er synlige på siden med datasæt for Premium Capacity Metrics-appen. Kapacitetsadministratorer kan bruge dette værktøj til at generere belastning og se, hvordan den pågældende belastning vises.

### <a name="reviewing-the-test-results"></a>Gennemgang af testresultaterne

Hvis du vil se virkningen af belastningstesten i appen Metrics, når testene er blevet kørt, skal du følge vejledningen nedenfor. Du kan forvente en forsinkelse på op til 15 minutter, fra det tidspunkt hvor testen starter med at generere belastning, indtil indlæsningen er synlig i målepunkterne.

1. Udvid fanen **Datasæt** på landingssiden i [Metrics-appen](../../admin/service-admin-premium-monitor-capacity.md).
2. Start en opdatering efter behov ved at klikke på **Opdater nu**. Administratorer skal.

    ![Power BI Premium-kapacitetsmålinger](media/embedded-capacity-planning/embedded-capacity-planning.png)

## <a name="power-bi-capacity-tools-github-repository"></a>GitHub-lager til Power BI-kapacitetsværktøjer

[GitHub-lageret til Power BI-kapacitetsværktøjer](https://github.com/microsoft/PowerBI-Tools-For-Capacities) blev oprettet til at hoste kapacitetsplanlægningsværktøjet og andre fremtidige værktøjer og hjælpeprogrammer.

Lageret har åben kildekode, og brugerne opfordres til at bidrage og tilføje yderligere værktøjer, der er relateret til Power BI Premium- og Embedded-kapaciteter, og forbedre de eksisterende.

## <a name="next-steps"></a>Næste trin

> [!div class="nextstepaction"]
>[Kapacitet og SKU'er i integreret analyse i Power BI](embedded-capacity.md)

> [!div class="nextstepaction"]
>[Bedste praksis for ydeevnen i Power BI Embedded](embedded-performance-best-practices.md)