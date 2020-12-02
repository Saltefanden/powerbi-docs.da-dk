---
title: Opret forbindelse til Dashboard til understøttelse af beslutninger i forbindelse med hospitalernes akutberedskab
description: Sådan henter og installerer du skabelonappen Dashboard til understøttelse af beslutninger i forbindelse med COVID-19, og sådan opretter du forbindelse til data
author: paulinbar
ms.author: painbar
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: how-to
ms.date: 05/13/2020
LocalizationGroup: Connect to services
ms.openlocfilehash: 823c8429c95a0b4d858540b2cf1183ca1c7caac7
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96403139"
---
# <a name="connect-to-the-hospital-emergency-response-decision-support-dashboard"></a>Opret forbindelse til Dashboard til understøttelse af beslutninger i forbindelse med hospitalernes akutberedskab
Skabelonappen Dashboard til understøttelse af beslutninger i forbindelse med hospitalernes akutberedskab er rapporteringskomponenten i [Microsoft Power Platform-løsningen til akutberedskab](https://powerapps.microsoft.com/blog/emergency-response-solution-a-microsoft-power-platform-solution-for-healthcare-emergency-response/). Dashboardet viser beredskabschefers samlede data på tværs af sundhedssystemet for at hjælpe dem med at træffe rettidige og korrekte beslutninger.

![Rapport i appen Dashboard til understøttelse af beslutninger i forbindelse med hospitalernes akutberedskab](media/service-connect-to-health-emergency-response/service-health-emergency-response-app-report.png)

I denne artikel får du oplysninger om, hvordan du installerer appen, og hvordan du opretter forbindelse til datakilderne. Hvis du vil have mere at vide om, hvordan du bruger rapporten i denne app, kan du se [dokumentationen til Dashboard til understøttelse af beslutninger i forbindelse med hospitalernes akutberedskab](/powerapps/sample-apps/emergency-response/deploy-configure#view-the-power-bi-dashboard).

Når du har installeret skabelonappen og har oprettet forbindelse til datakilderne, kan du tilpasse rapporten i henhold til dine behov. Du kan derefter distribuere den som en app til kolleger i organisationen.

## <a name="prerequisites"></a>Forudsætninger

Før du installerer denne skabelonapp, skal du først installere og konfigurere [Power Platform-løsningen til hospitalernes akutberedskab](/powerapps/sample-apps/emergency-response/deploy-configure). Når du installerer denne løsning, oprettes de referencer til datakilden, der er nødvendige for at udfylde appen med data.

Når du installerer Power Platform-løsningen til hospitalernes akutberedskab, kan du se [URL-adressen til din instans af Common Data Service-miljøet](/powerapps/sample-apps/emergency-response/deploy-configure#publish-the-power-bi-dashboard). Du skal bruge den til at oprette forbindelse mellem skabelonappen og dataene.

## <a name="install-the-app"></a>Installér programmet

1. Klik på følgende link for at få adgang til appen: [Skabelonappen Dashboard til understøttelse af beslutninger i forbindelse med hospitalernes akutberedskab](https://aka.ms/AppSource_Hospital_offer)

1. Vælg [**Hent den nu**](https://aka.ms/AppSource_Hospital_offer) på AppSource-siden for appen.

    [![Appen Dashboard til understøttelse af beslutninger i forbindelse med hospitalernes akutberedskab i AppSource](media/service-connect-to-health-emergency-response/service-health-emergency-response-app-appsource-get-it-now.png)](https://aka.ms/AppSource_Hospital_offer)

1. Læs oplysningerne i **Én ting mere**, og vælg **Fortsæt**.

    ![Appen Dashboard til understøttelse af beslutninger i forbindelse med hospitalernes akutberedskab, Én ting mere](media/service-connect-to-health-emergency-response/service-health-emergency-response-1-more-thing.png)

1. Vælg **Installér**. 

    ![Installer appen Dashboard til understøttelse af beslutninger i forbindelse med hospitalernes akutberedskab](media/service-connect-to-health-emergency-response/service-health-emergency-response-select-install.png)

    Når appen er installeret, kan du se den på siden med dine apps.

   ![Appen Dashboard til understøttelse af beslutninger i forbindelse med hospitalernes akutberedskab på siden med apps](media/service-connect-to-health-emergency-response/service-health-emergency-response-app-apps-page-icon.png)

## <a name="connect-to-data-sources"></a>Opret forbindelse til datakilder

1. Vælg ikonet på siden med apps for at åbne appen.

1. På velkomstskærmen skal du vælge **Udforsk**.

   ![Velkomstskærmbilledet for skabelonappen](media/service-connect-to-health-emergency-response/service-health-emergency-response-app-splash-screen.png)

   Appen åbnes, og der vises eksempeldata.

1. Vælg linket **Opret forbindelse til dine data** på banneret øverst på siden.

   ![Appen Dashboard til understøttelse af beslutninger i forbindelse med hospitalernes akutberedskab, linket Opret forbindelse til dine data](media/service-connect-to-health-emergency-response/service-health-emergency-response-app-connect-data.png)

1. I dialogboksen:
   1. Angiv navnet på din organisation i feltet organisationsnavn, f.eks. "Contoso Health Systems". Feltet er valgfrit. Dette navn vises i øverste venstre hjørne af dashboardet.
   1. I feltet CDS_base_solution skal du angive [URL-adressen til din instans af Common Data Service-miljøet](/powerapps/sample-apps/emergency-response/deploy-configure#publish-the-power-bi-dashboard). For eksempel: https://[myenv].crm.dynamics.com. Klik på **Næste**, når du er færdig.

   ![Dashboard til understøttelse af beslutninger i forbindelse med hospitalernes akutberedskab, URL-dialogboks](media/service-connect-to-health-emergency-response/service-health-emergency-response-app-url-dialog.png)

1. I den næste dialogboks, der vises, skal du angive godkendelsesmetoden til **OAuth2**. Du behøver ikke at foretage dig noget med indstillingen for beskyttelsesniveau.

   Vælg **Log på**.

   ![Dashboard til understøttelse af beslutninger i forbindelse med hospitalernes akutberedskab, godkendelsesdialogboks](media/service-connect-to-health-emergency-response/service-health-emergency-response-app-authentication-dialog.png)

1. Log på Power BI, når du er logget på Microsoft.

   ![Microsoft-logonskærmbillede](media/service-connect-to-health-emergency-response/service-health-emergency-response-app-microsoft-login.png)

   Når du har logget på, opretter rapporten forbindelse til datakilderne og udfyldes med opdaterede data. Aktivitetsovervågningen aktiveres i dette tidsrum.

   ![Opdateringen af appen Dashboard til understøttelse af beslutninger i forbindelse med hospitalernes akutberedskab er i gang](media/service-connect-to-health-emergency-response/service-health-emergency-response-app-refresh-monitor.png)

## <a name="schedule-report-refresh"></a>Planlæg rapportopdatering

Når dataene er blevet opdateret, [kan du konfigurere en opdateringsplan](../connect-data/refresh-scheduled-refresh.md) for at holde rapportdataene opdateret.

1. Vælg **Power BI** på den øverste overskriftslinje.

   ![Power BI-brødkrumme](media/service-connect-to-health-emergency-response/service-health-emergency-response-app-powerbi-breadcrumb.png)

1. I navigationsruden til venstre skal du finde arbejdsområdet for Dashboard til understøttelse af beslutninger i forbindelse med hospitalernes akutberedskab under **Arbejdsområder** og følge instruktionerne, der er beskrevet i artiklen [Konfigurer planlagt opdatering](../connect-data/refresh-scheduled-refresh.md).

## <a name="customize-and-share"></a>Tilpas og del

Se [Tilpas og del appen](../connect-data/service-template-apps-install-distribute.md#customize-and-share-the-app) for at få flere oplysninger. Sørg for at gennemse [ansvarsfraskrivelserne for rapporten](../create-reports/sample-covid-19-us.md#disclaimers), før du udgiver eller distribuerer appen.

## <a name="next-steps"></a>Næste trin
* [Om rapporten Hospitalernes akutberedskab](/powerapps/sample-apps/emergency-response/deploy-configure#view-the-power-bi-dashboard)
* [Konfigurer og få mere at vide om skabelonen med krisekommunikationseksemplet i Power Apps](/powerapps/maker/canvas-apps/sample-crisis-communication-app)
* Har du spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
* [Hvad er Power BI-skabelonapps?](../connect-data/service-template-apps-overview.md)
* [Installér og distribuer skabelonapps i din organisation](../connect-data/service-template-apps-install-distribute.md)