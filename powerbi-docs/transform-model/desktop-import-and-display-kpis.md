---
title: Importér og få vist KPI'er i Power BI
description: Importér og få vist KPI'er
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-transform-model
ms.topic: how-to
ms.date: 05/08/2019
LocalizationGroup: Model your data
ms.openlocfilehash: c7aeb70d99b8ce32191d04d002c638c6bb69c7fb
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96415628"
---
# <a name="import-and-display-kpis-in-power-bi"></a>Importér og få vist KPI'er i Power BI
Med **Power BI Desktop** kan du importere og få vist KPI'er i tabeller, i matrixer og på kort.

Følg disse trin for at importere og få vist KPI'er.

1. Start med en Excel-projektmappe, der har en Power Pivot-model og KPI'er. I denne opgave bruges der en projektmappe, der kaldes *KPIs*.

1. Importér Excel-projektmappen i Power BI ved hjælp af **Filer -> Importér -> Indhold i Excel-projektmappe**. Du kan også [læse om, hvordan du importerer projektmapper](../connect-data/desktop-import-excel-workbooks.md). 

1. Efter importen til Power BI vises KPI'en i ruden **Felter**, og den er markeret med ikonet med ![trafiklys](media/desktop-import-and-display-kpis/traffic.png). Hvis du vil bruge en KPI i rapporten, skal du sørge for at udvide indholdet, så du får vist felterne **Værdi**, **Mål** og **Status**.

    ![Skærmbillede af Power BI Desktop, der viser filteret DeltaKPI i ruden Filtre.](media/desktop-import-and-display-kpis/desktoppreviewfeatureon2.png)
 
1. Det er bedst at bruge importerede KPI'er i standardvisualiseringstyper, f.eks. typen **Tabel**. Power BI indeholder også visualiseringstypen **KPI**, som kun skal bruges til at oprette nye KPI'er.
   
    ![Skærmbillede af Power BI Desktop, hvor Table1-felter er markeret i ruden Felt.](media/desktop-import-and-display-kpis/desktoppreviewfeatureon3.png)

Så nemt er det. Du kan bruge KPI'er til at fremhæve tendenser, status eller andre vigtige indikatorer.
