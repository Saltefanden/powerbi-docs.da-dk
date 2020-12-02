---
title: Opret forbindelse til Snowflake-databehandlingswarehouse i Power BI Desktop
description: Opret let forbindelse til og brug Snowflake-databehandlingswarehouse i Power BI Desktop
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 05/08/2019
LocalizationGroup: Connect to data
ms.openlocfilehash: 115fba44c69fceb3a4f309cd92358ef5bc2eff42
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96405738"
---
# <a name="connect-to-a-snowflake-computing-warehouse-in-power-bi-desktop"></a>Opret forbindelse til et Snowflake-databehandlingswarehouse i Power BI Desktop
I Power BI Desktop kan du oprette forbindelse til et **Snowflake**-databehandlingswarehouse og bruge de underliggende data på samme måde som enhver anden datakilde i Power BI Desktop. 

## <a name="connect-to-a-snowflake-computing-warehouse"></a>Opret forbindelse til et Snowflake-databehandlingswarehouse
Hvis du vil oprette forbindelse til et **Snowflake**-databehandlingswarehouse, skal du vælge **Hent data** på båndet **Hjem** i Power BI Desktop. Vælg **Database** blandt kategorierne til venstre, hvorefter du kan se **Snowflake**.

![Skærmbillede af dialogboksen Hent data, hvor databasen Snowflake er markeret.](media/desktop-connect-snowflake/connect-snowflake-2b.png)

I det viste vindue, **Snowflake**, skal du skrive eller indsætte navnet på dit Snowflake-databehandlingswarehouse i feltet og vælge **OK**. Bemærk, at du kan vælge at **importere** data direkte i Power BI, eller du kan bruge **DirectQuery**. Du kan få mere at vide om [brug af DirectQuery](desktop-use-directquery.md). Bemærk, at AAD SSO kun understøtter DirectQuery.

![Skærmbillede af dialogboksen Snowflake, hvor alternativknappen Importér er markeret.](media/desktop-connect-snowflake/connect-snowflake-3.png)

Når du bliver bedt om det, skal du angive dit brugernavn og din adgangskode.

![Skærmbillede af anmodningen om Snowflake-legitimationsoplysninger, hvor felterne Brugernavn og Adgangskode vises.](media/desktop-connect-snowflake/connect-snowflake-4.png)

> [!NOTE]
> Når du angiver dit brugernavn og din adgangskode for en bestemt **Snowflake**-server, anvendes de samme legitimationsoplysninger i efterfølgende forsøg på at oprette forbindelse via Power BI Desktop. Du kan ændre disse legitimationsoplysninger ved at gå til **Filer > Indstillinger > Indstillinger for datakilde**.
> 
> 

Hvis du vil bruge indstillingen Microsoft-konto, skal Snowflake AAD-integrationen konfigureres på Snowflake-siden. Det kan du gøre ved at læse afsnittet med introduktionen i [dokumentationen til Snowflake om emnet](https://docs.snowflake.net/manuals/user-guide/oauth-powerbi.html#power-bi-sso-to-snowflake).

![Godkendelsestype af Microsoft-konto i Snowflake-connector.](media/desktop-connect-snowflake/connect-snowflake-6.png)


Når du har oprettet forbindelse, vises der et vindue af typen **Navigator**, hvor de data, der er tilgængelige på serveren, vises. Her kan du vælge et eller flere elementer, der skal importeres og bruges i **Power BI Desktop**.

![ODBC-fejl 28000 medfører, at der ikke kan oprettes forbindelse.](media/desktop-connect-snowflake/connect-snowflake-5.png)

Du kan **indlæse** den valgte tabel, der fører hele tabellen ind i **Power BI Desktop**, eller du kan **redigere** forespørgslen, der åbner **Forespørgselseditor**, så du kan filtrere og finindstille det datasæt, du vil bruge, og derefter indlæse dette finindstillede datasæt i **Power BI Desktop**.

## <a name="next-steps"></a>Næste trin
Du kan oprette forbindelse til mange forskellige typer data ved hjælp af Power BI Desktop. Du kan finde flere oplysninger om datakilder i følgende ressourcer:

* [Hvad er Power BI Desktop?](../fundamentals/desktop-what-is-desktop.md)
* [Datakilder i Power BI Desktop](desktop-data-sources.md)
* [Udform og kombiner data med Power BI Desktop](desktop-shape-and-combine-data.md)
* [Opret forbindelse til Excel-projektmapper i Power BI Desktop](desktop-connect-excel.md)   
* [Angiv data direkte i Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   
