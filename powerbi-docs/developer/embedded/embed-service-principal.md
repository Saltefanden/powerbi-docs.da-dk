---
title: Integrer Power BI-indhold med tjenesteprincipal og en programhemmelighed
description: Få mere at vide om, hvordan du godkender for integreret analyse ved hjælp af en tjenesteprincipal i et Azure Active Director-program og en programhemmelighed.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: how-to
ms.custom: ''
ms.date: 05/12/2020
ms.openlocfilehash: e9faa50cd7e2c4a1a51dfb4a72dda950cf3a396a
ms.sourcegitcommit: 6bc66f9c0fac132e004d096cfdcc191a04549683
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2020
ms.locfileid: "91746786"
---
# <a name="embed-power-bi-content-with-service-principal-and-an-application-secret"></a>Integrer Power BI-indhold med tjenesteprincipal og en programhemmelighed

[!INCLUDE[service principal overview](../../includes/service-principal-overview.md)]

I denne artikel beskrives godkendelse af tjenesteprincipalen ved hjælp af et *program-id* og en *programhemmelighed*.

>[!NOTE]
>Vi anbefaler, at du sikrer dine backend-tjenester ved hjælp af certifikater i stedet for hemmelige nøgler.
>* [Få mere at vide om at hente adgangstoken fra Azure AD ved hjælp af hemmelige nøgler eller certifikater](/azure/architecture/multitenant-identity/client-assertion).
>* [Integrer Power BI-indhold med tjenesteprincipal og et certifikat](embed-service-principal-certificate.md).

## <a name="method"></a>Metode

Hvis du vil bruge tjenesteprincipalen og et program-id med integreret analyse, skal du følge disse trin:

1. Opret en [Microsoft Azure AD-app](/azure/active-directory/manage-apps/what-is-application-management).

    1. Opret Microsoft Azure AD-appens hemmelighed.
    
    2. Hent appens *program-id* og *programhemmelighed*.

    >[!NOTE]
    >Disse trin er beskrevet i **trin 1**. Du kan finde flere oplysninger om, hvordan du opretter en Microsoft Azure AD-app, i artiklen [Opret en Microsoft Azure ADD-app](/azure/active-directory/develop/howto-create-service-principal-portal).

2. Opret en Microsoft Azure AD-sikkerhedsgruppe.

3. Aktivér indstillingerne for Power BI-tjenesteadministration.

4. Føj tjenesteprincipalen til dit arbejdsområde.

5. Integrer dit indhold.

> [!IMPORTANT]
> Når du aktiverer en tjenesteprincipal, der skal bruges med Power BI, er AD-tilladelserne for programmet ikke længere gældende. Tilladelserne for programmet administreres derefter via Power BI-administrationsportalen.

## <a name="step-1---create-an-azure-ad-app"></a>Trin 1 – Opret en Microsoft Azure AD-app

