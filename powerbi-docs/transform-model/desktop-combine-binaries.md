---
title: Kombiner filer (binære) i Power BI Desktop
description: Kombiner nemt datakilder med filer (binære) i Power BI Desktop
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-transform-model
ms.topic: how-to
ms.date: 01/13/2020
LocalizationGroup: Transform and shape data
ms.openlocfilehash: bf75a5656de956be5ddd38330d659cba06e30455
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96415835"
---
# <a name="combine-files-binaries-in-power-bi-desktop"></a>Kombiner filer (binære) i Power BI Desktop

Her er en effektiv tilgang til import af data til **Power BI Desktop**: Hvis du har flere filer med det samme skema, kan du kombinere dem i en enkelt logisk tabel. Denne populære teknik er gjort mere praktisk og omfattende.

Du starter processen med at kombinere filer fra samme mappe ved at vælge **Hent data**, **Fil** > **Mappe** og derefter vælge **Opret forbindelse**.

![Opret forbindelse til mappefilen, dialogboksen Hent data, Power BI Desktop](media/desktop-combine-binaries/combine-binaries_1.png)

Angiv stien til mappen, Vælg **OK**, og vælg derefter **Transformér data** for at se mappens filer i Power Query-editor.

## <a name="combine-files-behavior"></a>Funktionsmåden Kombiner filer

Hvis du vil kombinere binære filer i Power Query-editor, skal du vælge **Indhold** (første kolonneetiket) og vælge **Hjem** > **Kombiner filer**. Du kan også blot vælge ikonet **Kombiner filer** ud for **Indhold**.

![Kommandoen Kombiner filer, Power Query-editor, Power BI Desktop](media/desktop-combine-binaries/combine-binaries_2a.png)

Transformationen *Kombiner filer* fungerer på følgende måde:

* Transformationen Kombiner filer analyserer de enkelte inputfiler og bestemmer det rette filformat, der skal bruges, f.eks. en fil af typen *tekst*, *Excel-projektmappe* eller *JSON*.
* Transformeringen giver dig mulighed for at vælge et bestemt objekt fra den første fil, f.eks. en Excel-projektmappe, der skal trækkes ud.
  
  ![Dialogboksen Kombiner filer, Power Query-editor, Power BI Desktop](media/desktop-combine-binaries/combine-binaries_3.png)
* Disse handlinger foretages automatisk for transformationen af de kombinerede filer:
  
  * Opretter et eksempel på en forespørgsel, der udfører alle nødvendige udtrækningstrin i en enkelt fil.
  * Opretter en *funktionsforespørgsel*, der angiver parametre for filen/det binære input i *eksempelforespørgslen*. Exempelforespørgslen og funktionsforespørgslen er kædet sammen, så ændringer i eksempelforespørgslen afspejles i funktionsforespørgslen.
  * Anvender *funktionsforespørgslen* på den oprindelige forespørgsel med binære inputværdier, f.eks. forespørgslen *Mappe*. Den anvender funktionsforespørgslen for binære input på hver række og udvider derefter den resulterende dataudtrækning som kolonner på øverste niveau.

    ![Resultater af transformationen Kombiner filer, Power Query-editor, Power BI Desktop](media/desktop-combine-binaries/combine-binaries_4.png)

> [!NOTE]
> Omfanget af dit valg i en Excel-projektmappe vil påvirke funktionsmåden for Kombiner binære filer. Du kan f.eks. vælge et bestemt regneark for at kombinere dette regneark eller vælge roden for at kombinere hele filen. Når du vælger en mappe, kombineres de filer, der findes i den pågældende mappe. 

Med funktionsmåden for kombinationen af filer kan du nemt kombinere alle filer i en bestemt mappe, så længe de har samme filtype og struktur (f.eks. de samme kolonner).

Derudover kan du nemt anvende yderligere transformations- eller udtrækningstrin ved at ændre den automatisk oprettede eksempelforespørgsel uden at skulle bekymre dig om at ændre eller oprette yderligere trin til funktionsforespørgslen. Ændringer i eksempelforespørgslen oprettes automatisk i den tilknyttede funktionsforespørgsel.

## <a name="next-steps"></a>Næste trin

Du kan oprette forbindelse til mange forskellige typer data ved hjælp af Power BI Desktop. Du kan finde flere oplysninger om datakilder i følgende ressourcer:

* [Hvad er Power BI Desktop?](../fundamentals/desktop-what-is-desktop.md)
* [Datakilder i Power BI Desktop](../connect-data/desktop-data-sources.md)
* [Udform og kombiner data med Power BI Desktop](../connect-data/desktop-shape-and-combine-data.md)
* [Opret forbindelse til CSV-filer i Power BI Desktop](../connect-data/desktop-connect-csv.md)
* [Angiv data direkte i Power BI Desktop](../connect-data/desktop-enter-data-directly-into-desktop.md)
