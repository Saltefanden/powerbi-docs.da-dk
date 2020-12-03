---
title: Selvstudium i intelligente narrativer
description: 'Selvstudium: Opret visualiseringer af en oversigt over intelligente narrativer i Power BI'
author: aphilip94
ms.author: anphil
ms.reviewer: mihart
ms.service: powerbi
ms.subservice: pbi-visuals
ms.topic: how-to
ms.date: 11/06/2020
ms.custom: video
LocalizationGroup: Visualizations
ms.openlocfilehash: 7ebb9d4c3682f1ce5cac5e587cb326d4e4ba506b
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96418756"
---
# <a name="create-smart-narrative-summaries-preview"></a>Opret oversigter over intelligente narrativer (prøveversion)

[!INCLUDE[consumer-appliesto-nyyn](../includes/consumer-appliesto-nyyn.md)]    

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

Visualiseringen af intelligente narrativer hjælper dig med at få et hurtigt overblik over visualiseringer og rapporter. Den giver dig relevant innovativ indsigt, som du kan tilpasse.

![Skærmbillede, der viser en oversigt over intelligente narrativer til højre i en rapport.](media/power-bi-visualization-smart-narratives/1.png)

Brug oversigter over intelligente narrativer i dine rapporter til at belyse vigtigste punkter og tendenser samt til at redigere sproget og formatet for en bestemt målgruppe. I stedet for at indsætte et skærmbillede af rapportens vigtigste punkter i PowerPoint, kan du tilføje narrativer, der opdateres ved hver opdatering. Dine slutbrugere kan bruge oversigterne til at forstå dataene, til at få hurtigere adgang til centrale punkter og til at forklare dataene til andre.

>[!NOTE]
> Da funktionen til intelligente narrativer findes i prøveversion, skal du slå den til, hvis du vil bruge den. Vælg **Filer** > **Indstillinger** > **Indstillinger** > **Prøveversionsfunktioner** i Power BI. Vælg derefter **Visualisering til intelligent narrativ**.
>
>![Skærmbillede, der viser Power BI-indstillinger. Indstillingen Visualisering til intelligent narrativ er valgt.](media/power-bi-visualization-smart-narratives/2.png)



