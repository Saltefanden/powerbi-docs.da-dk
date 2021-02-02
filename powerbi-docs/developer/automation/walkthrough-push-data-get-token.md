---
title: Få et adgangstoken til godkendelse i en integreret Power BI-analyse for at få bedre integreret BI-indsigt
description: Se, hvordan du overfører data – hent et adgangstoken til godkendelse. Aktivér bedre integreret BI-indsigt ved hjælp af Power BI-integreret analyse.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: madia
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: tutorial
ms.date: 05/29/2019
ms.openlocfilehash: 8959a0ac63ff1f182bcb3544b1925529b1ad3663
ms.sourcegitcommit: 2e81649476d5cb97701f779267be59e393460097
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/02/2021
ms.locfileid: "99422392"
---
# <a name="step-2-get-an-authentication-access-token"></a>Trin 2: Hent et adgangstoken til godkendelse

Denne artikel er det andet trin i serien [Overfør data til et datasæt i Power BI](walkthrough-push-data.md).

I trin 1 [registrerede du en klientapp i Azure AD](../embedded/register-app.md). På dette trin henter du et adgangstoken til godkendelse. Power BI-apps er integreret med Azure Active Directory for at give sikker logon og godkendelse til din app. Din app bruger et token til at godkende til Azure AD og få adgang til Power BI-ressourcer.

## <a name="get-an-authentication-access-token"></a>Hent et adgangstoken til godkendelse

Før du starter, skal du sikre, at du har fuldført det [forrige trin](../embedded/register-app.md) i serien [Overfør data til et datasæt i Power BI](walkthrough-push-data.md). 

Denne fremgangsmåde kræver Visual Studio 2015 eller nyere.

1. Opret et nyt C#-projekt med et **konsolprogram** i Visual Studio 2015.

2. Installér [Azure AD-godkendelsesbiblioteket til .NET NuGet-pakker](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/2.22.302111727). Din .Net-app skal bruge denne pakke til at hente et sikkerhedstoken til godkendelse. 

     a. Vælg **Værktøjer** > **NuGet Package Manager** > **Package Manager Console**.

     b. Åbn **Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory -Version 2.21.301221612**

     c. Tilføj `using Microsoft.IdentityModel.Clients.ActiveDirectory;` i Program.cs.

3. Tilføj den eksempelkode, der er angivet efter disse trin, i Program.cs.

4. Erstat "{ClientID}" med det **klient-id**, du fik i den [tidligere artikel i serien](../embedded/register-app.md), når du har registreret din app.

5. Kør konsolprogrammet, og log på din Power BI-konto. 

   En tokenstreng bør blive vist i konsolvinduet.

**Eksempelkode til at hente et sikkerhedstoken til godkendelse**

Tilføj denne kode i Program {...}.

* En tokenvariabel til kald: 
  
  ```csharp
  private static string token = string.Empty;
  
  static void Main(string[] args)
  {
  }
  ```
* I static void Main(string[] args):
  
  ```csharp
  static void Main(string[] args)
  {
    //Get an authentication access token
    token = GetToken();
  }
  ```
* Tilføj metoden GetToken():

```csharp
       #region Get an authentication access token
       private static async Task<string> GetToken()
       {
           // TODO: Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory -Version 2.21.301221612
           // and add using Microsoft.IdentityModel.Clients.ActiveDirectory

           //The client id that Azure AD created when you registered your client app.
           string clientID = "{Client_ID}";

           //RedirectUri you used when you register your app.
           //For a client app, a redirect uri gives Azure AD more details on the application that it will authenticate.
           // You can use this redirect uri for your client app
           string redirectUri = "https://login.live.com/oauth20_desktop.srf";

           //Resource Uri for Power BI API
           string resourceUri = "https://analysis.windows.net/powerbi/api";

           //OAuth2 authority Uri
           string authorityUri = "https://login.microsoftonline.com/common/";

           //Get access token:
           // To call a Power BI REST operation, create an instance of AuthenticationContext and call AcquireToken
           // AuthenticationContext is part of the Active Directory Authentication Library NuGet package
           // To install the Active Directory Authentication Library NuGet package in Visual Studio,
           //  run "Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory" from the nuget Package Manager Console.

           // AcquireToken will acquire an Azure access token
           // Call AcquireToken to get an Azure token from Azure Active Directory token issuance endpoint
           AuthenticationContext authContext = new AuthenticationContext(authorityUri);
           var token = authContext.AcquireTokenAsync(resourceUri, clientID, new Uri(redirectUri)).Result.AccessToken;

           Console.WriteLine(token);
           Console.ReadLine();

           return token;
       }

       #endregion
```

Når du har hentet et godkendelsestoken, kan du kalde enhver Power BI-handling.

I næste artikel i serien kan du se, hvordan du [opretter et datasæt i Power BI](walkthrough-push-data-create-dataset.md).


## <a name="complete-code-listing"></a>Komplet kodeliste

```csharp
using System;
using Microsoft.IdentityModel.Clients.ActiveDirectory;

namespace walkthrough_push_data
{
    class Program
    {
        private static string token = string.Empty;

        static void Main(string[] args)
        {

            //Get an authentication access token
            token = GetToken();

        }

        #region Get an authentication access token
        private static async Task<string> GetToken()
        {
            // TODO: Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory -Version 2.21.301221612
            // and add using Microsoft.IdentityModel.Clients.ActiveDirectory

            //The client id that Azure AD created when you registered your client app.
            string clientID = "{Client_ID}";

            //RedirectUri you used when you register your app.
            //For a client app, a redirect uri gives Azure AD more details on the application that it will authenticate.
            // You can use this redirect uri for your client app
            string redirectUri = "https://login.live.com/oauth20_desktop.srf";

            //Resource Uri for Power BI API
            string resourceUri = "https://analysis.windows.net/powerbi/api";

            //OAuth2 authority Uri
            string authorityUri = "https://login.microsoftonline.com/common/";

            //Get access token:
            // To call a Power BI REST operation, create an instance of AuthenticationContext and call AcquireToken
            // AuthenticationContext is part of the Active Directory Authentication Library NuGet package
            // To install the Active Directory Authentication Library NuGet package in Visual Studio,
            //  run "Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory" from the nuget Package Manager Console.

            // AcquireToken will acquire an Azure access token
            // Call AcquireToken to get an Azure token from Azure Active Directory token issuance endpoint
            AuthenticationContext authContext = new AuthenticationContext(authorityUri);
            var token = authContext.AcquireTokenAsync(resourceUri, clientID, new Uri(redirectUri)).Result.AccessToken;

            Console.WriteLine(token);
            Console.ReadLine();

            return token;
        }

        #endregion

    }
}
```



## <a name="next-steps"></a>Næste trin

* Den næste artikel i denne serie er [Opret et datasæt i Power BI](walkthrough-push-data-create-dataset.md)
* [Oversigt over Power BI REST-API](overview-of-power-bi-rest-api.md)  
* [REST-API'er til Power BI](/rest/api/power-bi/)  

Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)