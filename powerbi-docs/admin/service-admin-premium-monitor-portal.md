---
title: Overvåg Power BI Premium-kapaciteter ved hjælp af administrationsportalen
description: Brug Power BI-administrationsportalen til at overvåge dine Premium-kapaciteter.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-premium
ms.topic: how-to
ms.date: 05/11/2020
LocalizationGroup: Premium
ms.openlocfilehash: 3948cca3a7e274c22ac1ea5cc80773edd0d5e451
ms.sourcegitcommit: 51b965954377884bef7af16ef3031bf10323845f
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 09/30/2020
ms.locfileid: "91599790"
---
# <a name="monitor-capacities-in-the-admin-portal"></a>Overvåg kapaciteter på administrationsportalen

Fanen **Tilstand** i området **Kapacitetsindstillinger** i administrationsportalen indeholder en målepunktsoversigt over din kapacitet og de aktiverede arbejdsbelastninger.  

![Fanen Kapacitetstilstand på portalen](media/service-admin-premium-monitor-portal/admin-portal-health.png)

Hvis du har brug for mere omfattende målepunkter, skal du bruge appen [Power BI Premium-kapacitetsmålinger](service-admin-premium-monitor-capacity.md). Appen indeholder detailudledning og filtrering og de mest detaljerede målepunkter til næsten alle aspekter, der påvirker kapacitetsydeevnen. Du finder flere oplysninger under [Overvåg Premium-kapaciteter vha. appen](service-admin-premium-monitor-capacity.md).

