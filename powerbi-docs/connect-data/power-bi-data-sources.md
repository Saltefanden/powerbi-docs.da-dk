---
title: Power BI-datakilder
description: Denne artikel indeholder en liste over de datakilder, som Power BI understøtter, herunder oplysninger om DirectQuery og datagatewayen i det lokale miljø.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 11/17/2020
ms.author: davidi
ms.openlocfilehash: 11f9db0282cd0b302c5293ca59dd44c87dcdb955
ms.sourcegitcommit: 5240990f998851c4854eb565de681099264c5a61
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 11/18/2020
ms.locfileid: "94719046"
---
# <a name="power-bi-data-sources"></a>Power BI-datakilder

Følgende tabel indeholder de datakilder, som Power BI understøtter for datasæt, herunder oplysninger om DirectQuery og datagatewayen i det lokale miljø. Du kan finde oplysninger om dataflow under [Opret forbindelse til datakilder for Power BI-dataflow](../transform-model/dataflows/dataflows-configure-consume.md).

| Datakilde | Opret forbindelse fra skrivebord | Opret forbindelse og opdater fra tjenesten | DirectQuery/direkte forbindelse | Gateway (understøttes) | Gateway (påkrævet) | Power BI-dataflow |
|---|---|---|---|---|---|---|---|
| Access-database | Ja | Ja | Nej | Ja <sup>1</sup> | Ja | Ja |
| ActiveDirectory | Ja | Ja | Nej | Ja | Ja | Ja |
| Adobe Analytics | Ja | Ja | Nej | Nej | Nej | Nej |
| Amazon Redshift | Ja | Ja | Ja | Ja | Nej | Ja |
| appFigures | Ja | Ja | Nej | Nej | Nej | Nej |
| AtScale-kuber | Ja | Ja | Ja | Ja | Nej | Nej |
| Azure Analysis Services | Ja | Ja | Ja | Nej | Nej | Nej |
| Azure Blob Storage | Ja | Ja | Nej | Ja | Nej | Ja |
| Azure Cosmos DB | Ja | Ja | Nej | Nej | Nej | Nej |
| Azure Cost Management | Ja | Ja | Nej | Nej | Nej | Nej |
| Azure Data Explorer (kusto) | Ja | Ja | Ja | Ja | Nej | Ja |
| Azure Data Lake Storage Gen1 | Ja | Ja | Nej | Nej | Nej | Nej |
| Azure Data Lake Storage Gen2 | Ja | Ja | Nej | Ja | Nej | Ja |
| Azure DevOps | Ja | Ja | Nej | Nej | Nej | Nej |
| Azure DevOps Server | Ja | Ja | Nej | Ja | Ja | Nej |
| Azure HDInsight (HDFS) | Ja | Ja | Nej | Nej | Nej | Nej |
| Azure HDInsight Spark | Ja | Ja | Ja | Nej | Nej | Ja |
| Azure SQL Database | Ja | Ja | Ja | Ja | Nej | Ja |
| Azure SQL Data Warehouse | Ja | Ja | Ja | Ja | Nej | Ja |
| Azure Table Storage | Ja | Ja | Nej | Ja | Nej | Ja |
| BI Connector | Ja | Ja | Ja | Ja | Ja | Nej |
| BI360 – Budgeting & Financial Reporting | Ja | Ja | Nej | Nej | Nej | Nej |
| Common Data Service | Ja | Ja | Nej | Nej | Nej | Ja |
| Data.World – Hent datasæt | Ja | Ja | Nej | Nej | Nej | Nej |
| Denodo | Ja | Ja | Ja | Ja | Ja | Nej |
| Dremio | Ja | Ja | Ja | Ja | Ja | Nej |
| Dynamics 365 (online) | Ja | Ja | Nej | Nej | Nej | Nej |
| Dynamics 365 Business Central | Ja | Ja | Nej | Nej | Nej | Nej |
| Dynamics 365 Business Central (i det lokale miljø) | Ja | Ja | Nej | Nej | Nej | Nej |
| Dynamics 365 Customer Insights | Ja | Ja | Nej | Nej | Nej | Nej |
| Dynamics NAV | Ja | Ja | Nej | Nej | Nej | Nej |
| Emigo-datakilde | Ja | Ja | Nej | Nej | Nej | Nej |
| Entersoft Business Suite | Ja | Ja | Nej | Nej | Nej | Nej |
| Essbase | Ja | Ja | Ja | Ja | Ja | Nej |
| Exasol | Ja | Ja | Ja | Ja | Ja | Nej |
| Excel | Ja <sup>3</sup> | Ja <sup>3</sup> | Nej | Ja <sup>3</sup> | Nej <sup>4</sup> | Yes |
| Facebook | Ja | Ja | Nej | Nej | Nej | Nej |
| Fil | Ja | Ja | Nej | Ja | Ja | Ja |
| Mappe | Ja | Ja | Nej | Ja | Ja | Ja |
| GitHub | Ja | Ja | Nej | Nej | Nej | Nej |
| Google Analytics | Ja | Ja | Nej | Nej | Nej | Nej |
| Google BigQuery | Ja | Ja | Ja | Ja | Nej | Ja |
| Hadoop File (HDFS) | Ja | Nej | Nej | Nej | Nej | Nej |
| Hive LLAP | Ja | Ja | Ja | Ja | Nej | Nej |
| Interaktiv HDInsight-forespørgsel | Ja | Ja | Ja | Nej | Nej | Nej |
| IBM DB2 | Ja | Ja | Ja | Ja | Nej | Ja |
| IBM Informix Database | Ja | Ja | Nej | Ja | Nej | Nej |
| IBM Netezza | Ja | Ja | Ja | Ja | Ja | Nej |
| Impala | Ja | Ja | Ja | Ja | Ja | Ja |
| Indexima | Ja | Ja | Ja | Ja | Ja | Nej |
| Industrial App Store | Ja | Ja | Nej | Nej | Nej | Nej |
| Information Grid | Ja | Ja | Nej | Nej | Nej | Nej |
| Intersystems IRIS | Ja | Ja | Ja | Ja | Ja | Nej |
| Intune Data Warehouse | Ja | Ja | Nej | Nej | Nej | Nej |
| Jethro ODBC | Ja | Ja | Ja | Ja | Ja | Nej |
| JSON | Ja | Ja | Nej | Ja** | Nej <sup>4</sup> | Ja |
| Kyligence Enterprise | Ja | Ja | Ja | Ja | Ja | Nej |
| MailChimp | Ja | Ja | Nej | Nej | Nej | Nej |
| Marketo | Ja | Ja | Nej | Nej | Nej | Nej |
| MarkLogic ODBC | Ja | Ja | Ja | Ja | Ja | Nej |
| Microsoft Azure Consumption Insights | Ja | Ja | Nej | Nej | Nej | Nej |
| Microsoft Exchange | Ja | Ja | Nej | Ja | Nej | Nej |
| Microsoft Exchange Online | Ja | Ja | Nej | Nej | Nej | Ja |
| Microsoft Graph Security | Ja | Ja | Nej | Ja | Nej | Nej |
| Mixpanel | Ja | Ja | Nej | Nej | Nej | Nej |
| MySQL | Ja | Ja | Nej | Ja | Ja | Ja |
| OData | Ja | Ja <sup>7</sup> | Nej | Ja | Nej | Ja |
| ODBC | Ja | Ja | Nej | Ja | Ja | Ja |
| OleDb | Ja | Ja | Nej | Ja | Ja | Nej |
| Oracle | Ja | Ja | Ja | Ja | Ja | Ja |
| Paxata <sup>8</sup> | Ja | Ja | Nej | Ja | Nej | Nej |
| PDF | Ja | Ja | Nej | Ja | Nej <sup>4</sup> | Yes |
| Planview Enterprise One – CTM | Ja | Ja | Nej | Nej | Nej | Nej |
| Planview Enterprise One – PRM | Ja | Ja | Nej | Nej | Nej | Nej |
| Planview Projectplace | Ja | Ja | Nej | Nej | Nej | Nej |
| PostgreSQL | Ja | Ja | Ja | Ja | Nej | Ja |
| Power BI-dataflow | Ja | Ja | Nej | Nej | Nej | Ja |
| Power BI-datasæt | Ja | Ja | Ja | Nej | Nej | Nej |
| Dataflow for Power Platform | Ja | Ja | Nej | Nej | Nej | Ja |
| Python-script | Ja | Ja <sup>5</sup> | Nej | Ja <sup>5</sup> | Ja | Nej |
| QubolePresto | Ja | Ja | Ja | Ja | Ja | Nej |
| Quick Base | Ja | Ja | Nej | Ja | Ja | Nej |
| QuickBooks Online | Ja | Ja | Nej | Nej | Nej | Nej |
| R-script | Ja | Ja <sup>5</sup> | Nej | Ja <sup>5</sup> | Nej | Nej |
| Roamler | Ja | Ja | Nej | Ja | Nej | Nej |
| Salesforce-objekter | Ja | Ja | Nej | Nej | Nej | Ja |
| Salesforce-rapporter | Ja | Ja | Nej | Nej | Nej | Ja |
| SAP Business Warehouse-meddelelsesserver | Ja | Ja | Ja | Ja | Ja | Ja |
| SAP Business Warehouse-server | Ja | Ja | Ja | Ja | Ja | Ja |
| SAP HANA | Ja | Ja | Ja | Ja | Ja | Yes |
| SharePoint-mappe | Ja | Ja | Nej | Ja | Nej <sup>4</sup> | Ja |
| SharePoint-liste | Ja | Ja | Nej | Ja | Nej <sup>4</sup> | Ja |
| SharePoint Online-liste | Ja | Ja | Nej | Ja | Nej | Ja |
| Smartsheet | Ja | Ja | Nej | Nej | Nej | Ja |
| Snowflake | Ja | Ja | Ja | Ja | Nej | Ja |
| Spark | Ja | Ja | Ja | Ja | Nej | Ja |
| SparkPost | Ja | Ja | Nej | Nej | Nej | Nej |
| SQL Server | Ja | Ja | Ja | Ja | Ja | Ja |
| SQL Server Analysis Services | Ja | Ja | Ja | Ja | Ja | Nej |
| Stripe | Ja | Ja | Nej | Nej | Nej | Nej |
| SurveyMonkey | Ja | Ja | Nej | Ja | Nej | Nej |
| SweetIQ | Ja | Ja | Nej | Nej | Nej | Nej |
| Sybase | Ja | Ja | Nej | Ja | Ja | Ja |
| TeamDesk | Ja | Ja | Nej | Ja | Nej | Nej |
| Tenforce | Ja | Ja | Nej | Nej | Nej | Nej |
| Teradata | Ja | Ja | Ja | Ja | Ja | Yes |
| Tekst/CSV | Ja | Ja | Nej | Ja | Nej <sup>4</sup> | Yes |
| Twilio | Ja | Ja | Nej | Nej | Nej | Nej |
| tyGraph | Ja | Ja | Nej | Nej | Nej | Nej |
| Vertica | Ja | Ja | Ja | Ja | Ja | Yes |
| Web | Ja | Ja | Nej | Ja | Ja <sup>6</sup> | Yes |
| Webtrends | Ja | Ja | Nej | Nej | Nej | Nej |
| Workforce Dimensions | Ja | Ja | Nej | Ja | Nej | Nej |
| XML | Ja | Ja | Nej | Ja | Nej <sup>4</sup> | Yes |
| Zendesk | Ja | Ja | Nej | Nej | Nej | Nej |
| | | | | | | | |

