---
title: 'Eksempel på analyse af it-forbrug til Power BI: Få en introduktion'
description: 'Eksempel på analyse af it-forbrug til Power BI: Få en introduktion'
author: maggiesMSFT
ms.author: maggies
ms.reviewer: amac
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: conceptual
ms.date: 07/05/2019
LocalizationGroup: Samples
ms.openlocfilehash: cdde0e702333feed54637c72fa3193052fde139f
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96414961"
---
# <a name="it-spend-analysis-sample-for-power-bi-take-a-tour"></a>Eksempel på analyse af it-forbrug til Power BI: Få en introduktion

Indholdspakken til analysen af it-forbruget indeholder et dashboard, en rapport og et datasæt, der analyserer de planlagte omkostninger i forhold til de faktiske omkostninger i en it-afdeling. Sammenligningen hjælper os med at forstå, om virksomheden har lagt en god plan for året, og giver os mulighed for at undersøge de områder, som afviger væsentligt fra planen. Virksomheden i eksemplet gennemgår en årlig planlægningscyklus og genererer et nyt 'Seneste estimat' (Latest Estimate, LE) hvert kvartal for at gøre det nemmere at analysere ændringer i it-forbruget i løbet af regnskabsåret.

![Dashboard for eksemplet IT Spend Analysis](media/sample-it-spend/it1.png)

