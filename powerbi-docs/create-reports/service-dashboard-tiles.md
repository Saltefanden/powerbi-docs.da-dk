---
title: Introduktion til dashboardfelter for Power BI-designere
description: I denne artikel beskrives dashboardfelter i Power BI, hvilket omfatter felter, der er oprettet fra rapporter i SQL Server Reporting Services (SSRS).
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 04/17/2020
LocalizationGroup: Dashboards
ms.openlocfilehash: 56f00568b22d236b498446065cf97ff565993e7a
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96418231"
---
# <a name="intro-to-dashboard-tiles-for-power-bi-designers"></a>Introduktion til dashboardfelter for Power BI-designere

Et felt er et snapshot af dine data, der er fastgjort til dashboardet. Et felt kan oprettes ud fra en rapport, et datasæt, et dashboard, feltet Spørgsmål og svar, Excel og SSRS-rapporter (SQL Server Reporting Services) med flere.  Dette skærmbillede viser mange forskellige felter, der er fastgjort til et dashboard.

![Power BI-dashboard](media/service-dashboard-tiles/power-bi-dashboard.png)

Dashboards og dashboardfelter er en funktion i Power BI-tjenesten ikke Power BI Desktop. Du kan ikke oprette dashboards på mobilenheder, men du kan [få vist og dele](../consumer/mobile/mobile-apps-view-dashboard.md) dem der.

Ud over fastgørelse af felter kan du oprette separate felter direkte på dashboardet ved hjælp af kontrolelementet [Tilføj felt](service-dashboard-add-widget.md). Separate felter omfatter: tekstfelter, billeder, videoer, streamingdata og webindhold.

Har du brug for hjælp til at forstå de komponenter, der udgør Power BI? Se [Grundlæggende begreber for designere i Power BI-tjenesten](../fundamentals/service-basic-concepts.md).

> [!NOTE]
> Hvis den oprindelige visualisering, der blev brugt til at oprette feltet, ændres, er det ikke tilfældet med feltet.  Hvis du f.eks. har fastgjort et kurvediagram fra en rapport, og du derefter har ændret kurvediagrammet til et søjlediagram, fortsætter dashboardfeltet med at vise et kurvediagram. Dataene opdateres, men visualiseringstypen bliver ikke.
> 
> 

## <a name="pin-a-tile"></a>Fastgør et felt
Der er mange forskellige måder at føje (fastgøre) et felt til et dashboard på. Du kan fastgøre felter fra:

* [Power BI Spørgsmål og svar](service-dashboard-pin-tile-from-q-and-a.md)
* [En rapport](service-dashboard-pin-tile-from-report.md)
* [Et andet dashboard](service-pin-tile-to-another-dashboard.md)
* [Excel-projektmappe på OneDrive for Business](service-dashboard-pin-tile-from-excel.md)
* [Quick Insights (Hurtig indsigt)](service-insights.md)
* [En sideinddelt rapport i det lokale miljø i Power BI-rapportserver eller SQL Server Reporting Services](/sql/reporting-services/pin-reporting-services-items-to-power-bi-dashboards)

Du kan oprette separate felter til billeder, tekstfelter, videoer, streamingdata og webindhold direkte på dashboardet ved hjælp af kontrolelementet [Tilføj felt](service-dashboard-add-widget.md).

  ![Ikonet Tilføj felt](media/service-dashboard-tiles/add_widgetnew.png)

## <a name="interact-with-tiles-on-a-dashboard"></a>Interager med felter på et dashboard
Når du har føjet et felt til et dashboard, kan du flytte og tilpasse størrelsen af det eller ændre dets udseende og funktionsmåde.

### <a name="move-and-resize-a-tile"></a>Flyt og tilpas størrelsen på et felt
Tag et felt, og [flyt det rundt på dashboardet](service-dashboard-edit-tile.md). Hold over håndtaget ![Felthåndtag](media/service-dashboard-tiles/resize-handle.jpg), og vælg det, for at tilpasse størrelsen af feltet.

### <a name="hover-over-a-tile-to-change-the-appearance-and-behavior"></a>Peg på et felt for at ændre udseende og funktionalitet
1. Hold over feltet for at få vist ellipsen.
   
    ![Feltets ellipse](media/service-dashboard-tiles/ellipses_new.png)
