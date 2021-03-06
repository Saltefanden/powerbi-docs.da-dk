---
title: Aktivér godkendelse med tjenesteprincipal for skrivebeskyttede administrator-API'er (prøveversion)
description: Få mere at vide om, hvordan du aktiverer godkendelse med tjenesteprincipal for at tillade brug af skrivebeskyttede administrator-API'er.
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: how-to
ms.date: 02/04/2021
ms.author: painbar
ms.custom: ''
LocalizationGroup: Administration
ms.openlocfilehash: e255fbef8b29422ea7736e43adaa5e4197a6338f
ms.sourcegitcommit: afdc9d41da6a4fced63030648d3f976425131732
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/05/2021
ms.locfileid: "99569939"
---
# <a name="enable-service-principal-authentication-for-read-only-admin-apis-preview"></a>Aktivér godkendelse med tjenesteprincipal for skrivebeskyttede administrator-API'er (prøveversion)

Tjenesteprincipal er en godkendelsesmetode, som kan bruges til at give et Azure AD-program (Azure Active Directory) adgang til Power BI-tjenesteindhold og API'er.
Når du opretter et Azure AD-program, oprettes der et [objekt for en tjenesteprincipal](/azure/active-directory/develop/app-objects-and-service-principals#service-principal-object). Objektet for tjenesteprincipalen, der også ganske enkelt er kendt som tjenesteprincipal, giver Azure AD mulighed for at godkende dit program. Når appen er godkendt, kan den få adgang til Microsoft Azure AD-lejerressourcer.

## <a name="method"></a>Metode

Følg disse trin for at aktivere godkendelse med tjenesteprincipal for skrivebeskyttede API'er til Power BI:

1. [Opret et Azure AD-program](/azure/active-directory/develop/howto-create-service-principal-portal). Du kan springe dette trin over, hvis du allerede har et Azure AD-program, du vil bruge. Notér program-id'et til senere trin. 
2. Opret en ny **sikkerhedsgruppe** i Azure Active Directory. [Få mere at vide om, hvordan du opretter en grundlæggende gruppe og tilføjer medlemmer ved hjælp af Azure Active Directory](/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal). Du kan springe dette trin over, hvis du allerede har en sikkerhedsgruppe, du vil bruge.
    Sørg for at vælge **Sikkerhed** som gruppetype.

    ![Skærmbillede af dialogboksen til oprettelse af en ny gruppe på Azure Portal.](media/read-only-apis-service-principal-auth/azure-portal-new-group-dialog.png)

3. Tilføj dit program-id som medlem af den sikkerhedsgruppe, du har oprettet. Sådan gør du:
    1. Naviger til **Azure Portal > Azure Active Directory > Grupper**, og vælg den sikkerhedsgruppe, du oprettede i Trin 2.
    1. Vælg **Tilføj medlemmer**.
    Bemærk! Sørg for, at der ikke er angivet nogen Power BI-administratorroller for det anvendte program på Azure Portal. Sådan tjekker du dette: 
       * Log på **Azure Portal** som global administrator, programadministrator eller administrator af cloudprogram. 
        * Vælg **Azure Active Directory** og derefter **Virksomhedsprogrammer**. 
        * Vælg det program, som du vil tildele adgang til Power BI. 
        * Vælg **Tilladelser**. Sørg for, at der ikke er angivet tilladelser af typen admin-consent-required i Power BI for dette program. Se [Administration af samtykke til programmer og evaluering af anmodninger om indhold](/azure/active-directory/manage-apps/manage-consent-requests) for at få flere oplysninger. 
4. Aktivér indstillingerne for Power BI-tjenesteadministration. Hvis du vil dette, skal du gøre som følger:
    1. Log på Power BI-administrationsportalen. Du skal være Power BI-administrator for at se siden med lejerindstillinger.
    1. Under **API-indstillinger for administrator** kan du se **Giv tjenesteprincipaler tilladelse til at bruge skrivebeskyttede administrator-API'er i Power BI (prøveversion)** . Indstil til/fra-knappen til Aktiveret, og vælg derefter alternativknappen for **specifikke sikkerhedsgrupper**. Føj den sikkerhedsgruppe, du oprettede i Trin 2, til den tekstfelt, som vises under den, som vist på nedenstående figur.

        ![Skærmbillede af lejerindstillingen for tilladelse af tjenesteprincipaler.](media/read-only-apis-service-principal-auth/allow-service-principals-tenant-setting.png)

 5. Begynd at bruge de skrivebeskyttede administrator-API'er. Se listen over understøttede API'er nedenfor.

    >[!IMPORTANT]
    >Når du aktiverer den tjenesteprincipal, der skal bruges med Power BI, er Azure AD-tilladelserne for programmet ikke længere gældende. Tilladelserne for programmet administreres derefter via Power BI-administrationsportalen.

## <a name="supported-apis"></a>Understøttede API'er

Tjenesteprincipalen understøtter i øjeblikket følgende API'er:
* [GetGroupsAsAdmin](/rest/api/power-bi/admin/groups_getgroupsasadmin) med $expand for dashboards, datasæt, rapporter og dataflow 
* [GetDashboardsAsAdmin](/rest/api/power-bi/admin/dashboards_getdashboardsasadmin) med $expand-felter
* [GetDatasourcesAsAdmin](/rest/api/power-bi/admin/datasets_getdatasourcesasadmin) 
* [GetDatasetToDataflowsLinksAsAdmin](/rest/api/power-bi/admin/datasets_getdatasettodataflowslinksingroupasadmin)
* [GetDataflowDatasourcesAsAdmin](/rest/api/power-bi/admin/dataflows_getdataflowdatasourcesasadmin) 
* [GetDataflowUpstreamDataflowsAsAdmin](/rest/api/power-bi/admin/dataflows_getupstreamdataflowsingroupasadmin) 
* [GetCapacitiesAsAdmin](/rest/api/power-bi/admin/getcapacitiesasadmin)
* [GetActivityLog](/rest/api/power-bi/admin/getactivityevents)
* [GetModifiedWorkspaces](/rest/api/power-bi/admin/workspaceinfo_getmodifiedworkspaces)
* [WorkspaceGetInfo](/rest/api/power-bi/admin/workspaceinfo_postworkspaceinfo)
* [WorkspaceScanStatus](/rest/api/power-bi/admin/workspaceinfo_getscanstatus)
* [WorkspaceScanResult](/rest/api/power-bi/admin/workspaceinfo_getscanresult)

## <a name="considerations-and-limitations"></a>Overvejelser og begrænsninger

* Du kan ikke logge på Power BI-portalen ved hjælp af en tjenesteprincipal.
* Du skal have rettigheder som Power BI-administrator for at aktivere tjenesteprincipalen under API-indstillinger for administrator på Power BI-administrationsportalen.