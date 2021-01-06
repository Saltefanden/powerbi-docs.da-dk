---
title: Opret forbindelse til en PDF-fil i Power BI Desktop
description: Opret nemt forbindelse til og brug data fra PDF-filer i Power BI Desktop
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 01/04/2021
LocalizationGroup: Connect to data
ms.openlocfilehash: 5a6b0d47b524c4f36938878cfe48a64d47470854
ms.sourcegitcommit: 932f6856849c39e34229dc9a49fb9379c56a888a
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 01/06/2021
ms.locfileid: "97926326"
---
# <a name="connect-to-pdf-files-in-power-bi-desktop"></a>Opret forbindelse til PDF-filer i Power BI Desktop
I Power BI Desktop kan du oprette forbindelse til en **PDF-fil** og bruge dataene fra filen på samme måde som enhver anden datakilde i Power BI Desktop.

![Opret forbindelse til data i PDF-filer](media/desktop-connect-pdf/connect-pdf-04.png)

I følgende afsnit beskrives det, hvordan du opretter forbindelse til en **PDF-fil**, vælger data og indfører disse data i **Power BI Desktop**.

Vi anbefaler, at du altid opgraderer til den nyeste version af **Power BI Desktop**, hvilket du kan gøre via et link i [Power BI Desktop](../fundamentals/desktop-get-the-desktop.md). 

## <a name="connect-to-a-pdf-file"></a>Opret forbindelse til en PDF-fil
Hvis du vil oprette forbindelse til en **PDF-fil**, skal du vælge **Hent data** på båndet **Hjem** i Power BI Desktop. Vælg **Fil** blandt kategorierne til venstre, hvorefter du kan se **PDF**.

![Vælg PDF i Hent data](media/desktop-connect-pdf/connect-pdf-01.png)

Du bliver bedt om at angive placeringen af den PDF-fil, du vil bruge. Når du har angivet placeringen, og PDF-filen indlæses, vises der et vindue af typen **Navigator**, hvor de data, der er tilgængelige fra filen, vises. Her kan du vælge et eller flere elementer, der skal importeres og bruges i **Power BI Desktop**.

![Opret forbindelse til data i PDF-filer](media/desktop-connect-pdf/connect-pdf-04.png)

Hvis du markerer et afkrydsningsfelt ud for de registrerede elementer i PDF-filen, vises de i ruden til højre. Når du er klar til at importere, skal du vælge knappen **Indlæse** for at overføre dataene til **Power BI Desktop**.

Fra og med udgivelsen af **Power BI Desktop** i november 2018 kan du angive **Startside** og **Slutside** som valgfrie parametre for din PDF-forbindelse. Du kan også angive disse parametre i computersproget med M-formlen i følgende format:

`Pdf.Tables(File.Contents("c:\sample.pdf"), [StartPage=10, EndPage=11])`

## <a name="limitations-and-considerations"></a>Begrænsninger og overvejelser

Når du arbejder med PDF-connectoren på datasæt i en Premium-kapacitet, opretter PDF-connectoren ikke forbindelsen korrekt. Hvis du vil gøre det muligt for PDF-connectoren at arbejde på et datasæt i Premium-kapacitet, skal du konfigurere dette datasæt til at bruge en gateway og bekræfte forbindelsen til dette datasæt via gatewayen.  


## <a name="next-steps"></a>Næste trin
Du kan oprette forbindelse til mange forskellige typer data ved hjælp af Power BI Desktop. Du kan finde flere oplysninger om datakilder i følgende ressourcer:

* [Hvad er Power BI Desktop?](../fundamentals/desktop-what-is-desktop.md)
* [Datakilder i Power BI Desktop](desktop-data-sources.md)
* [Udform og kombiner data med Power BI Desktop](desktop-shape-and-combine-data.md)
* [Opret forbindelse til Excel-projektmapper i Power BI Desktop](desktop-connect-excel.md)   
* [Angiv data direkte i Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   
