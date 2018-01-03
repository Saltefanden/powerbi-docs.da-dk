---
title: Tabelvisualiseringer i Power BI-rapporter og -dashboards (selvstudium)
description: Tip til at arbejde med tabelvisualiseringer i Power BI-rapporter og dashboards, herunder, hvordan du tilpasser kolonnebredder.
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: 
qualityfocus: 
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/27/2017
ms.author: mihart
ms.openlocfilehash: e4a2e162ca193af756e7182fb118bc7e72d38d28
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 11/13/2017
---
# <a name="working-with-tables-in-power-bi-reports-and-dashboards-tutorial"></a>Arbejd med tabeller i Power BI-rapporter og -dashboards (selvstudium)
En tabel er et gitter, der indeholder relaterede data i logiske serier af rækker og kolonner. Den kan også indeholde overskrifter og en række til totaler. Tabeller fungerer godt med kvantitative sammenligninger, hvor du får vist mange værdier for en enkelt kategori. Denne tabel viser for eksempel fem forskellige målinger for **Category**.

![](media/power-bi-visualization-tables/table.png)

## <a name="when-to-use-a-table"></a>Du skal bruge en tabel, til at
Tabeller er et godt valg til at:

* Se og sammenligne detaljerede data og nøjagtige værdier (i stedet for visuelle repræsentationer).
* Se data i tabelformat.
* Se numeriske data efter kategorier.   

> [!NOTE]
> Hvis en tabel indeholder for mange værdier, kan du overveje at konvertere den til en matrix og/eller bruge detailudledning.
> 
> 

## <a name="create-a-table"></a>Opret en tabel
Hvis du selv vil følge med i trinnene i dette selvstudium, skal du logge på Power BI og vælge **Hent data > Eksempler > Eksempel på detailhandelsanalyse**. I selvstudiet kan du oprette den tabel, der vises herover, for at få vist salgsværdierne efter varekategori.

1. Vælg fanen Datasæt under **Mit arbejdsområde**, og rul ned til datasættet Detailhandelsanalyse, som du lige har tilføjet.  Vælg ikonet **Opret rapport**.
   
    ![](media/power-bi-visualization-tables/power-bi-create-report.png)
2. Vælg **Item** > **Category** i rapporteditoren.  Power BI opretter automatisk en tabel over alle kategorierne.
   
    ![](media/power-bi-visualization-tables/power-bi-table1.png)
3. Vælg **Sales > Average Unit Price**, **Sales > Last Year Sales** og **Sales > This Year Sales**, og vælg alle tre indstillinger (Value, Goal, Status).   
4. Find **Værdier** i ruden Visualiseringer, og træk og slip værdierne, indtil rækkefølgen af diagramkolonnerne stemmer overens med det første billede på denne side.  Du skulle nu se følgende under Værdier.
   
    ![](media/power-bi-visualization-tables/power-bi-table2.png)
5. Fastgør tabellen til dashboardet ved at vælge ikonet med tavlenålen  
   
     ![](media/power-bi-visualization-tables/pbi_pintile.png)

## <a name="format-the-table"></a>Formatér tabellen
Der er mange måder, hvorpå du kan formatere en tabel, og jeg beskriver kun nogle få af dem her. Hvis du vil vide mere om andre formateringsindstillinger, kan du åbne ruden Format (ikonet med malerullen ![](media/power-bi-visualization-tables/power-bi-format.png)) og prøve dig frem.

* Prøv at formatere tabelgitteret. Her har jeg tilføjet et blåt lodret gitter, tilføjet mellemrum mellem rækkerne og forstørret kanten og tekststørrelsen en smule.
  
    ![](media/power-bi-visualization-tables/power-bi-table-grid2-new.png)
  
    ![](media/power-bi-visualization-tables/power-bi-table-grid3.png)
* I kolonneoverskrifterne har jeg ændret baggrundsfarven, tilføjet en kant og øget skriftstørrelsen. 
  
    ![](media/power-bi-visualization-tables/power-bi-table-column.png)
  
    ![](media/power-bi-visualization-tables/power-bi-table-column2.png)
