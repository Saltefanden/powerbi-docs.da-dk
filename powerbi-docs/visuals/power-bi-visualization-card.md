---
title: Kortvisualiseringer (felter med store tal)
description: Opret en kortvisualisering i Power BI
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 05/05/2020
ms.author: rien
LocalizationGroup: Visualizations
ms.openlocfilehash: 8ee29bcfb85c627ed6e9bb4c33c48b941ded7dd7
ms.sourcegitcommit: d153cfc0ce559480c53ec48153a7e131b7a31542
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 09/29/2020
ms.locfileid: "91526811"
---
# <a name="create-card-visualizations"></a>Opret kortvisualiseringer

[!INCLUDE[consumer-appliesto-nyyn](../includes/consumer-appliesto-nyyn.md)]

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

Nogle gange er et enkelt tal det vigtigste, du vil finde frem til på dit Power BI-dashboard eller i din Power BI-rapport som f.eks. salg i alt, markedsandel fra år til år eller salgsmuligheder i alt. Denne type visualisering kaldes et *kort*. Som med næsten alle de oprindelige Power BI-visualiseringer kan kort oprettes ved hjælp af rapporteditoren eller Spørgsmål og svar.

![kortvisualisering](media/power-bi-visualization-card/pbi-opptuntiescard.png)

> [!NOTE]
> Når du deler din rapport med en Power BI-kollega, kræves det, at I begge har individuelle Power BI Pro-licenser, eller at rapporten er gemt i en Premium-kapacitet.

## <a name="prerequisite"></a>Forudsætning

I dette selvstudium bruges [PBIX-filen med eksemplet Detailhandelsanalyse](https://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix)

1. Vælg **Filer** \> **Åbn** i øverste venstre afsnit af menulinjen
   
2. Find din kopi af **PBIX-filen med eksemplet Detailhandelsanalyse**

1. Åbn **PBIX-filen med eksemplet Detailhandelsanalyse** i rapportvisning ![ikon for skærmbillede af rapportvisning.](media/power-bi-visualization-kpi/power-bi-report-view.png).

1. Markér ![Skærmbillede af den gule fane.](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) for at tilføje en ny side.

## <a name="option-1-create-a-card-using-the-report-editor"></a>Mulighed 1: Opret et kort ved hjælp af rapporteditoren

Den første metode, der kan bruges til at oprette et kort, er at bruge rapporteditoren i Power BI Desktop.

1. Start på en tom rapportside, og vælg feltet **Store** \> **Open store count**.

    Power BI opretter et søjlediagram med det ene tal.

   ![eksempel på diagram med feltnummer](media/power-bi-visualization-card/pbi-overview-chart.png)

2. Vælg kortikonet i ruden Visualiseringer.

   ![eksempel på kort med feltnummer](media/power-bi-visualization-card/power-bi-card-visualization.png)

Du har nu oprettet et kort ved hjælp af rapporteditoren. Nedenfor er den anden mulighed, der kan bruges til at oprette et kort ved hjælp af spørgsmålsfeltet i Spørgsmål og svar.

## <a name="option-2-create-a-card-from-the-qa-question-box"></a>Mulighed 2: Opret et kort fra feltet til spørgsmål i Spørgsmål og svar
Spørgsmålsfeltet i Spørgsmål og svar er en anden mulighed, du kan bruge, til at oprette et kort. Spørgsmålsfeltet i Spørgsmål og svar er tilgængeligt i Power BI Desktop-rapportvisning.

1. Start på en tom rapportside

1. Vælg ikonet **Stil et spørgsmål** øverst i vinduet. 

    Power BI opretter et kort og et felt til dit spørgsmål. 

   ![placering af ikon for stil et spørgsmål](media/power-bi-visualization-card/power-bi-q-and-a-overview.png)

2. Du kan f.eks. skrive "Samlet salg for Tina" i spørgsmålsfeltet.

    Feltet til spørgsmål kommer med forslag og tilpasninger og viser til sidst det samlede antal.  

   ![eksempel på spørgsmålsfelt](media/power-bi-visualization-card/power-bi-q-and-a-box.png)

   ![eksempel på kort fra metoden med spørgsmål](media/power-bi-visualization-card/power-bi-q-and-a-card.png)

Du har nu oprettet et kort ved hjælp af spørgsmålsfeltet i Spørgsmål og svar. Nedenfor kan du finde trin til at formaterer dit kort til dine specifikke behov.

## <a name="format-a-card"></a>Formatér et kort
Du har mange muligheder for at ændre etiketter, tekst, farve og meget mere. Den bedste måde at få mere at vide på er ved at oprette et kort og derefter udforske formateringsruden. Her er nogle af de formateringsindstillinger, der er tilgængelige. 

Ruden Formatering er tilgængelig, når du interagerer med kortet i en rapport. 

1. Start med at vælge ikonet for malerrullen for at åbne ruden Formatering. 

    ![kort med malerrullen fremhævet](media/power-bi-visualization-card/power-bi-format-card-2.png)

2. Med kortet markeret skal du udvide **Datamærkat** og ændre farven, størrelsen og skrifttypefamilien. Hvis du havde tusindvis af butikker, kunne du bruge **Vis enheder** til at få vist antallet af butikker i tusinder samt styre decimalerne. For eksempel 125.8K i stedet for 125.832,00.

    ![eksempel på kort med dataformat](media/power-bi-visualization-card/power-bi-card-format-2.png)

3.  Udvid **Kategorietiket**, og rediger farven og størrelsen.

    ![eksempel på kort med kategori](media/power-bi-visualization-card/power-bi-card-format-category.png)

4. Udvid **Baggrund**, og flyt skyderen til Til.  Nu kan du ændre baggrundsfarven og gennemsigtigheden.

    ![skyderen slået TIL](media/power-bi-visualization-card/power-bi-format-color-2.png)

5. Fortsæt med at udforske formateringsindstillingerne, indtil dit kort er præcis, som du vil det. 

## <a name="considerations-and-troubleshooting"></a>Overvejelser og fejlfinding

Hvis du ikke kan se feltet til spørgsmål, skal du kontakte din Power BI-administrator.

## <a name="next-steps"></a>Næste trin
[Kombinationsdiagrammer i Power BI](power-bi-visualization-combo-chart.md)

[Visualiseringstyper i Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)
