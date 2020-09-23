---
title: Få mere at vide om, hvordan du opretter forbindelse til dataflow i Power BI
description: Få mere at vide om, hvordan dataflows fungerer i Power BI
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 09/20/2019
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: a3659a2d39faad1d975a5e3c989cb40e800deb76
ms.sourcegitcommit: 9350f994b7f18b0a52a2e9f8f8f8e472c342ea42
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 09/22/2020
ms.locfileid: "90853488"
---
# <a name="connect-to-data-sources-for-power-bi-dataflows"></a>Opret forbindelse til datakilder til Power BI-dataflow

Med Power BI-dataflow kan du oprette forbindelse til mange forskellige datakilder for at oprette nye dataflow eller føje nye enheder til et eksisterende dataflow.

Denne artikel indeholder en liste over de mange tilgængelige datakilder til oprettelse eller tilføjelse af dataflow og beskriver, hvordan du kan oprette disse dataflow ved hjælp af disse datakilder.

Du kan se en oversigt over, hvordan du opretter og bruger dataflow, i [Oprettelse og brug af dataflow i Power BI](service-dataflows-create-use.md).

## <a name="create-a-dataflow-from-a-data-source"></a>Opret et dataflow fra en datakilde

Du opretter forbindelse til data ved at vælge menuelementet **+ Opret** i **Power BI-tjenesten** og derefter vælge **dataflow** i den menu, der vises. Når du har foretaget et valg, vises følgende billede på lærredet i Power BI-tjenesten. 

![Tilføj nyt dataflow eller ny enhed](media/service-dataflows-data-sources/dataflows-data-sources_01.png)

Hvis dit dataflow findes allerede, kan du føje nye enheder til dit dataflow ved at vælge **Tilføj enheder**, som vises nedenfor, eller ved at vælge **Hent data** i oprettelsesværktøjet til dataflow.

![Føj enheder til et eksisterende dataflow](media/service-dataflows-data-sources/dataflows-data-sources_02.png)

På følgende billede vises knappen **Hent data** i oprettelsesværktøjet til dataflow. 

![Tilføj enheder ved hjælp af Hent data](media/service-dataflows-data-sources/dataflows-data-sources_03.png)


## <a name="data-sources-for-dataflows"></a>Datakilder til dataflow

Du kan få vist de tilgængelige datakilder ved at vælge **Hent Data** i oprettelsesværktøjet til dataflow, som derefter viser en dialogboks til valg af kategorier og hver enkelt datakilde, som vist på følgende billede.


![Hent datakategorier til dataflow](media/service-dataflows-data-sources/dataflows-data-sources_04.png)

Datakilder til dataflow er organiseret i følgende kategorier, der vises langs toppen af dialogboksen **Hent data**:

* Alle kategorier
* Filer
* Database
* Power BI
* Azure
* Onlinetjenester
* Andet

Kategorien **Alle kategorier** indeholder alle datakilder fra alle kategorier. 

Kategorien **Fil** indeholder følgende tilgængelige dataforbindelser til dataflow:

* Giv adgang
* Excel
* JSON
* Tekst/CSV
* XML

Kategorien **Database** indeholder følgende tilgængelige dataforbindelser til dataflow:

* IBM DB2-database
* MySQL Database
* Oracle-database
* PostgreSQL-database
* SQL Server-database
* Sybase-database
* Teradata
* Vertica

Kategorien **Power BI** indeholder følgende tilgængelige dataforbindelser til dataflow:

* Power BI-dataflow

Kategorien **Azure** indeholder følgende tilgængelige dataforbindelser til dataflow:

* Azure Blobs
* Azure Data Explorer
* Azure SQL Data Warehouse
* Azure SQL Database
* Azure-tabeller

Kategorien **Onlinetjenester** indeholder følgende tilgængelige dataforbindelser til dataflow:

* Amazon Redshift
* Common Data Service til Apps
* Microsoft Exchange Online
* Salesforce-objekter
* Salesforce-rapporter
* SharePoint Online-liste
* Smartsheet

Kategorien **Andet** indeholder følgende tilgængelige dataforbindelser til dataflow:

* Active Directory
* OData
* SharePoint-liste
* Web-API
* Webside
* Tom tabel
* Tom forespørgsel


## <a name="connecting-to-a-data-source"></a>Oprettelse af forbindelse til en datakilde

Hvis du vil oprette forbindelse til en datakilde, skal du vælge den pågældende datakilde. Vi bruger et eksempel til at vise, hvordan processen fungerer, men hver dataforbindelse til dataflow benytter samme proces. Forskellige forbindelser kan kræve særlige legitimationsoplysninger eller andre oplysninger, men flowet er det samme. I vores eksempel kan du på følgende billede se, at **CDS for Apps** er valgt fra dataforbindelseskategorien **Onlinetjenester**.

![Vælg CDS for Apps](media/service-dataflows-data-sources/dataflows-data-sources_05.png)

