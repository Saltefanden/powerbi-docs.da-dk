---
title: 'Eksempel på analyse af salgsmuligheder til Power BI: Få en introduktion'
description: 'Eksempel på analyse af salgsmuligheder til Power BI: Få en introduktion'
author: maggiesMSFT
ms.author: maggies
ms.reviewer: amac
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: conceptual
ms.date: 07/02/2019
LocalizationGroup: Samples
ms.openlocfilehash: 63bbbedd24facfdd485f14b96eb608efc001dd55
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96395802"
---
# <a name="opportunity-analysis-sample-for-power-bi-take-a-tour"></a>Eksempel på analyse af salgsmuligheder til Power BI: Få en introduktion

Indholdspakken til eksemplet på analyse af salgsmuligheder indeholder et dashboard, en rapport og et datasæt for en softwarevirksomhed, der har 2 salgskanaler: *direkte* og *partner*. Salgschefen har oprettet dette dashboard for at spore salgsmuligheder og indtægt efter område, aftalestørrelse og kanal.

Eksemplet anvender to målinger af indtægt:

* Indtægt: En sælgers estimat over, hvad indtægten vil blive.
* Indregnet indtægt: Dette beregnes som indtægt x sandsynlighedsprocent og anerkendes som værende en mere nøjagtig indikator for den faktiske salgsindtægt. Sandsynligheden afhænger af, hvor i *salgsfasen* aftalen befinder sig:
  * Kundeemne: 10 %  
  * Kvalificer: 20 %  
  * Løsning: 40 %  
  * Tilbud: 60 %  
  * Færdiggør: 80 %

![Dashboard for eksemplet på analyse af salgsmuligheder](media/sample-opportunity-analysis/opportunity1.png)

