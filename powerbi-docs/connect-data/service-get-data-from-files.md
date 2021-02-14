---
title: Hent data fra filer til Power BI
description: Få mere at vide om, hvordan du kan hente data fra Excel, Power BI Desktop og CSC-filer til Power BI
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 05/08/2019
LocalizationGroup: Data from files
ms.openlocfilehash: 2ed532986dd31e97e535f27d70c9f5cfd8c66fd5
ms.sourcegitcommit: 24887643bd3e1b3749ce325dc0ae407432d7fee4
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/14/2021
ms.locfileid: "100489871"
---
# <a name="get-data-from-files-for-power-bi"></a>Hent data fra filer til Power BI
![Ikon for Excel, Power BI Desktop og CSV](media/service-get-data-from-files/file_icons.png)

I Power BI kan du oprette forbindelse til eller importere data og rapporter fra tre filtyper.

* Microsoft Excel (.xlsx eller .xlsm)
* Power BI Desktop (.pbix)
* Kommaseparerede værdier (.csv)

## <a name="what-does-get-data-from-a-file-really-mean"></a>Hvad betyder det i virkeligheden at hente data fra en fil?
I Power BI kommer de data, du udforsker, fra et datasæt. Men for at få et datasæt skal du først at hente nogle data. I denne artikel fokuserer vi på at hente data fra filer.

For bedre at forstå betydningen af datasæt og hvordan vi kan hente data til dem, så lad os bruge en bil som eksempel. Sæt dig ind i din bil, og kig på instrumentpanelet. Det er meget, som at sidde foran din computer og se på et dashboard i Power BI. Instrumentpanelet (dashboardet) viser alle de ting, som din bil gør: hvor hurtigt motoren øger omdrejningshastigheden, temperaturen, hvilket gear du er i, din hastighed osv.

I Power BI er et datasæt ligesom motoren i din bil. Datasættet leverer de data, målinger og oplysninger, der vises i Power BI-dashboardet. Selvfølgelig har din motor, eller datasæt, brug for brændstof, og i Power BI er dette brændstof data. Din bil har en brændstofbeholder, der giver brændstof til motoren. På samme måde har du i Power BI brug for en brændstofbeholder, der har data, du kan tilføre dit datasæt. I dette tilfælde er brændstofbeholderen en Power BI Desktop-fil, en Excel-projektmappefil eller en .CSV-fil.

Vi kan også tage det ét trin videre. En brændstofbeholder i en bil skal fyldes med brændstof. Brændstof til vores Power BI Desktop-, Excel- eller .CSV-fil er data fra en anden datakilde. Vi får data fra en anden datakilde og placerer dem i en Excel-, Power BI Desktop- eller .CSV-fil. Hvis det er en Excel-projektmappe eller .CSB-fil, kan vi manuelt angive rækker med data. Vi kan også oprette forbindelse til en ekstern datakilde til forespørgsel og indlæsning af data i vores fil. Når vi har en fil med nogle data, kan vi få det til Power BI som et datasæt.

> [!NOTE]
> Data i Excel-projektmapper skal være i en tabel eller i datamodellen, der skal importeres af Power BI.
> 
> 

## <a name="where-your-file-is-saved-makes-a-difference"></a>Det gør en forskel, hvor din fil gemmes
**Lokalt** – Hvis du gemmer din fil på et lokalt drev på din computer eller en anden placering i din organisation fra Power BI, kan du *importere* filen til Power BI. Filen forbliver på den lokale harddisk, så det er ikke hele filen, der importeres til Power BI. Der sker det, at et nyt datasæt oprettes på dit Power BI-websted, og data, og i nogle tilfælde datamodellen, indlæses i datasættet. Hvis filen indeholder rapporter, vises de på Power BI-webstedet under Rapporter.

**Onedrive – erhverv** – hvis du har OneDrive for Business, og du logger på med den samme konto, som du bruger til at logge på Power bi med, er det yderst den mest effektive måde at bevare dit arbejde i Excel, Power bi desktop eller a. CSV-filen og dit datasæt, rapporter og dashboards i Power BI i synkronisering. Da både Power BI og OneDrive findes i skyen, kan Power BI oprette forbindelse til din fil på OneDrive ca. hver time. Hvis der findes ændringer, opdateres datasættet, rapporter og dashboards automatisk i Power BI.

**OneDrive – personlig** – Hvis du gemmer dine filer på din egen OneDrive-konto, får du mange af de samme fordele som med OneDrive for Business. Den største forskel er, at når du første gang opretter forbindelse til din fil (med funktionen Hent data > Filer > OneDrive - personlig), skal du logge på OneDrive med din Microsoft-konto, som normalt er forskellig fra, hvad du bruger til at logge på Power BI. Når du logger på med OneDrive med din Microsoft-konto, skal du sørge for at vælge indstillingen Forbliv logget på. På denne måde kan Power BI oprette forbindelse til din fil ca. hver time og sikre, at dit datasæt i Power BI er synkroniseret.

**SharePoint – teamwebsteder** – Lagring af dine Power BI Desktop-filer på SharePoint – Teamwebsteder er stort set det samme som at gemme på OneDrive for Business. Den største forskel er, hvordan du opretter forbindelse til filen fra Power BI. Du kan angive en URL-adresse, eller du kan oprette forbindelse til rodmappen.

## <a name="ready-to-get-started"></a>Er du klar til at komme i gang?
Se følgende artikler for at få mere at vide om, hvordan du overfører din fil til Power BI.

* [Hent data fra Excel-projektmappefiler](service-excel-workbook-files.md)
* [Hent data fra Power BI Desktop-filer](service-desktop-files.md)
* [Hent data fra kommaseparerede værdifiler](service-comma-separated-value-files.md)

