---
title: Opret forbindelse til rapport om eksisterende krisekommunikation
description: Sådan henter og installerer du rapporten om eksisterende krisekommunikation i forbindelse med COVID-19, og sådan opretter du forbindelse til data
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: how-to
ms.date: 04/06/2020
ms.author: painbar
LocalizationGroup: Connect to services
ms.openlocfilehash: 97501fe6e5a3e12e1b6773ce1b3fd67b503bf0f1
ms.sourcegitcommit: 9350f994b7f18b0a52a2e9f8f8f8e472c342ea42
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 09/22/2020
ms.locfileid: "90860296"
---
# <a name="connect-to-the-crisis-communication-presence-report"></a>Opret forbindelse til rapport om eksisterende krisekommunikation

Denne Power BI-app er det rapport-/dashboardartefakt, der findes i Microsoft Power Platform-løsningen til krisekommunikation. Den sporer placeringen af medarbejdere for brugere af appen til krisekommunikation. Løsningen kombinerer funktioner i Power Apps, Power Automate, Teams, SharePoint og Power BI. Den kan bruges på internettet, mobilenheder eller i Teams.

![Rapport om eksisterende krisekommunikation, apprapport](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report.png)

Dashboardet viser beredskabschefers samlede data på tværs af sundhedssystemet for at hjælpe dem med at træffe rettidige og korrekte beslutninger.

I denne artikel får du oplysninger om, hvordan du installerer appen, og hvordan du opretter forbindelse til datakilderne. Du kan finde flere oplysninger om appen til krisekommunikation under [Konfigurer og få mere at vide om eksempelskabelonen til krisekommunikation i Power Apps](/powerapps/maker/canvas-apps/sample-crisis-communication-app)

Når du har installeret skabelonappen og oprettet forbindelse til datakilderne, kan du tilpasse rapporten i henhold til dine behov. Du kan derefter distribuere den som en app til kolleger i organisationen.

## <a name="prerequisites"></a>Forudsætninger

Før du installerer denne skabelonapp, skal du først installere og konfigurere [krisekommunikationseksemplet](/powerapps/maker/canvas-apps/sample-crisis-communication-app). Når du installerer denne løsning, oprettes de referencer til datakilden, der er nødvendige for at udfylde appen med data.

Når du installerer krisekommunikationseksemplet, skal du notere [stien til mappen med SharePoint-listen for "CI_Employee Status" og liste-ID](/powerapps/maker/canvas-apps/sample-crisis-communication-app#monitor-office-absences-with-power-bi).

## <a name="install-the-app"></a>Installér programmet

1. Klik på følgende link for at få adgang til appen: [Skabelonappen Rapport om eksisterende krisekommunikation](https://appsource.microsoft.com/en-us/product/power-bi/pbi-contentpacks.crisiscomms)

1. Vælg [**Hent den nu**](https://appsource.microsoft.com/en-us/product/power-bi/pbi-contentpacks.crisiscomms) på AppSource-siden for appen.

    [![Appen Rapport om eksisterende krisekommunikation i AppSource](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-appsource-get-it-now.png)](https://appsource.microsoft.com/en-us/product/power-bi/pbi-contentpacks.crisiscomms)

1. Læs oplysningerne i **Én ting mere**, og vælg **Fortsæt**.

    ![Appen Rapport om eksisterende krisekommunikation, Én ting mere](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-1-more-thing.png)

1. Vælg **Installér**. 

    ![Installer appen Rapport om eksisterende krisekommunikation](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-select-install.png)

    Når appen er installeret, kan du se den på siden med dine apps.

   ![Appen Rapport om eksisterende krisekommunikation på appsiden](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-apps-page-icon.png)

## <a name="connect-to-data-sources"></a>Opret forbindelse til datakilder

1. Vælg ikonet på siden med apps for at åbne appen.

1. På velkomstskærmen skal du vælge **Udforsk**.

   ![Velkomstskærmbilledet for skabelonappen](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-splash-screen.png)

   Appen åbnes, og der vises eksempeldata.

1. Vælg linket **Opret forbindelse til dine data** på banneret øverst på siden.

   ![Appen Rapport om eksisterende krisekommunikation, Opret forbindelse til dine data](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-connect-data.png)

1. I dialogboksen:
   1. I feltet SharePoint_Folder skal du angive [stien til SharePoint-listen "CI_Employee Status"](/powerapps/maker/canvas-apps/sample-crisis-communication-app#monitor-office-absences-with-power-bi).
   1. I feltet List_ID skal du angive det liste-id, du har fået fra listeindstillingerne. Klik på **Næste**, når du er færdig.

   ![Appen Rapport om eksisterende krisekommunikation, URL-dialogboks](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-url-dialog.png)

1. I den næste dialogboks, der vises, skal du angive godkendelsesmetoden til **OAuth2**. Du behøver ikke at foretage dig noget med indstillingen for beskyttelsesniveau.

   Vælg **Log på**.

   ![Appen Rapport om eksisterende krisekommunikation, godkendelsesdialogboks](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-authentication-dialog.png)

1. Log på Power BI, når du er logget på Microsoft.

   ![Microsoft-logonskærmbillede](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-microsoft-login.png)

   Når du har logget på, opretter rapporten forbindelse til datakilderne og udfyldes med opdaterede data. Aktivitetsovervågningen aktiveres i dette tidsrum.

   ![Opdateringen af rapporten om eksisterende krisekommunikation er i gang](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-refresh-monitor.png)

## <a name="schedule-report-refresh"></a>Planlæg rapportopdatering

Når dataene er blevet opdateret, [kan du konfigurere en opdateringsplan](../connect-data/refresh-scheduled-refresh.md) for at holde rapportdataene opdateret.

1. Vælg **Power BI** på den øverste overskriftslinje.

   ![Power BI-brødkrumme](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-powerbi-breadcrumb.png)

1. I navigationsruden til venstre skal du finde arbejdsområdet for Dashboard til understøttelse af beslutninger i forbindelse med hospitalernes akutberedskab under **Arbejdsområder** og følge instruktionerne, der er beskrevet i artiklen [Konfigurer planlagt opdatering](../connect-data/refresh-scheduled-refresh.md).

## <a name="customize-and-share"></a>Tilpas og del

Se [Tilpas og del appen](../connect-data/service-template-apps-install-distribute.md#customize-and-share-the-app) for at få flere oplysninger. Sørg for at gennemse [ansvarsfraskrivelserne for rapporten](../create-reports/sample-covid-19-us.md#disclaimers), før du udgiver eller distribuerer appen.

## <a name="next-steps"></a>Næste trin
* [Konfigurer og få mere at vide om skabelonen med eksempel på krisekommunikation i Power Apps](/powerapps/maker/canvas-apps/sample-crisis-communication-app)
* Har du spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
* [Hvad er Power BI-skabelonapps?](../connect-data/service-template-apps-overview.md)
* [Installér og distribuer skabelonapps i din organisation](../connect-data/service-template-apps-install-distribute.md)