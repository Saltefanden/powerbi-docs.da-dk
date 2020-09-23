---
title: Opret forbindelse til det områderelaterede dashboard til akutberedskab
description: Sådan henter og installerer du skabelonappen Dashboard til områderelateret akutberedskab i forbindelse med COVID-19, og sådan opretter du forbindelse til data
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: how-to
ms.date: 04/24/2020
ms.author: painbar
LocalizationGroup: Connect to services
ms.openlocfilehash: a6cb38d17a84ab41acda96f0564b12188c719254
ms.sourcegitcommit: 9350f994b7f18b0a52a2e9f8f8f8e472c342ea42
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 09/22/2020
ms.locfileid: "90860733"
---
# <a name="connect-to-the-regional-emergency-response-dashboard"></a>Opret forbindelse til det områderelaterede dashboard til akutberedskab
Det områderelaterede dashboard til akutberedskab er komponenten til rapportering i [Microsoft Power Platform-løsningen til områderelateret akutberedskab](/powerapps/sample-apps/regional-emergency-response/overview). Administratorer af regionale organisationer kan få vist dashboardet i deres Power BI-lejer, så de hurtigt kan få vist vigtige data og målepunkter, der kan hjælpe dem med at træffe effektive beslutninger.

![Rapport i appen Dashboard til områderelateret akutberedskab](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-report.png)

I denne artikel kan du se, hvordan du installerer appen Områderelateret akutberedskab, og hvordan du opretter forbindelse til datakilderne.

Du kan finde detaljerede oplysninger om, hvad der vises i dashboardet, under [Hent indsigt](/powerapps/sample-apps/regional-emergency-response/portals-admin-reporting#get-insights).

Når du har installeret skabelonappen og oprettet forbindelse til datakilderne, kan du tilpasse rapporten i henhold til dine behov. Du kan derefter distribuere den som en app til kolleger i organisationen.

## <a name="prerequisites"></a>Forudsætninger

Før du installerer denne skabelonapp, skal du først installere og konfigurere [Power Platform-løsningen til områderelateret akutberedskab](/powerapps/sample-apps/regional-emergency-response/deploy). Når du installerer denne løsning, oprettes de referencer til datakilden, der er nødvendige for at udfylde appen med data.

Når du installerer løsningen til områderelateret akutberedskab, kan du se [URL-adressen til din forekomst af Common Data Service-miljøet](/powerapps/sample-apps/regional-emergency-response/deploy#step-5-configure-and-publish-power-bi-dashboard). Du skal bruge den til at oprette forbindelse mellem skabelonappen og dataene.

## <a name="install-the-app"></a>Installér programmet

1. Klik på følgende link for at få adgang til appen: [Skabelonappen Dashboard til områderelateret akutberedskab](https://appsource.microsoft.com/product/power-bi/powerapps_cxo.regional_response)

1. Vælg [**Hent den nu**](https://appsource.microsoft.com/product/power-bi/powerapps_cxo.regional_response) på AppSource-siden for appen.

    [![Appen Dashboard til områderelateret akutberedskab i AppSource](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-appsource-get-it-now.png)](https://appsource.microsoft.com/product/power-bi/powerapps_cxo.regional_response)

1. Vælg **Installér**. 

    ![Installer appen Områderelateret dashboard til akutberedskab](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-select-install.png)

    Når appen er installeret, kan du se den på siden med dine apps.

   ![Appen Dashboard til områderelateret akutberedskab på appsiden](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-apps-page-icon.png)

## <a name="connect-to-data-sources"></a>Opret forbindelse til datakilder

1. Vælg ikonet på siden med apps for at åbne appen.

1. På velkomstskærmen skal du vælge **Udforsk**.

   ![Velkomstskærmbilledet for skabelonappen](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-splash-screen.png)

   Appen åbnes, og der vises eksempeldata.

1. Vælg linket **Opret forbindelse til dine data** på banneret øverst på siden.

   ![Appen Dashboard til områderelateret akutberedskab på appsiden – link til oprettelse af forbindelse til data](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-connect-data.png)

1. I den dialogboks, der vises, skal du skrive [URL-adressen til din forekomst af Common Data Service-miljøet](/powerapps/sample-apps/emergency-response/deploy-configure#publish-the-power-bi-dashboard). For eksempel: https://[myenv].crm.dynamics.com. Klik på **Næste**, når du er færdig.

   ![Appen Dashboard til områderelateret akutberedskab – dialogboks til URL-adresse](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-url-dialog.png)

1. I den næste dialogboks, der vises, skal du angive godkendelsesmetoden til **OAuth2**. Du behøver ikke at foretage dig noget med indstillingen for beskyttelsesniveau.

   Vælg **Log på**.

   ![Appen Dashboard til områderelateret akutberedskab – dialogboks til godkendelse](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-authentication-dialog.png)

1. Log på Power BI, når du er logget på Microsoft.

   ![Microsoft-logonskærmbillede](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-microsoft-login.png)

   Når du har logget på, opretter rapporten forbindelse til datakilderne og udfyldes med opdaterede data. Aktivitetsovervågningen aktiveres i dette tidsrum.

   ![Appen Dashboard til områderelateret akutberedskab – igangværende opdatering](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-refresh-monitor.png)

## <a name="schedule-report-refresh"></a>Planlæg rapportopdatering

Når dataene er blevet opdateret, [kan du konfigurere en opdateringsplan](../connect-data/refresh-scheduled-refresh.md) for at holde rapportdataene opdateret.

1. Vælg **Power BI** på den øverste overskriftslinje.

   ![Power BI-brødkrumme](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-powerbi-breadcrumb.png)

1. I navigationsruden til venstre skal du finde arbejdsområdet for Dashboard til områderelateret akutberedskab under **Arbejdsområder** og følge instruktionerne, der er beskrevet i artiklen [Konfigurer planlagt opdatering](../connect-data/refresh-scheduled-refresh.md).

## <a name="customize-and-share"></a>Tilpas og del

Se [Tilpas og del appen](../connect-data/service-template-apps-install-distribute.md#customize-and-share-the-app) for at få flere oplysninger. Sørg for at gennemse [ansvarsfraskrivelserne for rapporten](/powerapps/sample-apps/regional-emergency-response/overview#disclaimer), før du udgiver eller distribuerer appen.

## <a name="next-steps"></a>Næste trin
* [Om Dashboard til områderelateret akutberedskab](/powerapps/sample-apps/regional-emergency-response/portals-admin-reporting#get-insights)
* [Konfigurer og få mere at vide om skabelonen med krisekommunikationseksemplet i Power Apps](/powerapps/maker/canvas-apps/sample-crisis-communication-app)
* Har du spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
* [Hvad er Power BI-skabelonapps?](../connect-data/service-template-apps-overview.md)
* [Installér og distribuer skabelonapps i din organisation](../connect-data/service-template-apps-install-distribute.md)