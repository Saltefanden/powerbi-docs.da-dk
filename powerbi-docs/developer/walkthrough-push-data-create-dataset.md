---
title: "Opret et datasæt"
description: "Gennemgang – Send data til et datasæt – Opret et datasæt i Power BI"
services: powerbi
documentationcenter: 
author: guyinacube
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: get-started-article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 08/10/2017
ms.author: asaxton
ms.openlocfilehash: b45a6f76a710bc158d0d1763ca10f2125164952a
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 11/15/2017
---
# <a name="step-3-create-a-dataset-in-power-bi"></a>Trin 3: Opret et datasæt i Power BI
Denne artikel er en del af en trinvis gennemgang af, hvordan du [sender data til et datasæt](walkthrough-push-data.md).

I **trin 2** af Send data til et datasæt, [Hent et adgangstoken til godkendelse](walkthrough-push-data-get-token.md), fik du et token til godkendelse til **Azure AD**. I dette trin skal du bruge dette token for at kalde handlingen [Opret datasæt](https://msdn.microsoft.com/library/mt203562.aspx).

Du kalder en REST-ressource ved at bruge en URL-adresse, som finder ressourcen, og sende en JSON-streng (JavaScript Object Notation), som beskriver datasættet, til Power BI-tjenesteressourcen. En REST-ressource identificerer den del af Power BI-tjenesten, som du vil arbejde med. For at sende data til datasættet skal målressourcen være et **datasæt**. URL-adressen, der identificerer et datasæt, er https://api.PowerBI.com/v1.0/myorg/datasets. Hvis du sender data i en gruppe, er URL-adressen https://api.PowerBI.com/v1.0/myorg/groups/{group_id}/datasets.

For at godkende en Power BI REST-handling skal du føje det token, du fik under [Hent et adgangstoken til godkendelse](walkthrough-push-data-get-token.md), til en anmodningsheader:

Når du kalder handlingen [Opret datasæt](https://msdn.microsoft.com/library/mt203562.aspx), oprettes der et nyt datasæt. Hvis du vil se eksempler på, hvordan du bruger Power BI REST-API'en, skal du se [Power BI REST-API på APIARY](http://docs.powerbi.apiary.io/).

![](media/walkthrough-push-data-create-dataset/powerbi-developer-create-dataset.png)

Sådan opretter du et datasæt i Power BI.

## <a name="create-a-dataset-in-power-bi"></a>Opret et datasæt i Power BI
> [!NOTE]
> Før du begynder, skal du kontrollere, at du har fulgt de foregående trin i gennemgangen [Send data til et datasæt](walkthrough-push-data.md).
> 
> 

1. I det konsolprogramprojekt, du oprettede under [Trin 2 – Hent et adgangstoken til godkendelse](walkthrough-push-data-get-token.md), skal du føje **using System.Net;** og **using System.IO;** til Program.cs.
2. Føj nedenstående kode til Program.cs.
3. Kør konsolprogrammet, og log på din Power BI-konto. Du bør kunne se **Datasæt oprettet** i konsolvinduet. Du kan også logge på Power BI for at se det nye datasæt.

**Send prøvedata til et datasæt**

Føj denne kode til Program.cs.

* I static void Main(string[] args):
  
    ```
    static void Main(string[] args)
    {
        //Get an authentication access token
        token = GetToken();
  
        //Create a dataset in Power BI
        CreateDataset();
    }
    ```
* Tilføj en CreateDataset()-metode:
  
    ```
    #region Create a dataset in Power BI
    private static void CreateDataset()
    {
        //TODO: Add using System.Net and using System.IO
  
        string powerBIDatasetsApiUrl = "https://api.powerbi.com/v1.0/myorg/datasets";
        //POST web request to create a dataset.
        //To create a Dataset in a group, use the Groups uri: https://api.PowerBI.com/v1.0/myorg/groups/{group_id}/datasets
        HttpWebRequest request = System.Net.WebRequest.Create(powerBIDatasetsApiUrl) as System.Net.HttpWebRequest;
        request.KeepAlive = true;
        request.Method = "POST";
        request.ContentLength = 0;
        request.ContentType = "application/json";
  
        //Add token to the request header
        request.Headers.Add("Authorization", String.Format("Bearer {0}", token));
  
        //Create dataset JSON for POST request
        string datasetJson = "{\"name\": \"SalesMarketing\", \"tables\": " +
            "[{\"name\": \"Product\", \"columns\": " +
            "[{ \"name\": \"ProductID\", \"dataType\": \"Int64\"}, " +
            "{ \"name\": \"Name\", \"dataType\": \"string\"}, " +
            "{ \"name\": \"Category\", \"dataType\": \"string\"}," +
            "{ \"name\": \"IsCompete\", \"dataType\": \"bool\"}," +
            "{ \"name\": \"ManufacturedOn\", \"dataType\": \"DateTime\"}" +
            "]}]}";
  
        //POST web request
        byte[] byteArray = System.Text.Encoding.UTF8.GetBytes(datasetJson);
        request.ContentLength = byteArray.Length;
  
        //Write JSON byte[] into a Stream
        using (Stream writer = request.GetRequestStream())
        {
            writer.Write(byteArray, 0, byteArray.Length);
  
            var response = (HttpWebResponse)request.GetResponse();
  
            Console.WriteLine(string.Format("Dataset {0}", response.StatusCode.ToString()));
  
            Console.ReadLine();
        }
    }
    #endregion
    ```

I det næste trin kan du se, hvordan du [henter et datasæt for at føje rækker til en Power BI-tabel](walkthrough-push-data-get-datasets.md).

Nedenfor kan du se den [komplette kodeliste](#code).

<a name="code"/>

## <a name="complete-code-listing"></a>Komplet kodeliste
    using System;
    using Microsoft.IdentityModel.Clients.ActiveDirectory;
    using System.Net;
    using System.IO;

    namespace walkthrough_push_data
    {
        class Program
        {
            private static string token = string.Empty;

            static void Main(string[] args)
            {

                //Get an authentication access token
                token = GetToken();

                //Create a dataset in Power BI
                CreateDataset();

            }

            #region Get an authentication access token
            private static string GetToken()
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
                string authorityUri = "https://login.windows.net/common/oauth2/authorize";

                //Get access token:
                // To call a Power BI REST operation, create an instance of AuthenticationContext and call AcquireToken
                // AuthenticationContext is part of the Active Directory Authentication Library NuGet package
                // To install the Active Directory Authentication Library NuGet package in Visual Studio,
                //  run "Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory" from the nuget Package Manager Console.

                // AcquireToken will acquire an Azure access token
                // Call AcquireToken to get an Azure token from Azure Active Directory token issuance endpoint
                AuthenticationContext authContext = new AuthenticationContext(authorityUri);
                string token = authContext.AcquireToken(resourceUri, clientID, new Uri(redirectUri)).AccessToken;

                Console.WriteLine(token);
                Console.ReadLine();

                return token;
            }

            #endregion


            #region Create a dataset in Power BI
            private static void CreateDataset()
            {
                //TODO: Add using System.Net and using System.IO

                string powerBIDatasetsApiUrl = "https://api.powerbi.com/v1.0/myorg/datasets";
                //POST web request to create a dataset.
                //To create a Dataset in a group, use the Groups uri: https://api.PowerBI.com/v1.0/myorg/groups/{group_id}/datasets
                HttpWebRequest request = System.Net.WebRequest.Create(powerBIDatasetsApiUrl) as System.Net.HttpWebRequest;
                request.KeepAlive = true;
                request.Method = "POST";
                request.ContentLength = 0;
                request.ContentType = "application/json";

                //Add token to the request header
                request.Headers.Add("Authorization", String.Format("Bearer {0}", token));

                //Create dataset JSON for POST request
                string datasetJson = "{\"name\": \"SalesMarketing\", \"tables\": " +
                    "[{\"name\": \"Product\", \"columns\": " +
                    "[{ \"name\": \"ProductID\", \"dataType\": \"Int64\"}, " +
                    "{ \"name\": \"Name\", \"dataType\": \"string\"}, " +
                    "{ \"name\": \"Category\", \"dataType\": \"string\"}," +
                    "{ \"name\": \"IsCompete\", \"dataType\": \"bool\"}," +
                    "{ \"name\": \"ManufacturedOn\", \"dataType\": \"DateTime\"}" +
                    "]}]}";

                //POST web request
                byte[] byteArray = System.Text.Encoding.UTF8.GetBytes(datasetJson);
                request.ContentLength = byteArray.Length;

                //Write JSON byte[] into a Stream
                using (Stream writer = request.GetRequestStream())
                {
                    writer.Write(byteArray, 0, byteArray.Length);

                    var response = (HttpWebResponse)request.GetResponse();

                    Console.WriteLine(string.Format("Dataset {0}", response.StatusCode.ToString()));

                    Console.ReadLine();
                }
            }
            #endregion
        }
    }


[Næste trin >](walkthrough-push-data-get-datasets.md)

## <a name="next-steps"></a>Næste trin
[Hent et datasæt for at føje rækker til en Power BI-tabel](walkthrough-push-data-get-datasets.md)  
[Hent et adgangstoken til godkendelse](walkthrough-push-data-get-token.md)  
[Opret datasæt](https://msdn.microsoft.com/library/mt203562.aspx)  
[Send data til et Power BI-dashboard](walkthrough-push-data.md)  
[Oversigt over Power BI REST-API](overview-of-power-bi-rest-api.md)  
[Reference til Power BI REST-API](https://msdn.microsoft.com/library/mt147898.aspx)  
[Power BI REST-API på APIARY](http://docs.powerbi.apiary.io/)  

Har du flere spørgsmål? [Prøv Power BI-community'et](http://community.powerbi.com/)
