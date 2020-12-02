---
title: Opret forbindelse til data med generiske grænseflader i Power BI Desktop
description: Få mere at vide om, hvordan du opretter forbindelse mellem forskellige datakilder og generiske grænseflader i Power BI Desktop
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 05/08/2019
LocalizationGroup: Connect to data
ms.openlocfilehash: b7e0ec270ad70be91d5aea598148e69e88df09f9
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96405554"
---
# <a name="connect-to-data-by-using-power-bi-desktop-generic-interfaces"></a>Opret forbindelse til data med generiske grænseflader i Power BI Desktop 

Du kan oprette forbindelse til en lang række forskellige datakilder i **Power BI Desktop** ved hjælp af de indbyggede dataforbindelser, der strækker sig lige fra **Access-databaser** til **Zendesk**-ressourcer, som vist i vinduet **Hent data**. Du kan også oprette forbindelse til mange *andre* typer datakilder for at få endnu flere muligheder for at oprette forbindelse ved hjælp af de generiske grænseflader (f.eks **ODBC** eller **REST API'er**), der er indbygget i **Power BI Desktop**.

![Skærmbillede af dialogboksen Hent data, hvor ODBC er markeret.](media/desktop-connect-using-generic-interfaces/generic-data-interfaces_1.png)

## <a name="power-bi-desktop-data-interfaces"></a>Datagrænseflader i Power BI Desktop
**Power BI Desktop** indeholder en stadig stigende samling af dataforbindelser, der er udviklet til at oprette forbindelse til en bestemt datakilde. Dataforbindelsen **SharePoint-liste** leverer f.eks. specifikke felter og understøttende oplysninger under den forbindelsessekvens, der er udviklet til **SharePoint-lister**. Det samme er gældende for de andre datakilder, der findes i det vindue, der vises, når du vælger **Hent data > Flere...**  (som vist i det forrige billede).

Desuden kan du i **Power BI Desktop** oprette forbindelse til de datakilder, der ikke er identificeret på listerne **Hent data**, ved hjælp af en af følgende generiske datagrænseflader:

* **ODBC**
* **OLE DB**
* **OData**
* **REST API'er**
* **R-Scripts**

Ved at angive de relevante parametre i de forbindelsesvinduer, som disse generiske grænseflader leverer, vil det antal datakilder, som du kan få adgang til og bruge i **Power BI Desktop**, vokse væsentligt.

Du kan finde en liste over de datakilder, disse generiske grænseflader kan få adgang til, i de følgende afsnit.

Kan du ikke finde den datakilde, du vil bruge med **Power BI Desktop**? Indsend din idé til Power BI teamets [liste over idéer og anmodninger](https://ideas.powerbi.com/).

## <a name="data-sources-accessible-through-odbc"></a>Datakilder, der er tilgængelige via ODBC
Med **ODBC**-connectoren i **Power BI Desktop** kan du importere data fra en ODBC-driver fra en tredjepart ved at angive et **datakildenavn** eller en  *forbindelsesstreng*. Du kan også vælge at angive en SQL-sætning, som skal køres mod ODBC-driveren.

![Skærmbillede af dialogboksen ODBC-connector, der viser indstillingerne DSN og Avanceret.](media/desktop-connect-using-generic-interfaces/generic-data-interfaces_2.png)

Følgende liste indeholder nogle eksempler på de datakilder, som **Power BI Desktop** kan oprette forbindelse til ved hjælp af den generiske grænseflade **ODBC**.

| Generisk connector i Power BI Desktop | Ekstern datakilde | Link til flere oplysninger |
| --- | --- | --- |
| ODBC |Cassandra |[Cassandra ODBC-driveren](https://www.simba.com/drivers/cassandra-odbc-jdbc/) |
| ODBC |Couchbase DB |[Couchbase og Power BI](https://powerbi.microsoft.com/blog/visualizing-data-from-couchbase-server-v4-using-power-bi/) |
| ODBC |DynamoDB |[DynamoDB ODBC-driveren](https://www.simba.com/drivers/dynamodb-odbc-jdbc/) |
| ODBC |Google BigQuery |[BigQuery ODBC-driveren](https://www.simba.com/drivers/bigquery-odbc-jdbc/) |
| ODBC |Hbase |[Hbase ODBC-driveren](https://www.simba.com/drivers/hbase-odbc-jdbc/) |
| ODBC |Hive |[Hive ODBC-driveren](https://www.simba.com/drivers/hive-odbc-jdbc/) |
| ODBC |IBM Netezza |[IBM Netezza-oplysninger](https://www.ibm.com/support/knowledgecenter/SSULQD_7.2.1/com.ibm.nz.datacon.doc/c_datacon_plg_overview.html) |
| ODBC |Presto |[Presto ODBC-driveren](https://www.simba.com/drivers/presto-odbc-jdbc/) |
| ODBC |Projekt Online |[Project Online-artikel](desktop-project-online-connect-to-data.md) |
| ODBC |Progress OpenEdge |[Blogindlæg om Progress OpenEdge ODBC-driveren](https://www.progress.com/blogs/connect-microsoft-power-bi-to-openedge-via-odbc-driver) |

## <a name="data-sources-accessible-through-ole-db"></a>Datakilder, der er tilgængelige via OLE DB
Med **OLE DB**-connectoren i **Power BI Desktop** kan du importere data fra en OLE DB-driver fra en tredjepart ved at angive en *forbindelsesstreng*. Du kan også vælge at angive en SQL-sætning, som skal køres mod OLE DB-driveren.

![Skærmbillede af dialogboksen OLEDB-connector, der viser Forbindelsesstreng og Avancerede indstillinger.](media/desktop-connect-using-generic-interfaces/generic-data-interfaces_3.png)

Følgende liste indeholder nogle eksempler på de datakilder, som **Power BI Desktop** kan oprette forbindelse til ved hjælp af den generiske grænseflade **OLE DB**.

| Generisk connector i Power BI Desktop | Ekstern datakilde | Link til flere oplysninger |
| --- | --- | --- |
| OLE DB |SAS OLE DB |[SAS-provider til OLE DB](https://support.sas.com/downloads/package.htm?pid=648) |
| OLE DB |Sybase OLE DB |[Sybase-provider til OLE DB](http://infocenter.sybase.com/help/index.jsp?topic=/com.sybase.infocenter.dc35888.1550/doc/html/jon1256941734395.html) |

## <a name="data-sources-accessible-through-odata"></a>Datakilder, der er tilgængelige via OData
Med **OData**-connectoren i **Power BI Desktop** kan du importere data fra en hvilken som helst URL-adresse til **OData** ved at skrive eller indsætte URL-adressen til **OData**. Du kan tilføje flere URL-adressedele ved at indtaste eller indsætte disse links i tekstfelterne i vinduet **OData Feed**.

![Skærmbillede af dialogboksen OData-feed, der viser felterne URL-adressedele og Eksempelvisning af URL-adresse.](media/desktop-connect-using-generic-interfaces/generic-data-interfaces_4.png)

Følgende liste indeholder nogle eksempler på de datakilder, som **Power BI Desktop** kan oprette forbindelse til ved hjælp af den generiske grænseflade **OData**.

| Generisk connector i Power BI Desktop | Ekstern datakilde | Link til flere oplysninger |
| --- | --- | --- |
| OData |Kommer snart |Vend snart tilbage for at se en liste over OData-datakilder |

## <a name="data-sources-accessible-through-rest-apis"></a>Datakilder, der er tilgængelige via REST API'er
Du kan oprette forbindelse til datakilder med **REST API'er** og dermed bruge data fra alle mulige forskellige datakilder, der understøtter **REST**.

![Skærmbillede af Forespørgsel, der viser datakilderne.](media/desktop-connect-using-generic-interfaces/generic-data-interfaces_5.png)

Følgende liste indeholder nogle eksempler på de datakilder, som **Power BI Desktop** kan oprette forbindelse til ved hjælp af den generiske grænseflade **REST API'er**.

| Generisk connector i Power BI Desktop | Ekstern datakilde | Link til flere oplysninger |
| --- | --- | --- |
| REST API'er |Couchbase DB |[Couchbase REST API-oplysninger](https://powerbi.microsoft.com/blog/visualizing-data-from-couchbase-server-v4-using-power-bi/) |

## <a name="data-sources-accessible-through-r-script"></a>Datakilder, der er tilgængelige via R Script
Du kan bruge **R Scripts** til at få adgang til datakilder og bruge disse data i **Power BI Desktop**.

![Skærmbillede af dialogboksen R-script, der viser udførelsesscriptet.](media/desktop-connect-using-generic-interfaces/r-scripts-2.png)

Følgende liste indeholder nogle eksempler på de datakilder, som **Power BI Desktop** kan oprette forbindelse til ved hjælp af den generiske brugergrænseflade **OData**.

| Generisk connector i Power BI Desktop | Ekstern datakilde | Link til flere oplysninger |
| --- | --- | --- |
| R Script |SAS-filer |[R Script-vejledning fra CRAN](https://cran.r-project.org/doc/manuals/R-data.html) |
| R Script |SPSS-filer |[R Script-vejledning fra CRAN](https://cran.r-project.org/doc/manuals/R-data.html) |
| R Script |Statistiske R-filer |[R Script-vejledning fra CRAN](https://cran.r-project.org/doc/manuals/R-data.html) |

## <a name="next-steps"></a>Næste trin
Du kan oprette forbindelse til mange forskellige typer datakilder ved hjælp af **Power BI Desktop**. Du kan finde flere oplysninger om datakilder i følgende ressourcer:

* [Hvad er Power BI Desktop?](../fundamentals/desktop-what-is-desktop.md)
* [Datakilder i Power BI Desktop](desktop-data-sources.md)
* [Udform og kombiner data med Power BI Desktop](desktop-shape-and-combine-data.md)
* [Opret forbindelse til Excel-projektmapper i Power BI Desktop](desktop-connect-excel.md)   
* [Angiv data direkte i Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   
