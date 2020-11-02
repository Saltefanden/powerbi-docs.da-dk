---
title: 'Opret en rapport fra en Excel-fil i Power BI-tjenesten '
description: Opret en Power BI-rapport fra en Excel-fil i Power BI-tjenesten.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 10/14/2020
ms.author: maggies
LocalizationGroup: Reports
ms.openlocfilehash: d6a52fd72ab96541eee621d6be6cb50005f293e2
ms.sourcegitcommit: fddba666c6ea90d525a1c3188bbd3c4a03410cdc
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 10/23/2020
ms.locfileid: "92462685"
---
# <a name="create-a-report-from-an-excel-file-in-the-power-bi-service"></a>Opret en rapport fra en Excel-fil i Power BI-tjenesten
Du har læst [Rapporter i Power BI](../consumer/end-user-reports.md), og nu vil du oprette din egen. Der er forskellige måder at oprette en rapport på. I denne artikel starter vi med at oprette en grundlæggende rapport i Power BI-tjenesten fra en Excel-fil. Når du har forstået de grundlæggende ting i forbindelse med at oprette en rapport, skal du se de [Næste trin](#next-steps) nederst for at se mere avancerede rapportemner.  

## <a name="prerequisites"></a>Forudsætninger
- [Tilmeld dig Power BI-tjenesten](../fundamentals/service-self-service-signup-for-power-bi.md). 
- [Download Excel-filen med Retail Analysis-eksemplet](https://go.microsoft.com/fwlink/?LinkId=529778), og gem den i OneDrive for Business eller lokalt.

## <a name="import-the-excel-file"></a>Importér Excel-filen
Denne metode til oprettelse af en rapport starter med en fil og et tomt rapportlærred. Du kan følge med ved at se Excel-filen med Retail Analysis-eksemplet.

1. Vælg **Mit arbejdsområde** i navigationsruden.
   
   :::image type="content" source="media/service-report-create-new/power-bi-select-my-workspace.png" alt-text="Skærmbillede af valg af Mit arbejdsområde.":::
2. Vælg **Hent data** nederst i navigationsruden.
   
   ![Hent data](media/service-report-create-new/power-bi-get-data3.png)
3. Vælg **Filer** , og naviger til den placering, hvor du har gemt Retail Analysis-eksemplet.
   
    ![vælg Filer](media/service-report-create-new/power-bi-select-files.png)
4. Til denne øvelse skal du vælge **Importér** .
   
   ![vælg Importér](media/service-report-create-new/power-bi-import.png)
5. Vælg **Åbn** .

   Når Excel-filen er importeret, angives den som et *datasæt* på listen i arbejdsområdet.

1. Vælg **Flere indstillinger (...)** ud for datasættet, og vælg **Opret rapport** .
   
   :::image type="content" source="media/service-report-create-new/power-bi-dataset-create-report.png" alt-text="Skærmbillede af valg af Mit arbejdsområde.":::
6. Rapporteditoren åbnes. 
   
   ![Skærmbillede af rapporteditoren.](media/service-report-create-new/power-bi-blank-report.png)

> [!TIP]
> Vælg menuikonet for at skjule navigationsruden, så du får mere plads.
> 
> :::image type="content" source="../media/power-bi-hide-navigation-pane.png" alt-text="Skærmbillede af valg af Mit arbejdsområde.":::


## <a name="add-a-radial-gauge-to-the-report"></a>Føj en radial måler til rapporten
Nu hvor vores datasæt er blevet importeret, så lad os komme i gang med at besvare nogle spørgsmål.  Vores marketingchef (CMO) vil vide, hvor tæt vi er på at nå dette års salgsmål. En måler er et [godt visualiseringsvalg](../visuals/power-bi-report-visualizations.md) til at vise denne type oplysninger.

1. I ruden Fields skal du vælge **Sales** > **This Year Sales** > **Værdi** .
   
    ![liggende søjlediagram i rapporteditor](media/service-report-create-new/power-bi-report-step1.png)
2. Konvertér din visual til en måler ved at vælge skabelonen Gauge ![ målerikon](media/service-report-create-new/powerbi-gauge-icon.png) i ruden **Visualiseringer** .
   
    ![Målervisualisering i rapporteditor](media/service-report-create-new/power-bi-report-step2.png)
3. Træk **Sales** > **This Year Sales** > **Goal** til feltet **Target value** . Det ser ud til, at vi er meget tæt på vores mål.
   
    ![Målervisualiseringer med Mål som Målværdi](media/service-report-create-new/power-bi-report-step3.png)
4. Det er nu en god idé at gemme rapporten.
   
   ![Filmenu](media/service-report-create-new/powerbi-save.png)

## <a name="add-an-area-chart-and-slicer-to-the-report"></a>Tilføj et områdediagram og et udsnit i rapporten
Vores marketingchef har nogle yderligere spørgsmål, vi skal besvare. Vedkommende vil gerne vide, hvordan salget i år er sammenlignet med sidste år. Og vedkommende vil gerne have vist resultaterne efter område.

1. Vi starter med at lave plads på vores lærred. Markér måleren, og flyt den til øverste højre hjørne. Træk derefter i hjørnerne for at gøre den mindre.
2. Fjern markeringen af måleren. I ruden Felter skal du vælge **Sales** > **This Year Sales** > **Value** og vælge **Sales** > **Last Year Sales** .
   
    ![rapporteditor med Måler og liggende søjlediagram](media/service-report-create-new/power-bi-report-step4.png)
3. Konvertér din visualisering til et områdediagram ved at vælge skabelonen Area chart ![diagramikon](media/service-report-create-new/power-bi-areachart-icon.png) i ruden **Visualiseringer** .
4. Vælg **Time** > **Period** for at føje den til feltet **Axis** .
   
    ![rapporteditor med aktivt områdediagram](media/service-report-create-new/power-bi-report-step5.png)
5. Hvis du vil sortere visualiseringen efter tidsperiode, skal du vælge ellipsen og vælge **Sortér efter periode** .
6. Nu vil vi tilføje udsnittet. Markér et tomt område på lærredet, og vælg skabelonen Udsnit ![Udsnit-ikon](media/service-report-create-new/power-bi-slicer-icon.png) . Vi har nu et tomt udsnit på vores lærred.
   
    ![rapportcanvas](media/service-report-create-new/power-bi-report-step6.png)    
7. Vælg **District** > **District** i ruden Fields. Flyt og tilpas størrelsen af udsnitsværktøjet.
   
    ![Rapporteditor, tilføj District](media/service-report-create-new/power-bi-report-step7.png)  
8. Brug udsnitsværktøjet til at søge efter mønstre og indsigt efter område (District).
   
   ![video om brugen af udsnitsværktøj](media/service-report-create-new/power-bi-slicer-video2.gif)  

Fortsæt med at udforske dine data og tilføje visualiseringer. Når du finder interessant viden, kan du [fastgøre den til et dashboard](service-dashboard-pin-tile-from-report.md).

## <a name="next-steps"></a>Næste trin

* [Fastgør visualiseringer til et dashboard](service-dashboard-pin-tile-from-report.md)
* [Skift rapportindstillinger i Power BI-tjenesten](power-bi-report-settings.md)
* Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
