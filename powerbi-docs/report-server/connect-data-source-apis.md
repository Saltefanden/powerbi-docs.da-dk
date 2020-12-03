---
title: Skift forbindelsesstrenge til datakilden med PowerShell
description: Skift forbindelsesstrenge til datakilden ved hjælp af API'er i PowerShell – Power BI-rapportserver.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: how-to
ms.date: 10/26/2020
ms.openlocfilehash: 4e1947abe0fa0f17e1db92619f0aa7fba5df5575
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96415467"
---
# <a name="change-data-source-connection-strings-in-power-bi-reports-with-powershell---power-bi-report-server"></a>Skift forbindelsesstrenge til datakilden i Power BI-rapporter ved hjælp PowerShell – Power BI-rapportserver


Fra og med versionen af Power BI-rapportserver fra oktober 2020 aktiverer vi muligheden for at opdatere forbindelser for Power BI-rapporter til DirectQuery og opdatering.

> [!IMPORTANT]
> Dette er også en banebrydende ændring af, hvordan du kunne konfigurere dette i tidligere versioner. Hvis du bruger en version af Power BI-rapportserver fra før oktober 2020, kan du se [Skift af forbindelsesstrenge for datakilden i Power BI-rapporter med PowerShell – Power BI-rapportserver fra før oktober 2020](connect-data-source-apis-pre-oct-2020.md)

## <a name="prerequisites"></a>Forudsætninger:
- Download versionen af [Power BI-rapportserver og Power BI Desktop optimeret til Power BI-rapportserver](https://powerbi.microsoft.com/report-server/) fra oktober 2020.
- En rapport, der er gemt med udgivelsen af Power BI Desktop optimeret til rapportserver fra oktober 2020, med **forbedret metadata for datasæt** aktiveret.
- En rapport, der bruger parameteriserede forbindelser. Det er kun rapporter med parameteriserede forbindelser og databaser, der kan opdateres efter udgivelsen.
- Dette eksempel bruger værktøjerne til Reporting Services PowerShell. Du kan opnå det samme ved at bruge de nye REST API'er.

## <a name="create-a-report-with-parameterized-connections"></a>Opret en rapport med parameteriserede forbindelser
    
1. Opret en SQL Server-forbindelse til en server. I eksemplet nedenfor opretter vi forbindelse til den lokale vært for en database med navnet ReportServer og henter data fra ExecutionLog.

    :::image type="content" source="media/connect-data-source-apis/sql-server-connect-database.png" alt-text="Opret forbindelse til SQL Server-databasen":::

    Sådan ser M-forespørgslen ud på dette tidspunkt:

    ```
    let
        Source = Sql.Database("localhost", "ReportServer"),
        dbo_ExecutionLog3 = Source{[Schema="dbo",Item="ExecutionLog3"]}[Data]
    in
        dbo_ExecutionLog3
    ```

2. Vælg **Administrer parametre** på båndet i Power Query-editor.

    :::image type="content" source="media/connect-data-source-apis/power-query-manage-parameters.png" alt-text="Vælg Administrer parametre":::

1.  Opret parametre for servernavnet og databasenavnet.

    :::image type="content" source="media/connect-data-source-apis/report-server-manage-parameters.png" alt-text="Administrer parametre, angiv servernavn og databasenavn.":::


3. Rediger forespørgslen for den første forbindelse, og tilknyt databasen og servernavnet.

    :::image type="content" source="media/connect-data-source-apis/report-server-map-database-server.png" alt-text="Tilknyt server- og databasenavnet":::

    Nu kommer forespørgslen til at se sådan ud:

    ```
    let
        Source = Sql.Database(ServerName, Databasename),
        dbo_ExecutionLog3 = Source{[Schema="dbo",Item="ExecutionLog3"]}[Data]
    in
        dbo_ExecutionLog3
    ```
    
    4. Publicer denne rapport på serveren. I dette eksempel hedder rapporten executionlogparameter. Det følgende billede er et eksempel på en side med administration af datakilder.

    :::image type="content" source="media/connect-data-source-apis/report-server-manage-data-source-credentials.png" alt-text="Siden til administration af datakilder.":::

## <a name="update-parameters-using-the-powershell-tools"></a>Opdater parametre ved hjælp af PowerShell-værktøjerne

1. Åbn PowerShell, og installér de nyeste Reporting Services-værktøjer ved at følge vejledningen til [https://github.com/microsoft/ReportingServicesTools](https://github.com/microsoft/ReportingServicesTools).
    
2.  Hvis du vil hente parameteren til rapporten, skal du bruge den nye REST DataModelParameters-API ved hjælp af følgende PowerShell-kald:

    ```powershell
    Get-RsRestItemDataModelParameters '/executionlogparameter'

        Name         Value
        ----         -----
        ServerName   localhost
        Databasename ReportServer
    ```

3. Vi gemmer resultatet af dette kald i en variabel:

    ```powershell
    $parameters = Get-RsRestItemDataModelParameters '/executionlogparameter'
    ```

4. Denne variabel opdateres med de værdier, som vi skal ændre.
5. Vi gemmer resultatet af dette kald i en variabel:

    ```powershell
    $parameters[0].Value = 'myproductionserver'
    $parameters[1].Value = 'myproductiondatabase'
    ```

6. Med de opdaterede værdier kan vi bruge commandlet'en `Set-RsRestItemDataModelParameters` til at opdatere værdierne på serveren:

    ```powershell
    Set-RsRestItemDataModelParameters -RsItem '/executionlogparameter' -DataModelParameters $parameters
    ```

7. Når parametrene er blevet opdateret, opdaterer serveren alle datakilder, der var bundet til parametrene. Hvis du går tilbage til dialogboksen **Rediger datakilde**, kan du angive legitimationsoplysninger for den opdaterede server og databasen.

    :::image type="content" source="media/connect-data-source-apis/report-server-manage-executionlogparameter-dialog.png" alt-text="Angiv legitimationsoplysninger for den opdaterede server og databasen.":::

## <a name="next-steps"></a>Næste trin

[Sideinddelte rapportdatakilder på Power BI-rapportserver](connect-data-sources.md) 

Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
