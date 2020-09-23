---
title: Sammenlign Power BI-rapportserveren med Power BI-tjenesten
description: I denne artikel sammenlignes funktionerne i Power BI-rapportserveren og Power BI-tjenesten.
keywords: ''
author: maggiesMSFT
ms.author: maggies
ms.topic: overview
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.custom: mvc
ms.date: 07/28/2020
ms.openlocfilehash: 18629f38db7d8b88c47d4a1af3a5c3f6512433b4
ms.sourcegitcommit: 9350f994b7f18b0a52a2e9f8f8f8e472c342ea42
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 09/22/2020
ms.locfileid: "90859146"
---
# <a name="comparing-power-bi-report-server-and-the-power-bi-service"></a>Sammenlign Power BI-rapportserveren med Power BI-tjenesten

Power BI-rapportserveren og Power BI-tjenesten har mange ligheder og nogle vigtige forskelle. I denne tabel forklares det, hvad der er hvad.

## <a name="features-of-power-bi-report-server-and-the-power-bi-service"></a>Funktioner i Power BI-rapportserveren og Power BI-tjenesten

| Funktioner | Power BI-rapportserver | Power BI-tjeneste | Noter |
|---------|---------|---------|---------|
| Installation | I det lokale miljø eller i hostet cloud | Cloud | Power BI-rapportserveren kan udrulles i Azure VM'er (hostet cloud), hvis den er givet i licens via Power BI Premium eller SQL Server Enterprise med Software Assurance|
| Kildedata | Cloud og/eller i det lokale miljø | Cloud og/eller i det lokale miljø |  |
| Licens | Power BI Premium eller SQL Server EE med SA (Software Assurance) | Power BI Pro-og/eller Power BI Premium | |  
| Livscyklus | Politik for moderne livscyklus | Fuldt administreret tjeneste |  |
| Versionscyklus | Tre gange om året (januar, maj, september) | En gang om måneden | Nyeste funktioner og løsninger optræder først i Power BI-tjenesten. I hver udgivelse kommer der en række funktioner til tjenesten fra udgivelser af Power BI Desktop til Power BI-rapportserver. De fleste funktioner er kun beregnet til Power BI-tjenesten. |
| Opret Power BI-rapporter i Power BI Desktop | Ja | Ja |  |
| Opret Power BI-rapporter i browseren | Nej | Ja |  |
| Host og opret forbindelse til delte datasæt i Power BI | Nej | Ja | [Introduktion til datasæt på tværs af arbejdsområder](../connect-data/service-datasets-across-workspaces.md) |
| Gateway er påkrævet | Nej | Ja, for datakilder i det lokale miljø |  |
| Streaming i realtid | Nej | Ja | [Streaming i realtid i Power BI](../connect-data/service-real-time-streaming.md) |
| Dashboards | Nej | Ja | [Dashboards i Power BI-tjenesten](../consumer/end-user-dashboards.md) |
| Distribuer gruppe af rapporter ved hjælp af apps | Nej | Ja | [Opret og udgiv apps med dashboards og rapporter](../collaborate-share/service-create-distribute-apps.md) |
| Indholdspakker | Nej | Ja | [Organisationsindholdspakker: Introduktion](../collaborate-share/service-organizational-content-pack-introduction.md) |
| Opret forbindelse til tjenester som Salesforce | Ja | Ja | [Opret forbindelse til de tjenester, du bruger](../connect-data/service-connect-to-services.md) med indholdspakker i Power BI-tjenesten. På Power BI-rapportserveren skal du bruge certificerede connectorer til at oprette forbindelse til tjenester. Du kan finde flere detaljer i [Power BI-rapportdatakilderne på Power BI-rapportserver](data-sources.md). |
| Spørgsmål og svar | Nej | Ja | [Spørgsmål og svar i Power BI-tjenesten og Power BI Desktop](../create-reports/power-bi-tutorial-q-and-a.md) 
| Hurtig indsigt | Nej | Ja | [Generér automatisk dataindsigt med Power BI](../consumer/end-user-insights.md) |
| Analysér i Excel | Nej | Ja | [Analysér i Excel](../collaborate-share/service-analyze-in-excel.md) 
| Sideinddelte rapporter | Ja | Ja | [Sideinddelte rapporter er tilgængelige i Power BI-tjenesten](../paginated-reports/paginated-reports-report-builder-power-bi.md) som prøveversion i en Premium-kapacitet |
| Power BI-mobilapps | Ja | Ja | [Oversigt over Power BI-mobilapps](../consumer/mobile/mobile-apps-for-mobile-devices.md) |
| ARC GIS-kort | Nej | Ja | [ArcGIS-kort i Power BI-tjenesten og Power BI Desktop fra Esri](../visuals/power-bi-visualization-arcgis.md) |
| Mailabonnementer på Power BI-rapporter | Nej | Ja | [Meld dig selv eller andre til et abonnement](../collaborate-share/service-report-subscribe.md) på en rapport eller et dashboard i Power BI-tjenesten |
| Mailabonnementer på sideinddelte rapporter | Ja | Ja | [Meld dig selv og andre til et abonnement på sideinddelte rapporter i Power BI-tjenesten](../consumer/paginated-reports-subscriptions.md)<br><br>[Maillevering i Reporting Services](/sql/reporting-services/working-with-subscriptions-web-portal)  |
| Databeskeder | Nej | Ja | [Databeskeder](../create-reports/service-set-data-alerts.md) i Power BI-tjenesten
| Sikkerhed på rækkeniveau (RLS) | Ja | Ja | Tilgængelige i både DirectQuery- (datakilde) og importtilstand <br><br>Sikkerhed på rækkeniveau i [Power BI-tjenesten](../admin/service-admin-rls.md) <br><br>Sikkerhed på rækkeniveau i [Power BI-rapportserver](row-level-security-report-server.md) |
| Mange til mange-relationer | Nej | Ja | [Anvend mange til mange-relationer](../transform-model/desktop-many-to-many-relationships.md) i Power BI Desktop |
| Detaljeadgang på tværs af rapporter | Nej | Ja | [Brug detaljeadgang på tværs af rapporter](../create-reports/desktop-cross-report-drill-through.md) |
| Fuldskærmsvisning | Nej | Ja | [Fuldskærmsvisning](../consumer/end-user-focus.md) i Power BI-tjenesten |
| Avanceret Microsoft 365-samarbejde | Nej | Ja | [Samarbejd i et arbejdsområde](../collaborate-share/service-collaborate-power-bi-workspace.md) med Microsoft 365 |
| R-scripts og -visuals | Nej | Ja | [Opret R-visuals](../create-reports/desktop-r-visuals.md) og kør R-scripts i Power BI Desktop, og publicer dem i Power BI-tjenesten. Du kan ikke gemme Power BI-rapporter med R-scripts eller -visuals på Power BI-rapportserver.  |
| Python-scripts og -visuals | Nej | Ja | [Opret Python-scripts](../connect-data/desktop-python-scripts.md) og -visuals i Power BI Desktop, og publicer dem i Power BI-tjenesten. Du kan ikke gemme Power BI-rapporter med Python-scripts eller -visuals på Power BI-rapportserver. |
| Prøveversionsfunktioner | Nej | Ja | [Tilmeld dig prøveversioner af funktioner i Power BI-tjenesten](../consumer/end-user-preview-features.md) |
| Power BI-visualiseringer | Ja | Ja | [Power BI-visuals](../developer/visuals/power-bi-custom-visuals.md) |
| Sammensatte modeller | Nej | Ja |
| Power BI Desktop | Version, der er optimeret til rapportserveren, kan downloades med rapportserveren | Version, der er optimeret til Power BI-tjenesten, er tilgængelig fra Windows Store | [Power BI Desktop til rapportserveren](https://powerbi.microsoft.com/report-server/) <br><br> [Power BI Desktop til Power BI-tjenesten](https://aka.ms/pbidesktopstore) |

## <a name="next-steps"></a>Næste trin

[Installer Power BI-rapportserver](install-report-server.md)