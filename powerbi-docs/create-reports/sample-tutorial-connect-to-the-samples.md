---
title: Udforsk Eksempel på detailhandelsanalyse
description: Få mere at vide om, hvordan du installerer og udforsker Eksempel på detailhandelsanalyse i Power BI-tjenesten og Power BI Desktop.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: amac
ms.custom: seodec18
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: conceptual
ms.date: 03/27/2020
LocalizationGroup: Samples
ms.openlocfilehash: 87296ca881550180ec62262def3aff44eead956b
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96395722"
---
# <a name="explore-the-retail-analysis-sample"></a>Udforsk Eksempel på detailhandelsanalyse

I denne vejledning lærer du, hvordan du kan: 
- Importér indholdspakken Eksempel på detailanalyse, føj den til Power BI-tjenesten og åbn indholdet. En *indholdspakke* er en eksempeltype, hvor datasættet er pakket sammen med et dashboard og en rapport. 
- Åbn .PBIX-filen med Eksempel på detailhandelsanalyse i Power BI Desktop.

Hvis du gerne vil have flere baggrundsoplysninger, kan du se [Eksempeldatasæt til Power BI](sample-datasets.md). I den artikel lærer du alt om eksemplerne. Hvordan du får fat i dem, hvor du gemmer dem, hvordan du bruger dem og nogle af de historier, som hvert eksempel fortæller. 

## <a name="prerequisites"></a>Forudsætninger
Eksemplerne er tilgængelige for Power BI-tjenesten og Power BI Desktop. Hvis du vil følge med, skal du bruge Eksempel på detailhandelsanalyse.

Indholdspakke med eksemplet *Retail Analysis*, der bruges i dette selvstudium, består af et dashboard, en rapport og et datasæt.
Lær denne indholdspakke og dens scenarie at kende ved at se [Eksempel på detailhandelsanalyse til Power BI: Få en præsentation](sample-retail-analysis.md), før du går i gang.

## <a name="import-the-sample-in-the-power-bi-service"></a>Importér eksemplet i Power BI-tjenesten

1. Åbn Power BI-tjenesten (app.powerbi.com), log på, og åbn det arbejdsområde, hvor du vil gemme eksemplet. 

    Hvis du ikke har en Power BI Pro-licens, kan du gemme eksemplet i Mit arbejdsområde.

2. Vælg **Hent data** nederst i navigationsruden. 

   ![Vælg Hent data](media/sample-datasets/power-bi-get-data.png)

   Hvis du ikke kan se **Hent data**, kan du udvide navigationsruden ved at vælge følgende ikon øverst i ruden: ![hamburgerikon](media/sample-tutorial-connect-to-the-samples/expand-nav.png).

5. På siden **Hent data**, der vises, skal du vælge **Eksempler**.
   
6. Vælg **Eksempel på detailhandelsanalyse**, og vælg derefter **Opret forbindelse**.   
   
   ![Knappen Opret forbindelse](media/sample-tutorial-connect-to-the-samples/pbi_retailanalysissampleconnect.png)

## <a name="what-was-imported"></a>Hvad er importeret?
Når du bruger indholdspakkerne med eksempler og vælger **Opret forbindelse**, henter Power BI en kopi af indholdspakken og gemmer den for dig i cloudmiljøet. Eftersom den person, der oprettede indholdspakken, inkluderede et datasæt, en rapport og et dashboard, er det, det du får, når du vælger **Opret forbindelse**. 

1. Når du vælger **Opret forbindelse**, opretter Power BI det nye dashboard og viser det på fanen **Dashboards**. 
   
   ![Posten Eksempel på detailhandelsanalyse](media/sample-retail-analysis/retail-entry.png)
