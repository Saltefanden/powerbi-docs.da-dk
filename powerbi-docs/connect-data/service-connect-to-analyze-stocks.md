---
title: Analysér populære lagre med Power BI
description: Analysér populære lagre med Power BI
author: paulinbar
ms.author: painbar
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: how-to
ms.date: 02/09/2021
LocalizationGroup: Connect to services
ms.openlocfilehash: 934451c06927237fd252d60102e2e5db73e31bc1
ms.sourcegitcommit: de3b45cad5ae21c77692ce4490e21de01d21e6f3
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/10/2021
ms.locfileid: "100082725"
---
# <a name="analyze-popular-stocks-with-power-bi"></a>Analysér populære lagre med Power BI

Appen aktie marked viser flere KPI'er, så du kan starte din Analytics-rejse i Power BI. Du kan bruge den til at spore de daglige tilbud samt ugentlige, månedlige eller årlige tendenser for populære lagre og ETFs. Appen viser dig, at du Power BI i praksis, med sporing af store mængder og laveste, glidende gennemsnit, sektor baseret distribution, Bollinger-bånd og endda sammenligning af ydeevne for populære lagre over tid.

Appen indeholder fire dashboards:
* **ETF-Dashboard**: viser, at du lukker trends for fire store indekser. 
* **Lager-og ETFs-sammenligning**: giver normaliserede diagrammer, som gør det nemt for dig at sammenligne aktier og EFTs.
* **Analyse af aktie performance**: muliggør detaljeret analyse af udvalgte lagre med visuelle elementer til lukning af tendenser, volumen, OHLC og Bollinger.
* **Fordeling i sektor –** det giver dig mulighed for at bryde aktieens ydeevne efter sektor.

Du kan navigere mellem dashboards ved hjælp af Navigationsside ruden eller fremad-og tilbage-pilene øverst til højre på siden.

![Skærmbillede af appen med lagre.](media/service-connect-to-analyze-stocks/stocks-app.png)

## <a name="etf-dashboard"></a>ETF-Dashboard

ETF-dashboardet har visuelle elementer, der viser luknings tendenser for fire store indekser. 
* **NASDAQ**: Nasdaq-sammensatte indeks måler ændringen i mere end 3.000 lagre, der handles på NASDAQ Exchange.
* **S&P 500**: s&p 500 anses for at være den bedste Equities med stor måleenhed i USA.
* **Dow Jones**: Dow Jones viser dig den markeds vækst, der er førende inden for branchen, f. eks. Microsoft. Den afsluttende tendens for Dow Jones betyder, at trends har de lagre, der er underlagt dette indeks, der har været lukket efter dagens afslutning.
* **Russell 2000**: Russel 2000 er den mest almindelige benchmark for gensidige fonde. Det visuelle element Russell 2000-luknings tendens kan bruges til at levere en investerings vejledning til mere end 2000 lave lagerplads.

Et kørende banner øverst på dashboardet viser, hvornår dags dato er lukket, og prisændringen fra de forrige dage er tæt på de fire indeks, der vises på siden.

Standardvisningen af Graph-visningen – hjælper dig med at forstå, hvor dramatisk tendensen har ændret sig over tid. Du kan bruge tidsskala knapperne øverst til venstre i dashboardet til at vælge at få vist tendensen for en uge, en måned eller et år. Hold markøren over diagrammet for at få det nøjagtige datapunkt på en bestemt dag.

![Skærmbillede af ETF Dashboard grafvisning.](media/service-connect-to-analyze-stocks/etf-dashboard-graph.png)  

På x-aksen kan du se tidsperioden, og på y-aksen kan du se slutværdien.

Du kan også skifte til et lysestage-diagram ved at klikke på til/fra-knappen øverst til højre på dashboardet. I lysestage-visning kan du se de åbne, højeste, laveste og sidste kurs for hvert datapunkt. Hold markøren over diagrammet for at få det nøjagtige datapunkt på en bestemt dag.

![Skærmbillede af ETF Dashboard lysestage View.](media/service-connect-to-analyze-stocks/etf-dashboard-candlestick.png)

## <a name="stocks-and-etfs-comparison"></a>Lagre og ETFs-sammenligning

Dashboardet for lager-og ETFs-sammenligning viser to normaliserede diagrammer, der gør det nemt at sammenligne valgte lagre og ETFs.

![Skærmbillede af dashboardet valg af aktie sammenlignings knap.](media/service-connect-to-analyze-stocks/stocks-comparison-dashboard.png)

