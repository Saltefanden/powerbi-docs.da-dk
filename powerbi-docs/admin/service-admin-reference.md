---
title: PowerShell-cmdlet'er, REST-API'er og .NET-klientbiblioteker til administratorer
description: Få mere at vide om de måder, hvorpå du kan administrere Power BI via scripts og programmerings-API'er.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/09/2019
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: c26d169a4c8ef876d1fe92e4967b07c982f510db
ms.sourcegitcommit: 9350f994b7f18b0a52a2e9f8f8f8e472c342ea42
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 09/22/2020
ms.locfileid: "90856869"
---
# <a name="powershell-cmdlets-rest-apis-and-net-client-library-for-power-bi-administration"></a>PowerShell-cmdlet'er, REST-API'er og .NET-klientbiblioteker til Power BI-administration
Power BI gør det muligt for administratorer at scripte almindelige opgaver med PowerShell-cmdlet'er. Den eksponerer også REST API'er og giver et .NET-klientbibliotek til udvikling af administrative løsninger. Dette emne viser en liste over cmdlet'er og de tilsvarende API'er og REST API-slutpunktet. Her finder du flere oplysninger:

- PowerShell [download](https://www.powershellgallery.com/packages/MicrosoftPowerBIMgmt/) og [dokumentation](/powershell/power-bi/overview?view=powerbi-ps)
- REST API-[dokumentation](/rest/api/power-bi/admin)
- [Download](https://www.nuget.org/packages/Microsoft.PowerBI.Api/) af .NET-klientbibliotek

> Nedenstående cmdlet'er skal kaldes vha. `-Scope Organization` for at fungere i forhold til administration af lejeren.

| **Cmdlet-navn** | **Aliasser** | **API** | **REST API-slutpunkt** | **Beskrivelse** |
| --- | --- | --- | --- | --- |
| `Get-PowerBIDatasource` | I/T | `Datasets_GetDataSourcesAsAdmin` | /v1.0/myorg/admin/datasets/{datasetkey}/datasources | Henter datakilderne for et givet datasæt. |
| `Get-PowerBIDataset` | I/T | `Datasets_GetDatasetsAsAdmin` | /v1.0/myorg/admin/datasets | Henter den komplette liste over datasæt i en Power BI-lejer. |
| `Get-PowerBIWorkspace` | `Get-PowerBIGroup` | `Groups_GetGroupsAsAdmin` | /v1.0/myorg/admin/groups | Henter den komplette liste over arbejdsområder i en Power BI-lejer. |
| `Add-PowerBIWorkspaceUser` | `Add-PowerBIGroupUser` | `Groups_AddUserAsAdmin` | /v1.0/myorg/admin/groups/{groupId}/users | Tilføjer en bruger som medlem af et givet arbejdsområde. |
| `Remove-PowerBIWorkspaceUser` | `Remove-PowerBIGroupUser` | `Groups_DeleteUserAsAdmin` | /v1.0/myorg/admin/groups/{groupId}/users/{user} | Fjerner en bruger fra medlemslisten for et givet arbejdsområde. |
| `Restore-PowerBIWorkspace` |`Restore-PowerBIGroup` | `Groups_RestoreDeletedGroupAsAdmin` | /v1.0/myorg/admin/groups/{groupId}/restore | Gendanner et slettet arbejdsområde. |
| `Set-PowerBIWorkspace` |`Set-PowerBIGroup` | `Groups_UpdateGroupAsAdmin` | /v1.0/myorg/admin/groups/{groupId} | Opdaterer egenskaberne for et givet arbejdsområde. |
| `Get-PowerBIDataset -WorkspaceId` | I/T | `Groups_GetDatasetsAsAdmin` | /v1.0/myorg/admin/groups/{group\_id}/datasets | Henter datasættene inden for et givet arbejdsområde. |
| `Get-PowerBIReport` | I/T | `Reports_GetReportsAsAdmin` | /v1.0/myorg/admin/reports | Henter den komplette liste over rapporter i en Power BI-lejer. |
| `Get-PowerBIDashboard` | I/T | `Dashboards_GetDashboardsAsAdmin` | /v1.0/myorg/admin/dashboards | Henter den komplette liste over dashboards i en Power BI-lejer. |
| `Get-PowerBIDashboard -WorkspaceId` | I/T | `Groups_GetDashboardsAsAdmin` | /v1.0/myorg/admin/groups/{group\_id}/dashboards | Henter dashboards inden for et givet arbejdsområde. |
| `Get-PowerBITile` | `Get-PowerBIDashboardTile` | `Dashboards_GetTilesAsAdmin` | /v1.0/myorg/admin/dashboards/{dashboard\_id}/tiles | Henter felterne til et givet dashboard. |
| `Get-PowerBIReport` | I/T | `Groups_GetReportsAsAdmin` | /v1.0/myorg/admin/groups/{group\_id}/reports | Henter rapporterne inden for et givet arbejdsområde. |
| `Get-PowerBIImport` | I/T | `Imports_GetImportsAsAdmin` | /v1.0/myorg/admin/imports | Henter den komplette liste over importer i en Power BI-lejer. |
| `Connect-PowerBIServiceAccount` | `Login-PowerBI` &  `Login-PowerBIServiceAccount` | I/T | I/T | Log på Power BI, og begynd en session. |
| `Disconnect-PowerBIServiceAccount` | `Logout-PowerBI` & `Logout-PowerBIServiceAccount` | I/T | I/T | Log af Power BI, og luk den eksisterende session. |
| `Invoke-PowerBIRestMethod`| I/T | I/T | I/T | Send vilkårlige REST API-kald til Power BI. |
| `Get-PowerBIAccessToken`| I/T | I/T | I/T | Få adgangstokenet til Power BI i en session. |
| `Resolve-PowerBIError`| I/T | I/T | I/T | Få detaljerede fejloplysninger for mislykkedes cmdlet-kald. |