2. Åbn fanen **Rapporter**. Her kan du se en ny rapport med navnet *Detailhandelsanalyse*.
   
   ![Rapporten Detailhandelsanalyse](media/sample-tutorial-connect-to-the-samples/power-bi-new-report.png)
   
   Tjek fanen **Datasæt**. Her er der også et nyt datasæt.
   
   ![Datasættet Detailhandelsanalyse](media/sample-tutorial-connect-to-the-samples/power-bi-new-dataset.png)

## <a name="explore-your-new-content"></a>Udforsk dit nye indhold
Udforsk nu dashboardet, datasættet og rapporten på egen hånd. Der er mange forskellige måder at navigere til dine dashboards, rapporter og datasæt på. En af disse måder er beskrevet i følgende procedure.  

1. Naviger tilbage til fanen **Dashboards**, og vælg dashboardet **Detailhandelsanalyse** for at åbne det.       

   Dashboardet åbnes og indeholder en række visualiseringsfelter.   
 
1. Vælg et af felterne i dashboardet for at åbne den underliggende rapport. I dette eksempel vælger vi områdediagrammet **Dette års salg, sidste års salg efter regnskabsmåned**.  

   ![Dashboardet Detailhandelsanalyse, hvor en visualisering er fremhævet](media/sample-tutorial-connect-to-the-samples/power-bi-dashboards2new.png)

   Rapporten åbnes på den side, der indeholder det områdediagram, du har valgt. I dette tilfælde siden **Månedligt salg pr. distrikt** i rapporten.
   
   ![Rapportsiden Månedligt salg pr. distrikt](media/sample-tutorial-connect-to-the-samples/power-bi-report.png)
   
   > [!NOTE]
   > Hvis feltet blev oprettet ved hjælp af [Spørgsmål og svar i Power BI](power-bi-tutorial-q-and-a.md), åbnes siden Spørgsmål og svar i stedet for. Hvis feltet er [fastgjort fra Excel](service-dashboard-pin-tile-from-excel.md), åbnes Excel Online i Power BI.
   > 
   > 
1. Når en person deler en indholdspakke med kolleger, ønsker de typisk at dele indsigt og ikke give deres kolleger adgang til dataene. På fanen **Datasæt** har du flere muligheder for at udforske dit datasæt. Du kan dog ikke få vist rækkerne og kolonnerne i dine data, som du kan i Power BI Desktop eller Excel. 
   
   ![Datasættet Detailhandelsanalyse](media/sample-tutorial-connect-to-the-samples/power-bi-new-dataset.png)
   
1. En af måderne til at udforske datasættet er ved at oprette dine egne visualiseringer og rapporter fra bunden. Vælg ikonet Diagram ![Ikonet Diagram](media/sample-tutorial-connect-to-the-samples/power-bi-chart-icon4.png) for at åbne datasættet i rapportredigeringstilstand.
     
   ![Helt ny rapport](media/sample-tutorial-connect-to-the-samples/power-bi-report-editing.png)

1. En anden måde at udforske datasættet på er ved at køre [Hurtig indsigt](../consumer/end-user-insights.md). Vælg **Flere indstillinger** (...), og vælg derefter **Få hurtigt indsigt**. Vælg **Vis indsigt**, når indsigten er klar.
     
    ![Rapporten Indsigt](media/sample-tutorial-connect-to-the-samples/power-bi-insights.png)

## <a name="download-the-sample-in-power-bi-desktop"></a>Hent eksemplet til Power BI Desktop 
Når du åbner PBIX-eksempelfilen for første gang i Power BI Desktop, vises den i Rapportvisning, hvor du kan udforske, oprette og redigere et vilkårligt antal rapportsider med visualiseringer. Med Rapportvisning får du næsten samme designoplevelse som i Redigeringsvisning af en rapport i Power BI-tjenesten. Du kan f.eks. flytte visualiseringer rundt og kopiere, indsætte og flette dem. 

I modsætning til redigering af en rapport i Power BI-tjenesten kan du i Power BI Desktop arbejde med dine forespørgsler og modellere dine data for at sikre, at dataene giver den bedste indsigt i dine rapporter. Du kan derefter gemme din Power BI Desktop-fil et sted efter eget valg, uanset om det er på dit lokale drev eller i cloudmiljøet.

