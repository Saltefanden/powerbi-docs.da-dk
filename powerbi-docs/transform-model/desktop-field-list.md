---
title: Brug af feltlisten i Power BI Desktop (prøveversion)
description: Brug feltlisten til at udforme data og oprette rapporter i Power BI Desktop
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-transform-model
ms.topic: conceptual
ms.date: 11/11/2020
LocalizationGroup: Transform and shape data
ms.openlocfilehash: ced861f0d229153866c1d52616494f8b444220ae
ms.sourcegitcommit: 8993400b32a44f4e7ce9a2db998ddebda18c7698
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/02/2020
ms.locfileid: "96536478"
---
# <a name="using-the-field-list-in-power-bi-desktop-preview"></a>Brug af feltlisten i Power BI Desktop (prøveversion)

Fra og med opdateringen i november 2020 samler vi **felt** lister på tværs af Modelvisning, Datavisning og Rapportvisning i Power BI Desktop. Samlingen af disse visninger skaber en ensartet funktionalitet og brugergrænseflade på tværs af visninger, og er baseret på brugernes feedback.

Ændringer, du vil bemærke på tværs af visninger, omfatter følgende:

* Ikonografi
* Søgefunktionalitet
* Genvejsmenupunkter
* Lignende funktionsmåde for træk og slip
* Værktøjstip
* Forbedringer af Hjælp til handicappede

Hensigten er at forbedre Power BI Desktop-brugervenligheden. Ændringerne har en minimal indvirkning på din typiske dataarbejdsproces.

## <a name="enabling-the-new-field-list-preview"></a>Aktivering af den nye feltliste (eksempelvisning)

Den samlede feltliste starter med **Model** visning og aktiveres derefter for andre visninger. Du aktiverer den samlede feltvisning ved at gå til **Filer > Indstillinger > Indstillinger** i Power BI Desktop og derefter vælge **Prøveversionsfunktioner** i ruden til venstre. Markér afkrydsningsfeltet ud for **Ny feltliste** i afsnittet Prøveversionsfunktioner.

![Aktivér den nye Feltliste](media/desktop-field-list/field-list-01.png)

Du bliver bedt om at genstarte Power BI Desktop, for at valget træder i kraft.

## <a name="field-list-changes"></a>Feltlisteændringer

Opdateringerne af feltlisten vises i følgende tabeller: 


|**Oprindelig feltliste (Modelvisning)**  | **Ny feltliste (Modelvisning)**  |
|:---------:|:---------:|
|**Oprindelig** |**Ny** |
|**Ikoner og brugergrænseflade**       ||
|![oprindelig feltliste](media/desktop-field-list/field-list-01a.png)     |![ny feltliste](media/desktop-field-list/field-list-01b.png)    |
|**Genvejsmenu – felt**       ||
|![oprindelig genvejsmenu for felt](media/desktop-field-list/field-list-02a.png)     |![ny genvejsmenu for felt](media/desktop-field-list/field-list-02b.png)    |
|**Genvejsmenu – tabel**       ||
|![oprindelig genvejsmenu for tabel](media/desktop-field-list/field-list-03a.png)     |![ny genvejsmenu for tabel](media/desktop-field-list/field-list-03b.png)    |
|**Værktøjstip**       ||
|![oprindeligt værktøjstip](media/desktop-field-list/field-list-04a.png)     |![nyt værktøjstip](media/desktop-field-list/field-list-04b.png)    |

## <a name="field-list-icons"></a>Ikoner for feltliste

Der er også nye feltlisteikoner. I følgende tabel vises de oprindelige ikoner og den nye version, og der er en kort beskrivelse af hver enkelt. 


