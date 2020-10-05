---
title: Opret forbindelse til Power BI Premium Capacity Metrics
description: Sådan får og installerer du skabelonappen Power BI Premium Capacity Metrics, og sådan opretter du forbindelse til data
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: how-to
ms.date: 05/18/2020
ms.author: painbar
LocalizationGroup: Connect to services
ms.openlocfilehash: 42526dbae857c6488fe129cc7781672691782de1
ms.sourcegitcommit: 02b5d031d92ea5d7ffa70d5098ed15e4ef764f2a
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 09/26/2020
ms.locfileid: "91375229"
---
# <a name="connect-to-power-bi-premium-capacity-metrics"></a>Opret forbindelse til Power BI Premium Capacity Metrics

Overvågning af dine kapaciteter er afgørende for at træffe beslutninger om den bedste måde, du kan udnytte dine ressourcer i Premium-kapaciteten på. Appen Power BI Premium Capacity Metrics giver de mest detaljerede oplysninger om ydeevnen af dine kapaciteter.

![Rapport i appen Power BI Premium Capacity Metrics](media/service-connect-to-pbi-premium-capacity-metrics/service-pbi-premium-capacity-metrics-app-report.png)

Denne artikel indeholder en beskrivelse af, hvordan du installerer appen og opretter forbindelse til datakilder. Du kan finde oplysninger om indholdet af rapporter, og hvordan du bruger det i [Overvåg Premium-kapaciteter med appen](../admin/service-admin-premium-monitor-capacity.md) og i [blogindlægget om appen Premium Capacity Metrics](https://powerbi.microsoft.com/blog/premium-capacity-metrics-app-new-health-center-with-kpis-to-explore-relevant-metrics-and-steps-to-mitigate-issues/).

Når du har installeret appen og oprettet forbindelse til datakilderne, kan du tilpasse rapporten til dine behov. Du kan derefter distribuere den til kolleger i organisationen.

> [!NOTE]
> Installation af skabelonapps kræver [tilladelser](./service-template-apps-install-distribute.md#prerequisites). Kontakt din Power BI-administrator, hvis du oplever, at du ikke har tilstrækkelige tilladelser.

## <a name="install-the-app"></a>Installér programmet

1. Klik på følgende link for at få adgang til appen: [Skabelonappen Power BI Premium Capacity Metrics](https://app.powerbi.com/groups/me/getapps/services/pbi_pcmm.capacity-metrics-dxt)

1. Vælg [**Hent den nu**](https://app.powerbi.com/groups/me/getapps/services/pbi_pcmm.capacity-metrics-dxt) på AppSource-siden for appen.

    [![Appen Power BI Premium Capacity Metrics i AppSource](media/service-connect-to-pbi-premium-capacity-metrics/service-pbi-premium-capacity-metrics-app-appsource-get-it-now.png)](https://app.powerbi.com/groups/me/getapps/services/pbi_pcmm.capacity-metrics-dxt)

1. Vælg **Installér**. 

    ![Installér appen Power BI Premium Capacity Metrics](media/service-connect-to-pbi-premium-capacity-metrics/service-pbi-premium-capacity-metric-select-install.png)

    > [!NOTE]
    > Hvis du tidligere har installeret appen, bliver du spurgt, om du vil [overskrive denne installation](./service-template-apps-install-distribute.md#update-a-template-app) eller installere i et nyt arbejdsområde.

    Når appen er installeret, kan du se den på siden med dine apps.

   ![Appen Power BI Premium Capacity Metrics på siden App](media/service-connect-to-pbi-premium-capacity-metrics/service-pbi-premium-capacity-metrics-app-apps-page-icon.png)

## <a name="connect-to-data-sources"></a>Opret forbindelse til datakilder

1. Vælg ikonet på siden med apps for at åbne appen.

1. På velkomstskærmen skal du vælge **Udforsk**.

   ![Velkomstskærmbilledet for skabelonappen](media/service-connect-to-pbi-premium-capacity-metrics/service-pbi-premium-capacity-metrics-app-splash-screen.png)

   Appen åbnes, og der vises eksempeldata.

1. Vælg linket **Opret forbindelse til dine data** på banneret øverst på siden.

   ![Appen Power BI Premium Capacity Metrics opretter forbindelse til dit datalink](media/service-connect-to-pbi-premium-capacity-metrics/service-pbi-premium-capacity-metrics-app-connect-data.png)

1. I den viste dialogboks skal du angive UTC-forskydningen, dvs. den forskel i timer, der er mellem Coordinated Universal Time og din tidszone. Klik derefter på **Next** (Næste).
  
   ![UTC-dialogboksen i appen Power BI Premium Capacity Metrics](media/service-connect-to-pbi-premium-capacity-metrics/service-pbi-premium-capacity-metrics-app-setutc-dialog.png)
   **Bemærk: Til angivelse af halve timer anvendes decimalformatet (f.eks. 5,5 og 2,5).**

1. I den næste dialogboks, der vises, behøver du ikke at foretage dig noget. Du skal blot vælge **Log på**.

   ![Godkendelsesdialogboksen i appen Power BI Premium Capacity Metrics](media/service-connect-to-pbi-premium-capacity-metrics/service-pbi-premium-capacity-metrics-app-authentication-dialog.png)

1. Log på Power BI, når du er logget på Microsoft.

   ![Microsoft-logonskærmbillede](media/service-connect-to-pbi-premium-capacity-metrics/service-pbi-premium-capacity-metrics-app-microsoft-login.png)

   Når du har logget på, opretter rapporten forbindelse til datakilderne og udfyldes med opdaterede data. Aktivitetsovervågningen aktiveres i dette tidsrum.

   ![Opdatering i gang i appen Power BI Premium Capacity Metrics](media/service-connect-to-pbi-premium-capacity-metrics/service-pbi-premium-capacity-metrics-app-refresh-monitor.png)

   Dine rapportdata opdateres automatisk én gang om dagen, medmindre du deaktiverede dette under logonprocessen. Du kan også [konfigurere din egen opdateringsplan](./refresh-scheduled-refresh.md) for at holde rapportdataene opdateret, hvis du vil.

## <a name="customize-and-share"></a>Tilpas og del

Klik på blyantikonet i øverste højre hjørne for at begynde at tilpasse appen.

 ![Ikonet Rediger](media/service-connect-to-pbi-premium-capacity-metrics/service-pbi-premium-capacity-metrics-app-customize.png)

Se [Tilpas og del appen](./service-template-apps-install-distribute.md#customize-and-share-the-app) for at få flere oplysninger.

## <a name="next-steps"></a>Næste trin
* [Overvåg Premium-kapaciteter vha. appen](../admin/service-admin-premium-monitor-capacity.md)
* [Blogindlæg om appen Premium Capacity Metrics](https://powerbi.microsoft.com/blog/premium-capacity-metrics-app-new-health-center-with-kpis-to-explore-relevant-metrics-and-steps-to-mitigate-issues/)
* [Hvad er Power BI-skabelonapps?](./service-template-apps-overview.md)
* [Installér og distribuer skabelonapps i din organisation](./service-template-apps-install-distribute.md)
* Har du spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)