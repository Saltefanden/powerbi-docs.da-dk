---
title: Tip og trick til at stille spørgsmål ved hjælp af Spørgsmål og svar
description: Tip og tricks til at stille spørgsmål med Spørgsmål og svar i Power BI
author: mihart
ms.author: mihart
ms.reviewer: Mohammad.ali
ms.service: powerbi
ms.subservice: pbi-explore
ms.topic: how-to
ms.date: 09/23/2020
LocalizationGroup: Ask questions of your data
ms.openlocfilehash: 7757c883daee390b8cdcc93e0d6b9f8376d53f62
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96389822"
---
# <a name="tips-for-asking-questions-in-power-bi-qa"></a>Tip til at stille spørgsmål med Spørgsmål og svar i Power BI

[!INCLUDE[consumer-appliesto-yyny](../includes/consumer-appliesto-yyny.md)]

## <a name="words-and-terminology-that-qa-recognizes"></a>Ord og terminologi, som Spørgsmål og svar genkender
Listen over nøgleord på denne side er ikke udtømmende.  Den bedste måde at se, om Power BI genkender et nøgleord, er ved at prøve at indtaste det i spørgsmålsfeltet.  Hvis ordet eller begrebet er nedtonet, genkender Power BI det ikke.

Listen nedenfor bruger nutid, men alle tider genkendes i de fleste tilfælde. "er" omfatter f.eks.: **er**, **var**, **være**, **vil være**, **have**, **har**, **havde**, **vil have**, **har fået**, **gøre**, **gør**, **gjorde**.  Og "sortér" omfatter: **sorteret** og **sorterer**.  Desuden genkender og inkluderer Power BI entals- og flertalsformer af et ord. 

> [!NOTE]
> Spørgsmål og svar er også tilgængelig i [Microsoft Power BI-appen til iOS på iPads, iPhones og iPod Touch-enheder](mobile/mobile-apps-ios-qna.md).
>  


|Kategori  |Nøgleord  |
|---------|---------|---------|
|**Samlinger**     | total, sum, beløb, tal, mængde, antal, gennemsnit, mest, mindst, færrest, størst, højest, maksimum, max, maks., lavest, minimum, min.          |
|     |         |         
**Kendeord**     |  en, et, den, det              |
|     |         |         
|**Tom og boolesk**     |   blank, tom, null, indledes med "ikke" eller "ikke-", tom streng, tom tekst, sand, falsk          |
|     |         |         |
|**Sammenligninger**     |   vs., versus, sammenlignet med, sammenlignes med            |
|     |         |         |
|**Bindeord**     |  og, eller, hver af, med, versus, &, og, men, hverken, sammen med, ud over       |         
|          |         |
|**Sammentrækninger**     |  Spørgsmål og svar genkender næsten alle sammentrækninger. Prøv det.  Her er nogle få eksempler på engelsk: didn’t, haven’t, he’d, he’s, isn’t, it’s, she’ll, they’d, weren’t, who’s, won’t, wouldn’t          |
|        |         |
|**Datoer**     |       Power BI genkender de fleste datobegreber (dag, uge, måned, år, kvartal, årti osv.) og datoer, der er skrevet i mange forskellige formater (se nedenfor). Power BI genkender også følgende nøgleord: Månednavn, dage 1-31, årti. Eksempler: 3. januar 1995, jan 03 1995, 3 jan 1995, den 3. januar 1995, januar 1995, 1995 januar, 1995-01, 01/1995, navne på måneder         |
|        |         |
|**Relative datoer**     |   i dag, lige nu, aktuelt klokkeslæt, i går, i morgen, dags dato, næste, den kommende, sidst, tidligere, siden, før nu, tidligere end, efter, senere end, fra, på, fra nu, efter nu, i fremtiden, fortid, forrige, inden for, over, N dage siden, N dage fra nu, næste, en gang, to gange.|
|    |  Eksempel: antallet af ordrer i løbet af de sidste 6 dage.  |            |
|        |         |
|**Lighed (interval)**     |   i, er lig med, =, efter, er større end, mellem, før  |
|  |Eksempler: Ordreår er før 2012? Pris lig med mellem 10 og 20? Er Johns alder større end 40? Samlet salg i 200-300?              |
|        |         |
|**Lighed (værdi)**     |   er, lig med, i, af, for, inden for, er i, er på |
|   | Eksempler: Hvilke produkter er grønne? Ordredato lig med 2012. Er Johns alder 40? Samlet salg, der ikke er lig med 200? Ordredato den 1/1/2016. 10 i pris? Grøn som farve? 10 i pris?              |
|        |         |
|**Navne**     |       Hvis en kolonne i datasættet indeholder udtrykket "navn" (f.eks. Medarbejdernavn), forstår Spørgsmål og svar, at værdierne i den pågældende kolonne er navne. Du kan stille spørgsmål som "hvilke medarbejdere hedder Robert".          |
|        |         |
**Stedord**  | sin, sit, han, ham, hans, hun, sig selv, hende, hendes, den, det, de, deres, dem selv, dette, denne, disse
|**Forespørgselskommandoer**     |    sorteret, sorter efter, retning, gruppér, gruppér efter, efter, vis, få vist, giv mig, navngiv, kun, blot, arranger, ranger, sammenlign, til, med, i forhold til, alfabetisk, stigende, faldende, rækkefølge             |
|        |         |
|**Interval**     |      større, mere, over, >, mindre, færre, under, <, mindst, ikke mindre end, >=, højest, ikke mere end, <=, i, mellem, i området, fra, senere, tidligere, efter, på, ved, senere end, siden, starter med, starter fra, slutter med           |
|        |         |
**Klokkeslæt**  |am, pm, klokken, middag, midnat, time, minut, sekund, tt:mm:ss  |
|  |  Eksempler: 10 pm, 10:35 pm, 10:35:15 pm, klokken 10, middag, midnat, time, minut, sekund.  |
|  |  |
|**Top N**     |     (sortering, rangering): top, bund, højeste, laveste, første, sidste, næste, tidligste, nyeste, ældste, seneste            |
|        |         |
|**Visualiseringstyper**     |  alle visualiseringstyper, der er indbygget i Power BI.  Hvis det er en indstilling i ruden med visuelle effekter, kan du medtage den i dit spørgsmål.  Undtagelsen til denne regel er [brugerdefinerede Power BI-visualiseringer](../developer/visuals/power-bi-custom-visuals.md), som du manuelt har føjet til visualiseringsruden.  |
|  |  Eksempel: vis distrikter efter måned og samlet salg som søjlediagram               |
|        |         |
|**HV (relation, kvalificeret)**  | hvornår, hvor, hvilken, hvem, hvor mange, hvor meget, hvor ofte, hvor mange gange, hvor hyppigt, antal, tal, mængde, hvor længe, hvad                |