Dette eksempel er en del af en serie, der viser, hvordan du kan bruge Power BI med forretningsrelaterede data, rapporter og dashboards. Det blev oprettet af [obviEnce](http://www.obvience.com/) med rigtige data, som er blevet anonymiseret. Dataene er tilgængelige i flere formater: indholdspakke, .pbix-fil til Power BI Desktop eller Excel-projektmappe. Se [Eksempler til Power BI](sample-datasets.md). 

I dette selvstudium udforskes indholdspakken med eksemplet på analyse af it-forbrug i Power BI-tjenesten. Da rapportoplevelsen i Power BI Desktop og i tjenesten minder meget om hinanden, kan du også følge med ved at bruge .pbix-eksempelfilen i Power BI Desktop. 

Du behøver ikke en Power BI-licens for at udforske eksemplerne i Power BI Desktop. Hvis du ikke har en Power BI Pro-licens, kan du gemme eksemplet i Mit arbejdsområde i Power BI-tjenesten. 

## <a name="get-the-sample"></a>Hent eksemplet

 Før du kan bruge eksemplet, skal du først downloade det som en [indholdspakke](#get-the-content-pack-for-this-sample), [.pbix-fil](#get-the-pbix-file-for-this-sample) eller [Excel-projektmappe](#get-the-excel-workbook-for-this-sample).

### <a name="get-the-content-pack-for-this-sample"></a>Hent indholdspakken for dette eksempel

1. Åbn Power BI-tjenesten (app.powerbi.com), log på, og åbn det arbejdsområde, hvor du vil gemme eksemplet.

   Hvis du ikke har en Power BI Pro-licens, kan du gemme eksemplet i Mit arbejdsområde.

2. Vælg **Hent data** i nederste venstre hjørne.
   
   ![Vælg Hent data](media/sample-datasets/power-bi-get-data.png)
3. På siden **Hent data**, der vises, skal du vælge **Eksempler**.
   
4. Vælg **IT Spend Analysis Sample**, og vælg **Opret forbindelse**.  
  
   ![Opret forbindelse til eksempel](media/sample-it-spend/it-connect.png)
   
5. Power BI importerer indholdspakken og føjer derefter et nyt dashboard, en rapport og datasæt til dit aktuelle arbejdsområde.
   
   ![Post i IT Spend Analysis Sample](media/sample-it-spend/it-spend-analysis-sample-entry.png)
  
### <a name="get-the-pbix-file-for-this-sample"></a>Hent .pbix-filen knyttet til dette eksempel

Du kan også hente eksemplet IT Spend Analysis som en [.pbix-fil](https://download.microsoft.com/download/E/9/8/E98CEB6D-CEBB-41CF-BA2B-1A1D61B27D87/IT%20Spend%20Analysis%20Sample%20PBIX.pbix), som er beregnet til brug med Power BI Desktop.

### <a name="get-the-excel-workbook-for-this-sample"></a>Hent Excel-projektmappen for dette eksempel

Hvis du vil have vist datakilden for dette eksempel, er den også tilgængelig som en [Excel-projektmappe](https://go.microsoft.com/fwlink/?LinkId=529783). Projektmappen indeholder Power View-ark, som du kan få vist og redigere. Hvis du vil se rådataene, skal du aktivere tilføjelsesprogrammerne Dataanalyse og derefter vælge **Power Pivot > Administrer**. Hvis du vil aktivere tilføjelsesprogrammerne Power View og Power Pivot, kan du finde flere oplysninger under [Udforsk Excel-eksemplerne i Excel](sample-datasets.md#explore-excel-samples-inside-excel).

## <a name="it-spend-analysis-sample-dashboard"></a>Dashboardet IT Spend Analysis Sample
De to talfelter til venstre for dashboardet, **Var Plan %** og **Variance Latest Estimate % Quarter 3**, giver os et overblik over, hvor godt vi klarer os i forhold til planen og i forhold til estimatet for det seneste kvartal (LE3 = Latest Estimate Quarter 3). Samlet set er vi omtrent 6 % fra planen. Lad os undersøge årsagen til denne varians: hvornår, hvor og hvilken kategori.

## <a name="ytd-it-spend-trend-analysis-page"></a>Siden YTD IT Spend Trend Analysis
Når du vælger dashboardfeltet **Var Plan % by Sales Region**, vises siden **YTD IT Spend Trend Analysis** i rapporten IT Spend Analysis Sample. Vi kan hurtigt se, at vi har positiv varians i USA og Europa og negativ varians i Canada, Latinamerika og Australien. USA havde ca. 6 % +LE-varians, og Australien har ca. 7 % -LE-varians.

![Variansplan i % efter salgsområde](media/sample-it-spend/it2.png)

Men det kan være vildledende kun at kigge på dette diagram og udlede konklusioner. Vi er nødt til at se på de faktiske dollarbeløb for at få tingene i det rette perspektiv.

1. Vælg **Aus and NZ** i diagrammet **Var Plan % by Sales Region**, og hold så øje med diagrammet **Var Plan by IT Area**.

   ![Siden YTD IT Spend Trend Analysis](media/sample-it-spend/it3.png)
2. Vælg nu **USA**. Bemærk, at Australien og New Zealand er en meget lille del af vores samlede forbrug sammenlignet med USA.

    Lad os nu undersøge, hvilken kategori i USA der er skyld i variansen.

## <a name="ask-questions-of-the-data"></a>Stil spørgsmål til dataene
1. Vælg **Eksempel på analyse af it-forbrug** i den øverste navigationsrude for at vende tilbage til eksempeldashboardet.
2. Vælg **Stil et spørgsmål om dine data**.
3. På listen **Spørgsmål, som kan hjælpe dig i gang** til venstre skal du vælge **hvad er planen efter it-område**.

   ![Diagrammet Plan by IT Area](media/sample-it-spend/it-area-chart.png)

4. I feltet Spørgsmål og svar skal du rydde den forrige post og skrive *show IT areas, var plan % and var le3 % bar chart*.

   ![Diagrammet Var Plan % and Var LE3 % by IT Area](media/sample-it-spend/it4.png)

   I det første it-område **Infrastructure** kan du se, at procentdelen er ændret drastisk mellem den første variansplan og variansplanens seneste estimat.

## <a name="ytd-spend-by-cost-elements-page"></a>Siden YTD Spend by Cost Elements

1. Vend tilbage til dashboardet, og kig på dashboardfeltet **Variance Plan %, Variance Latest Estimate % - Quarter 3**.

   ![Feltet Var Plan %, Var LE3](media/sample-it-spend/it5.png)

   Bemærk, at området Infrastructure skiller sig ud med en stor positiv varians i forhold til planen.

1. Vælg dette felt til at åbne rapporten og se siden **YTD Spend by Cost Elements**.
2. Vælg bjælken **Infrastructure** i diagrammet **Var Plan % and Var LE3 % by IT Area** nederst til højre, og hold øje med værdivariansen i forhold til planen i diagrammet **Var Plan % by Sales Region** nederst til venstre.

    ![Siden YTD Spend by Cost Elements](media/sample-it-spend/it6.png)
3. Vælg de enkelte navne hver for sig i udsnittet **Cost Element Group** for at finde omkostningselementet med den største varians.
4. Når **Other** er valgt, skal du vælge **Infrastructure** i udsnittet **IT Area** og vælge underområderne i udsnittet **IT Sub Area** for at finde underområdet med den største varians.  

   Læg mærke til den store varians for **Networking**. Firmaet har tilsyneladende valgt at give medarbejderne telefonitjenester som et frynsegode, men dette træk var ikke planlagt.

## <a name="plan-variance-analysis-page"></a>Siden Plan Variance Analysis

1. Vælg fanen **Plan Variance Analysis** nederst på siden.

2. I diagrammet **Var Plan and Var Plan % by Business Area** til venstre skal du vælge kolonnen **Infrastructure** for at fremhæve infrastrukturværdier for forretningsområdet på resten af siden.

    ![Siden Plan Variance Analysis](media/sample-it-spend/it7.png)

   I diagrammet **Var plan % by Month and Business Area** skal du lægge mærke til, at forretningsområdet for infrastrukturen har startet en positiv varians i februar. Læg også mærke til, hvordan værdien for varians i forhold til planen for forretningsområdet varierer afhængigt af land, sammenlignet med alle andre forretningsområder. 

3. Brug udsnittene **IT Area** og **IT Sub Areas** til højre til at filtrere værdierne på resten af siden og til at udforske dataene. 

## <a name="edit-the-report"></a>Rediger rapporten
Vælg **Rediger rapport** i det øverste venstre hjørne for at udforske den i redigeringsvisning:

* Se, hvordan siderne er oprettet – felterne i de enkelte diagrammer og filtrene på siderne.
* Tilføj sider og diagrammer baseret på de samme data.
* Skift til en anden type visualisering for hvert diagram.
* Fastgør diagrammer, du er interesseret i, til dit dashboard.

## <a name="next-steps-connect-to-your-data"></a>Næste trin: Opret forbindelse til dine data
Det er sikkert at eksperimentere i dette miljø, fordi du kan vælge ikke at gemme dine ændringer. Hvis du gemmer dem, kan du altid vælge **Hent data** for at få en ny kopi af dette eksempel.

Vi håber, at denne rundtur har vist, hvordan Power BI-dashboards, spørgsmål og svar samt rapporter kan give indsigt i eksempeldata. Nu er det din tur: Opret forbindelse til dine egne data. Med Power BI kan du oprette forbindelse til en lang række datakilder. Få mere at vide ved at se [Introduktion til Power BI-tjenesten](../fundamentals/service-get-started.md).
