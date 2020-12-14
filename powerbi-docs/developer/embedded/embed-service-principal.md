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
ms.date: 11/23/2020
ms.openlocfilehash: 41b8cfe8515efbf3cc42794afcb2562f7d0c171a
ms.sourcegitcommit: 30d0668434283c633bda9ae03bc2aca75401ab94
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/09/2020
ms.locfileid: "96907089"
---
# <a name="embed-power-bi-content-with-service-principal-and-an-application-secret"></a>Integrer Power BI-indhold med tjenesteprincipal og en programhemmelighed

Tjeneste principalen er en godkendelsesmetode, der kan bruges til at lade et Microsoft Azure AD-program få adgang indhold og API'er i Power BI-tjenesten.

Når du opretter en Azure Active Directory-app, oprettes der et [tjenesteprincipalobjekt](/azure/active-directory/develop/app-objects-and-service-principals#service-principal-object). Tjenesteprincipalobjektet, der også blot kaldes *tjenesteprincipal*, gør det muligt for Microsoft Azure AD at godkende din app. Når appen er godkendt, kan den få adgang til Microsoft Azure AD-lejerressourcer.

For at kunne godkende skal tjenesteprincipalen bruge Microsoft Azure AD-appens *program-id* og et af følgende:

* Certifikat
* Programhemmelighed

I denne artikel beskrives godkendelse af tjenesteprincipalen ved hjælp af et *program-id* og en *programhemmelighed*.

>[!NOTE]
>Azure AD anbefaler, at du beskytter dine back end-tjenester ved hjælp af certifikater i stedet for hemmelige nøgler.
>* [Få mere at vide om at hente adgangstoken fra Azure AD ved hjælp af hemmelige nøgler eller certifikater](/azure/architecture/multitenant-identity/client-assertion).
>* Du beskytter din løsning ved hjælp af et certifikat ved at fuldføre instruktionerne i denne artikel og derefter følge de trin, der er beskrevet i [Integrer Power BI-indhold med tjenesteprincipal og et certifikat](embed-service-principal-certificate.md).

## <a name="method"></a>Metode

Hvis du vil bruge en tjenesteprincipal og et program-id med integreret analyse, skal du følge disse trin:

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

* [Opret en app på Microsoft Azure Portal](embed-service-principal.md#creating-an-azure-ad-app-in-the-microsoft-azure-portal)

* [Opret appen ved hjælp af PowerShell](embed-service-principal.md#creating-an-azure-ad-app-using-powershell)

### <a name="creating-an-azure-ad-app-in-the-microsoft-azure-portal"></a>Oprettelse af en Microsoft Azure AD-app i Microsoft Azure-portalen

1. Log på [Microsoft Azure](https://ms.portal.azure.com/#allservices).

2. Søg efter **appregistreringer**, og klik på linket **Appregistreringer**.

    ![azure-appregistrering](media/embed-service-principal/azure-app-registration.png)

3. Klik på **Ny registrering**.

    ![ny registrering](media/embed-service-principal/new-registration.png)

4. Udfyld de påkrævede oplysninger:
    * **Navn** – Angiv et navn til programmet
    * **Understøttede kontotyper** – Vælg understøttede kontotyper
    * (Valgfrit) **URI til omdirigering** – Angiv en URI, hvis det er nødvendigt

5. Klik på **Registrer**.

6. Efter registrering er *program-id'et* tilgængeligt via fanen **Oversigt**. Kopiér og gem *program-id'et* til senere brug.

    ![Skærmbillede, der viser, hvor du kan få vist et program-id under fanen Oversigt.](media/embed-service-principal/application-id.png)

7. Klik på fanen **Certifikater og hemmeligheder**.

     ![Et skærmbillede, der viser ruden Certifikater og hemmeligheder for en app på Azure Portal.](media/embed-service-principal/certificates-and-secrets.png)

8. Klik på **Ny klienthemmelighed**

    ![Et skærmbillede, der viser knappen Ny klienthemmelighed i ruden Certifikater og hemmeligheder.](media/embed-service-principal/new-client-secret.png)

9. Angiv en beskrivelse i vinduet *Tilføj klienthemmelighed*, angiv, hvornår klientens hemmelighed skal udløbe, og klik på **Tilføj**.

10. Kopiér og gem værdien for *Klienthemmelighed*.

    ![Et skærmbilleder, der viser en sløret hemmelighedsværdi i ruden Certifikater og hemmeligheder.](media/embed-service-principal/client-secret-value.png)

    >[!NOTE]
    >Når du forlader dette vindue, skjules værdien for klienthemmeligheden, og du kan ikke se eller kopiere den igen.

### <a name="creating-an-azure-ad-app-using-powershell"></a>Oprettelse af en Microsoft Azure AD-app ved hjælp af PowerShell

Dette afsnit indeholder et eksempelscript til oprettelse af en ny Microsoft Azure AD-app ved hjælp af [PowerShell](/powershell/azure/create-azure-service-principal-azureps).

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
* [Manuelt (i Azure)](embed-service-principal.md#create-a-security-group-manually)
* [Brug af PowerShell](embed-service-principal.md#create-a-security-group-using-powershell)

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

>[!div class="mx-imgBorder"]
>:::image type="content" source="media/embed-service-principal/admin-portal.png" alt-text="Skærmbillede, der viser indstillinger for udviklere i administratorindstillingerne i Power BI-tjenesten.":::

## <a name="step-4---add-the-service-principal-to-your-workspace"></a>Trin 4 – Føj tjenesteprincipalen til dit arbejdsområde

Hvis du vil aktivere adgangsartefakter til din Azure AD-app, f.eks. rapporter, dashboards og datasæt i Power BI-tjenesten, skal du føje enheden for tjenesteprincipalen eller den sikkerhedsgruppe, som indeholder dine tjenesteprincipal, til dit arbejdsområde som medlem eller administrator.

>[!NOTE]
>Dette afsnit indeholder instruktioner til brugergrænsefladen. Du kan også føje en tjenesteprincipal eller en sikkerhedsgruppe til et arbejdsområde ved hjælp af [API'en Grupper – tilføj gruppebruger](/rest/api/power-bi/groups/addgroupuser).

1. Rul til det arbejdsområde, du vil aktivere adgang til, og vælg **Adgang til arbejdsområde** i menuen **Mere**.

    :::image type="content" source="media/embed-service-principal/workspace-access.png" alt-text="Skærmbillede, der viser arbejdsområdets adgangsknap i menuen Mere i et Power BI-arbejdsområde.":::

2. Tilføj en af følgende i tekstfeltet i ruden **Adgang**:

    * Din **tjenesteprincipal**. Navnet på din tjenesteprincipal er det *viste navn* for din Azure AD-app, som det vises under oversigtsfanen i din Azure AD-app.

    * Den **sikkerhedsgruppe**, der indeholder din tjenesteprincipal.

3. Vælg **Medlem** eller **Administrator** i rullemenuen.

4. Vælg **Tilføj**

## <a name="step-5---embed-your-content"></a>Trin 5 – Integrer dit indhold

Du kan [integrere dit indhold i et eksempelprogram](embed-sample-for-customers.md) eller i dit eget program.

Når dit indhold er integreret, er du klar til at [gå videre til produktionen](move-to-production.md).

>[!NOTE]
>Du beskytter dit indhold ved hjælp af et certifikat ved at fuldføre de trin, der er beskrevet i [Integrer Power BI-indhold med tjenesteprincipal og et certifikat](embed-service-principal-certificate.md).

## <a name="considerations-and-limitations"></a>Overvejelser og begrænsninger

* Tjenesteprincipalen fungerer kun med [nye arbejdsområder](../../collaborate-share/service-create-the-new-workspaces.md).
* **Mit arbejdsområde** understøttes ikke til brug sammen med tjenesteprincipalen.
* Der kræves en kapacitet for at kunne flytte til produktion.
* Du kan ikke logge på Power BI-portalen ved hjælp af en tjenesteprincipal.
* Der kræves rettigheder som Power BI-administrator for at kunne aktivere tjenesteprincipalen under Indstillinger for udvikler på Power BI-administrationsportalen.
* Programmer til [integration i din organisation](embed-sample-for-your-organization.md) kan ikke bruge en tjenesteprincipal.
* Administration af [dataflow](../../transform-model/dataflows/dataflows-introduction-self-service.md) understøttes ikke.
* Tjenesteprincipaler understøtter i øjeblikket ingen administrator-API'er.
* Når du bruger en tjenesteprincipal med en [Azure Analysis Services](/azure/analysis-services/analysis-services-overview)-datakilde, skal selve tjenesteprincipalen have tilladelser til en forekomst af Azure Analysis Services. Brug af en sikkerhedsgruppe, der indeholder tjenesteprincipalen til dette formål, fungerer ikke.

## <a name="next-steps"></a>Næste trin

>[!div class="nextstepaction"]
>[Registrer et program](register-app.md)

> [!div class="nextstepaction"]
>[Power BI Embedded til dine kunder](embed-sample-for-customers.md)

>[!div class="nextstepaction"]
>[Integrer ved hjælp af en tjenesteprincipal og et certifikat](embed-service-principal-certificate.md)

>[!div class="nextstepaction"]
>[Objekter for et program og en tjenesteprincipal i Azure Active Directory](/azure/active-directory/develop/app-objects-and-service-principals)

>[!div class="nextstepaction"]
>[Sikkerhed på rækkeniveau ved hjælp af datagateway i det lokale miljø med tjenesteprincipal](embedded-row-level-security.md#on-premises-data-gateway-with-service-principal)