2. Vælg ellipsen for at åbne menuen med felthandlinger.
   
    ![Ikon for ellipse](media/service-dashboard-tiles/power-bi-tile-menu.png)
   
    Herfra kan du:
   
     * [Føj kommentarer til dashboardet](../consumer/end-user-comment.md).
     * [Åbn den rapport, der blev brugt til at oprette dette felt](../consumer/end-user-reports.md).  
     * [Se i fokuseringstilstand](../consumer/end-user-focus.md).   
     * [Eksportér de data, der bruges i feltet](../visuals/power-bi-visualization-export-data.md).
     * [Rediger titlen og undertitlen, og tilføj et link](service-dashboard-edit-tile.md). 
     * [Kør indsigt](service-insights.md). 
     * [Fastgør feltet til et andet dashboard](service-pin-tile-to-another-dashboard.md).
     * [Slet feltet](service-dashboard-edit-tile.md).

3. Vælg et tomt område på dashboardet for at lukke handlingsmenuen.

### <a name="select-a-tile"></a>Vælg et felt
Når du vælger et felt, afhænger næste handling af, hvordan du oprettede feltet. Ellers vil valget af feltet føre dig til rapporten, Excel Online-projektmappen, Reporting Services-rapporten i det lokale miljø eller spørgsmålet i Spørgsmål og svar. Hvis der er et [brugerdefineret link](service-dashboard-edit-tile.md), føres du til linket, når du vælger feltet.

> [!NOTE]
> En undtagelse er videofelter, der er oprettet direkte på dashboardet ved hjælp af **Tilføj felt**. Hvis du vælger et videofelt (der blev oprettet på denne måde), afspilles videoen direkte på dashboardet.   
> 
> 

## <a name="considerations-and-troubleshooting"></a>Overvejelser og fejlfinding

* Hvis den rapport, der blev brugt til at oprette visualiseringen, ikke blev gemt, sker der ikke noget, når feltet vælges.
* Hvis feltet blev oprettet vha. en projektmappe i Excel Online, skal du som minimum have læserettigheder til den pågældende projektmappe. Ellers åbnes projektmappen ikke i Excel Online, hvis du vælger feltet.
* Lad os sige, at du opretter et felt direkte på dashboardet ved hjælp af **Tilføj felt** og angiver et brugerdefineret link for det. Hvis du gør det, åbnes den pågældende URL-adresse, når du vælger titlen, undertitlen eller feltet. Ellers sker der som standard ingenting, når du vælger et felt, der er oprettet direkte på dashboardet for et billede, en webkode eller et tekstfelt.
* Felter kan oprettes fra sideinddelte rapporter i det lokale miljø i Power BI-rapportserver eller SQL Server Reporting Services. Hvis du ikke har tilladelse til at tilgå rapporten i det lokale miljø, bliver du ført til en side, der angiver, at du ikke har adgang, når du vælger feltet (rsAccessDenied).
* Lad os sige, at du vælger et felt, der er oprettet fra en sideinddelt rapport i det lokale miljø i Power BI-rapportserver eller SQL Server Reporting Services. Hvis du ikke har adgang til netværket, hvor rapportserveren er placeret, bliver du ført til en side, der angiver, at serveren ikke blev fundet (HTTP 404), når du vælger et felt. Enheden skal have netværksadgang til rapportserveren, for at du kan få vist rapporten.
* Selvom den oprindelige visualisering, der blev brugt til at oprette feltet, bliver ændret, så ændres feltet ikke. Hvis du f.eks. fastgør et kurvediagram fra en rapport og derefter ændrer kurvediagrammet til et søjlediagram, fortsætter dashboardfeltet med at vise et kurvediagram. Dataene opdateres, men det gør visualiseringstypen ikke.

## <a name="next-steps"></a>Næste trin
- [Opret et kort (felt med stort tal) til dit dashboard](../visuals/power-bi-visualization-card.md)
- [Introduktion til dashboards for Power BI-designere](service-dashboards.md)  
- [Opdatering af data i Power BI](../connect-data/refresh-data.md)
- [Grundlæggende begreber for designere i Power BI-tjenesten](../fundamentals/service-basic-concepts.md)
- [Integrering af Power BI-felter i Office-dokumenter](https://powerbi.microsoft.com/blog/integrating-power-bi-tiles-into-office-documents/)
- [Fastgør Reporting Services-elementer til Power BI-dashboards](/sql/reporting-services/pin-reporting-services-items-to-power-bi-dashboards)

Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/).