|Oprindeligt ikon  |Nyt ikon  |Beskrivelse  |
|:---------:|:---------:|:---------|
|![oprindeligt mappeikon](media/desktop-field-list/field-list-05a.png)     |![nyt mappeikon](media/desktop-field-list/field-list-05b.png)           |Mappe på listen Felter         |
|![oprindeligt ikon for numerisk felt](media/desktop-field-list/field-list-06a.png)     |![nyt ikon for numerisk felt](media/desktop-field-list/field-list-06b.png)         |Numerisk felt: Numeriske felter er samlinger, der f.eks. kan sammenlægges eller beregnes som gennemsnit. Samlinger importeres med dataene og defineres i den datamodel, som din rapport er baseret på. Du kan finde flere oplysninger i [Aggregeringer i Power BI-rapporter](../create-reports/service-aggregates.md).         |
|![oprindeligt ikon for beregnet kolonne](media/desktop-field-list/field-list-07a.png)     |![nyt ikon for beregnet kolonne](media/desktop-field-list/field-list-07b.png)         |Beregnet kolonne med en datatype, der ikke er numerisk: En ny ikke-numerisk kolonne, du opretter, med en DAX-formel (Data Analysis Expressions), der definerer kolonnens værdier. Læs mere om [beregnede kolonner](desktop-calculated-columns.md).        |
|![oprindeligt ikon for numerisk beregnet kolonne](media/desktop-field-list/field-list-08a.png)     |![nyt ikon for numerisk beregnet kolonne](media/desktop-field-list/field-list-08b.png)          |Numerisk beregnet kolonne: En ny kolonne, du opretter, med en DAX-formel (Data Analysis Expressions), der definerer kolonnens værdier. Læs mere om [beregnede kolonner](desktop-calculated-columns.md).         |
|![oprindeligt ikon for måling](media/desktop-field-list/field-list-09a.png)     |![nyt ikon for måling](media/desktop-field-list/field-list-09b.png)          |Måling: Hver måling har sin egen hårdt kodede formel. Rapportlæsere kan ikke ændre beregningen – hvis det f.eks. er en sum, kan det kun være en sum. Værdierne gemmes ikke i en kolonne. De beregnes løbende, udelukkende afhængigt af hvordan de er placeret i en visualisering. Du kan finde flere oplysninger i [Forstå målinger](desktop-measures.md).         |
|![oprindeligt ikon for målingsgruppe](media/desktop-field-list/field-list-10a.png)     |![nyt ikon for målingsgruppe](media/desktop-field-list/field-list-10b.png)         |Målingsgruppe.         |
|![oprindeligt KPI-ikon](media/desktop-field-list/field-list-11a.png)     |![nyt KPI-ikon](media/desktop-field-list/field-list-11b.png)         |KPI: Et visuelt tip, der viser statussen mod et målbart mål. Læs mere om [KPI-visualiseringer (Key Performance Indicator)](../visuals/power-bi-visualization-kpi.md).         |
|![oprindeligt ikon for felthierarki](media/desktop-field-list/field-list-12a.png)     |![nyt ikon for felthierarki](media/desktop-field-list/field-list-12b.png)           |Felthierarki: Vælg pilen for at se de felter, der udgør hierarkiet. Du kan få flere oplysninger ved at se denne Power BI-video på YouTube om, [hvordan du opretter og arbejder med hierarkier](https://www.youtube.com/watch?v=q8WDUAiTGeU).         |
|![oprindeligt ikon for geo-data](media/desktop-field-list/field-list-13a.png)     |![nyt ikon for geo-data](media/desktop-field-list/field-list-13b.png)         |Geo-data: Disse placeringsfelter kan bruges til at oprette kortvisualiseringer.         |
|![oprindeligt ikon for id-felt](media/desktop-field-list/field-list-14a.png)     |![nyt ikon for id-felt](media/desktop-field-list/field-list-14b.png)          |Id-felt: Felter med dette ikon er entydige felter, som er angivet til at vise alle værdier, også selvom der er dubletter. Dine data kan f.eks. have poster for to forskellige personer med navnet "Robin Smith", og hver enkelt behandles som entydig. De opsummeres ikke.         |
|![oprindeligt parameterikon](media/desktop-field-list/field-list-15a.png)     |![nyt parameterikon](media/desktop-field-list/field-list-15b.png)          |Parameter: Angiv parametre for at gøre dele af dine rapporter og datamodeller (f.eks. et forespørgselsfilter, en datakildereference, en målingsdefinition osv.) afhængige af en eller flere parameterværdier. Du kan finde flere oplysninger i dette Power BI-blogindlæg om [forespørgselsparametre](https://powerbi.microsoft.com/blog/deep-dive-into-query-parameters-and-power-bi-templates/).         |
|![oprindeligt ikon for kalenderdatofelt](media/desktop-field-list/field-list-16a.png)     |![nyt ikon for kalenderdatofelt](media/desktop-field-list/field-list-16b.png)         |Kalenderdatofelt med en indbygget datotabel.         |
|![oprindeligt ikon for beregnet tabel](media/desktop-field-list/field-list-17a.png)     |![nyt ikon for beregnet tabel](media/desktop-field-list/field-list-17b.png)          |Beregnet tabel: En tabel, der er oprettet med en DAX-formel (Data Analysis Expressions), som er baseret på data, der allerede er indlæst i modellen. Disse er bedst egnet til mellemliggende beregninger og gemmes som en del af modellen.         |
|![oprindeligt advarselsikon](media/desktop-field-list/field-list-18a.png)     |![nyt advarselsikon](media/desktop-field-list/field-list-18b.png)         |Advarsel! Et beregnet felt med en fejl. Syntaksen i DAX-udtrykket kan f. eks. være forkert.         |
|![oprindeligt gruppeikon](media/desktop-field-list/field-list-19a.png)     |![nyt gruppeikon](media/desktop-field-list/field-list-19b.png)         |Gruppe: Værdierne i denne kolonne er baseret på grupperingsværdier fra en anden kolonne ved hjælp af grupperings- og placeringsfunktionen. Du kan læse, hvordan du bruger funktionen, under [Brug gruppering og gruppering](../create-reports/desktop-grouping-and-binning.md).         |
| intet oprindeligt ikon    |![nyt ikon for skift af registreringsmåling](media/desktop-field-list/field-list-20b.png)          |Skift registreringsmåling: Når du konfigurerer en side til automatisk opdatering af sider, kan du konfigurere en [registreringsmåling](../create-reports/desktop-grouping-and-binning.md), der forespørges, for at finde ud af om resten af en sides visualiseringer skal opdateres.         |


## <a name="next-steps"></a>Næste trin

Du vil måske også være interesseret i følgende artikler:

* [Opret beregnede kolonner i Power BI Desktop](desktop-calculated-columns.md)
* [Brug gruppering og gruppering i beholder i Power BI Desktop](../create-reports/desktop-grouping-and-binning.md)
* [Brug gitterlinjer og fastgørelse til gitter i Power BI Desktop-rapporter](../create-reports/desktop-gridlines-snap-to-grid.md)