Hvis du vil bruge denne side, skal du først vælge de beholdninger, du vil sammenligne. 
1. Klik på knappen **Vælg** knap  ![ på skærmbilledet Vælg knap på dashboardet for aktie sammenligning Ryd valg.](media/service-connect-to-analyze-stocks/stocks-comparison-dashboard-select.png)
1. På siden **Vælg lagre** , der vises, skal du klikke på **Ryd** for at fjerne eventuelle tidligere valg og derefter vælge de bestands, du vil sammenligne  ![ skærmbilledet af dashboardet for aktie sammenligning Select.](media/service-connect-to-analyze-stocks/stocks-comparison-dashboard-select-clear.png)
1. Klik på **Anvend**

Når du har valgt de aktier, du er interesseret i, kan du bruge rullepilen til at vælge de bestemte beholdninger, du vil sammenligne.

![Skærmbillede af dashboardet med aktie sammenligning Vælg rullelisten.](media/service-connect-to-analyze-stocks/stocks-comparison-dashboard-select-dropdown.png)

## <a name="stock-performance-analysis"></a>Analyse af aktie ydeevne

 Dashboardet til analyse af aktie performance viser dig vigtige KPI'ER om udvalgt lager, f. eks. den forrige dages lukning, lukning, åbning, høj og lav. Vælg rullelisten for at vælge det lager, du vil se, blandt de aktier, du har valgt til analyse. Du kan se, at værdien ændres, når du klikker på det lager, du vælger.

![Skærmbillede af analyse af aktie ydelse.](media/service-connect-to-analyze-stocks/stocks-performance-select.png)
 
### <a name="closing-trend"></a>Lukker tendens

Du kan se den afsluttende tendens for den valgte aktie, og du kan vælge at skifte til visningen månedsvisning eller år ved at klikke på knapperne øverst til venstre på siden. Hvis du har et år, får du hjælp til at se, hvor en del af året varer, der har fået tilført eller mistet værdi.

![Skærmbillede af luknings tendenser for udvalgte lagre](media/service-connect-to-analyze-stocks/stocks-performance-closing-trend.png)  

### <a name="volume"></a>Omfang

Du kan se den valgte lagermængde ved at rulle ned til næste visuelle element. Du kan holde musen til et tidsinterval for at se, hvor stor en del af året befinder sig.

![Skærmbillede af volumen af valgte lagre](media/service-connect-to-analyze-stocks/stocks-performance-volume.png)
 
### <a name="ohlc-chart"></a>OHLC-diagram

OHLC-diagrammer er meget nyttige, da de viser fire overordnede data Points for et bestemt lager på samme tid. Så i det næste visuelle element på siden kan du se OHLC-visualiseringen, hvor du får vist, hvordan du åbner, lukker, er høj og har lav den valgte lagerplads. Du kan også se dybere ud i dataene ved at ændre det glidende gennemsnit. 

![Skærmbillede af OHLC](media/service-connect-to-analyze-stocks/stocks-performance-ohlc.png)

### <a name="bollinger-band"></a>Bollinger-bånd

Bollinger-båndets brug komplekse matematik til at vise tendenserne. Du kan se et antal KPI-OHLC, som var i, og sammen med du kan se flere tre linjer. Den midterste linje viser det bevægelige gennemsnit. Den øverste linje flyttes op med et bestemt antal standardafvigelse, og den nederste linje flyttes ned med en standardafvigelse.

![Skærmbillede af Bollinger-bånd.](media/service-connect-to-analyze-stocks/stocks-performance-bollinger.png) 

## <a name="sectorwise-distribution"></a>Sectorwise-distribution

På siden sektor-års distribution kan du se de forskellige lagre og det marked, de hører til. Hvis du klikker på en af sektorerne, bliver lagerbeholdningerne filtreret fra, og de lagre, der hører til den valgte sektor, begynder at blive vist. 

![Skærmbillede af fordeling i sektoren.](media/service-connect-to-analyze-stocks/sector-wise-distribution.png)
 
Du kan derefter holde markøren over lageret for at se de vigtige KPI'ER, f. eks. tidligere lukning, lukning og forskel. Forskellen vil være en hjælp til at forstå, hvor meget lageret har fået eller mistet siden i går.

![Skærmbillede af detaljer om sektor baseret distribution.](media/service-connect-to-analyze-stocks/sector-wise-distribution-detail.png)

Du kan rulle ned for at se alle lagerbeholdninger i den pågældende kategori.
 
Hvis du vil se distributionen af marked for forskellige sektorer, har vi det visuelle element "sektor-top distribution", der viser oppefra og ned for de sektorer, der har den højeste forskel i deres slutkurs fra sidste dag.

![Skærmbillede af distribution af marked for forskellige sektorer](media/service-connect-to-analyze-stocks/stocks-comparison-based-on-sector.png)


## <a name="next-steps"></a>Næste trin

* [Hvad er Power BI skabelon apps](service-template-apps-overview.md)
* [Opret en skabelonapp i Power BI](service-template-apps-create.md)
* [Installér og distribuer skabelonapps i din organisation](service-template-apps-install-distribute.md)
* Har du spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