<sup>1</sup> Understøttes med [ACE OLEDB-provideren](https://www.microsoft.com/download/details.aspx?id=54920) installeret på samme maskine som gatewayen.

<sup>3</sup> Filer af typen Excel 1997-2003 (.xls) kræver [ACE OLEDB-provideren](https://www.microsoft.com/download/details.aspx?id=54920).

<sup>4</sup> Kræves til teknologiversionen i det lokale miljø.

<sup>5</sup> Understøttes kun med den [personlige gateway](service-gateway-personal-mode.md).

<sup>6</sup> Kræves til HTML, XLS og Access-databaser

<sup>7</sup> Power BI-tjenesten understøtter ikke generisk OAuth2.

<sup>8</sup> Paxata understøttes i den version af Power BI Desktop, der er optimeret til Power BI-rapportserver. Den understøttes ikke i Power BI-rapporter, der er publiceret til Power BI-rapportserver. Du finder listen over understøttede datakilder i [Power BI-rapportdatakilderne på Power BI-rapportserver](../report-server/data-sources.md).

## <a name="considerations-and-limitations"></a>Overvejelser og begrænsninger

- Mange dataconnectors til Power BI Desktop kræver Internet Explorer 10 (eller nyere) til godkendelse. 
- Nogle datakilder, som er tilgængelige i Power BI Desktop, er optimeret til Power BI-rapportserver, men understøttes ikke, når der publiceres til Power BI-rapportserver. Du finder listen over understøttede datakilder i [Power BI-rapportdatakilderne på Power BI-rapportserver](../report-server/data-sources.md).

## <a name="single-sign-on-sso-for-directquery-sources"></a>Enkeltlogon til DirectQuery-kilder

Når indstillingen for enkeltlogon er aktiveret, og dine brugere får adgang til rapporter, som er baseret på datakilden, sender Power BI deres godkendte Azure AD-legitimationsoplysninger i forespørgslerne til den underliggende datakilde. På den måde kan Power BI overholde de sikkerhedsindstillinger, der er konfigureret på datakildeniveauet.
Indstillingen for SSO gælder for alle datasæt, der bruger denne datakilde. Den påvirker ikke den godkendelsesmetode, der bruges til import af scenarier. Følgende datakilder understøtter enkeltlogon for forbindelser via DirectQuery:

- Azure SQL Database
- Azure SQL Data Warehouse
- Impala
- SAP HANA
- SAP BW
- SAP BW-meddelelsesserver
- Snowflake
- Spark
- SQL Server
- Teradata

## <a name="next-steps"></a>Næste trin

[Opret forbindelse til data i Power BI Desktop](desktop-quickstart-connect-to-data.md)  
[Brug af DirectQuery in Power BI](desktop-directquery-about.md)  
[Dynamiske data i SQL Server Analysis Services i Power BI](sql-server-analysis-services-tabular-data.md)  
[Hvad er en datagateway i det lokale miljø?](service-gateway-onprem.md)  
[Power BI-rapportdatakilder på Power BI-rapportserver](../report-server/data-sources.md)