Opret en Microsoft Azure AD-app ved hjælp af en af disse metoder:
* Opret appen i [Microsoft Azure-portalen](https://portal.azure.com/#allservices)
* Opret appen ved hjælp af [PowerShell-](/powershell/azure/create-azure-service-principal-azureps?view=azps-3.6.1).

### <a name="creating-an-azure-ad-app-in-the-microsoft-azure-portal"></a>Oprettelse af en Microsoft Azure AD-app i Microsoft Azure-portalen

[!INCLUDE[service create app](../../includes/service-principal-create-app.md)]

7. Klik på fanen **Certifikater og hemmeligheder**.

     ![Skærmbillede, der viser ruden Certifikater og hemmeligheder for en app på Azure Portal.](media/embed-service-principal/certificates-and-secrets.png)


8. Klik på **Ny klienthemmelighed**

    ![ny klienthemmelighed](media/embed-service-principal/new-client-secret.png)

9. Angiv en beskrivelse i vinduet *Tilføj klienthemmelighed*, angiv, hvornår klientens hemmelighed skal udløbe, og klik på **Tilføj**.

10. Kopiér og gem værdien for *Klienthemmelighed*.

    ![værdi for klienthemmelighed](media/embed-service-principal/client-secret-value.png)

    >[!NOTE]
    >Når du forlader dette vindue, skjules værdien for klienthemmeligheden, og du kan ikke se eller kopiere den igen.

### <a name="creating-an-azure-ad-app-using-powershell"></a>Oprettelse af en Microsoft Azure AD-app ved hjælp af PowerShell

Dette afsnit indeholder et eksempelscript til oprettelse af en ny Microsoft Azure AD-app ved hjælp af [PowerShell](/powershell/azure/create-azure-service-principal-azureps?view=azps-1.1.0).

```powershell
# The app ID - $app.appid
# The service principal object ID - $sp.objectId
# The app key - $key.value

# Sign in as a user that's allowed to create an app
Connect-AzureAD

# Create a new Azure AD web application
$app = New-AzureADApplication -DisplayName "testApp1" -Homepage "https://localhost:44322" -ReplyUrls "https://localhost:44322"

# Creates a service principal
$sp = New-AzureADServicePrincipal -AppId $app.AppId

# Get the service principal key
$key = New-AzureADServicePrincipalPasswordCredential -ObjectId $sp.ObjectId
```

## <a name="step-2---create-an-azure-ad-security-group"></a>Trin 2 – Opret en Microsoft Azure AD-sikkerhedsgruppe

Din tjenesteprincipal har ikke adgang til Power BI-indholdet og API'erne. Hvis du vil give tjenesteprincipalen adgang, skal du oprette en sikkerhedsgruppe i Microsoft Azure AD og tilføje den tjenesteprincipal, du har oprettet til den pågældende sikkerhedsgruppe.

Du kan oprette en Microsoft Azure AD-sikkerhedsgruppe på to måder:
* Manuelt (i Azure)
* Brug af PowerShell

### <a name="create-a-security-group-manually"></a>Opret en sikkerhedsgruppe manuelt

Hvis du vil oprette en Azure-sikkerhedsgruppe manuelt, skal du følge vejledningen i artiklen [Opret en basisgruppe, og tilføj medlemmer ved hjælp af Azure Active Directory (Create a basic group and add members using Azure Active Directory)](/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal). 

### <a name="create-a-security-group-using-powershell"></a>Opret en sikkerhedsgruppe ved hjælp af PowerShell

Nedenfor er et eksempelscript, der kan bruges til at oprette en ny sikkerhedsgruppe og føje et program til den pågældende sikkerhedsgruppe.

>[!NOTE]
>Hvis du vil give tjenesteprincipaler adgang til hele organisationen, skal du springe dette trin over.

```powershell
# Required to sign in as admin
Connect-AzureAD

# Create an Azure AD security group
$group = New-AzureADGroup -DisplayName <Group display name> -SecurityEnabled $true -MailEnabled $false -MailNickName notSet

# Add the service principal to the group
Add-AzureADGroupMember -ObjectId $($group.ObjectId) -RefObjectId $($sp.ObjectId)
```

## <a name="step-3---enable-the-power-bi-service-admin-settings"></a>Trin 3 – Aktivér indstillingerne for Power BI-tjenesteadministration

Hvis en Microsoft Azure AD-app skal kunne få adgang til Power BI-indholdet og API'erne, skal en Power BI-administrator have mulighed for at aktivere adgangen til tjenesteprincipalen i Power BI-administrationsportalen.

Føj den sikkerhedsgruppe, du oprettede i Microsoft Azure AD, til det specifikke afsnit for sikkerhedsgruppen under **Indstillinger for udvikler**.

>[!IMPORTANT]
>Tjenesteprincipalerne har adgang til alle de lejerindstillinger, de er aktiveret for. Afhængigt af administratorindstillingerne omfatter dette specifikke sikkerhedsgrupper eller hele organisationen.
>
>Hvis du vil begrænse tjenesteprincipalers adgang til specifikke lejerindstillinger, skal du kun give adgang til specifikke sikkerhedsgrupper. Du kan også oprette en dedikeret sikkerhedsgruppe til tjenesteprincipaler og udelukke den fra de ønskede lejerindstillinger.

![Administrationsportal](media/embed-service-principal/admin-portal.png)

## <a name="step-4---add-the-service-principal-to-your-workspace"></a>Trin 4 – Føj tjenesteprincipalen til dit arbejdsområde

Hvis du vil aktivere dine Microsoft Azure AD-adgangsartefakter, f. eks. rapporter, dashboards og datasæt i Power BI-tjenesten, skal du tilføje tjenestens principalenhed som medlem eller administrator til dit arbejdsområde.

>[!NOTE]
>Dette afsnit indeholder instruktioner til brugergrænsefladen. Du kan også føje en tjenesteprincipal til et arbejdsområde ved hjælp af [Grupper – Tilføj API for gruppebruger](/rest/api/power-bi/groups/addgroupuser).

1. Rul til det arbejdsområde, du vil aktivere adgang til, og vælg **Adgang til arbejdsområde** i menuen **Mere**.

    ![Indstillinger for arbejdsområde](media/embed-service-principal/workspace-access.png)

2. Tilføj tjenesteprincipalen som **Administrator** eller **Medlem** til det nye arbejdsområde.

    ![Arbejdsområdeadministrator](media/embed-service-principal/add-service-principal-in-the-UI.png)

## <a name="step-5---embed-your-content"></a>Trin 5 – Integrer dit indhold

Du kan integrere dit indhold i et eksempelprogram eller i dit eget program.

* [Integrer indhold ved hjælp af eksempelprogrammet](embed-sample-for-customers.md#embed-content-using-the-sample-application)
* [Integrer indhold i dit program](embed-sample-for-customers.md#embed-content-within-your-application)

Når dit indhold er integreret, er du klar til at [gå videre til produktionen](embed-sample-for-customers.md#move-to-production).

[!INCLUDE[service principal limitations](../../includes/service-principal-limitations.md)]

## <a name="next-steps"></a>Næste trin

>[!div class="nextstepaction"]
>[Registrer et program](register-app.md)

> [!div class="nextstepaction"]
>[Power BI Embedded til dine kunder](embed-sample-for-customers.md)

>[!div class="nextstepaction"]
>[Objekter for et program og en tjenesteprincipal i Azure Active Directory](/azure/active-directory/develop/app-objects-and-service-principals)

>[!div class="nextstepaction"]
>[Sikkerhed på rækkeniveau ved hjælp af datagateway i det lokale miljø med tjenesteprincipal](embedded-row-level-security.md#on-premises-data-gateway-with-service-principal)

>[!div class="nextstepaction"]
>[Integrer Power BI-indhold med tjenesteprincipal og et certifikat](embed-service-principal-certificate.md)