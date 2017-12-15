---
title: "Hent et datasæt for at indsætte rækker"
description: "Se, hvordan du overfører data – hent et datasæt for at indsætte rækker i en Power BI-tabel"
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
ms.openlocfilehash: f0ca594b6f87ab2e186909f10a8ba4b7e1bce062
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 11/15/2017
---
# <a name="step-4-get-a-dataset-to-add-rows-into-a-power-bi-table"></a>Trin 4: Hent et datasæt for at indsætte rækker i en Power BI-tabel
Denne artikel er en del af en trinvis vejledning til, hvordan du [overfører data til et datasæt](walkthrough-push-data.md).

På **trin 3** i overførslen af data til et datasæt, [Opret et datasæt i Power BI](walkthrough-push-data-create-dataset.md), kaldte du handlingen [Create Dataset](https://msdn.microsoft.com/library/mt203562.aspx) for at oprette et datasæt i Power BI. På dette trin skal du bruge handlingen [Get Datasets](https://msdn.microsoft.com/library/mt203567.aspx) og Newtonsoft.Json til at hente et datasæt-id. Du kan bruge datasættet på trin 4 til at indsætte rækker i et datasæt. Hvis du vil se eksempler på, hvordan du kan bruge Power BI REST-API'en, skal du se [Power BI REST-API på APIARY](http://docs.powerbi.apiary.io/).

Hvis du vil overføre data til et Power BI-datasæt, skal du henvise til tabellen i datasættet. Hvis du vil henvise til en tabel i et datasæt, skal du først hente et **datasæt-id**. Du henter et **datasæt-id** ved hjælp af handlingen [Get Dataset](https://msdn.microsoft.com/library/mt203567.aspx). Handlingen **Get Dataset** returnerer en JSON-streng, der indeholder en liste over alle datasæt i Power BI. Den anbefalede måde at deserialisere en JSON-streng er med [Newtonsoft.Json](http://www.newtonsoft.com/json).

Sådan henter du et datasæt.

## <a name="get-a-power-bi-dataset"></a>Hent et Power BI-datasæt
> **Bemærk**! Før du begynder, skal du kontrollere, at du har fulgt de foregående trin i vejledningen til, [hvordan du overfører data til et datasæt](walkthrough-push-data.md).
> 
> 

1. Installer pakken Newtonsoft.Json NuGet i projektet Console Application, som du oprettede i Trin 2: Vejledning til overførsel af data, [Hent et adgangstoken til godkendelse](walkthrough-push-data-get-token.md). Sådan installerer du pakken:
   
     a. I Visual Studio 2015 skal du vælge **Tools** > **NuGet Package Manager** > **Package Manager Console**.
   
     b. Angiv Install-Package Newtonsoft.Json i **Package Manager Console**.
2. Når pakken er installeret, skal du indsætte **using Newtonsoft.Json;** i Program.cs.
3. Tilføj koden nedenfor i Program.cs for at hente et **datasæt-id**.
4. Kør konsolprogrammet, og log på din Power BI-konto. Du bør kunne se **Dataset ID:** efterfulgt af et id i konsolvinduet.

**Eksempel på at hente et datasæt**

Indsæt denne kode i Program.cs.

* In static void Main(string[] args):
  
  ```
  static void Main(string[] args)
  {
  
    //Get an authentication access token
    token = GetToken();
  
    //Create a dataset in Power BI
    CreateDataset();
  
    //Get a dataset to add rows into a Power BI table
    string datasetId = GetDataset();
  }
  ```
* Tilføj en GetDatset()-metode:
  
  ```
    #region Get a dataset to add rows into a Power BI table
    private static string GetDataset()
    {
        string powerBIDatasetsApiUrl = "https://api.powerbi.com/v1.0/myorg/datasets";
        //POST web request to create a dataset.
        //To create a Dataset in a group, use the Groups uri: https://api.PowerBI.com/v1.0/myorg/groups/{group_id}/datasets
        HttpWebRequest request = System.Net.WebRequest.Create(powerBIDatasetsApiUrl) as System.Net.HttpWebRequest;
        request.KeepAlive = true;
        request.Method = "GET";
        request.ContentLength = 0;
        request.ContentType = "application/json";
  
        //Add token to the request header
        request.Headers.Add("Authorization", String.Format("Bearer {0}", token));
  
        string datasetId = string.Empty;
        //Get HttpWebResponse from GET request
        using (HttpWebResponse httpResponse = request.GetResponse() as System.Net.HttpWebResponse)
        {
            //Get StreamReader that holds the response stream
            using (StreamReader reader = new System.IO.StreamReader(httpResponse.GetResponseStream()))
            {
                string responseContent = reader.ReadToEnd();
  
                //TODO: Install NuGet Newtonsoft.Json package: Install-Package Newtonsoft.Json
                //and add using Newtonsoft.Json
                var results = JsonConvert.DeserializeObject<dynamic>(responseContent);
  
                //Get the first id
                datasetId = results["value"][0]["id"];
  
                Console.WriteLine(String.Format("Dataset ID: {0}", datasetId));
                Console.ReadLine();
  
                return datasetId;
            }
        }
    }
    #endregion
  ```

Det næste trin viser dig, hvordan du [indsætter rækker i en Power BI-tabel](walkthrough-push-data-add-rows.md).

Nedenfor kan du se den [komplette kodeliste](#code).

<a name="code"/>

## <a name="complete-code-listing"></a>Komplet kodeliste
    using System;
    using Microsoft.IdentityModel.Clients.ActiveDirectory;
    using System.Net;
    using System.IO;
    using Newtonsoft.Json;

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

                //Get a dataset to add rows into a Power BI table
                string datasetId = GetDataset();

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

            #region Get a dataset to add rows into a Power BI table
            private static string GetDataset()
            {
                string powerBIDatasetsApiUrl = "https://api.powerbi.com/v1.0/myorg/datasets";
                //POST web request to create a dataset.
                //To create a Dataset in a group, use the Groups uri: https://api.PowerBI.com/v1.0/myorg/groups/{group_id}/datasets
                HttpWebRequest request = System.Net.WebRequest.Create(powerBIDatasetsApiUrl) as System.Net.HttpWebRequest;
                request.KeepAlive = true;
                request.Method = "GET";
                request.ContentLength = 0;
                request.ContentType = "application/json";

                //Add token to the request header
                request.Headers.Add("Authorization", String.Format("Bearer {0}", token));

                string datasetId = string.Empty;
                //Get HttpWebResponse from GET request
                using (HttpWebResponse httpResponse = request.GetResponse() as System.Net.HttpWebResponse)
                {
                    //Get StreamReader that holds the response stream
                    using (StreamReader reader = new System.IO.StreamReader(httpResponse.GetResponseStream()))
                    {
                        string responseContent = reader.ReadToEnd();

                        //TODO: Install NuGet Newtonsoft.Json package: Install-Package Newtonsoft.Json
                        //and add using Newtonsoft.Json
                        var results = JsonConvert.DeserializeObject<dynamic>(responseContent);

                        //Get the first id
                        datasetId = results["value"][0]["id"];

                        Console.WriteLine(String.Format("Dataset ID: {0}", datasetId));
                        Console.ReadLine();

                        return datasetId;
                    }
                }
            }
            #endregion
        }
    }

[Næste trin >](walkthrough-push-data-add-rows.md)

## <a name="next-steps"></a>Næste trin
[Indsæt rækker i en Power BI-tabel](walkthrough-push-data-add-rows.md)  
[Newtonsoft.Json](http://www.newtonsoft.com/json)  
[Hent datasæt](https://msdn.microsoft.com/library/mt203567.aspx)  
[Overfør data til Power BI](walkthrough-push-data.md)  
[Oversigt over Power BI REST-API'en](overview-of-power-bi-rest-api.md)  
[Power BI REST-API-reference](https://msdn.microsoft.com/library/mt147898.aspx)  
[Power BI REST-API på APIARY](http://docs.powerbi.apiary.io/)  

Har du flere spørgsmål? [Prøv Power BI-community'et](http://community.powerbi.com/)
