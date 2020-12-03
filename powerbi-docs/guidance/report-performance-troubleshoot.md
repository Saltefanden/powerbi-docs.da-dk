---
title: Foretag fejlfinding af en rapports ydeevne i Power BI
description: Vejledning til fejlfinding for at diagnosticere langsom rapportydeevne i Power BI.
author: peter-myers
ms.author: v-pemyer
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: troubleshooting
ms.date: 04/15/2020
ms.openlocfilehash: 97af45ea90db1f0ccd2fdab7eba67ec91e580983
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96417859"
---
# <a name="troubleshoot-report-performance-in-power-bi"></a>Foretag fejlfinding af en rapports ydeevne i Power BI

Denne artikel indeholder en vejledning, der gør det muligt for udviklere og administratorer at foretage fejlfinding af langsom rapportydeevne. Det gælder både for Power BI-rapporter og sideinddelte Power BI-rapporter.

Langsomme rapporter kan identificeres af rapportbrugere, der oplever, at det tager lang tid at indlæse eller opdatere rapporterne, når der interageres med udsnit eller andre funktioner. Når rapporter hostes på en Premium-kapacitet, kan langsomme rapporter også identificeres ved at overvåge [Power BI Premium Metrics-programmet](../admin/service-admin-premium-monitor-capacity.md). Dette program hjælper dig med at overvåge tilstanden af og kapaciteten i dit Power BI Premium-abonnement.

## <a name="follow-flowchart-steps"></a>Følg trinnene i rutediagrammet

Brug følgende rutediagram til at forstå årsagen til langsom ydeevne og for at fastslå, hvilken handling der skal udføres.

:::image type="content" source="media/report-performance-troubleshoot/flowchart.png" alt-text="Billede af rutediagrammet, som er fuldt beskrevet i teksten i artiklen." border="true":::

Der er seks afslutninger i rutediagrammet, som hver beskriver en handling, der kan udføres:

|Afslutning|Handling(er)|
|---------|---------|
|![Afslutning 1 i rutediagrammet.](media/common/icon-01-red-30x30.png)|Administrer kapacitet<br />Skaler kapacitet |
|![Afslutning 2 i rutediagrammet.](media/common/icon-02-red-30x30.png)|Undersøg aktivitet for kapaciteten under almindelig rapportbrug|
|![Afslutning 3 i rutediagrammet.](media/common/icon-03-red-30x30.png)|Ret arkitektur<br />Overvej Azure Analysis Services<br />Kontrollér gatewayen i det lokale miljø|
|![Afslutning 4 i rutediagrammet.](media/common/icon-04-red-30x30.png)|Overvej Azure Analysis Services<br />Overvej Power BI Premium|
|![Afslutning 5 i rutediagrammet.](media/common/icon-05-red-30x30.png)|Brug Effektivitetsanalyse i Power BI Desktop<br />Optimer rapporten, modellen eller DAX|
|![Afslutning 6 i rutediagrammet.](media/common/icon-06-red-30x30.png)|Åbn en supportanmodning|

## <a name="take-action"></a>Udfør handlingen

Det første, du skal finde ud af, er, om den langsomme rapport er hostet på en Premium-kapacitet.

### <a name="premium-capacity"></a>Premium-kapacitet

Når rapporten hostes på en Premium-kapacitet, skal du bruge **Power BI Premium Metrics-programmet** til at fastslå, om kapaciteten til hosting af rapporten ofte overstiger kapacitetsressourcerne. Det er tilfældet for CPU'en, når den ofte overstiger 80 %. Hvis det er hukommelse, sker det, når den [aktive hukommelsesmetrik](../admin/service-premium-metrics-app.md#the-active-memory-metric) overstiger 50. Når ressourcerne er under pres, kan det være tid til at [administrere eller skalere kapaciteten](../admin/service-admin-premium-manage.md) (afslutning 1 i rutediagrammet). Når der er tilstrækkelige ressourcer, kan du undersøge aktivitet for kapaciteten under typisk rapportbrug (afslutning 2 i rutediagrammet).

### <a name="shared-capacity"></a>Delt kapacitet

Når rapporten hostes på en delt kapacitet, er det ikke muligt at overvåge kapacitetstilstanden. Du bliver nødt til at bruge en anden tilgang.

Først skal du fastslå, om den langsomme ydeevne forekommer på bestemte tidspunkter på dagen eller i måneden. Hvis det er tilfældet – og mange brugere åbner rapporten på disse tidspunkter – skal du overveje to muligheder:

- Øg gennemløbet af forespørgslen ved at migrere datasættet til [Azure Analysis Services](/azure/analysis-services/analysis-services-overview) eller en Premium-kapacitet (afslutning 4 i rutediagrammet).
- Brug [Effektivitetsanalyse](../create-reports/desktop-performance-analyzer.md) i Power BI Desktop til at finde ud af, hvordan hvert element i din rapport, f.eks. visualiseringer og DAX-formler, opfører sig. Det er især nyttigt at fastslå, om det er forespørgslen eller gengivelsen af visualiseringen, der bidrager til ydeevneproblemer (afslutning 5 i rutediagrammet).

Hvis du fastslår, at der ikke er noget tidsmønster, skal du overveje, om den langsomme ydeevne er isoleret til en bestemt geografi eller et bestemt område. Hvis det er tilfældet, er det sandsynligt, at datakilden er ekstern, og at der er en langsom netværkskommunikation. I dette tilfælde skal du overveje følgende:

- Ret arkitekturen ved hjælp af [Azure Analysis Services](/azure/analysis-services/analysis-services-overview) (afslutning 3 i rutediagrammet).
- Optimer [ydeevnen af datagatewayen i det lokale miljø](/data-integration/gateway/service-gateway-performance) (afslutning 3 i rutediagrammet).

Hvis du fastslår, at der ikke er noget tidsmønster _og_ den langsomme ydeevne forekommer i alle områder, skal du undersøge, om der forekommer langsom ydeevne på bestemte enheder, klienter eller webbrowsere. Hvis det ikke er tilfældet, kan du bruge [Effektivitetsanalyse](../create-reports/desktop-performance-analyzer.md) i Power BI Desktop, som beskrevet tidligere, til at optimere rapporten eller modellen (afslutning 5 i rutediagrammet).

Når du fastslår, at det er bestemte enheder, klienter eller webbrowsere, der bidrager til den langsomme ydeevne, anbefaler vi, at du opretter en supportanmodning via [Power BI-supportsiden](https://powerbi.microsoft.com/support/) (afslutning 6 i rutediagrammet).

## <a name="next-steps"></a>Næste trin

Du kan finde flere oplysninger om denne artikel i følgende ressourcer:

- [Power BI-vejledning](index.yml)
- [Overvågning af rapportens ydeevne](monitor-report-performance.md)
- [Effektivitetsanalyse](../create-reports/desktop-performance-analyzer.md)
- Whitepaper: [Planlægning af en Power BI Enterprise-udrulning](https://go.microsoft.com/fwlink/?linkid=2057861)
- Har du spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
- Forslag? [Få ideer til at forbedre Power BI](https://ideas.powerbi.com/)