## <a name="get-started"></a>Kom i gang 
Se Justyna vise dig, hvordan du bruger smarte fortællinger, og prøv derefter selv ved hjælp af selvstudiet under videoen.  For at følge med i dette selvstudium skal du downloade [eksempelfilen](https://github.com/microsoft/powerbi-desktop-samples/blob/master/Monthly%20Desktop%20Blog%20Samples/2020/2020SU09%20Blog%20Demo%20-%20September.pbix) med et onlinesalgsscenarie.

> [!VIDEO https://youtu.be/01UrT-z37sw]

Vælg ikonet **Intelligent narrativ** i ruden **Visualiseringer** for at oprette en oversigt automatisk.

![Skærmbillede, der viser ruden Visualiseringer. Ikonet Intelligent narrativ valgt.](media/power-bi-visualization-smart-narratives/3.png)

Du får vist et narrativ, der er baseret på alle visualiseringerne på siden. I eksempelfilen kan intelligente narrativer f.eks. automatisk generere en oversigt over de visualiseringer i rapporten, der belyser indtægter, besøg på websteder og salg. Power BI analyserer automatisk tendenser for at vise, at indtægter og antallet af besøg er steget. Det beregner endda stigningen, hvilket i dette tilfælde er 72 %.
 
![Skærmbillede, der viser, hvordan du opretter en oversigt over intelligente narrativer.](media/power-bi-visualization-smart-narratives/4.gif)
 
Hvis du vil oprette et intelligent narrativ af en visualisering, skal du højreklikke på den og derefter vælge **Opsummer**. I eksempelfilen kan du f.eks. prøve at opsummere et punktdiagram, der viser forskellige transaktioner. Power BI analyserer dataene og viser, hvilken by eller hvilket område der har den højeste indtægt pr. transaktion og det største antal transaktioner. De intelligente narrativer viser også det forventede værdiinterval for disse målepunkter. Du kan se, at de fleste byer producerer mindre end 45 USD pr. transaktion og har færre end 10 transaktioner.
 
  
![Skærmbillede, der viser et intelligent narrativ, der opsummerer et punktdiagram.](media/power-bi-visualization-smart-narratives/5.gif)
 
## <a name="edit-the-summary"></a>Rediger oversigten
 
Oversigten over intelligente narrativer kan tilpasses i meget stort omfang. Du kan redigere eller føje til den eksisterende tekst ved hjælp af tekstfeltkommandoerne. Du kan f.eks. gøre teksten fed eller ændre tekstens farve.
 
![Skærmbillede, der viser kommandoer til tekstformatering på en værktøjslinje.](media/power-bi-visualization-smart-narratives/6.png)
  
Hvis du vil tilpasse oversigten eller tilføje din egen indsigt, skal du bruge *dynamiske værdier*. Du kan knytte tekst til eksisterende felter og målinger eller bruge naturligt sprog til at definere en ny måling, der skal knyttes til tekst. Hvis du f.eks. vil tilføje oplysninger om antallet af returnerede elementer i eksempelfilen, skal du tilføje en værdi. 

Når du skriver et værdinavn, kan du vælge på en liste over forslag, som du gør i en visualisering til Spørgsmål og svar. Og ud over at stille spørgsmål om dine data i en visualisering til Spørgsmål og svar kan du nu oprette dine egne beregninger også uden at bruge DAX (Data Analysis Expressions). 
  
![Skærmbillede, der viser, hvordan du opretter en dynamisk værdi for en visualisering af et intelligent narrativ.](media/power-bi-visualization-smart-narratives/7.gif)
  
Du kan også formatere dynamiske værdier. I eksempelfilen kan du f.eks. få vist værdier som valuta, angive decimaler og vælge en tusindtalsseparator. 
   
![Skærmbillede, der viser, hvordan du formaterer en dynamisk værdi.](media/power-bi-visualization-smart-narratives/8.gif)
   
Hvis du vil formatere en dynamisk værdi, skal du vælge værdien i oversigten for at se dine redigeringsindstillinger under fanen **Gennemse**. Du kan også vælge knappen Rediger ud for den værdi, du vil redigere, i tekstfeltet. 
   
![Skærmbillede, der viser tekstfeltet, hvor fanen Værdi er valgt. Ud for værdinavnet er knappen Rediger fremhævet.](media/power-bi-visualization-smart-narratives/9.png)
   
Du kan også bruge fanen **Gennemse** til at gennemse, slette eller genbruge tidligere definerede værdier. Vælg plustegnet (+) for at indsætte værdien i oversigten. Du kan også få vist automatisk genererede værdier ved at aktivere indstillingen nederst under fanen **Gennemse**.

Nogle gange vises der et symbol for skjult oversigt i det intelligente narrativ. Det indikerer, at aktuelle data og filtre intet resultat giver for værdien. En oversigt er tom, når der ikke er tilgængelige indsigter. I et kurvediagram i eksempelfilen kan en oversigt over høje og lave værdier f.eks. være tom, når diagrammets kurve er flad. Men oversigten vises muligvis under andre betingelser. Symboler for skjulte oversigter er kun synlige, når du forsøger at redigere en oversigt.


![Skærmbillede, der viser to symboler for skjulte oversigter i en oversigt over intelligente narrativer.](media/power-bi-visualization-smart-narratives/10.png)
   
## <a name="visual-interactions"></a>Interaktioner mellem visualiseringer
En oversigt er dynamisk. Den opdaterer automatisk den genererede tekst og de dynamiske værdier, når du krydsfiltrerer. Hvis du f.eks. vælger elektronikprodukter i eksempelfilen, krydsfiltreres resten af rapporten, og oversigten krydsfiltreres også for at fokusere på elektronikprodukterne.  

I dette tilfælde er der forskellige tendenser for besøg og indtægter, og oversigtsteksten opdateres for at afspejle tendenserne. Antallet af returværdier, vi har tilføjet, opdateres til 4196 USD. Tomme oversigter kan opdateres, når du krydsfiltrerer.
   
![Skærmbillede, der viser, hvordan en markering i et diagram kan krydsfiltrere en oversigt.](media/power-bi-visualization-smart-narratives/11.gif)
   
Du kan også udføre mere avanceret filtrering. Du kan f.eks. se på visualiseringen af tendenser for flere produkter i eksempelfilen. Hvis du kun er interesseret i en tendens for et bestemt kvartal, skal du vælge de relevante datapunkter for at opdatere oversigten for den pågældende tendens.
   
![Skærmbillede, der viser, hvordan du vælger en tendenslinje for at filtrere oversigten, så den kun viser den pågældende tendens.](media/power-bi-visualization-smart-narratives/12.gif)
   
## <a name="limitations"></a>Begrænsninger

Funktionen for intelligente narrativer understøtter ikke følgende funktionalitet:
- Fastgørelse til et dashboard 
- Brug af dynamiske værdier og betinget formatering (f.eks. databundet titel)
- Azure Analysis Services, AS i det lokale miljø
- KPI'er, kort, kort med flere rækker, tilknytninger, tabeller, matrixer, R-visualiseringer eller Python-visualiseringer, brugerdefinerede visualiseringer 
- Oversigter over visualiseringer, hvis kolonner er grupperet efter andre kolonner, og for visualiseringer, der er bygget på et datagruppefelt 
- Krydsfiltrering ud fra en visualisering
- Omdøbning af dynamiske værdier eller redigering af automatisk genererede dynamiske værdier
- Oversigter over visualiseringer, der indeholder løbende beregninger som spørgsmål og svar med aritmetik og procent af samlet beløb 
- [Beregningsgrupper](/analysis-services/tabular-models/calculation-groups)
   

