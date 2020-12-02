---
title: 'Hurtig start: Opret forbindelse til data i Power BI Desktop'
description: Sådan opretter du forbindelse til de datakilder, der er tilgængelige i Power BI Desktop
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: quickstart
ms.date: 01/10/2020
LocalizationGroup: quickstart
ms.openlocfilehash: 94bd9d64ae7e85cb66e20ad44a03bf4ccf7e28df
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96411051"
---
# <a name="quickstart-connect-to-data-in-power-bi-desktop"></a>Hurtig introduktion: Opret forbindelse til data i Power BI Desktop

I denne hurtige introduktion opretter du forbindelse til data ved hjælp af Power BI Desktop, som er det første skridt til oprettelse af datamodeller og rapporter.

![Power BI Desktop](media/desktop-what-is-desktop/what-is-desktop_01.png)

Hvis du ikke er tilmeldt Power BI, skal du [tilmelde dig en gratis prøveversion](https://app.powerbi.com/signupredirect?pbi_source=web), før du begynder.

## <a name="prerequisites"></a>Forudsætninger

Hvis du vil udføre trinnene i denne artikel, skal du bruge følgende ressourcer:

* Hent og installér Power BI Desktop, som er et gratis program, der kører på din lokale computer. Du kan [downloade Power BI Desktop ](https://powerbi.microsoft.com/desktop) direkte, eller du kan hente det i [Microsoft Store](https://aka.ms/pbidesktopstore).
* [Download dette eksempel på en Excel-projektmappe](https://go.microsoft.com/fwlink/?LinkID=521962), og opret en mappe med navnet *C:\PBID-qs*, hvor du kan gemme Excel-filen. I senere trin i denne hurtige introduktion forudsættes det, at dette er filplaceringen for den downloadede Excel-projektmappe.
* For mange dataconnectors i Power BI Desktop kræves der Internet Explorer 10 (eller nyere) til godkendelse.

## <a name="launch-power-bi-desktop"></a>Start Power BI Desktop

Når du har installeret Power BI Desktop, skal du starte programmet, så det kører på den lokale computer. Du bliver præsenteret for et Power BI-selvstudium. Følg selvstudiet, eller luk dialogboksen for at starte med et tomt lærred. Lærredet er det sted, hvor du opretter visualiseringer og rapporter fra dine data.

![Power BI Desktop med et tomt lærred](media/desktop-quickstart-connect-to-data/qs-connect-data_01.png)

## <a name="connect-to-data"></a>Opret forbindelse til data

Med Power BI Desktop kan du oprette forbindelse til mange forskellige typer data. Disse kilder omfatter grundlæggende datakilder, f.eks. en Microsoft Excel-fil. Du kan oprette forbindelse til onlinetjenester, der indeholder alle mulige forskellige slags data, f.eks. Salesforce, Microsoft Dynamics, Azure Blob Storage og meget mere.

Hvis du vil oprette forbindelse til data, skal du vælge **Hent data** på båndet **Hjem**.

![Hent data på båndet Hjem](media/desktop-quickstart-connect-to-data/qs-connect-data_02.png)

Vinduet **Hent data** vises. Du kan vælge mellem mange forskellige datakilder, som Power BI Desktop kan oprette forbindelse til. I denne hurtige introduktion skal du bruge den Excel-projektmappe, du har downloadet i [Forudsætninger](#prerequisites).

![Hent data til alle kilder](media/desktop-quickstart-connect-to-data/qs-connect-data_03.png)

Da denne datakilde er en Excel-fil, vælger vi **Excel** i vinduet **Hent data**, og vi vælger derefter knappen **Opret forbindelse**.

I Power BI bliver du bedt om at angive placeringen af den Excel-fil, som du vil oprette forbindelse til. Den hentede fil kaldes *Økonomieksempel*. Vælg filen, og vælg derefter **Åbn**.

![Hent data i et økonomieksempel](media/desktop-quickstart-connect-to-data/qs-connect-data_04.png)

Power BI Desktop indlæser derefter projektmappen og læser indholdet. Derefter får du vist de tilgængelige data i filen ved hjælp af vinduet **Navigator**. I det vindue kan du vælge, hvilke data der skal indlæses i Power BI Desktop. Vælg tabellerne ved at markere afkrydsningsfeltet ud for de tabeller, du vil importere. Importér begge tilgængelige tabeller.

![Vælg data i vinduet Navigator](media/desktop-quickstart-connect-to-data/qs-connect-data_05.png)

Når du har foretaget dine valg, skal du vælge **Indlæs** for at importere dataene til Power BI Desktop.

## <a name="view-data-in-the-fields-pane"></a>Få vist data i ruden felter

Når du har indlæst tabellerne, vises dataene i ruden **Felter**. Du kan udvide de enkelte tabeller ved at vælge pilen ud for deres navn. På følgende billede er tabellen *financials* udvidet, så alle felter vises.

![Hent data](media/desktop-quickstart-connect-to-data/qs-connect-data_06.png)

Det var det hele! Du har oprettet forbindelse til data i Power BI Desktop, indlæst disse data, og nu kan du se alle de tilgængelige felter i disse tabeller.

## <a name="next-steps"></a>De næste trin

Der er mange forskellige ting, du kan gøre med Power BI Desktop, når du har oprettet forbindelse til data. Du kan oprette visualiseringer og rapporter. Tag et kig på følgende ressourcer for at komme i gang:

* [Kom i gang med Power BI Desktop](../fundamentals/desktop-getting-started.md)
