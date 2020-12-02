---
title: Opret forbindelse til den amerikanske sporingsrapport for COVID-19
description: Sådan henter og installerer du skabelonappen Tilfælde af COVID-19 i USA og opretter forbindelse til dataene.
author: paulinbar
ms.author: painbar
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: how-to
ms.date: 04/05/2020
LocalizationGroup: Connect to services
ms.openlocfilehash: 19dc9f5c5adfa5853d98cd6b0ef427c8bccebada
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96410614"
---
# <a name="connect-to-the-covid-19-us-tracking-report"></a>Opret forbindelse til den amerikanske sporingsrapport for COVID-19
I denne artikel får du oplysninger om, hvordan du installerer skabelonappen til den amerikanske sporingsrapport for COVID-19, og hvordan du opretter forbindelse til datakilderne.

![Amerikansk sporingsrapport for COVID-19](media/service-connect-to-covid-19-tracking/service-covid-19-us-tracking-report-title-screen.png)

Hvis du vil have detaljerede oplysninger om selve rapporten, herunder ansvarsfraskrivelser og oplysninger om dataene, kan du se [eksemplet på sporingsrapport for COVID-19 til centralregeringen og delstatsregeringerne i USA](../create-reports/sample-covid-19-us.md).

Når du har installeret skabelonappen og oprettet forbindelse til datakilderne, kan du tilpasse rapporten i henhold til dine behov. Du kan derefter distribuere den som en app til kolleger i organisationen.

## <a name="install-the-app"></a>Installér programmet

1. Klik på følgende link for at få adgang til appen: [Skabelonappen Amerikansk sporingsrapport for COVID-19](https://app.powerbi.com/groups/me/getapps/services/pbi-contentpacks.covid19ms)

1. Når du er på appens Appsource-side, skal du klikke på [**Hent den nu**](https://app.powerbi.com/groups/me/getapps/services/pbi-contentpacks.covid19ms).

    [![Amerikansk sporingsrapport for Covid-19 i Appsource](media/service-connect-to-covid-19-tracking/service-covid-19-us-tracking-report-appsource-icon.png)](https://app.powerbi.com/groups/me/getapps/services/pbi-contentpacks.covid19ms)

1. Klik på **Installer**, når du bliver bedt om det. Når appen er installeret, kan du se den på siden med dine apps.

   ![Amerikansk sporingsrapport for COVID-19 på appsiden](media/service-connect-to-covid-19-tracking/service-covid-19-us-tracking-report-apps-page-icon.png)

## <a name="connect-to-data-sources"></a>Opret forbindelse til datakilder

1. Klik på ikonet på appsiden for at åbne appen.

1. Vælg **Opret forbindelse** på den velkomstskærm, der vises.

   ![Velkomstskærmbilledet for skabelonappen](media/service-connect-to-covid-19-tracking/service-covid-19-us-tracking-report-splash-screen.png)

1. Dialogboksen for parametre vises. Der er ingen påkrævede parametre. Klik på **Next**.

   ![Skærmbillede af dialogboksen for parameteren i forbindelse med Sporingsrapport for Covid-19 i USA.](media/service-connect-to-covid-19-tracking/service-covid-19-us-tracking-report-parameters-dialog.png)

1. Dialogboksen for godkendelsesmetode vises. De anbefalede værdier er udfyldt på forhånd. Undlad at ændre disse, medmindre du har specifik viden om forskellige værdier.

    Klik på **Next**.

   ![Skærmbillede af dialogboksen for godkendelse i forbindelse med Sporingsrapport for Covid-19 i USA.](media/service-connect-to-covid-19-tracking/service-covid-19-us-tracking-report-authentication-dialog.png)

1. Klik på **Log på**.

   ![Skærmbillede af dialogboksen for logon i forbindelse med Sporingsrapport for Covid-19 i USA.](media/service-connect-to-covid-19-tracking/service-covid-19-us-tracking-report-signin-dialog.png)
 
   Rapporten opretter forbindelse til datakilderne og udfyldes med opdaterede data. I denne periode får du vist eksempeldata, og at en opdatering er i gang.

   ![Opdatering af amerikansk sporingsrapport for COVID-19 er i gang](media/service-connect-to-covid-19-tracking/service-covid-19-us-tracking-report-refresh-monitor.png)

## <a name="schedule-report-refresh"></a>Planlæg rapportopdatering

Når dataene er blevet opdateret, er du i det arbejdsområde, der er knyttet til appen. Du kan [konfigurere en opdateringsplan](../connect-data/refresh-scheduled-refresh.md) for at holde rapportdataene opdaterede.

## <a name="customize-and-share"></a>Tilpas og del

Se [Tilpas og del appen](../connect-data/service-template-apps-install-distribute.md#customize-and-share-the-app) for at få flere oplysninger. Sørg for at gennemse [ansvarsfraskrivelserne for rapporten](../create-reports/sample-covid-19-us.md#disclaimers), før du udgiver eller distribuerer appen.

## <a name="next-steps"></a>Næste trin
* [COVID-19-sporingseksempel til centralregeringen og delstatsregeringerne i USA](../create-reports/sample-covid-19-us.md)
* Har du spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
* [Hvad er Power BI-skabelonapps?](../connect-data/service-template-apps-overview.md)
* [Installér og distribuer skabelonapps i din organisation](../connect-data/service-template-apps-install-distribute.md)
