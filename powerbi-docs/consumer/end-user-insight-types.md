---
title: Indsigtstyper, der understøttes af Power BI
description: Hurtige indsigter og Vis indsigter i Power BI.
author: mihart
ms.reviewer: mihart
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 09/09/2020
ms.author: mihart
LocalizationGroup: Dashboards
ms.openlocfilehash: 7b5a935418aacb8de15ea6e7e942f2de440ecec1
ms.sourcegitcommit: 92b033ee7a6e36808371b247b7b41536cee6c2f6
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 09/10/2020
ms.locfileid: "90008687"
---
# <a name="types-of-insights-supported-by-power-bi"></a>Indsigtstyper, der understøttes af Power BI

[!INCLUDE[consumer-appliesto-yyny](../includes/consumer-appliesto-yyny.md)]

Du kan bede Power BI om at se nærmere på dine data og finde interessante tendenser og mønstre. Disse tendenser og mønstre præsenteres i form af visualiseringer, der kaldes *indsigter*. 

Se [Power BI-indsigt](end-user-insights.md) for at få mere at vide om, hvordan du bruger indsigter

![et sæt indsigter](media/end-user-insight-types/power-bi-insight.png)

## <a name="how-does-insights-work"></a>Hvordan fungerer indsigter?
Power BI søger hurtigt i forskellige undersæt af dit datasæt. I takt med at Power BI søger, anvendes et sæt avancerede algoritmer for at finde indsigt, der kan være interessant. Power BI-*virksomhedsbrugere* kan køre indsigter på dashboardfelter.

## <a name="some-terminology"></a>Terminologi
Power BI bruger statistiske algoritmer til at afdække indsigt. Algoritmerne er angivet og beskrevet i næste afsnit i denne artikel. Før vi går videre med algoritmerne, er der her nogle definitioner for nogle af de ord, som du muligvis ikke kender. 

* **Måling** – en måling er et kvantitativt (numerisk) felt, der kan bruges til at foretage beregninger. Almindelige beregninger er sum, gennemsnit og minimum. Hvis vores virksomhed f.eks. fremstiller og sælger skateboards, kan vores målinger være antallet af skateboards, der er solgt, og den gennemsnitlige indtjening pr. år.  
* **Dimension** – dimensioner er kategoriske data (tekst). En dimension beskriver en person, et objekt, et element, produkter, en placering og et klokkeslæt. I et datasæt er dimensioner en metode til at gruppere *målinger* i nyttige kategorier. For vores skateboard-virksomhed kan nogle dimensioner inkludere at se på salg (en måling) efter model, farve, land eller markedsføringskampagne.   
* **Korrelation** – en korrelation fortæller os, hvordan funktionsmåden for ting er relateret til hinanden.  Hvis deres mønstre for stigning og fald er det samme, er de positivt korreleret. Og hvis deres mønstre er modsatte, er de negativt korreleret. Hvis f.eks. salg af vores røde skateboard stiger, hver gang vi kører en tv-marketingkampagne, er salg af det røde skateboard og tv-kampagnen positivt korreleret.
* **Tidsserie** – en tidsserie er den måde, hvorpå du kan få vist klokkeslæt som efterfølgende datapunkter. Disse datapunkter kan være trinvise, f.eks. sekunder, timer, måneder eller år.  
* **Fortløbende variabel** – en fortløbende variabel kan være en hvilken som helst værdi mellem minimum- og maksimumgrænserne, ellers er den en diskret variabel. Eksempler er temperatur, vægt, alder og tid. Fortløbende variabler kan indeholde brøker eller dele af værdien. Det samlede antal blå skateboards, der er solgt, er en diskret variabel, da vi ikke kan sælge halvdelen af et skateboard.  

## <a name="what-types-of-insights-can-you-find"></a>Hvilke typer indsigt kan vi finde?
Dette er de algoritmer, Power BI bruger. 

### <a name="category-outliers-topbottom"></a>Kategori med udenforliggende værdier (top/bund)
Fremhæver tilfælde, hvor en eller to kategorier har meget større værdier end andre kategorier.  

