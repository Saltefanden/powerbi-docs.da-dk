---
title: Brug af beregnede kolonner i Power BI Desktop
description: Beregnede kolonner i Power BI Desktop
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-transform-model
ms.topic: how-to
ms.date: 05/07/2019
LocalizationGroup: Model your data
ms.openlocfilehash: 9c7285f90b963166c643c2bb20f9323eddb7ce85
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96415927"
---
# <a name="create-calculated-columns-in-power-bi-desktop"></a>Opret beregnede kolonner i Power BI Desktop
Med beregnede kolonner kan du føje nye data til en tabel, der allerede findes i din model. Men i stedet for at forespørge efter og indlæse værdier i din nye kolonne fra en datakilde kan du oprette en DAX-formel (Data Analysis Expressions), der definerer værdierne i kolonnen. I Power BI Desktop oprettes der beregnede kolonner ved hjælp af funktionen Ny kolonne i visningen **Rapport**.

I modsætning til brugerdefinerede kolonner, der oprettes som en del af en forespørgsel ved hjælp af **Tilføj brugerdefineret kolonne** i forespørgselseditoren, er beregnede kolonner, der oprettes i visningen **Rapport** eller **Data** baseret på data, du allerede har indlæst i modellen. Du kan f.eks. vælge at sammenkæde værdier fra to forskellige kolonner i to forskellige men relaterede tabeller, udføre addition eller udtrække understrenge.

Beregnede kolonner, du opretter, vises på listen **Felter** på samme måde som alle andre felter, men de har et særligt ikon, der viser, at værdierne er et resultat af en formel. Du kan navngive kolonnerne, som du vil, og føje dem til en rapportvisualisering på samme måde som alle andre felter.

![Skærmbillede af Power BI Desktop, der viser beregnede kolonner i visningen Felter.](media/desktop-calculated-columns/calccolinpbid_fields.png)
 
Beregnede kolonner beregner resultater ved hjælp af DAX, et formelsprog, der er udviklet til at arbejde sammen med relationsdata som i Power BI Desktop. DAX inkluderer et bibliotek med mere end 200 funktioner, operatorer og konstruktioner. Det giver stor fleksibilitet, når du opretter formler til beregning af resultater for stort set alle typer dataanalyse. Du kan få mere at vide om DAX under [Grundlæggende DAX i Power BI Desktop](desktop-quickstart-learn-dax-basics.md).

DAX-formler ligner Excel-formler. Faktisk har DAX mange af de samme funktioner som Excel. Men DAX-funktioner er udviklet til at arbejde via data, der opdeles eller filtreres interaktivt i en rapport som i Power BI Desktop. I Excel kan du have forskellige formler for hver række i en tabel. Når du i Power BI opretter en DAX-formel til en ny kolonne, beregner den et resultat for hver række i tabellen. Kolonneværdier genberegnes efter behov, f.eks. når de underliggende data opdateres, og værdier er ændret.

## <a name="lets-look-at-an-example"></a>Lad os tage et kig på et eksempel
Jeff er shipping manager ved Contoso og vil gerne oprette en rapport, der viser antallet af forsendelser til diverse byer. Jeff har tabellen **Geography** med separate felter for by og stat. Men Jeff vil gerne have, at rapporten skal vise værdierne for byen og staten som en enkelt værdi i samme række. Jeffs **Geography**-tabel indeholder i øjeblikket ikke det ønskede felt.

![Skærmbillede af Power BI Desktop, der viser filteret Geografi i visningen Felter.](media/desktop-calculated-columns/calccolinpbid_cityandstatefields.png)

Men med en beregnet kolonne kan Jeff samle, eller sammenkæde, byerne fra kolonnen **City** med staterne fra kolonnen **State**.

Jeff højreklikker på tabellen **Geography** og vælger derefter på **Ny kolonne**. Derefter indtaster Jeff følgende DAX-formel i formellinjen:

![Skærmbillede af Power BI Desktop, der viser DAX-formelinput.](media/desktop-calculated-columns/calccolinpbid_formula.png)

Denne formel opretter blot en ny kolonne med navnet **CityState**. For hver række i tabellen **Geography** henter den værdier fra kolonnen **City**, tilføjer et komma og et mellemrum og sammenkæder derefter værdierne fra kolonnen **State**.

Jeff har nu det ønskede felt.

![Skærmbillede af Power BI Desktop, der viser CityState markeret i filteret Geografi i visningen Felter.](media/desktop-calculated-columns/calccolinpbid_citystatefield.png)

Jeff kan føje det til sit rapportlærred sammen med antallet af forsendelser. Jeff har nu meget hurtigt og med minimal indsats et felt af typen **CityState**, som kan føjes til stort set alle visualiseringstyper. Når Jeff opretter et nyt kort, ved Power BI Desktop allerede, hvordan værdierne for byen og staten i den nye kolonne skal læses.

![Skærmbillede af Power BI Desktop, der viser data repræsenteret i en kortvisualisering.](media/desktop-calculated-columns/calccolinpbid_citystatemap.png)

## <a name="next-steps"></a>Næste trin
Vi har kun givet en hurtig introduktion til beregnede kolonner her. Du kan finde flere oplysninger i følgende ressourcer:

* Du finder oplysninger om, hvordan du downloader en eksempelfil og får trinvise vejledninger i, hvordan du opretter flere kolonner, i [Selvstudium: Opret beregnede kolonner i Power BI Desktop](desktop-tutorial-create-calculated-columns.md)

* Du kan få mere at vide om DAX under [Grundlæggende DAX i Power BI Desktop](desktop-quickstart-learn-dax-basics.md).

* Du kan få mere at vide om kolonner, du opretter i forbindelse med en forespørgsel, ved at gå til afsnittet **Opret brugerdefinerede kolonner** i [Almindelige Query-opgaver i Power BI Desktop](desktop-common-query-tasks.md).  