1. Download [PBIX-filen Eksempel på detailhandelsanalyse](https://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix), og åbn den i Power BI Desktop. 

    ![Eksempel i Rapportvisning i Power BI](media/sample-tutorial-connect-to-the-samples/power-bi-samples-desktop.png)

1. Filen åbnes i Rapportvisning. Læg mærke til de fire faner nederst i rapporteditoren. Disse faner repræsenterer de fire sider i denne rapport. Siden **Nye butikker** er i dette eksempel markeret i øjeblikket. 

    ![Fanen Nye butikker fremhævet](media/sample-tutorial-connect-to-the-samples/power-bi-sample-tabs.png).

1. Hvis du vil have en detaljeret gennemgang af rapporteditoren, skal du se [Få en præsentation af rapporteditoren](service-the-report-editor-take-a-tour.md).

## <a name="whats-in-your-report"></a>Hvad er der i din rapport?
Når du downloader en PBIX-fil med et eksempel, har du ikke blot downloadet *en rapport*, men også det underliggende datasæt. Når du åbner filen, indlæser Power BI Desktop dataene med de tilknyttede forespørgsler og relationer. Du kan få vist de underliggende data og relationer, men du kan ikke få vist de underliggende forespørgsler i Forespørgselseditoren.


1. Skift til [Datavisning](../connect-data/desktop-data-view.md) ved at vælge ![tabelikonet](media/sample-tutorial-connect-to-the-samples/power-bi-data-icon.png).
 
    ![Visningen Data i Desktop](media/sample-tutorial-connect-to-the-samples/power-bi-desktop-sample-data.png)

    I Datavisning kan du undersøge, udforske og forstå data i din Power BI Desktop-model. Det er forskelligt fra den måde, du får vist tabeller, kolonner og data på i Forespørgselseditor. Dataene i Datavisning er allerede indlæst i modellen.

    Når du udformer dine data, har du nogle gange brug for at se, hvad der rent faktisk findes i rækkerne og kolonnerne i en tabel uden at skulle oprette et visual på rapportlærredet. Dette er særligt tilfældet, når du opretter målinger og beregnede kolonner, eller du har brug for at identificere en datatype eller datakategori.

1. Skift til [Relationsvisning](../transform-model/desktop-relationship-view.md) ved at vælge følgende ikon: ![Ikonet Relationsvisning](media/sample-tutorial-connect-to-the-samples/power-bi-desktop-relationship-icon.png).
 
    ![Relationsvisning i Power BI Desktop](media/sample-tutorial-connect-to-the-samples/power-bi-relationships.png)

    I Relationsvisning vises alle tabellerne, kolonnerne og relationerne i din model. Her kan du få vist, redigere og oprette relationer.

## <a name="next-steps"></a>Næste trin
Det er sikkert at eksperimentere i dette miljø, fordi du kan vælge ikke at gemme dine ændringer. Hvis du gemmer dem, kan du altid vælge **Hent data** for at få en ny kopi af dette eksempel.

Vi håber, at denne præsentation har vist, hvordan dashboards, datasæt, relationer og rapporter i Power BI kan give indsigt i eksempeldata. Nu er det din tur: Opret forbindelse til dine egne data. Med Power BI kan du oprette forbindelse til en lang række datakilder. Du kan få mere at vide i [Introduktion til Power BI-tjenesten](../fundamentals/service-get-started.md) og [Introduktion til Power BI Desktop](../fundamentals/desktop-getting-started.md).  

Her finder du flere oplysninger:  
- [Grundlæggende begreber for designere i Power BI-tjenesten](../fundamentals/service-basic-concepts.md)
- [Eksempler til Power BI-tjenesten](sample-datasets.md)
- [Datakilder til Power BI](../connect-data/service-get-data.md)

Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
