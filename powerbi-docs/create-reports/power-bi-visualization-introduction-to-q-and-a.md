---
title: Opret en visualisering med Spørgsmål og svar i Power BI
description: Lær, hvordan du opretter et visual med Spørgsmål og svar i Power BI-tjenesten ved hjælp af Eksempel på detailhandelsanalyse
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 05/13/2019
LocalizationGroup: Ask questions of your data
ms.openlocfilehash: 7eae93eb2b4594a180836f43a758c6bef7b3e90e
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96415030"
---
# <a name="create-a-visual-with-power-bi-qa"></a>Opret en visualisering med Spørgsmål og svar i Power BI

Den hurtigste måde at få svar ud af dine data på er nogle gange at stille et spørgsmål på et naturligt sprog.  I denne artikel ser vi på to forskellige måder at oprette den samme visualisering på: først ved at stille et spørgsmål i Spørgsmål og svar og derefter ved at bygge den i en rapport. Vi bruger Power BI-tjenesten til at bygge visual'et i rapporten, men processen er næsten identisk ved brug af Power BI Desktop.

![Udfyldt Power BI-diagram](media/power-bi-visualization-introduction-to-q-and-a/power-bi-qna-create-visual.png)

For at følge med skal du bruge en rapport, som du kan redigere, så vi vil bruge et eksempel, der fås med Power BI.

## <a name="create-a-visual-with-qa"></a>Opret en visualisering med spørgsmål og svar

Hvordan oprettes dette kurvediagram ved hjælp af Spørgsmål og svar?

1. Fra dit Power BI-arbejdsområde skal du vælge **Hent data** \> **Eksempler** \> **Eksempel på detailhandelsanalyse** > **Forbind**.

1. Åbn dashboardet Eksempel på detailhandelsanalyse, og placer markøren i feltet Spørgsmål og svar, og **stil et spørgsmål om dine data**.

    ![Placer markøren i feltet Spørgsmål og svar](media/power-bi-visualization-introduction-to-q-and-a/power-bi-qna-cursor-in-qna-box.png)

2. Skriv noget i stil med følgende spørgsmål i feltet Spørgsmål og svar:
   
    **dette års salg og sidste års salg efter måned som områdediagram**
   
    Imens du skriver dette spørgsmål, vælger Spørgsmål og svar den bedste visualisering til at vise dit svar, og visualiseringen ændres automatisk, når du ændrer spørgsmålet. Desuden hjælper Spørgsmål og svar dig med at formulere dit spørgsmål med forslag, automatisk færdiggørelse og rettelse af stavefejl. Spørgsmål og svar anbefaler en mindre ændring af formuleringen: "dette års salg og sidste års salg efter *gange om måneden* som områdediagram".  

    ![Formulering rettet af Spørgsmål og svar](media/power-bi-visualization-introduction-to-q-and-a/power-bi-qna-corrected-create-filled-chart.png)

4. Vælg den sætning, der skal acceptere forslaget. 
   
   Når du er færdig med at skrive dit spørgsmål, er resultatet det samme diagram, som du ser i rapporten.
   
   ![Områdediagram udfyldt af Spørgsmål og svar](media/power-bi-visualization-introduction-to-q-and-a/power-bi-qna-create-filled-chart.png)

4. Hvis du vil fastgøre diagrammet til dit dashboard, skal du vælge tegnestiftikonet ![Tegnestiftikon](media/power-bi-visualization-introduction-to-q-and-a/pinnooutline.png) i øverste højre hjørne.

## <a name="create-a-visual-in-the-report-editor"></a>Opret en visualisering i rapporteditoren

1. Naviger tilbage til dashboardet med eksemplet på detailhandelsanalyse.
   
2. Dashboardet indeholder det samme områdediagramfelt, der hedder "Sidste års salg og dette års salg".  Vælg dette felt. Vælg ikke det felt, du oprettede med Spørgsmål og svar. Hvis du vælger det, åbnes Spørgsmål og svar. Det oprindelige områdediagram blev oprettet i en rapport, så rapporten åbnes på den side, der indeholder denne visualisering.

    ![Dashboard med eksempel på detailhandelsanalyse](media/power-bi-visualization-introduction-to-q-and-a/power-bi-dashboard.png)

1. Vælg **Rediger rapport** for at åbne rapporten i Redigeringsvisning.  Hvis du ikke er ejer af en rapport, har du ikke mulighed for at åbne rapporten i Redigeringsvisning.
   
    ![Knappen Rediger rapport](media/power-bi-visualization-introduction-to-q-and-a/power-bi-edit-report.png)
4. Vælg områdediagrammet, og gennemse indstillingerne i ruden **Felter**.  Rapportopretteren byggede dette diagram ved at vælge disse tre værdier (**Sidste års salg** og **Dette års salg > Værdi** i tabellen **Salg** og **FiscalMonth** i tabellen **Tid**) og organisere dem i beholderne **Akse** og **Værdier**.
   
    ![Ruden Visualiseringer](media/power-bi-visualization-introduction-to-q-and-a/gnatutorial_3-new.png)

    Du kan se, at de sluttede med det samme visual. Hvis du opretter den på denne måde, er det ikke for kompliceret. Men det var nemmere at oprette den med Spørgsmål og svar!

## <a name="next-steps"></a>De næste trin

- [Brug Spørgsmål og svar på dashboards og i rapporter](power-bi-tutorial-q-and-a.md)  
- [Spørgsmål og svar til forbrugere](../consumer/end-user-q-and-a.md)
- [Få dine data til at fungere godt med Spørgsmål og svar i Power BI](service-prepare-data-for-q-and-a.md)

Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)
