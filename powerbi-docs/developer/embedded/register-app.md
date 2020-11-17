---
title: Registrer en app for at integrere Power BI-indhold
description: Få mere at vide om, hvordan du registrerer et program i Azure Active Directory, som skal bruges til at integrere Power BI-indhold.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: nishalit
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: how-to
ms.date: 04/02/2019
ms.openlocfilehash: 52e835f4ff0d3dc4cad13c2e3ecc77d254f3be9d
ms.sourcegitcommit: 5ccab484cf3532ae3a16acd5fc954b7947bd543a
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 11/06/2020
ms.locfileid: "93412186"
---
# <a name="register-an-azure-ad-application-to-use-with-power-bi"></a>Registrer et Azure AD-program, som skal bruges sammen med Power BI

Hvis du vil bruge Power BI Embedded-analyse, skal du registrere en Azure Active Directory-app i Azure. Azure Active Directory-appen opretter tilladelser til Power BI-REST-ressourcer og giver adgang til [Power BI-REST-API'er](/rest/api/power-bi/).

## <a name="determine-your-embedding-solution"></a>Fastlæg din integreringsløsning

Før du registrerer din app, skal du beslutte, hvilke af følgende løsninger der passer bedst til dig:

* Integrer indhold for dine kunder
* Integrer indhold for din organisation

### <a name="embed-for-your-customers"></a>Integrer indhold for dine kunder

Brug løsningen [Integrer indhold for dine kunder](embed-sample-for-customers.md), der også kaldes *Appen ejer data*, hvis du planlægger at oprette en app, der er designet til dine kunder. Brugerne behøver ikke at logge på Power BI eller have en Power BI-licens, for at du kan bruge din app. Din app bruger en af følgende metoder til at godkende i forhold til Power BI:

* **Masterbruger**-konto (en Power BI Pro-licens, der bruges til at logge på Power BI)

*  [Tjenesteprincipal](embed-service-principal.md)

Løsningen Integrer indhold for dine kunder bruges normalt af uafhængige softwareleverandører (ISV'er) og udviklere, der opretter programmer til tredjepart.

### <a name="embed-for-your-organization"></a>Integrer indhold for din organisation

Brug løsningen [Integrer indhold for din organisation](embed-sample-for-your-organization.md), der også kaldes *Bruger ejer data*, hvis du planlægger at oprette en app, der kræver, at brugerne skal bruge deres legitimationsoplysninger til at godkende i forhold til Power BI.

Løsningen Integrer indhold for din organisation bruges normalt af virksomheder og store organisationer og er beregnet til interne brugere.

## <a name="register-an-azure-ad-app"></a>Registrer en Microsoft Azure Active Directory-app

Den nemmeste måde at registrere en Microsoft Azure Active Directory-app på er ved hjælp af [installationsværktøjet til  Power BI-integrering](https://app.powerbi.com/embedsetup). Med værktøjet får du en hurtig registreringsproces til begge integreringsløsninger ved hjælp af en simpel grafisk grænseflade.

Hvis du opretter en *Integrer indhold for din organisation*-app og gerne vil have mere kontrol over din Microsoft Azure Active Directory-app, kan du registrere det manuelt i Azure Portal.

> [!IMPORTANT]
> Før du kan registrere et Power BI-app, skal du have en [Azure Active Directory-lejer og en organisationsbruger](create-an-azure-active-directory-tenant.md).

# <a name="embed-for-your-customers"></a>[Integrer indhold for dine kunder](#tab/customers)

I disse trin beskrives det, hvordan du registrerer en Microsoft Azure Active Directory-app til løsningen [Integrer indhold for dine kunder](embed-sample-for-customers.md) i Power BI.

[!INCLUDE[registration tool step 1](../../includes/register-tool-step-1.md)]

2. Vælg *Integrer indhold for dine kunder* i afsnittet **Vælg en integreringsløsning**.

[!INCLUDE[registration tool step 3](../../includes/register-tool-step-3.md)]

4. Udfyld følgende felter i *Trin 2 – Registrer din app*:

    * **Programnavn** – Angiv et navn til appen.

    * **API-adgang** – Vælg de Power BI-API'er (også kaldet områder), din app har brug for. Du kan bruge *Vælg alle* for at vælge alle API'erne. Du kan få flere oplysninger om Power BI-adgangstilladelser i [Tilladelser og indhold i slutpunktet for Microsoft-identitetsplatformen](/azure/active-directory/develop/v2-permissions-and-consent).

5. Vælg **Registrer**.

    Microsoft Azure Active Directory-**program-id'et** vises i feltet *Oversigt*. Kopiér denne værdi til senere brug.

[!INCLUDE[registration tool steps 6-7](../../includes/register-tool-steps-6-7.md)]

8. Vælg **Giv tilladelser**, og vælg **Accepter** i pop op-vinduet i *Trin 5 – Giv tilladelser*. Dette gør det muligt for din Microsoft Azure Active Directory-app at få adgang til de API'er, du har valgt (også kaldet områder) med den bruger, der er logget på. Denne bruger kaldes også **masterbruger**.

9. (Valgfrit) Hvis du har oprettet et Power BI-arbejdsområde og overført indhold til det ved hjælp af værktøjet, kan du nu vælge **Hent prøveprogram**. Sørg for at kopiere alle oplysningerne i feltet *Oversigt*.

[!INCLUDE[registration tool note](../../includes/register-tool-note.md)]

# <a name="embed-for-your-organization"></a>[Integrer til din organisation](#tab/organization)

I disse trin beskrives det, hvordan du registrerer en Microsoft Azure Active Directory-app til løsningen [Integrer indhold for din organisation](embed-sample-for-your-organization.md) i Power BI.

[!INCLUDE[registration tool step 1](../../includes/register-tool-step-1.md)]

2. Vælg *Integrer indhold for din organisation* i afsnittet **Vælg en integreringsløsning**.

[!INCLUDE[registration tool step 3](../../includes/register-tool-step-3.md)]

4. Udfyld følgende felter i *Trin 2 – Registrer din app*:

    * **Programnavn** – Angiv et navn til appen.

    * **URL-adresse til startsiden** – Angiv en URL-adresse til din startside.

    * **URL-adresse for omdirigering** – Ved logon omdirigeres appbrugerne til denne adresse, mens appen modtager en godkendelseskode fra Azure. Vælg en af disse indstillinger:

        * **Brug en standard-URL-adresse** – Denne indstilling vil automatisk oprette og downloade et prøveprogram til integreret analyse. Standard-URL-adressen er http://localhost:13526/.

        * **Brug en brugerdefineret URL-adresse** – Vælg denne indstilling, hvis du allerede har et program til integreret analyse, og du ved, hvad du vil bruge som omdirigerings-URL-adresse.

    * **API-adgang** – Vælg de Power BI-API'er (også kaldet områder), din app har brug for. Du kan bruge *Vælg alle* for at vælge alle API'erne. Du kan få flere oplysninger om Power BI-adgangstilladelser i [Tilladelser og indhold i slutpunktet for Microsoft-identitetsplatformen](/azure/active-directory/develop/v2-permissions-and-consent).

5. Vælg **Registrer**.

    Værdierne for **Program-id** og **Programhemmelighed** for Microsoft Azure Active Directory-appen vises i feltet *Oversigt*. Kopiér disse værdier til senere brug.

[!INCLUDE[registration tool steps 6-7](../../includes/register-tool-steps-6-7.md)]

8. (Valgfrit) Hvis du har oprettet et Power BI-arbejdsområde og overført indhold til det ved hjælp af værktøjet, kan du nu vælge **Hent prøveprogram**. Sørg for at kopiere alle oplysningerne i feltet *Oversigt*.

[!INCLUDE[registration tool note](../../includes/register-tool-note.md)]

# <a name="manual-registration"></a>[Manuel registrering](#tab/manual)

Brug kun registrering af Microsoft Azure Active Directory-appen, hvis du opretter løsningen *Integrer indhold for din organisation*. Du kan finde flere oplysninger om, hvordan du registrerer programmer i Microsoft Azure Active Directory i [Registrer en app med Azure Active Directory](/azure/active-directory/develop/quickstart-v2-register-an-app).

1. Log på [Azure-portalen](https://portal.azure.com).

2. Vælg din Microsoft Azure Active Directory-lejer ved at vælge din konto i øverste højre hjørne af siden.

3. Vælg **Appregistreringer**. Hvis du ikke kan se denne indstilling, skal du søge efter den.
 
4. Vælg *Ny registrering* i **Appregistreringer**.

5. Udfyld følgende felter:

    * **Navn** – Angiv et navn til appen.

    * **Understøttet kontotype** – Vælg, hvem der kan bruge programmet.

6. (Valgfrit) Tilføj en URL-adresse til omdirigering i **Omdirigerings-URI**.

7. Vælg **Registrer**. Når din app er registreret, sendes du videre til appens oversigtsside, hvor du kan hente *program-id'et*.

---

## <a name="change-your-azure-ad-apps-permissions"></a>Skift tilladelser for din Microsoft Azure Active Directory-app

Når du har registreret appen, kan du ændre dens tilladelser. Ændringer af tilladelser kan foretages via programmering eller i Azure Portal.

# <a name="azure"></a>[Azure](#tab/Azure)

I Azure Portal kan du få vist din app og foretage ændringer af dens tilladelser.

1. Log på [Azure-portalen](https://portal.azure.com).

2. Vælg din Microsoft Azure Active Directory-lejer ved at vælge din konto i øverste højre hjørne af siden.

3. Vælg **Appregistreringer**. Hvis du ikke kan se denne indstilling, skal du søge efter den.

4. Vælg din app på fanen **Ejede programmer**. Appen åbnes under fanen *Oversigt*, hvor du kan gennemse *program-id'et*.

5. Vælg fanen **API-tilladelser**.

6. Følg disse trin for at tilføje tilladelser:

    1. Vælg **Tilføj en tilladelse**, og vælg derefter **Power BI-tjeneste**.

    2. Vælg **Delegerede tilladelser**, og tilføj eller fjern de specifikke tilladelser, du har brug for.

    3. Vælg **Tilføj tilladelser**, når du er færdig, for at gemme dine ændringer.

7. Følg disse trin for at fjerne en tilladelse:

    1. Vælg ellipsen (...) til højre for tilladelsen.
    
    2. Vælg **Fjern tilladelse**.
    
    3. Vælg **Ja, fjern** i pop op-vinduet *Fjern tilladelse*.

# <a name="http"></a>[HTTP](#tab/HTTP)

Hvis du vil ændre dine Microsoft Azure Active Directory-apptilladelser via programmering, skal du hente de eksisterende tjeneste principaler (brugere) i din lejer. Du kan finde oplysninger om, hvordan du gør det, i [ servicePrincipal](/graph/api/resources/serviceprincipal).

1. Hvis du vil hente alle tjenesteprincipalerne i din lejer, skal du kalde `Get servicePrincipal`API'en uden `{ID}`.

2. Kig efter en tjenesteprincipal med appens *program-id* som `appId`-egenskaben.

    ```json
    Post https://graph.microsoft.com/v1.0/servicePrincipals HTTP/1.1
    Authorization: Bearer ey..qw
    Content-Type: application/json
    {
    "accountEnabled" : true,
    "appId" : "{App_Client_ID}",
    "displayName" : "{App_DisplayName}"
    }
    ```

    >[!NOTE]
    >`displayName` er valgfri.

3. Tildel Power BI-tilladelser til din app ved at tildele en af disse værdier til `consentType`:

    * `AllPrincipals` – Kan kun bruges af en Power BI-administrator til at tildele tilladelser på vegne af alle brugerne i lejeren.

    * `Principal` – Bruges til at give tilladelser på vegne af en bestemt bruger. Hvis du bruger denne indstilling, skal du føje egenskaben `principalId={User_ObjectId}` til anmodningens brødtekst.

     ```json
     Post https://graph.microsoft.com/v1.0/OAuth2PermissionGrants HTTP/1.1
     Authorization: Bearer ey..qw
     Content-Type: application/json
     {
     "clientId":"{Service_Plan_ID}",
     "consentType":"AllPrincipals",
     "resourceId":"c78a3685-1ce7-52cd-95f7-dc5aea8ec98e",
     "scope":"Dataset.ReadWrite.All Dashboard.Read.All Report.Read.All Group.Read Group.Read.All Content.Create Metadata.View_Any Dataset.Read.All Data.Alter_Any",
     "expiryTime":"2018-03-29T14:35:32.4943409+03:00",
     "startTime":"2017-03-29T14:35:32.4933413+03:00"
     }
     ```

    >[!NOTE]
    >* Hvis du bruger en **masterbruger** for at undgå at blive bedt om samtykke af Microsoft Azure Active Directory, skal du give tilladelser til masterkontoen.
    >* `resourceId` *c78a3685-1ce7-52cd-95f7-dc5aea8ec98e* er lejerafhængig og ikke universel. Denne værdi er *objectId* for programmet *Power BI-tjeneste* i Microsoft Azure Active Directory. Hvis du vil hente denne værdi fra Azure Portal, skal du gå til [Virksomhedsprogrammer > Alle programmer](https://portal.azure.com/#blade/Microsoft_AAD_IAM/StartboardApplicationsMenuBlade/AllApps) og søge efter *Power BI-tjeneste*.

4. Tildel apptilladelser til Microsoft Azure Active Directory ved at tildele en værdi til `consentType`.

    ```json
    Post https://graph.microsoft.com/v1.0/OAuth2PermissionGrants HTTP/1.1
    Authorization: Bearer ey..qw
    Content-Type: application/json
    {
    "clientId":"{Service_Plan_ID}",
    "consentType":"AllPrincipals",
    "resourceId":"61e57743-d5cf-41ba-bd1a-2b381390a3f1",
    "scope":"User.Read Directory.AccessAsUser.All",
    "expiryTime":"2018-03-29T14:35:32.4943409+03:00",
    "startTime":"2017-03-29T14:35:32.4933413+03:00"
    }
    ```

# <a name="c"></a>[C#](#tab/CSharp)

Du kan også ændre tilladelser til din Microsoft Azure Active Directory-app ved hjælp af C#. Denne metode kan være nyttig, hvis du overvejer at automatisere nogle af dine processer.

Du kan finde flere oplysninger om HTTP-anmodninger under [fanen HTTP](register-app.md?tabs=customers%2CHTTP#change-your-azure-ad-apps-permissions).

```csharp
var graphClient = GetGraphClient();

currentState.createdApp = await graphClient.Applications
    .Request()
    .AddAsync(application);

System.Threading.Thread.Sleep(2000);

var passwordCredential = new PasswordCredential
{
    DisplayName = "Client Secret Created in C#"
};

currentState.createdSecret = await graphClient.Applications[currentState.createdApp.Id]
    .AddPassword(passwordCredential)
    .Request()
    .PostAsync();

var servicePrincipal = new ServicePrincipal
{
    AppId = currentState.createdApp.AppId
};

currentState.createdServicePrincipal = await graphClient.ServicePrincipals
    .Request()
    .AddAsync(servicePrincipal);

```

---

## <a name="next-steps"></a>Næste trin

>[!div class="nextstepaction"]
>[Få et Azure AD-adgangstoken til dit Power BI-program](get-azuread-access-token.md)

Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)