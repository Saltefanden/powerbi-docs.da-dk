---
title: Visuel tabel og poster i visualiseringer i Power BI Desktop
description: Brug funktionerne Visuel tabel og Datapunkttabel i Power BI Desktop til at få vist detaljer
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 05/21/2020
LocalizationGroup: Learn more
ms.openlocfilehash: 05dcd5f0d7ca1681ee1e82762ea1557c79c5bc24
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96412799"
---
# <a name="use-visual-table-and-data-point-table-in-power-bi-desktop"></a>Brug den visuelle tabel og datapunkttabellen i Power BI Desktop
I **Power BI Desktop** kan du analysere alle visualiseringers detaljer og få vist en tekstrepræsentation af de underliggende data eller enkelte dataposter for den valgte visual. Disse funktioner kaldes nogle gange for *klikfrekvens*, *detaljeadgang* eller *detaljeadgang til oplysninger*.

Du kan bruge **Visuelle tabel** til at få vist dataene i et visuelt element som en tabel eller bruge **Datapunkttabel** til at få vist en tabel med de data, der bruges til at beregne et enkelt datapunkt. 

![Visuel tabel og Datapunkttabel](media/desktop-see-data-see-records/see-data-record.png)

>[!IMPORTANT]
>**Visuel tabel** og **Datapunkttabel** understøtter kun følgende visualiseringstyper:
>  - Liggende søjlediagram
>  - Søjlediagram
>  - Kransediagram
>  - Kartogram
>  - Tragt
>  - Kort
>  - Cirkeldiagram
>  - Træstruktur

## <a name="use-visual-table-in-power-bi-desktop"></a>Brug Visuel tabel i Power BI Desktop

**Visuel tabel** viser de data, der ligger under en visualisering. **Visuel tabel** er placeret på fanen **Data/Analysér** i sektionen **Vis** på båndet, når en visualisering vælges.

![Visuel tabel på båndet](media/desktop-see-data-see-records/visual-table-01.png)

Du kan også se dataene ved at højreklikke på en visualisering og derefter vælge **Vis Data** i den menu, der vises, eller ved at vælge **Flere indstillinger** (...) i øverste højre hjørne af en visualisering og derefter vælge **Vis som en tabel**.

![Vis Data, højreklik](media/desktop-see-data-see-records/visual-table-02.png)&nbsp;&nbsp;![Vis Data, flere indstillinger](media/desktop-see-data-see-records/visual-table-03.png)

> [!NOTE]
> Du skal pege på et datapunkt i den pågældende visual, før højrekliksmenuen er tilgængelig.

Når du vælger **Visuel tabel** eller **Datapunkttabel**, vises den pågældende visualisering og tekstrepræsentationen af dataene på canvasset i Power BI Desktop. I den *vandrette visning* vises den pågældende visual på den øverste halvdel af canvasset, og dataene vises på den nederste halvdel. 

![vandret visning](media/desktop-see-data-see-records/visual-table-04.png)

Du kan skifte mellem den vandrette visning og en *lodret visning* ved at vælge ikonet i øverste højre hjørne på canvasset.

![Skift til lodret visning](media/desktop-see-data-see-records/visual-table-05.png)

Du vender tilbage til rapporten ved at vælge **< Tilbage til rapport** i øverste venstre hjørne på canvasset.

![Tilbage til rapport](media/desktop-see-data-see-records/visual-table-06.png)

## <a name="use-data-point-table-in-power-bi-desktop"></a>Brug Datapunkttabel i Power BI Desktop

Du kan også fokusere på ét dataelement i en visualisering og analysere de underliggende data. Du bruger **Datapunkttabel** ved at vælge en visualisering, derefter vælge **Datapunkttabel** på fanen **Data/Analysér** i afsnittet **Visual Tools** på båndet og derefter vælge et datapunkt eller en datarække på visualiseringen. 

![Datapunkttabel på båndet](media/desktop-see-data-see-records/visual-table-07.png)

> [!NOTE]
> Hvis knappen **Datapunkttabel** på båndet er deaktiveret og nedtonet, betyder det, at den valgte visualisering ikke understøtter **Datapunkttabel**.

Du kan også højreklikke på et dataelement og vælge **Datapunkttabel** i den menu, der vises.

![Datapunkttabel ved at højreklikke](media/desktop-see-data-see-records/visual-table-08.png)

Når du vælger **Datapunkttabel** for et dataelement, vises alle de data, der er tilknyttet det valgte element, på canvasset i Power BI Desktop. 

![Skærmbillede af et lærred med alle de data, der er knyttet til det valgte element, når du vælger tabellen Datapunkt.](media/desktop-see-data-see-records/visual-table-09.png)

Du vender tilbage til rapporten ved at vælge **< Tilbage til rapport** i øverste venstre hjørne på canvasset.


> [!NOTE]
>**Datapunkttabel** har følgende begrænsninger:
> - Du kan ikke ændre dataene i visningen **Datapunkttabel** og gemme dem i rapporten igen.
> - Du kan ikke bruge **Datapunkttabel**, når der benyttes en beregnet måling i det pågældende visualisering i en (flerdimensional) målingsgruppe.
> - Du kan ikke bruge **Datapunkttabel**, når du har oprettet forbindelse til en live flerdimensionel model.

## <a name="next-steps"></a>Næste trin
**Power BI Desktop** indeholder mange forskellige funktioner til formatering af rapporter og dataadministration. I følgende ressourcer kan du se nogle eksempler:

* [Brug gruppering og gruppering i beholder i Power BI Desktop](desktop-grouping-and-binning.md)
* [Brug gitterlinjer, fastgørelse til gitter, z-rækkefølge, justering og fordeling i Power BI Desktop-rapporter](desktop-gridlines-snap-to-grid.md)