![Eksempel på kategori med udenforliggende værdier](./media/end-user-insight-types/pbi-auto-insight-type-category-outliers.png)

### <a name="change-points-in-a-time-series"></a>Skift punkter i en tidsserie
Fremhæver, når der er betydelige ændringer i tendenser i en tidsserie af data.

![Eksempel på skift af punkter i en tidsserie](./media/end-user-insight-types/pbi-auto-insight-type-changepoint.png)

### <a name="correlation"></a>Korrelation
Registrerer de tilfælde, hvor flere målinger viser et lignende mønster eller en lignende tendens, når de afbildes i forhold til en kategori eller værdi i datasættet.

![Eksempel på korrelation](./media/end-user-insight-types/pbi-auto-insight-type-correlation.png)

### <a name="low-variance"></a>Lav varians
Registrerer de tilfælde, hvor datapunkter for en dimension ikke er langt fra middelværdien, så "variansen" er lav. Lad os antage, at du har målet "salg" og en dimension "område". Når du ser på tværs af områder, kan du se, at der er meget lidt forskel mellem datapunkterne og middelværdien (for datapunkterne). Indsigten udløses, når variansen af salg på tværs af alle områder er lavere end en tærskel. Det vil sige, at når salget er forholdsvis ens på tværs af alle områder.

![Eksempel på lav varians](./media/end-user-insight-types/power-bi-insights-low-variance.png)

### <a name="majority-major-factors"></a>Majoritet (overordnede faktorer)
Finder tilfælde, hvor en majoritet af en samlet værdi kan tilskrives en enkelt faktor, når den opdeles på en anden dimension.  

![Eksempel på vigtige faktorer](./media/end-user-insight-types/pbi-auto-insight-type-majority.png)

### <a name="overall-trends-in-time-series"></a>Samlede tendenser i tidsserie
Registrerer op- eller nedadgående tendenser i tidsseriedata.

![Eksempel på generelle tendenser i tidsserie](./media/end-user-insight-types/pbi-auto-insight-type-trend.png)

### <a name="seasonality-in-time-series"></a>Sæsonudsving i tidsserie
Finder periodiske mønstre i tidsseriedata, f.eks. ugentlige, månedlige eller årlige sæsonudsving.

![Eksempel på sæsonudsving](./media/end-user-insight-types/pbi-auto-insight-type-seasonality-new.png)

### <a name="steady-share"></a>Konstant deling
Fremhæver tilfælde, hvor der er en overordnet-underordnet-korrelation mellem andelen af en underordnet værdi i forhold til den samlede værdi af den overordnede på tværs af en kontinuerlig variabel. Indsigten med den konstante deling gælder for konteksten af en måling, en dimension og en anden dato-/klokkeslætsdimension. Denne indsigt udløses, når en bestemt dimensionsværdi, f.eks. "det nordøstlige område", har en konstant procentdel af det samlede salg på tværs af denne dato-/klokkeslætsdimension.

Indsigten med den konstante deling ligner den lave varians, da de begge relaterer til den manglende varians for en værdi på tværs af tiden. Indsigten med den konstante deling måler dog den manglende varians for **den overordnede procentdel** på tværs af tiden, mens indsigten med lav varians måler den manglende varians for de absolutte målingsværdier på tværs af en dimension.

![Eksempel på konstant deling](./media/end-user-insight-types/pbi-auto-insight-type-steadyshare.png)

### <a name="time-series-outliers"></a>Tidsserier med udenforliggende værdier
Registrerer for data på tværs af en tidsserie, når der er specifikke datoer og klokkeslæt med værdier, som er væsentligt anderledes end de andre dato-/klokkeslætsværdier.

![Eksempel på tidsserier med udenforliggende værdier](./media/end-user-insight-types/pbi-auto-insight-type-time-series-outliers-purple.png)

## <a name="next-steps"></a>De næste trin
[Power BI-indsigter](end-user-insights.md)

Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)