Dette eksempel er en del af en serie, der viser, hvordan du kan bruge Power BI med forretningsrelaterede data, rapporter og dashboards. Det blev oprettet af [obviEnce](http://www.obvience.com/) med rigtige data, som er blevet anonymiseret. Dataene er tilgængelige i flere formater: indholdspakke, .pbix-fil til Power BI Desktop eller Excel-projektmappe. Se [Eksempler til Power BI](sample-datasets.md). 

I dette selvstudium udforskes indholdspakken med eksemplet på analyse af salgsmuligheder i Power BI-tjenesten. Da rapportoplevelsen i Power BI Desktop og i tjenesten minder meget om hinanden, kan du også følge med ved at bruge .pbix-eksempelfilen i Power BI Desktop. 

Du behøver ikke en Power BI-licens for at udforske eksemplerne i Power BI Desktop. Hvis du ikke har en Power BI Pro-licens, kan du gemme eksemplet i Mit arbejdsområde i Power BI-tjenesten. 

## <a name="get-the-sample"></a>Hent eksemplet

Før du kan bruge eksemplet, skal du først downloade det som en [indholdspakke](#get-the-content-pack-for-this-sample), [.pbix-fil](#get-the-pbix-file-for-this-sample) eller [Excel-projektmappe](#get-the-excel-workbook-for-this-sample).

### <a name="get-the-content-pack-for-this-sample"></a>Hent indholdspakken for dette eksempel

1. Åbn Power BI-tjenesten (app.powerbi.com), log på, og åbn det arbejdsområde, hvor du vil gemme eksemplet. 

    Hvis du ikke har en Power BI Pro-licens, kan du gemme eksemplet i Mit arbejdsområde.

2. Vælg **Hent data** i nederste venstre hjørne.

    ![Vælg Hent data](media/sample-datasets/power-bi-get-data.png)
3. På siden **Hent data**, der vises, skal du vælge **Eksempler**.

4. Vælg **Eksempel på analyse af salgsmuligheder**, og vælg derefter **Opret forbindelse**.  

   ![Opret forbindelse til eksempel](media/sample-opportunity-analysis/opportunity-connect.png)
5. Power BI importerer indholdspakken og føjer derefter et nyt dashboard, en ny rapport og et nyt datasæt til dit aktuelle arbejdsområde.

   ![Posten Eksempel på analyse af salgsmuligheder](media/sample-opportunity-analysis/opportunity-entry.png)

### <a name="get-the-pbix-file-for-this-sample"></a>Hent .pbix-filen knyttet til dette eksempel

Du kan også hente eksemplet på analyse af salgsmuligheder som en [.pbix-fil](https://download.microsoft.com/download/9/1/5/915ABCFA-7125-4D85-A7BD-05645BD95BD8/Opportunity%20Analysis%20Sample%20PBIX.pbix), som er beregnet til brug med Power BI Desktop.

### <a name="get-the-excel-workbook-for-this-sample"></a>Hent Excel-projektmappen for dette eksempel

Hvis du vil have vist datakilden for dette eksempel, er den også tilgængelig som en [Excel-projektmappe](https://go.microsoft.com/fwlink/?LinkId=529782). Projektmappen indeholder Power View-ark, som du kan få vist og redigere. Hvis du vil se rådataene, skal du aktivere tilføjelsesprogrammerne Dataanalyse og derefter vælge **Power Pivot > Administrer**. Hvis du vil aktivere tilføjelsesprogrammerne Power View og Power Pivot, kan du finde flere oplysninger under [Udforsk Excel-eksemplerne i Excel](sample-datasets.md#explore-excel-samples-inside-excel).

## <a name="what-is-our-dashboard-telling-us"></a>Hvad fortæller vores dashboard os?
Salgschefen har oprettet et dashboard for at spore de vigtigste målepunkter. Når vedkommende ser noget interessant, kan han eller hun vælge et felt for at se nærmere på dataene:

- Virksomhedens indtægter er $2 milliarder, og indregnede indtægter er $461 millioner.
- Antal salgsmuligheder og indtægt følger et velkendt tragtformet mønster, hvor totaler formindskes i hver efterfølgende fase.
- De fleste af vores salgsmuligheder er i det østlige område.
- Store salgsmuligheder genererer større indtægt end mellemstore eller små muligheder.
- Store partneraftaler genererer større indtægt: 8 millioner $ i gennemsnit i forhold til 6 millioner $ for direkte salg.

Da indsatsen for at få en aftale i hus er den samme, uanset om aftalen er klassificeret som stor, mellemstor eller lille, bør vores virksomhed analysere dataene for at få mere viden om de store muligheder.

1. I det arbejdsområde, hvor du har gemt eksemplet, skal du åbne fanen **Dashboards** og derefter finde og vælge dashboardet **Eksempel på analyse af salgsmuligheder**.

2. Vælg feltet **Antal salgsmuligheder efter partnerdrevet og salgsfase** felt for at åbne den første side i rapporten Eksempel på analyse af salgsmuligheder. 

    ![Feltet Antal salgsmuligheder efter partnerdrevet og salgsfase](media/sample-opportunity-analysis/opportunity2.png)

## <a name="explore-the-pages-in-the-report"></a>Gransk siderne i rapporten

Få hver enkelt side i rapporten vist ved at vælge sidefanerne forneden.

### <a name="opportunity-count-overview-page"></a>Siden Oversigt over antal salgsmuligheder
![Siden Antal salgsmuligheder](media/sample-opportunity-analysis/opportunity3.png)

Bemærk følgende oplysninger:
* East er vores største område med hensyn til antallet af salgsmuligheder.  
* Vælg et område ad gangen på cirkeldiagrammet **Antal salgsmuligheder efter område** for at filtrere siden efter det pågældende område. For alle områder kan du se, at partnere forfølger markant flere store muligheder.   
* Søjlediagrammet **Antal salgsmuligheder efter partnerdrevet og salgsmulighedsstørrelse** viser, at de fleste af de store salgsmuligheder er partnerdrevet, og flere af de små og mellemstore muligheder ikke er.
* I det liggende søjlediagram **Antal salgsmuligheder efter salgsfase** kan du vælge en **Salgsfase** ad gangen for at se forskellen i antal for de forskellige områder. Bemærk, at selvom det østlige område har det største antal salgsmuligheder, har alle tre områder sammenlignelige antal i salgsfaserne Løsning, Tilbud og Færdiggør. Det betyder, at der lukkes en højere procentdel af aftalerne i det centrale og vestlige område.

### <a name="revenue-analysis-page"></a>Siden Indtægtsanalyse
Denne side ser på dataene på en lignende måde, men anvender et indtægtsperspektiv i stedet for at tage udgangspunkt i antal.  

![Siden Oversigt over indtægt](media/sample-opportunity-analysis/opportunity4.png)

Bemærk følgende oplysninger:
* Det østlige område er ikke blot det største område, hvad angår antallet af salgsmuligheder, men også hvad angår indtægt.  
* Hvis du filtrerer diagrammet **Indtægt efter Salgsfase og Partnerdrevet** ved at vælge **Ja** for **Partnerdrevet**, kan du se en indtægt på 1,5 milliarder $ og en indregnet indtægt på 294 millioner $. Sammenlign disse beløb med de 644 millioner $ og 166 millioner $ for ikke-partnerdrevet indtægt. 
* Den gennemsnitlige indtægt for store konti er på 8 millioner, hvis muligheden er partnerdrevet, og dermed større i sammenligning med de 6 millioner for ikke-partnerdrevet forretning.  
* For partnerdrevet forretning er den gennemsnitlige indtægt for store muligheder næsten dobbelt så stor som for mellemstore muligheder.  
* Gennemsnitlige indtægter for små og mellemstore virksomheder er sammenlignelige for både partnerdrevet og ikke-partnerdrevet forretning.   

Det er tydeligt, at partnere er bedre end ikke-partnere til at sælge til kunderne. Det kan give mening at gennemføre flere handler via vores partnere.

### <a name="opportunity-count-by-region-and-stage"></a>Antal salgsmuligheder efter område og fase
Denne side i rapporten ser på dataene på en lignende måde som på den forrige side, men opdeler dem efter område og fase. 

![Siden Optælling af trin per område](media/sample-opportunity-analysis/opportunity5.png)

Bemærk følgende oplysninger:
* Hvis du vælger **Øst** i cirkeldiagrammet **Antal salgsmuligheder efter område** for at filtrere efter det østlige område, kan du se, at salgsmulighederne i dette område næsten er fordelt ligeligt mellem partnerdrevet og ikke-partnerdrevet.
* Store salgsmuligheder er mest almindelige i det centrale område, små salgsmuligheder er mest almindelige i det østlige område, og mellemstore salgsmuligheder er mest almindelige i det vestlige område.

### <a name="upcoming-opportunities-by-month-page"></a>Siden Kommende salgsmuligheder efter Måned
På denne side ser vi igen på lignende faktorer, men denne gang fra et dato og klokkeslæt-perspektiv. 
 
![Siden Kommende salgsmuligheder](media/sample-opportunity-analysis/opportunity6.png)

Vores CFO bruger denne side til at administrere arbejdsbyrde. Ved at se på indtægtsmulighederne efter salgsfase og måned kan vedkommende planlægge i forhold til dette.

Bemærk følgende oplysninger:
* Den gennemsnitlige indtægt for fasen Færdiggør er den højeste. Det har højeste prioritet at lukke disse handler.
* Hvis du filtrerer efter måned (ved at vælge en måned i udsnittet **Måned**), kan du se, at januar har en høj andel af store aftaler i salgsfasen Færdiggør med indregnet indtægt på 75 millioner $. Februar har på den anden side hovedsageligt mellemstore aftaler i salgsfaserne Løsning og Tilbud.
* Tallene for indregnede indtægter varierer generelt baseret på salgsfase, antal muligheder og handlens størrelse. Tilføj filtre for disse faktorer ved hjælp af ruden **Filter** til højre for at få yderligere indsigt.

## <a name="next-steps-connect-to-your-data"></a>Næste trin: Opret forbindelse til dine data
Det er sikkert at eksperimentere i dette miljø, fordi du kan vælge ikke at gemme dine ændringer. Hvis du gemmer dem, kan du altid vælge **Hent data** for at få en ny kopi af dette eksempel.

Vi håber, at denne rundtur har vist, hvordan Power BI-dashboards, spørgsmål og svar samt rapporter kan give indsigt i eksempeldata. Nu er det din tur: Opret forbindelse til dine egne data. Med Power BI kan du oprette forbindelse til en lang række datakilder. Få mere at vide ved at se [Introduktion til Power BI-tjenesten](../fundamentals/service-get-started.md).