## <a name="qa-helps-you-phrase-the-question"></a>Spørgsmål og svar hjælper dig med at stille spørgsmålet
Spørgsmål og svar gør sit bedste for at forstå og besvare det spørgsmål, der stilles. Det forsøger at forstå på flere måder. For alle disse vendinger kan du acceptere handlingen fuldt ud, delvist eller slet ikke. Mens du skriver dit spørgsmål, gør Spørgsmål og svar følgende:

* fuldfører automatisk ord og spørgsmål. Der bruges forskellige strategier, herunder automatisk fuldførelse af genkendte ord, gemte spørgsmål og tidligere anvendte spørgsmål, der har returneret brugbare svar. Hvis der er mere end én mulighed i forbindelse med automatisk fuldførelse, vises de på en rulleliste.
* udfører stavekontrol.
* giver et eksempel på svaret i form af en visualisering. Visualiseringen opdateres, mens du skriver og redigerer spørgsmålet (den venter ikke på, at du trykker på Enter).
* foreslår tilsvarende termer fra det eller de underliggende datasæt, når du flytter markøren tilbage i spørgsmålsfeltet.
* viser spørgsmålet igen baseret på dataene i det eller de underliggende datasæt. Spørgsmål og svar erstatter de ord, du brugte, med synonymer fra det eller de underliggende datasæt. Ved at læse tilpasningen ved du, om Spørgsmål og svar har forstået dit spørgsmål eller ej. 
* føjer en dobbelt understregning til ord, som ikke er forstået.
* føjer en enkelt understregning til ord, som er forstået.
* giver dig mulighed for at kontakte ejeren af rapporten eller dashboardet, når dit ord ikke blev fundet, eller hvis dit spørgsmål ikke giver nogen resultater.

## <a name="dont-stop-now"></a>Stop ikke her
Hold samtalen i gang, når Spørgsmål og svar har vist dine resultater! Brug de interaktive funktioner i visualiseringen og Spørgsmål og svar til at afdække mere indsigt.

## <a name="next-steps"></a>Næste trin
Tilbage til [Spørgsmål og svar i Power BI](end-user-q-and-a.md)  

[Power BI – Grundlæggende begreber](end-user-basic-concepts.md)  

Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)

