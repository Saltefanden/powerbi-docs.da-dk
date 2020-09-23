---
title: Opret en sideinddelt rapport til Power BI-rapportserver
description: Få mere at vide om, hvordan du opretter en sideinddelt rapport for Power BI-rapportserver med nogle få hurtige trin.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: how-to
ms.date: 01/07/2020
ms.author: maggies
ms.openlocfilehash: cf205603a4807b814e56904151e0ce8db66cfab1
ms.sourcegitcommit: 9350f994b7f18b0a52a2e9f8f8f8e472c342ea42
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 09/22/2020
ms.locfileid: "90853534"
---
# <a name="create-a-paginated-report-for-power-bi-report-server"></a>Opret en sideinddelt rapport til Power BI-rapportserver
I denne artikel kan du oprette en sideinddelt rapport for Power BI-rapportserver med nogle få hurtige trin.

Leder du efter hjælp til oprettelse af sideinddelte rapporter i Report Builder til Power BI-tjenesten? Se i stedet [Power BI Report Builder](../paginated-reports/report-builder-power-bi.md).

Som navnet antyder så kan sideinddelte rapporter løbe op i mange sider. De er udformet i et fast format og tillader præcis tilpasning. Sideinddelte rapporter er .rdl-filer.

Du kan gemme og administrere sideinddelte rapporter på Power BI-rapportserverens webportal nøjagtigt som på SQL Server Reporting Services (SSRS)-webportalen. Du kan oprette og redigere dem i Report Builder eller Rapportdesigner i SQL Server Data Tools (SSDT) og derefter publicere dem på den ene eller anden portal. Derefter kan rapportlæsere i din organisation få vist dem i en browser eller i en Power BI-mobilapp på en mobilenhed.

![Power BI-rapportserverens sideinddelte rapport](media/quickstart-create-paginated-report/reportserver-paginated-report.png)

Hvis du allerede har oprettet sideinddelte rapporter i Report Builder eller Rapportdesigner, så er du klar til at oprette sideinddelte rapporter for Power BI-rapportserveren. Hvis det ikke er tilfældet, får du her nogle hurtige trin til at komme i gang.

## <a name="step-1-start-report-builder"></a>Trin 1: Start Power BI Report Builder
Du har muligvis allerede installeret Report Builder for at oprette rapporter for en SSRS-server. Du kan bruge den samme version eller Report Builder til at oprette rapporter for Power BI-rapportserveren. Hvis du ikke har installeret den, så er fremgangsmåden ret nem.

1. I Power BI-rapportserverens webportal skal du vælge **Ny** > **Sideinddelt rapport**.
   
    ![Menuen Ny sideinddelt rapport](media/quickstart-create-paginated-report/reportserver-new-paginated-report-menu.png)
   
    Hvis du ikke allerede har installeret Report Builder, bliver du ført gennem installationsprocessen nu.
2. Når installationen er udført, åbner skærmen **Ny rapport eller datasæt** i Report Builder.
   
    ![Skærmen Ny rapport eller datasæt](media/quickstart-create-paginated-report/reportserver-paginated-new-report-screen.png)
3. Vælg guiden, svarende til rapporttypen, som du vil oprette:
   
   * Tabel eller matrix
   * Diagram
   * Kort
   * Tom
4. Lad os starte med guiden Diagram.
   
    Guiden Diagram fører dig gennem den trinvise vejledning i at oprette et grundlæggende diagram i en rapport. Derfra har du adgang til næsten ubegrænsede tilpasningsmuligheder af rapporten.

## <a name="step-2-go-through-the-chart-wizard"></a>Trin 2: Gå gennem guiden Diagram
Guiden Diagram fører dig gennem en trinvis grundlæggende vejledning i at oprette en visualisering i en rapport.

Sideinddelte rapporter kan tilsluttes en lang række datakilder, fra Microsoft SQL Server og Microsoft Azure SQL Database til Oracle, Hyperion og meget mere. Læs om [datakilder, der understøttes af sideinddelte rapporter](connect-data-sources.md).

På den første side i guiden Diagram – **Vælg et datasæt**, du kan oprette et datasæt eller vælge et delt datasæt på en server. *Datasæt* returnerer rapportdata fra en forespørgsel på en ekstern datakilde.

1. Vælg **Gennemse** > vælg et delt datasæt på en server > **Åbn** > **Næste**.
   
    ![Guiden Diagram: Vælg et datasæt](media/quickstart-create-paginated-report/reportserver-paginated-choose-dataset.png)
   
     Vil du oprette et datasæt? Se [Opret et delt eller integreret datasæt](/sql/reporting-services/report-data/create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs).
2. Vælg en diagramtype – i dette tilfælde et søjlediagram.
   
    ![Guiden Diagram: Diagramtype](media/quickstart-create-paginated-report/reportserver-paginated-choose-chart-type.png)
3. Organiser felter ved at trække dem hen til felterne **Kategorier**, **Serie** og **Værdier**.
   
    ![Guiden Diagram: Arranger felter](media/quickstart-create-paginated-report/reportserver-paginated-arrange-fields.png)
4. Vælg **Næste** > **Afslut**.

## <a name="step-3-design-your-report"></a>Trin 3: Design rapporten
Du er nu i visningen Rapportdesign. Bemærk, at dataene er pladsholderdata, ikke dine data.

![Visningen Reportdesign](media/quickstart-create-paginated-report/reportserver-paginated-preview-report.png)

* Vælg **Kør** for at få vist dine data.
  
     ![Kør rapport](media/quickstart-create-paginated-report/reportserver-paginated-run-report.png)
* Vælg **Design** for at gå tilbage til Designvisning.

Du kan tilpasse diagrammet, du lige har oprettet, ændre layoutet, værdierne, forklaringen... ja, næsten alt.

Du kan desuden tilføje alle mulige andre forskellige visualiseringer: målere, tabeller, matrixer, tabeller, kort m.m. Du kan tilføje sidehoveder og sidefødder for adskillelige sider. Se [Report Builder-selvstudierne](/sql/reporting-services/report-builder-tutorials), og prøv dem selv.

![Designvisningen Report Builder](media/quickstart-create-paginated-report/reportserver-paginated-finished-design-report.png)

## <a name="step-4-save-your-report-to-the-report-server"></a>Trin 4: Gem din rapport på rapportserveren
Når rapporten er klar, kan du gemme den på Power BI-rapportserveren.

1. I menuen **Filer** skal du vælge **Gem som** og gemme den på rapportserver. 
2. Nu kan du se den i browseren.
   
    ![Sideinddelt rapport i browseren](media/quickstart-create-paginated-report/reportserver-paginated-report.png)

## <a name="next-steps"></a>Næste trin
Der er mange fantastiske ressourcer til design af rapporter i Report Builder og i Rapportdesigner i SQL Server Data Tools. Report Builder-selvstudier er et godt sted at starte.

* [Report Builder-selvstudier](/sql/reporting-services/report-builder-tutorials)
* [Hvad er Power BI-rapportserveren?](get-started.md)  

Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)