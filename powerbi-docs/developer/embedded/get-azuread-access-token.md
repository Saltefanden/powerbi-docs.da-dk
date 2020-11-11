---
title: Godkend brugere, og få et Azure AD-adgangstoken til din applikation
description: Få mere at vide om, hvordan du registrerer et program i Azure Active Directory, som skal bruges til at integrere Power BI-indhold.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: how-to
ms.date: 06/04/2019
ms.openlocfilehash: 0743a7ac0d12cba8bbde54464a275a78f7c88eff
ms.sourcegitcommit: 37bd34053557089c4fbf0e05f78e959609966561
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 11/10/2020
ms.locfileid: "94396696"
---
# <a name="get-an-azure-ad-access-token-for-your-power-bi-application"></a>Få et Azure AD-adgangstoken til dit Power BI-program

I denne artikel får du mere at vide om, hvordan du godkender brugere i dit Power BI-program og henter et adgangstoken, der skal bruges sammen med [Power BI REST-API'en](/rest/api/power-bi/).

Før din app kalder Power BI REST-API'en, skal du have et Azure AD- **adgangstoken til godkendelse** (Azure Active Directory). Et adgangstoken bruges til at få adgang til Power BI-dashboards, -felter og -rapporter. Du kan få mere at vide i [Godkend adgang til Azure Active Directory-webprogrammer ved hjælp af flowet til tildeling af OAuth 2.0.-kode](/azure/active-directory/develop/v1-protocols-oauth-code).

Adgangstokenet hentes på forskellige måder, afhængigt af hvordan du integrerer indhold. I denne artikel bruges to forskellige metoder.

## <a name="access-token-for-power-bi-users-user-owns-data"></a>Adgangstoken til Power BI-brugere (brugeren ejer data)

Dette eksempel er relateret til, når brugerne manuelt logger på Azure AD med deres organisationslogon. Denne opgave bruges, når du integrerer indhold for brugere, der har adgang til Power BI-tjenesten.

### <a name="get-an-azure-ad-authorization-code"></a>Hent en godkendelseskode fra Azure AD

Det første trin til at få et **adgangstoken** er at få en godkendelseskode fra **Azure AD**. Konstruer en forespørgselsstreng med følgende egenskaber, og omdiriger til **Azure AD**.

#### <a name="authorization-code-query-string"></a>Forespørgselsstreng til godkendelseskode

```csharp
var @params = new NameValueCollection
{
    //Azure AD will return an authorization code. 
    //See the Redirect class to see how "code" is used to AcquireTokenByAuthorizationCode
    {"response_type", "code"},

    //Client ID is used by the application to identify themselves to the users that they are requesting permissions from.
    //You get the client id when you register your Azure app.
    {"client_id", Properties.Settings.Default.ClientID},

    //Resource uri to the Power BI resource to be authorized
    // https://analysis.windows.net/powerbi/api
    {"resource", Properties.Settings.Default.PowerBiAPI},

    //After user authenticates, Azure AD will redirect back to the web app
    {"redirect_uri", "https://localhost:13526/Redirect"}
};
```

Når du har konstrueret en forespørgselsstreng, omdirigerer du til **Azure AD** for at hente en **godkendelseskode**.  Nedenfor kan du se en komplet C#-metode til at konstruere en forespørgselsstreng til en **godkendelseskode** og omdirigere til **Azure AD**. Du kan derefter bruge **godkendelseskoden** til at få et **adgangstoken**.

I redirect.aspx.cs kaldes [AuthenticationContext.AcquireTokenByAuthorizationCode](/dotnet/api/microsoft.identitymodel.clients.activedirectory.authenticationcontext.acquiretokenbyauthorizationcodeasync#Microsoft_IdentityModel_Clients_ActiveDirectory_AuthenticationContext_AcquireTokenByAuthorizationCodeAsync_System_String_System_Uri_Microsoft_IdentityModel_Clients_ActiveDirectory_ClientCredential_System_String_) for at generere tokenet.

#### <a name="get-authorization-code"></a>Hent godkendelseskode

```csharp
protected void signInButton_Click(object sender, EventArgs e)
{
    //Create a query string
    //Create a sign-in NameValueCollection for query string
    var @params = new NameValueCollection
    {
        //Azure AD will return an authorization code. 
        //See the Redirect class to see how "code" is used to AcquireTokenByAuthorizationCode
        {"response_type", "code"},

        //Client ID is used by the application to identify themselves to the users that they are requesting permissions from. 
        //You get the client id when you register your Azure app.
        {"client_id", Properties.Settings.Default.ClientID},

        //Resource uri to the Power BI resource to be authorized
        // https://analysis.windows.net/powerbi/api
        {"resource", Properties.Settings.Default.PowerBiAPI},

        //After user authenticates, Azure AD will redirect back to the web app
        {"redirect_uri", "https://localhost:13526/Redirect"}
    };

    //Create sign-in query string
    var queryString = HttpUtility.ParseQueryString(string.Empty);
    queryString.Add(@params);

    //Redirect authority
    //Authority Uri is an Azure resource that takes a client id to get an Access token
    // AADAuthorityUri = https://login.microsoftonline.com/common/
    string authorityUri = Properties.Settings.Default.AADAuthorityUri;
    var authUri = String.Format("{0}?{1}", authorityUri, queryString);
    Response.Redirect(authUri);
}
```

### <a name="get-an-access-token-from-authorization-code"></a>Få et adgangstoken fra en godkendelseskode

Når **Azure AD** omdirigerer tilbage til din webapp med en **godkendelseskode** , skal du bruge godkendelseskoden til at få et adgangstoken. Nedenfor er et C#-eksempel, som du kan bruge på omdirigeringssiden og i `Page_Load`-hændelsen til siden default.aspx.

Du kan hente navneområdet **Microsoft.IdentityModel.Clients.ActiveDirectory** fra NuGet-pakken i [Active Directory Authentication Library](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/).

```powershell
Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory
```

#### <a name="redirectaspxcs"></a>Redirect.aspx.cs

```csharp
using Microsoft.IdentityModel.Clients.ActiveDirectory;

protected void Page_Load(object sender, EventArgs e)
{
    //Redirect uri must match the redirect_uri used when requesting Authorization code.
    string redirectUri = String.Format("{0}Redirect", Properties.Settings.Default.RedirectUrl);
    string authorityUri = Properties.Settings.Default.AADAuthorityUri;

    // Get the auth code
    string code = Request.Params.GetValues(0)[0];

    // Get auth token from auth code
    TokenCache TC = new TokenCache();

    AuthenticationContext AC = new AuthenticationContext(authorityUri, TC);
    ClientCredential cc = new ClientCredential
        (Properties.Settings.Default.ClientID,
        Properties.Settings.Default.ClientSecret);

    AuthenticationResult AR = AC.AcquireTokenByAuthorizationCode(code, new Uri(redirectUri), cc);

    //Set Session "authResult" index string to the AuthenticationResult
    Session[_Default.authResultString] = AR;

    //Redirect back to Default.aspx
    Response.Redirect("/Default.aspx");
}
```

#### <a name="defaultaspx"></a>Default.aspx

```csharp
using Microsoft.IdentityModel.Clients.ActiveDirectory;

protected void Page_Load(object sender, EventArgs e)
{

    //Test for AuthenticationResult
    if (Session[authResultString] != null)
    {
        //Get the authentication result from the session
        authResult = (AuthenticationResult)Session[authResultString];

        //Show Power BI Panel
        signInStatus.Visible = true;
        signInButton.Visible = false;

        //Set user and token from authentication result
        userLabel.Text = authResult.UserInfo.DisplayableId;
        accessTokenTextbox.Text = authResult.AccessToken;
    }
}
```

## <a name="access-token-for-non-power-bi-users-app-owns-data"></a>Adgangstoken til brugere, der ikke har Power BI (appen ejer data)

Denne metode bruges typisk til programmer af ISV-typen (Independent Software Vendor), hvor appen ejer adgang til dataene. Brugerne er ikke nødvendigvis Power BI-brugere, og programmet styrer godkendelse og adgang.

### <a name="access-token-with-a-master-account"></a>Adgangstoken med en masterkonto

Til denne metode skal du bruge en enkelt *masterkonto* , der er en Power BI Pro-bruger. Legitimationsoplysningerne for denne konto er gemt i programmet. Programmet godkender til Azure AD med disse gemte legitimationsoplysninger. Den viste eksempelkode nedenfor kommer fra [eksemplet, hvor appen ejer data](https://github.com/guyinacube/PowerBI-Developer-Samples)

### <a name="access-token-with-service-principal"></a>Adgangstoken med tjenesteprincipal

I denne fremgangsmåde bruger du en [tjenesteprincipal](embed-service-principal.md), som er et **kun program** -token. Programmet godkender til Azure AD med tjenesteprincipalen. Den viste eksempelkode nedenfor kommer fra [eksemplet, hvor appen ejer data](https://github.com/guyinacube/PowerBI-Developer-Samples)

#### <a name="embedservicecs"></a>EmbedService.cs

```csharp
var AuthorityURL  = "https://login.microsoftonline.com/<TenantId>/"
var ResourceURL  = "https://analysis.windows.net/powerbi/api"
var authenticationContext = new AuthenticationContext(AuthorityUrl);
       AuthenticationResult authenticationResult = null;
       if (AuthenticationType.Equals("MasterUser"))
       {
              // Authentication using master user credentials
              var credential = new UserPasswordCredential(Username, Password);
              authenticationResult = authenticationContext.AcquireTokenAsync(ResourceUrl, ApplicationId, credential).Result;
       }
       else
       {
             // Authentication using app credentials
             var credential = new ClientCredential(ApplicationId, ApplicationSecret);
             authenticationResult = await authenticationContext.AcquireTokenAsync(ResourceUrl, credential);
       }


m_tokenCredentials = new TokenCredentials(authenticationResult.AccessToken, "Bearer");
```

## <a name="troubleshoot"></a>Fejlfind

Fejlmeddelelse: "'AuthenticationContext' indeholder ikke en definition for 'AcquireToken', og der blev ikke fundet en tilgængelig 'AcquireToken', der accepterer et første argument af typen 'AuthenticationContext' (mangler du en reference til et direktiv eller en assembly?)".

   Prøv at hente [Microsoft.IdentityModel.Clients.ActiveDirectory](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/2.22.302111727), hvis du får vist denne fejl.

## <a name="next-steps"></a>Næste trin

Nu, hvor du har et adgangstoken, kan du kalde Power BI REST-API'en for at integrere indhold. Du kan finde oplysninger under [Sådan integrerer du dit Power BI-indhold](embed-sample-for-customers.md#embed-content-within-your-application).

Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)