Der vises et vindue med forbindelse til den valgte dataforbindelse. Hvis der kræves legitimationsoplysninger, bliver du bedt om at angive dem. På følgende billede vises en Server URL-adresse, der angives for at oprette forbindelse til en CDS for Apps-server.

![Legitimationsoplysninger eller URL-adresser til dataforbindelser](media/service-dataflows-data-sources/dataflows-data-sources_06.png)

Når forbindelsesoplysninger for URL-adressen eller ressourcen er angivet, skal du vælge **Log på** for at angive de legitimationsoplysninger, der skal bruges til dataadgang, og derefter vælge **Næste**.

**Power-forespørgsel Online** igangsætter og opretter forbindelse til datakilden og viser derefter de tilgængelige tabeller fra den pågældende datakilde i vinduet **Navigator**, som vist på følgende billede.

![Vinduet Navigator viser tabeller i datakilden](media/service-dataflows-data-sources/dataflows-data-sources_07.png)

Du kan vælge de tabeller og data, du vil indlæse, ved at markere afkrydsningsfeltet ud for hver i venstre rude. Du indlæser dataene ved at vælge **OK** nederst i vinduet **Navigator**. En Power-forespørgsel Online-dialogboks vises, hvor du kan redigere forespørgsler og udføre alle de andre ændringer, du vil foretage af de markerede data.

![Rediger forespørgsler og transformér i Power-forespørgselseditor](media/service-dataflows-data-sources/dataflows-data-sources_08.png)

Så nemt er det. Andre datakilder har lignende flow og bruger Power-forespørgsel Online til at redigere og transformere de data, du indsætter i dataflowet.

## <a name="connecting-to-additional-data-sources"></a>Oprettelse af forbindelse til flere datakilder

Der er flere dataforbindelser, der ikke vises i brugergrænsefladen til Power BI-dataflow, men som understøttes med nogle få ekstra trin. 

Du kan benytte følgende fremgangsmåde til at oprette en forbindelse til en connector, der ikke vises i brugergrænsefladen:

1. Åbn **Power BI Desktop**, og vælg **Hent data**.
2. Åbn **Power-forespørgselseditor** i Power BI Desktop, højreklik på den relevante forespørgsel, og åbn **Avanceret editor**, som vist på følgende billede. Herfra kan du kopiere det M-script, der vises i den avancerede editor.

    ![Kopiér M-scriptet fra den avancerede editor i Power BI Desktop](media/service-dataflows-data-sources/dataflows-data-sources_09.png) 

3. Åbn Power BI-dataflowet, og vælg **Hent data** for at få en tom forespørgsel, som vist på følgende billede.

    ![Opret en tom forespørgsel til et dataflow](media/service-dataflows-data-sources/dataflows-data-sources_10.png) 

4. Indsæt den kopierede forespørgsel i den tomme forespørgsel for dataflowet.

    ![Kopiér M-scriptet til editorens vindue](media/service-dataflows-data-sources/dataflows-data-sources_11.png) 

Hvorefter scriptet opretter forbindelse til den angivne datakilde. 

På følgende liste vises, hvilke connectorer du kan bruge i øjeblikket ved at kopiere og indsætte M-forespørgslen i en tom forespørgsel:

* Azure Analysis Services
* Adobe Analytics
* ODBC
* OLE DB
* Mappe
* SharePoint Online-mappe
* SharePoint-mappe
* Hadoop HDFS
* Azure HDInsight (HDFS)
* Hadoop-fil (HDFS)
* Informix (beta)

Det er det eneste, du skal gøre for at oprette forbindelse til datakilder i Power BI-dataflow.


## <a name="next-steps"></a>Næste trin

I denne artikel viste vi, hvilke datakilder du kan oprette forbindelse til for dataflow. De følgende artikler kommere nærmere ind på almindelige forbrugsscenarier for dataflows. 

* [Selvbetjent dataforberedelse i Power BI](service-dataflows-overview.md)
* [Opret og brug dataflow i Power BI](service-dataflows-create-use.md)
* [Brug af beregnede objekter i Power BI Premium](service-dataflows-computed-entities-premium.md)
* [Brug af dataflow med datakilder i det lokale miljø](service-dataflows-on-premises-gateways.md)
* [Udviklerressourcer til Power BI-dataflow](service-dataflows-developer-resources.md)
* [Integration af dataflow og Azure Data Lake (prøveversion)](service-dataflows-azure-data-lake-integration.md)

Du kan finde flere oplysninger om Power-forespørgsel og planlagt opdatering i disse artikler:
* [Oversigt over forespørgsler i Power BI Desktop](desktop-query-overview.md)
* [Konfiguration af planlagt opdatering](../connect-data/refresh-scheduled-refresh.md)

Du kan finde flere oplysninger om Common Data Model i denne oversigtsartikel:
* [Common Data Model – oversigt](/powerapps/common-data-model/overview)