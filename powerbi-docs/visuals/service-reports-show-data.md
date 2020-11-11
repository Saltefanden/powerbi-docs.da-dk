---
title: Vis de data, der blev brugt til at oprette Power BI-visualiseringen
description: I dette dokument forklares det, hvordan du får vist de data, der bruges til at oprette en visualisering i Power BI, og hvordan de pågældende data eksporteres til en .csv-fil.
author: msftrien
ms.reviewer: mihart
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 12/4/2019
ms.author: rien
LocalizationGroup: Visualizations
ms.openlocfilehash: c3e996da62b71c008f4f7a5929cc8b91d38cc26e
ms.sourcegitcommit: 5ccab484cf3532ae3a16acd5fc954b7947bd543a
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 11/06/2020
ms.locfileid: "93412780"
---
# <a name="display-a-visualizations-underlying-data"></a>Vis en visualiserings underliggende data

[!INCLUDE[consumer-appliesto-yyyn](../includes/consumer-appliesto-nyyn.md)]    

## <a name="show-data"></a>Vis data
En Power BI-visualisering er oprettet vha. data fra dine datasæt. Hvis du vil se bag kulisserne, kan du i Power BI *få vist* de data, der bruges til at oprette visualiseringen. Når du vælger **Vis data** , vises dataene under (eller ud for) visualiseringen i Power BI.

Du kan også eksportere de data, der bruges til at oprette visualiseringen som en .xlsx- eller .csv-fil og få den vist i Excel. Du kan finde flere oplysninger under [Eksportér data fra Power BI-visualiseringer](power-bi-visualization-export-data.md).

> [!NOTE]
> Både *Vis data* og *Eksportér data* er tilgængelige i Power BI-tjenesten og Power BI Desktop. Power BI Desktop indeholder dog et ekstra lag detaljer, og [*Vis poster* viser de faktiske rækker fra datasættet](../create-reports/desktop-see-data-see-records.md).
> 
> 

## <a name="using-show-data"></a>Brug af *Vis data* 
1. Vælg en visualisering i Power BI Desktop for at aktivere den.

2. Vælg **Flere handlinger** (...), og vælg **Vis data**. 
    ![visningsindstilling for Vis data](media/service-reports-show-data/power-bi-more-action.png)


3. Som standard vises dataene under visualiseringen.
   
   ![visning af visualisering og lodrette data](media/service-reports-show-data/power-bi-show-data-below.png)

4. Hvis du vil ændre retningen, skal du vælge lodret layout ![lille skærmbillede af ikon, der bruges til at skifte til lodret layout](media/service-reports-show-data/power-bi-vertical-icon-new.png) i øverste højre hjørne af visualiseringen.
   
   ![visning af visualisering og vandrette data](media/service-reports-show-data/power-bi-show-data-side.png)
5. Hvis du vil eksportere dataene til en .csv-fil, skal du vælge ellipsen og vælge **Eksportér data**.
   
    ![Vælg Eksportér data](media/service-reports-show-data/power-bi-export-data-new.png)
   
    Du kan finde flere oplysninger om eksport af data til Excel under [Eksportér data fra Power BI-visualiseringer](power-bi-visualization-export-data.md).
6. Hvis du vil skjule dataene, skal du fjerne markeringen af **Udforsk** > **Få vist data**.

## <a name="using-show-records"></a>Brug af Vis poster
Du kan også fokusere på ét dataelement i en visualisering og analysere de underliggende data. 

1. Hvis du vil bruge **Se poster** , skal du vælge en visualisering for at aktivere den. 

2. På Desktop-båndet skal du vælge fanen for **Visualiseringsværktøjer** > **Data/detailudledning** > **Se poster**. 

    ![Skærmbillede med Se poster valgt.](media/service-reports-show-data/power-bi-see-record.png)

3. Vælg et datapunkt eller en række i visualiseringen. I dette eksempel har vi valgt den fjerde kolonne fra venstre. Power BI viser os datasætposten for dette datapunkt.

    ![Skærmbillede af en enkelt post fra et datasæt.](media/service-reports-show-data/power-bi-row.png)

4. Vælg **Tilbage til rapport** for at vende tilbage til Desktop-rapportlærredet. 

## <a name="considerations-and-troubleshooting"></a>Overvejelser og fejlfinding

- Hvis knappen **Se poster** på båndet er deaktiveret og nedtonet, betyder det, at den valgte visualisering ikke understøtter Se poster.
- Du kan ikke ændre dataene i visningen Se poster og gemme dem i rapporten igen.
- Du kan ikke bruge Se poster, når der benyttes en beregnet måling i en flerdimensionel model.
- Du kan ikke bruge Se poster, når du har oprettet forbindelse til en live flerdimensionel model.  

## <a name="next-steps"></a>Næste trin
[Eksportér data fra Power BI-visualiseringer](power-bi-visualization-export-data.md)    

Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)


