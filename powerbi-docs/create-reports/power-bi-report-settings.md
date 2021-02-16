---
title: Skift indstillinger for Power BI-rapporter
description: Skift indstillinger for rapporter i Power BI-tjenesten
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 10/14/2020
LocalizationGroup: Reports
ms.openlocfilehash: 996c4a1e7b2bdda0bfdfa0951afc7922b2996084
ms.sourcegitcommit: 00e3eb2ec4f18d48a73cfd020bb42d08e859ad06
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/16/2021
ms.locfileid: "100531556"
---
# <a name="change-settings-for-power-bi-reports"></a>Skift indstillinger for Power BI-rapporter

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-desktop](../includes/yes-desktop.md)] [!INCLUDE [yes-service](../includes/yes-service.md)]

Med rapportindstillingerne i Power BI Desktop og Power BI-tjenesten kan du styre, hvordan læserne af rapporten interagerer med din rapport. Du kan f.eks. give dem tilladelse til at gemme filtre for rapporten, tilpasse visualiseringerne i rapporten eller få vist rapportsiderne som faner nederst i rapporten i stedet for ude i siden.

:::image type="content" source="media/power-bi-report-settings/service-report-settings-pane.png" alt-text="Skærmbillede af ruden Indstillinger for rapporten i Power BI-tjenesten.":::

Det kan være nyttigt at læse disse artikler først:

- [Opret en rapport i Power BI-tjenesten ved at importere et datasæt](service-report-create-new.md) for at forstå oprettelsesprocessen for rapporten.
- [Rapporter i Power BI](../consumer/end-user-reports.md) for at forstå, hvilken oplevelse læserne af din rapport får.

 Så lad os starte.

## <a name="prerequisites"></a>Forudsætninger

- Se [Desktop-rapportvisning](desktop-report-view.md) for at se, hvordan du opretter rapporter ved hjælp af Power BI Desktop.
- [Tilmeld dig Power BI-tjenesten](../fundamentals/service-self-service-signup-for-power-bi.md). 
- Du skal have redigeringstilladelser til rapporten i Power BI-tjenesten. Du kan finde flere oplysninger om tilladelser under [Roller i de nye arbejdsområder](../collaborate-share/service-new-workspaces.md#roles-in-the-new-workspaces).
- Hvis du ikke allerede har en rapport i Power BI-tjenesten, kan du [installere et eksempel på en indholdspakke](sample-datasets.md#install-built-in-content-packs), der indeholder et dashboard, en rapport og et datasæt.

## <a name="open-the-settings-pane-in-power-bi-desktop"></a>Åbn ruden Indstillinger i Power BI Desktop

1. Vælg **Fil** > **Indstillinger** > **Indstillinger**.
1. Under **Aktuel fil** skal du vælge **Rapportindstillinger**.

    :::image type="content" source="media/power-bi-report-settings/desktop-report-settings-pane.png" alt-text="Skærmbillede af ruden Indstillinger for rapporten i Power BI Desktop":::

    Resten af denne artikel omhandler nogle af de specifikke rapportindstillinger.

## <a name="open-the-settings-pane-in-the-power-bi-service"></a>Åbn ruden Indstillinger i Power BI-tjenesten

1. Vælg **Filer** > **Indstillinger** i Læsevisning i rapporten.

    :::image type="content" source="media/power-bi-report-settings/service-report-file-settings.png" alt-text="Skærmbillede af menuen Filer til Indstillinger.":::

1. I ruden **Indstillinger** kan du se et antal til/fra-knapper, som du kan angive, kun for denne rapport. Resten af denne artikel omhandler nogle af dem.

## <a name="set-featured-content"></a>Angiv udvalgt indhold

Du kan udvælge dashboards, rapporter og apps, så de vises i afsnittet Udvalgte på dine kollegers Power BI Start-side. Læs mere om, [hvordan du udvælger indhold](../collaborate-share/service-featured-content.md).

## <a name="set-the-pages-pane"></a>Angiv ruden Sider

I øjeblikket kan du kun ændre indstillingen for ruden Sider i Power BI-tjenesten. Når du slår **ruden Sider** til, ser læserne af rapporten faner med rapportsider nederst i rapporten i Læsevisning i stedet for ude i siden. I Redigeringsvisning er fanerne med rapportsiderne allerede nederst i rapporten.

:::image type="content" source="media/power-bi-report-settings/report-settings-pages-pane.png" alt-text="Skærmbillede af indstilling af ruden Sider.":::

## <a name="control-filters"></a>Styring af filtre

Ruden **Indstillinger** i rapporten indeholder tre indstillinger til styring af læsernes interaktioner med filtrene for din rapport. De følgende links går til [formatet Filtrer i Power BIs rapport](power-bi-report-filter.md) artikel for at få oplysninger om de enkelte indstillinger.

- **Faste filtre** giver læserne mulighed for at [gemme filtre for rapporten](power-bi-report-filter.md#allow-saving-filters).
- **Filtreringsoplevelse** har to indstillinger mere:
    
    Giv læserne af rapporten tilladelse til at [ændre filtertyperne](power-bi-report-filter.md#restrict-changes-to-filter-type).

    Aktivér [søgning i filterruden](power-bi-report-filter.md#filters-pane-search).

## <a name="export-data"></a>Eksportér data

[Læserne af rapporten kan som standard eksportere opsummerede eller underliggende data](../consumer/end-user-export.md) fra visualiseringer i din rapport. Med **Eksportér data** kan du give dem tilladelse til kun at eksportere opsummerede data eller ingen data fra din rapport.

## <a name="personalize-visuals"></a>Tilpas visualiseringer

Giv læserne tilladelse til at ændre og tilpasse visualiseringer i din rapport. Læs mere om, hvordan du giver [læserne af rapporten tilladelse til at tilpasse visualiseringer](power-bi-personalize-visuals.md).

## <a name="next-steps"></a>Næste trin

* [Udvælg indhold på andres startsider](../collaborate-share/service-featured-content.md)
* [Giv læserne af rapporten tilladelse til at tilpasse visualiseringer i en rapport](power-bi-personalize-visuals.md)
* Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
