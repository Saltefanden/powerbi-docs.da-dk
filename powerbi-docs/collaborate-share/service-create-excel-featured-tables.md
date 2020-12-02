---
title: Angiv fremhævede tabeller i Power BI Desktop (prøveversion)
description: Opret fremhævede tabeller i Power BI Desktop, så de vises i datatypegalleriet i Excel.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: how-to
ms.date: 09/17/2020
LocalizationGroup: Share your work
ms.openlocfilehash: d2d87f16b8100424b47277360354d79ee834d467
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96411925"
---
# <a name="set-featured-tables-in-power-bi-desktop-preview"></a>Angiv fremhævede tabeller i Power BI Desktop (prøveversion)

I datatypegalleriet i Excel kan dine brugere finde data fra *fremhævede tabeller* i dine Power BI-datasæt. I denne artikel får du mere at vide om, hvordan du angiver tabeller som *fremhævede* i dine datasæt. Disse tags gør det nemmere for dine brugere at føje virksomhedsdata til deres Excel-ark. Her er de grundlæggende trin, du skal udføre for at indstille og dele fremhævede tabeller.

1. Du identificerer fremhævede tabeller i dine datasæt i Power BI Desktop (denne artikel)
1. Du gemmer disse datasæt med fremhævede tabeller på et af de nye arbejdsområder. Rapportoprettere kan oprette rapporter med disse fremhævede tabeller. 
1. Resten af organisationen kan oprette forbindelse til disse fremhævede tabeller, der kaldes *datatyper* i Excel, for relevante data, der kan opdateres. I artiklen [Få adgang til Power BI-tabeller i Excel (prøveversion)](service-excel-featured-tables.md) beskrives, hvordan du bruger disse fremhævede tabeller i Excel.

> [!NOTE]
> Du kan [fremhæve eller certificere datasæt i Power BI](../collaborate-share/service-endorse-content.md). Det kaldes *godkendelse*. Excel prioriterer tabeller i godkendte datasæt i Datatypegalleriet. Excel viser først udvalgte tabeller i certificerede datasæt og derefter tabeller i promoverede datasæt. Derefter viser Excel udvalgte tabeller i ikke-godkendte datasæt. 

## <a name="turn-on-the-featured-table-preview"></a>Slå eksempelvisning af udvalgte tabeller til

1. Vælg **Filer** > **Indstillinger** > **Indstillinger** > **Funktioner til eksempelvisning** i Power BI Desktop.
2. Markér afkrydsningsfeltet **Fremhævede tabeller**.

    :::image type="content" source="media/service-excel-featured-tables/power-bi-preview-featured-tables.png" alt-text="Indstillingen Vis fremhævede tabeller":::

3. Genstart Power BI Desktop.

## <a name="select-a-table"></a>Vælg en tabel

1. Gå til Modelvisning i Power BI Desktop.

    :::image type="content" source="media/service-excel-featured-tables/power-bi-model-view.png" alt-text="Modelvisning":::
 
2. Vælg en tabel, og sæt **Er en fremhævet tabel** til **Ja**.

    :::image type="content" source="media/service-excel-featured-tables/power-bi-featured-table-yes.png" alt-text="Sæt Er en fremhævet tabel til Ja":::

4. I **Konfigurer denne tabel** skal du udfylde de påkrævede felter:

    - En **beskrivelse**. 
        > [!TIP]
        > Start beskrivelsen med "Fremhævet tabel" for at hjælpe forfattere af Power BI-rapporter med et identificere den.
    - Feltværdien **Rækkeetiket** bruges i Excel, så brugerne nemt kan identificere rækken. Den vises som celleværdien for en sammenkædet celle i ruden **Datavælger** og på kortet **Oplysninger**. 
    - Feltværdien **Nøglekolonne** indeholder det entydige id for rækken. Denne værdi gør det muligt for Excel at sammenkæde en celle med en bestemt række i tabellen.

    :::image type="content" source="media/service-excel-featured-tables/power-bi-set-up-featured-table.png" alt-text="Opsæt fremhævet tabel":::

1. Når du har udgivet eller importeret datasættet til Power BI-tjenesten, vises den fremhævede tabel i Excel-datatypegalleriet. Du og andre forfattere af rapporter kan også oprette rapporter, der er bygget ud fra dette datasæt.

1. I Excel: 
    - Excel cachelagrer listen over datatyper, så du skal genstarte Excel for at se nyligt udgivede, fremhævede tabeller.
    - Nogle datasæt understøttes ikke i prøveversionen. De fremhævede tabeller, der er defineret i disse datasæt, vises ikke i Excel. Se næste afsnit, Overvejelser og begrænsninger, for at få flere oplysninger.

## <a name="considerations-and-limitations"></a>Overvejelser og begrænsninger

Her er begrænsningerne for den oprindelige prøveversion.

- Udvalgte tabeller i Power BI-datasæt, der bruger følgende funktioner, vises ikke i Excel:

    - DirectQuery-datasæt.
    - Datasæt med en direkte forbindelse.

- Der vises kun data i kolonner og beregnede kolonner i den udvalgte tabel i Excel. De målinger, der defineres for relaterede tabeller, og implicitte målinger beregnet ud fra relationer er ikke medtaget i den indledende prøveversion.
- Excel viser kun udvalgte tabeller, der er gemt i de nye Power BI-arbejdsområder. Udvalgte tabeller, der er gemt i de klassiske arbejdsområder, vises ikke som datatyper i Excel. Du kan [opgradere klassiske arbejdsområder til de nye arbejdsområder](service-upgrade-workspaces.md) i Power BI.
- Under [Overvejelser og begrænsninger](service-excel-featured-tables.md#considerations-and-limitations) i artiklen "Få adgang til Power BI-tabeller i Excel" kan du finde andre Excel-overvejelser.

## <a name="next-steps"></a>Næste trin

- [Få adgang til Power BI-tabeller i Excel](service-excel-featured-tables.md)
- Læs om, hvordan du [bruger Excel-datatyper fra Power BI](https://support.office.com/article/use-excel-data-types-from-power-bi-preview-cd8938ce-f963-444d-b82a-7140848241e9) i dokumentationen til Excel.
- Har du spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)