> [!IMPORTANT]
> Hvis der er et højt forbrug af ressourcer i din Power BI Premium-kapacitet, hvilket medfører problemer med ydeevne eller pålidelighed, kan du modtage notifikationer via mail for at identificere og løse problemet. Dette kan være en strømlinet metode til fejlfinding af overbelastede kapaciteter. Se [notifikationer om kapacitet og pålidelighed](service-interruption-notifications.md#capacity-and-reliability-notifications) for at få flere oplysninger.


## <a name="system-metrics"></a>Systemmålepunkter

På det højeste niveau under fanen **Tilstand** giver CPU-forbrug og hukommelsesforbrug et hurtigt overblik over de vigtigste målepunkter for kapaciteten. Disse målepunkter er akkumulerede, inklusive alle aktiverede arbejdsbelastninger for kapaciteten.

| **Målepunkt** | **Beskrivelse** |
| --- | --- |
| CPU-UDNYTTELSE | Gennemsnitlig CPU-udnyttelse som en procentdel af den samlede tilgængelige CPU. |
| HUKOMMELSESFORBRUG | Gennemsnitligt hukommelsesforbrug i gigabyte (GB).|

## <a name="workload-metrics"></a>Arbejdsbelastningens målepunkter

For hver arbejdsbelastning, der er aktiveret for kapaciteten. CPU-forbrug og hukommelsesforbrug vises.

| **Målepunkt** | **Beskrivelse** |
| --- | --- |
| CPU-UDNYTTELSE | Gennemsnitlig CPU-udnyttelse som en procentdel af den samlede tilgængelige CPU. |
| HUKOMMELSESFORBRUG | Gennemsnitligt hukommelsesforbrug i gigabyte (GB).|

### <a name="detailed-workload-metrics"></a>Detaljerede målepunkter for arbejdsbelastning

Hver arbejdsbelastning har flere målepunkter. Den type målepunkter der vises, afhænger af arbejdsbelastningen. Hvis du vil se detaljerede målepunkter for en arbejdsbelastning, skal du klikke på pilen (ned) til udvidelse.

![Udvidet arbejdsbelastningstilstand](media/service-admin-premium-monitor-portal/admin-portal-health-expand.png)

#### <a name="dataflows"></a>Dataflow

##### <a name="dataflow-operations"></a>Dataflow-handlinger

| **Målepunkt** | **Beskrivelse** |
| --- | --- |
| Antal i alt | Det samlede antal opdateringer for hvert dataflow. |
| Antal succeser | Det samlede antal gennemførte opdateringer for hvert dataflow.|
| Gennemsnitlig varighed (minutter) | Den gennemsnitlige varighed af opdateringen af dataflowet i minutter |
| Maksimal varighed (minutter) | Varigheden af den længstvarende opdatering af dataflowet i minutter. |
| Gennemsnitlig ventetid (minutter) | Den gennemsnitlige mellemliggende tid mellem det planlagte tidspunkt og starttidspunktet for en opdatering af dataflowet i minutter. |
| Maks. ventetid (minutter) | Den maksimale ventetid for dataflowet i minutter.  |

#### <a name="datasets"></a>Datasæt

##### <a name="refresh"></a>Opdater

| **Målepunkt** | **Beskrivelse** |
| --- | --- |
| Antal i alt | Det samlede antal opdateringer for hvert datasæt. |
| Antal succeser | Det samlede antal vellykkede opdateringer for hvert datasæt. |
| Antal fejl | Det samlede antal mislykkede opdateringer for hvert datasæt. |
| Succesrate  | Det samlede antal vellykkede opdateringer divideret med det samlede antal opdateringer, der skal måles. pålidelighed. |
| Gennemsnitlig varighed (minutter) | Den gennemsnitlige varighed af opdateringen af datasættet i minutter.  |
| Maksimal varighed (minutter) | Varigheden af den længstvarende opdatering af datasættet i minutter. |
| Gennemsnitlig ventetid (minutter) | Den gennemsnitlige mellemliggende tid mellem det planlagte tidspunkt og starttidspunktet for en opdatering af datasættet i minutter. |
| Maks. ventetid (minutter) | Den maksimale ventetid for datasættet i minutter. |

##### <a name="query"></a>Forespørgsel

| **Målepunkt** | **Beskrivelse** |
| --- | --- |
| Antal i alt | Det samlede antal forespørgsler, der er kørt for datasættet. |
| Gennemsnitlig varighed (minutter) |Den gennemsnitlige varighed af forespørgsler for datasættet i millisekunder|
| Maksimal varighed (minutter) |Varigheden af den længstvarende forespørgsel i datasættet i millisekunder. |
| Gennemsnitlig ventetid (minutter) |Den gennemsnitlige ventetid for forespørgsler for datasættet i millisekunder. |
| Maks. ventetid (minutter) |Varigheden af den længstventende forespørgsel i datasættet i millisekunder. |

##### <a name="eviction"></a>Fjernelse

| **Målepunkt** | **Beskrivelse** |
| --- | --- |
| Antal modeller | Det samlede antal fjernelser af datasættet for denne kapacitet. Når en kapacitet står over for øget hukommelsesforbrug, fjerner noden et eller flere datasæt fra hukommelsen. Datasæt, der er inaktive (uden forespørgsels-/opdateringshandlinger, der udføres i øjeblikket), ryddes først. Derefter er fjernelsesrækkefølgen baseret på en måling af 'mindst brugt for nylig'. |

#### <a name="paginated-reports"></a>Sideinddelte rapporter

##### <a name="report-execution"></a>Rapportudførelse

| **Målepunkt** | **Beskrivelse** |
| --- | --- |
| Antal udførelser  | Antal gange, rapporten er blevet udført og set af brugere.|

##### <a name="report-usage"></a>Rapportanvendelse

| **Målepunkt** | **Beskrivelse** |
| --- | --- |
| Antal succeser | Antal gange, rapporten er blevet set af en bruger. |
| Antal fejl |Antal gange, rapporten er blevet set af en bruger.|
| Rækkeantal |Antallet af rækker med data i rapporten. |
| Varighed af datahentning (minutter) |Den gennemsnitlige mængde tid, det tager at hente data til rapporten, i millisekunder. Lange varigheder kan være et tegn på langsomme forespørgsler eller andre datakildeproblemer.  |
| Behandlingsvarighed (minutter) |Den gennemsnitlige mængde tid, det tager at behandle dataene til rapporten, i millisekunder. |
| Gengivelsesvarighed (minutter) |Den gennemsnitlige mængde tid, det tager at gengive en rapport i browseren, i millisekunder. |

> [!NOTE]
> Detaljerede målepunkter for **AI**-arbejdsbelastningen er endnu ikke tilgængelige.

## <a name="next-steps"></a>Næste trin

Nu, hvor du har en forståelse af, hvordan du overvåger Power BI Premium-kapaciteter, kan du få mere at vide om optimering af kapaciteter.

> [!div class="nextstepaction"]
> [Optimering af kapaciteter i Power BI Premium](service-premium-capacity-optimize.md)
