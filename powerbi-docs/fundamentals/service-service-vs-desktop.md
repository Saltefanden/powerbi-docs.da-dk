---
title: Sammenligning af Power BI Desktop og Power BI-tjenesten
description: Power BI Desktop er et komplet værktøj til dataanalyse og oprettelse af rapporter. Power BI-tjenesten er en cloudbaseret onlinetjeneste til let redigering af rapporter og samarbejde mellem teams og virksomheder.
author: maggiesMSFT
ms.reviewer: ''
featuredvideoid: IkJda4O7oGs
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/07/2020
ms.author: maggies
LocalizationGroup: Reports
ms.openlocfilehash: 0b4a1275a3b50fbadd37d953b77316d6021c800c
ms.sourcegitcommit: 37bd34053557089c4fbf0e05f78e959609966561
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 11/10/2020
ms.locfileid: "94397087"
---
# <a name="comparing-power-bi-desktop-and-the-power-bi-service"></a>Sammenligning af Power BI Desktop og Power BI-tjenesten

I et Venn-diagram, der sammenligner Power BI Desktop og Power BI-tjenesten, viser området i midten, hvordan de to overlapper hinanden. Nogle opgaver kan du foretage i enten Power BI Desktop eller tjenesten. De to sider af Venn-diagrammet viser de funktioner, der er unikke for programmet og for tjenesten.  

![Venn-diagram, der viser forholdet mellem Power BI Desktop og Power BI-tjenesten.](media/service-service-vs-desktop/power-bi-venn-desktop-service.png)

**Power BI Desktop** er et komplet værktøj til dataanalyse og rapportoprettelse, som du installerer gratis på din lokale computer. Det omfatter Forespørgselseditor, hvor du kan oprette forbindelse til mange forskellige datakilder og kombinere dem (også kaldet modellering) i en datamodel. Derefter designer du en rapport, der er baseret på den pågældende datamodel. I [Introduktionsvejledning til Power BI Desktop](desktop-getting-started.md) gennemgås processen.

**Power BI-tjenesten** er en cloudbaseret tjeneste. Den understøtter let rapportredigering og samarbejde for teams og organisationer. Du kan også oprette forbindelse til datakilder i Power BI-tjenesten, men mulighederne for modellering er begrænsede.

De fleste designere af Power BI-rapporter, der arbejder på business intelligence-projekter, bruger **Power BI Desktop** til at oprette Power BI-rapporter og bruger derefter **Power BI-tjenesten** til samarbejde om og distribution af deres rapporter.

Power BI-tjenesten hoster også *sideinddelte rapporter* i arbejdsområder, der understøttes af en Power BI Premium-kapacitet. Du opretter sideinddelte rapporter med Power BI Report Builder. Se [Sammenlign Power BI-rapporter og sideinddelte rapporter](../paginated-reports/paginated-reports-report-builder-power-bi.md#compare-power-bi-reports-and-paginated-reports) i artiklen "Hvad er sideinddelte rapporter i Power BI Premium?" for at få flere oplysninger.

## <a name="editing-power-bi-reports"></a>Redigering af Power BI-rapporter

Du kan oprette og redigere Power BI- *rapporter* i både programmet og tjenesten. En rapport kan have en eller flere sider med visualiseringer og samlinger af visualiseringer. Tilføj bogmærker, knapper, filtre og detaljeadgang for at forbedre navigationen i dine rapporter.

![Skærmbilleder af Power BI Desktop og Power BI-tjenesten med nummererede afsnit.](media/service-service-vs-desktop/power-bi-editing-desktop-service.png)

Rapporteditorerne i Power BI Desktop og i tjenesten er ens. De består af tre sektioner:  

1. De øverste navigationsruder, der ikke er de samme i Power BI Desktop og tjenesten    
2. Rapportcanvasset     
3. Ruderne **Felter** , **Visualiseringer** og **Filtre**

Denne video viser rapporteditoren i Power BI Desktop. 

<iframe width="560" height="315" src="https://www.youtube.com/embed/IkJda4O7oGs" frameborder="0" allowfullscreen></iframe>

## <a name="working-in-the-power-bi-service"></a>Arbejde i Power BI-tjenesten

### <a name="collaborating"></a>Samarbejde

Når du har oprettet dine rapporter, kan du gemme dem i et *arbejdsområde* i **Power BI-tjenesten** , hvor du og dine kolleger kan samarbejde. Du kan bygge *dashboards* oven på disse rapporter. Derefter deler du disse dashboards og rapporter med brugere af rapporter i og uden for din organisation. Brugerne af rapporterne får dem vist i Power BI-tjenesten i en *læsevisning* ikke redigeringsvisning. De har ikke adgang til alle de funktioner, der er tilgængelige for oprettere af rapporter.  Du kan også dele dine datasæt og lade andre bygge deres egne rapporter ud fra dem. Læs mere om [samarbejde i Power BI-tjenesten](../collaborate-share/service-new-workspaces.md).

### <a name="self-service-data-prep-with-dataflows"></a>Selvbetjent dataforberedelse med dataflow

Dataflows hjælper virksomheder med at samle data fra forskellige kilder og forberede dem til modellering. Analytikere kan nemt oprette dataflows ved hjælp af velkendte værktøjer til selvbetjening. Analytikere bruger dataflows til at indsamle, transformere, integrere og forbedre big data ved at definere datakildeforbindelser, ETL-logik, opdatere tidsplaner og meget mere. Læs mere om [selvbetjent dataforberedelse med dataflows](../transform-model/dataflows/dataflows-introduction-self-service.md).

## <a name="next-steps"></a>Næste trin

[Hvad er Power BI Desktop?](desktop-what-is-desktop.md)

[Opret en rapport](../create-reports/service-report-create-new.md) i Power BI-tjenesten

[De grundlæggende begreber for rapportdesignere](service-basic-concepts.md)

Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)