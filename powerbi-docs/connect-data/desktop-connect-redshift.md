---
title: Opret forbindelse til en Amazon Redshift-database i Power BI Desktop
description: Opret nemt forbindelse til og brug en Amazon Redshift-database i Power BI Desktop
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 05/08/2019
LocalizationGroup: Connect to data
ms.openlocfilehash: 60bf73e4500785c766a485fffc92a25bd8f2c852
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96411350"
---
# <a name="connect-to-an-amazon-redshift-database-in-power-bi-desktop"></a>Opret forbindelse til en Amazon Redshift-database i Power BI Desktop
I **Power BI Desktop** kan du oprette forbindelse til en **Amazon Redshift**-database og bruge de underliggende data på samme måde som enhver anden datakilde i Power BI Desktop.

## <a name="connect-to-an-amazon-redshift-database"></a>Opret forbindelse til en Amazon Redshift-database
Hvis du vil oprette forbindelse til en **Amazon Redshift**-database, skal du vælge **Hent data** på båndet **Hjem** i Power BI Desktop. Vælg **Database** blandt kategorierne til venstre, hvorefter du kan se **Amazon Redshift**.

![Skærmbillede af dialogboksen Hent data, hvor databasen Amazon Redshift er markeret.](media/desktop-connect-redshift/connect_redshift_3.png)

I det **Amazon Redshift**-vindue, der åbnes, skal du skrive eller indsætte navnet på din **Amazon Redshift**-server og -database i feltet. I feltet *Server* kan brugerne angive en port i følgende format: *ServerURL:Port*

![Skærmbillede af dialogboksen Amazon RedShift, hvor felterne Server og Database vises.](media/desktop-connect-redshift/connect_redshift_4.png)

Når du bliver bedt om det, skal du angive dit brugernavn og din adgangskode. Du bør bruge et servernavn, der passer nøjagtigt til SSL-certifikatet, for at undgå fejl. 

![Skærmbillede af anmodningen om Amazon Redshift-legitimationsoplysninger, hvor felterne Brugernavn og Adgangskode vises.](media/desktop-connect-redshift/connect_redshift_5.png)

Når du har oprettet forbindelse, vises der et vindue af typen **Navigator**, hvor de data, der er tilgængelige på serveren, vises. Her kan du vælge et eller flere elementer, der skal importeres og bruges i **Power BI Desktop**.

![Skærmbillede af dialogboksen Navigator, hvor de tilgængelige data på serveren vises.](media/desktop-connect-redshift/connect_redshift_6.png)

Når du har foretaget valg i vinduet **Navigator**, kan du enten **indlæse** eller **redigere** dataene.

* Hvis du vælger at **indlæse** data, bliver du spurgt, om du vil bruge tilstanden *Import* eller *DirectQuery* til at indlæse dataene. Du kan finde flere oplysninger i denne [artikel, der forklarer DirectQuery](desktop-use-directquery.md).
* Hvis du vælger at **redigere** data, vises **forespørgselseditoren**, hvor du kan anvende alle mulige forskellige transformeringer og filtre på dataene, hvoraf mange anvendes på selve den underliggende **Amazon Redshift**-database (hvis det understøttes).

## <a name="next-steps"></a>Næste trin
Du kan oprette forbindelse til mange forskellige typer data ved hjælp af Power BI Desktop. Du kan finde flere oplysninger om datakilder i følgende ressourcer:

* [Hvad er Power BI Desktop?](../fundamentals/desktop-what-is-desktop.md)
* [Datakilder i Power BI Desktop](desktop-data-sources.md)
* [Udform og kombiner data med Power BI Desktop](desktop-shape-and-combine-data.md)
* [Opret forbindelse til Excel-projektmapper i Power BI Desktop](desktop-connect-excel.md)   
* [Angiv data direkte i Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   