* Efter lidt yderligere formatering ser den endelige tabel sådan ud. Da der er så mange formateringsindstillinger, kan det være en god idé at starte med en almindelig tabel, åbne ruden Formatering ![](media/power-bi-visualization-tables/power-bi-format.png) og så ellers prøve dig frem. 
  
    ![](media/power-bi-visualization-tables/power-bi-table-format.png)

### <a name="conditional-formatting"></a>Betinget formatering
Der findes en type formatering, der kaldes *betinget formatering*, og den anvendes på felterne under **Værdier** i ruden **Visualiseringer** i Power BI-tjenesten eller Power BI Desktop. 

Med betinget formatering af tabeller kan du angive brugerdefinerede baggrundsfarver og skriftfarver for celler baseret på celleværdier, bl.a. ved hjælp af gradueringsfarver. 

1. Vælg den nedadvendte pil ud for den værdi under **Værdier** i ruden **Visualiseringer** i Power BI-tjenesten eller Power BI Desktop, du vil formatere (eller højreklik på feltet). Du kan kun administrere betinget formatering for felter i området **Værdier** under **Felter**.
   
    ![](media/power-bi-visualization-tables/power-bi-conditional-formatting-background.png)
2. Vælg **Baggrundsfarveskalaer**. Du kan konfigurere farven og *Minimum*- og *Maksimum*-værdierne i den dialogboks, der vises. Hvis du vælger feltet **Divergerende**, kan du også konfigurere en valgfri værdi af typen *Centreret*.
   
    ![](media/power-bi-visualization-tables/power-bi-conditional-formatting-background2.png)
   
    Jeg vil prøve at anvende brugerdefineret formatering til Average Unit Price-værdierne. Vælg **Divergerende**, tilføj nogle farver, og vælg **OK**. 
   
    ![](media/power-bi-visualization-tables/power-bi-conditional-formatting-data-background.png)
3. Tilføj et nyt felt i tabellen, der har både positive og negative værdier.  Vælg **Sales > Total Sales Variance**. 
   
    ![](media/power-bi-visualization-tables/power-bi-conditional-formatting2.png)
4. Tilføj betinget formatering for datalinjen ved at vælge den nedadvendte pil ud for **Total Sales Variance** og vælge **Betinget formatering > Datalinjer**.
   
    ![](media/power-bi-visualization-tables/power-bi-conditional-formatting-data-bars.png)
5. I den viste dialogboks kan du angive farver for **Positiv streg**, **Negativ streg**, markere afkrydsningsfeltet **Vis kun streg** og foretage eventuelle andre ændringer.
   
    ![](media/power-bi-visualization-tables/power-bi-data-bars.png)
   
    Når du vælger **OK**, erstatter datalinjerne de numeriske værdier i tabellen, så den er nemmere at skimme.
   
    ![](media/power-bi-visualization-tables/power-bi-conditional-formatting-data-bars2.png)
6. Hvis du vil fjerne betinget formatering fra en visualisering, skal du blot højreklikke på feltet igen og vælge **Fjern betinget formatering**.

> [!TIP]
> Du kan også angive betinget formatering i ruden Format (ikonet med malerullen). Vælg den værdi, du vil formatere, og angiv derefter **Farveskalaer** eller **Datalinjer** til Til for at anvende standardindstillingerne. Hvis du vil tilpasse indstillingerne, skal du vælge **Avancerede kontrolelementer**.
> 
> 

## <a name="adjust-the-column-width-of-a-table"></a>Tilpas kolonnebredden i en tabel
Nogle gange kan Power BI afskære en kolonneoverskrift i en rapport og på et dashboard. Hvis du vil kunne se hele kolonnenavnet, skal du pege på mellemrummet til højre for overskriften for at få vist dobbeltpilene og klikke og trække.

![](media/power-bi-visualization-tables/resizetable.gif)

Har du flere spørgsmål? [Prøv Power BI-community'et](http://community.powerbi.com/)
