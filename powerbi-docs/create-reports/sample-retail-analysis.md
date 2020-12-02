---
title: 'Eksempel på detailhandelsanalyse til Power BI: Få en introduktion'
description: 'Eksempel på detailhandelsanalyse til Power BI: Få en introduktion'
author: maggiesMSFT
ms.author: maggies
ms.reviewer: amac
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: conceptual
ms.date: 07/02/2019
LocalizationGroup: Samples
ms.openlocfilehash: 1a3a4bc467299f7baeb12ca68af1d2730d5839f0
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96395986"
---
# <a name="retail-analysis-sample-for-power-bi-take-a-tour"></a>Eksempel på detailhandelsanalyse til Power BI: Få en introduktion

Indholdspakken til eksemplet på detailhandelsanalyse indeholder et dashboard, en rapport og et datasæt, der analyserer data om detailsalg for varer, der er solgt på tværs af flere butikker og distrikter. I målepunkterne sammenlignes dette års resultat med sidste års inden for salg, enheder, bruttoavance og afvigelser samt analyse af nye butikker. 

![Dashboard til Eksempel på detailhandelsanalyse](media/sample-retail-analysis/retail1.png)

Dette eksempel er en del af en serie, der viser, hvordan du kan bruge Power BI med forretningsrelaterede data, rapporter og dashboards. Det blev oprettet af [obviEnce](http://www.obvience.com/) med rigtige data, som er blevet anonymiseret. Dataene er tilgængelige i flere formater: indholdspakke, .pbix-fil til Power BI Desktop eller Excel-projektmappe. Se [Eksempler til Power BI](sample-datasets.md). 

I dette selvstudium udforskes indholdspakken med eksemplet på detailhandelsanalysse i Power BI-tjenesten. Da rapportoplevelsen i Power BI Desktop og i tjenesten minder meget om hinanden, kan du også følge med ved at bruge .pbix-eksempelfilen i Power BI Desktop. 

Du behøver ikke en Power BI-licens for at udforske eksemplerne i Power BI Desktop. Hvis du ikke har en Power BI Pro-licens, kan du gemme eksemplet i Mit arbejdsområde i Power BI-tjenesten. 

## <a name="get-the-sample"></a>Hent eksemplet

 Før du kan bruge eksemplet, skal du først downloade det som en [indholdspakke](#get-the-content-pack-for-this-sample), [.pbix-fil](#get-the-pbix-file-for-this-sample) eller [Excel-projektmappe](#get-the-excel-workbook-for-this-sample).

### <a name="get-the-content-pack-for-this-sample"></a>Hent indholdspakken for dette eksempel

1. Åbn Power BI-tjenesten (app.powerbi.com), log på, og åbn det arbejdsområde, hvor du vil gemme eksemplet. 

    Hvis du ikke har en Power BI Pro-licens, kan du gemme eksemplet i Mit arbejdsområde.

2. Vælg **Hent data** i nederste venstre hjørne.

    ![Vælg Hent data](media/sample-datasets/power-bi-get-data.png)
3. På siden **Hent data**, der vises, skal du vælge **Eksempler**.
   
4. Vælg **Eksempel på detailhandelsanalyse**, og vælg derefter **Opret forbindelse**.  
  
   ![Opret forbindelse til eksempel](media/sample-retail-analysis/retail16.png)
   
5. Power BI importerer indholdspakken og føjer derefter et nyt dashboard, en ny rapport og et nyt datasæt til dit aktuelle arbejdsområde.
   
   ![Posten Eksempel på detailhandelsanalyse](media/sample-retail-analysis/retail-entry.png)
  
### <a name="get-the-pbix-file-for-this-sample"></a>Hent .pbix-filen knyttet til dette eksempel

Du kan også hente Eksempel på detailhandelsanalyse som en [.pbix-fil](https://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix), som er beregnet til brug med Power BI Desktop. 

### <a name="get-the-excel-workbook-for-this-sample"></a>Hent Excel-projektmappen for dette eksempel

Hvis du vil have vist datakilden for dette eksempel, er den også tilgængelig som en [Excel-projektmappe](https://go.microsoft.com/fwlink/?LinkId=529778). Projektmappen indeholder Power View-ark, som du kan få vist og redigere. Hvis du vil se rådataene, skal du aktivere tilføjelsesprogrammerne Dataanalyse og derefter vælge **Power Pivot > Administrer**. Hvis du vil aktivere tilføjelsesprogrammerne Power View og Power Pivot, kan du finde flere oplysninger under [Udforsk Excel-eksemplerne i Excel](sample-datasets.md#explore-excel-samples-inside-excel).

## <a name="start-on-the-dashboard-and-open-the-report"></a>Start på dashboardet, og åbn rapporten

1. I det arbejdsområde, hvor du har gemt eksemplet, skal du åbne fanen **Dashboards** og derefter finde og vælge dashboardet **Eksempel på detailhandelsanalyse**. 
2. På dashboardet skal du vælge feltet **Butikker i alt for nye og eksisterende butikker** t, som åbner siden **Oversigt over butikssalg** i rapporten Eksempel på detailhandelsanalyse. 

   ![Feltet Butikker i alt](media/sample-retail-analysis/retail-analysis-7.png)  

   På denne rapportside kan du se, at der er 104 butikker, heraf 10 nye. Vi har to kæder: Fashions Direct og Lindseys. Fashions Direct-butikkerne er gennemsnitligt større.
3. I cirkeldiagrammet **Dette års salg efter kæde** skal du vælge **Fashions Direct**.

   ![Diagrammet Dette års salg efter kæde](media/sample-retail-analysis/retail3.png)  

   Bemærk resultatet i boblediagrammet **Samlet salgsvarians i %** :

   ![Diagrammet Samlet salgsvarians i %](media/sample-retail-analysis/pbi_sample_retanlbubbles.png)  

   Distriktet **FD-01** har det største gennemsnitlige **Salg pr. kvm**, og FD-02 har den laveste **Samlet salgsvarians** sammenlignet med sidste år. FD-03 og FD-04 klarer sig dårligst samlet set.
4. Vælg individuelle bobler eller andre diagrammer for at se tværgående fremhævning, som viser effekten af dine valg.
5. Hvis du vil vende tilbage til dashboardet, skal du vælge **Eksempel på detailhandelsanalyse** i den øverste navigationsrude.

   ![Navigationslinje](media/sample-retail-analysis/power-bi-breadcrumbs.png)
6. På dashboardet, skal du vælge feltet **Dette års salg for nye og eksisterende butikker**, som er svarer til at skrive *Dette års salg* i feltet Spørgsmål og svar.

   ![Feltet Dette års salg](media/sample-retail-analysis/pbi_sample_retanlthisyrsales.png)

   Resultaterne i Spørgsmål og svar vises:

   ![Dette års salg i Spørgsmål og svar](media/sample-retail-analysis/retail7.png)

## <a name="review-a-tile-created-with-power-bi-qa"></a>Gennemgå et felt, der er oprettet med Spørgsmål og svar i Power BI
Lad os gå mere specifikt til værks.

1. Ret spørgsmålet til _dette års salg **efter distrikt**_ . Se resultatet: Spørgsmål og svar indsætter automatisk svaret i et liggende søjlediagram, og der foreslås andre sætninger:

   ![Dette års salg efter distrikt i Spørgsmål og svar](media/sample-retail-analysis/retail8.png)
2. Ret nu spørgsmålet til _dette års salg **efter postnummer og kæde**_ .

   Bemærk, hvordan Power BI besvarer spørgsmålet, mens du skriver, og viser det relevante diagram.
3. Eksperimentér med flere spørgsmål, og se, hvilken type resultater du får.
4. Når du er klar, kan du vende tilbage til dashboardet.

## <a name="dive-deeper-into-the-data"></a>Grav dybere ned i dataene
Lad os nu udforske på et mere detaljeret niveau, hvor vi ser på distrikternes præstationer.

1. På dashboardet skal du vælge feltet **Dette års salg, sidste års salg**, som åbner siden **Månedligt salg pr. distrikt** i rapporten.

   ![Feltet Dette års salg, sidste års salg](media/sample-retail-analysis/pbi_sample_retanlareacht.png)

   I diagrammel **Samlet salgsvarians i % efter regnskabsmåned** kan du se, at der er en stor variation i variansprocenten i forhold til sidste år, og at januar, april og juli var særligt dårlige måneder.

   ![Diagrammet Samlet salgsvarians i % efter regnskabsmåned](media/sample-retail-analysis/pbi_sample_retanlsalesvarcol.png)

   Lad os se, om vi kan indsnævre, hvor problemerne kan være.
2. I boblediagrammet skal du vælge boblen **020-Herrer**.

   ![Vælg 020-Herrer](media/sample-retail-analysis/retail11.png)  

   Bemærk, at herrernes kategori ikke var så alvorligt påvirket i april som det samlede forretningsresultat, men januar og juli var stadig problemmåneder.
1. Vælg nu boblen **010-Damer**.

   ![Vælg 010-Damer](media/sample-retail-analysis/retail12.png)

   Bemærk, at kvindernes kategori klarede sig meget dårligere end det samlede forretningsresultat på tværs af alle måneder og i næsten alle måneder i forhold til det foregående år.
1. Vælg boblen igen for at fjerne filteret.

## <a name="try-out-the-slicer"></a>Afprøv udsnittet
Lad os se på, hvordan bestemte distrikter klarer den.

1. Vælg **Allan Guinot** i udsnittet **Distriktschef** øverst til venstre.

   ![Vælg Allan Guinot](media/sample-retail-analysis/retail13.png)

   Bemærk, at Allans distrikt klarede sig bedre i marts og juni i forhold til sidste år.
2. Mens **Allan Guinot** stadig er markeret, skal du vælge boblen **010-Damer** i boblediagrammet.

   ![Allan Guinot og 010-Damer er valgt](media/sample-retail-analysis/power-bi-allan.png)

   Bemærk at for kategorien 010-Damer nåede Allans distrikt ikke samme mængde som sidste år.
3. Udforsk de andre distriktschefer og kategorier for at finde anden indsigt.
4. Når du er klar, skal du vende tilbage til dashboardet.

## <a name="what-the-data-says-about-sales-growth-this-year"></a>Hvad dataene fortæller om dette års salgsvækst
Det sidste område, vi vil udforske, er væksten. Dette gøres ved at undersøge de nye butikker, der åbnede i år.

1. Vælg feltet **Butikker åbnet i år efter åbningsmåned, kæde**, som åbner siden **Analyse af nye butikker** i rapporten.

   ![Siden Analyse af nye butikker](media/sample-retail-analysis/retail15.png)

   Som det fremgår af feltet, er der åbnet flere Fashions Direct-butikker end Lindseys-butikker i år.
2. Se nærmere på diagrammet **Salg pr. kvm efter navn**:

   ![Diagrammet Salg pr. kvm efter navn](media/sample-retail-analysis/retail14.png)

    Bemærk forskellen i gennemsnitligt salg pr. kvm på tværs af de nye butikker.
3. Vælg forklaringen **Fashions Direct** diagrammet **Antal åbne butikker efter åbningsmåned og kæde** øverst til højre. Bemærk, at den bedste butik (Winchester Fashions Direct), selv for den samme kæde, præsterer markant bedre end den værste butik (Cincinnati 2 Fashions Direct) med henholdsvis 21,22 $ ift. 12,86 $.

   ![Fashions Direct er valgt](media/sample-retail-analysis/power-bi-lindseys.png)
4. Vælg **Winchester Fashions Direct** i udsnittet **Navn**, og se nærmere på kurvediagrammet. De første salgstal blev rapporteret i februar.
5. Vælg **Cincinnati 2 Fashions Direct** i udsnittet, og se i kurvediagrammet, at den blev åbnet i juni og ser ud til at være den dårligst præsterende butik.
6. Udforsk diagrammerne ved at klikke på andre søjler, linjer og bobler, og se, hvilken indsigt du kan finde.

## <a name="next-steps-connect-to-your-data"></a>Næste trin: Opret forbindelse til dine data
Det er sikkert at eksperimentere i dette miljø, fordi du kan vælge ikke at gemme dine ændringer. Hvis du gemmer dem, kan du altid vælge **Hent data** for at få en ny kopi af dette eksempel.

Vi håber, at denne rundtur har vist, hvordan Power BI-dashboards, spørgsmål og svar samt rapporter kan give indsigt i eksempeldata. Nu er det din tur: Opret forbindelse til dine egne data. Med Power BI kan du oprette forbindelse til en lang række datakilder. Få mere at vide ved at se [Introduktion til Power BI-tjenesten](../fundamentals/service-get-started.md).
