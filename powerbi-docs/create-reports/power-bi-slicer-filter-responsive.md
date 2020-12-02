---
title: Opret et dynamisk udsnitsværktøj, som du kan ændre størrelsen på i Power BI
description: Få mere at vide om, hvordan du opretter et dynamisk udsnitsværktøj, du kan ændre størrelsen på, så det passer til din rapport
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 04/06/2020
LocalizationGroup: Create reports
ms.openlocfilehash: 5fde91f2cfabd1f5a7727d3ec8a80d8ecddc7fc6
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96393433"
---
# <a name="create-a-responsive-slicer-you-can-resize-in-power-bi"></a>Opret et dynamisk udsnitsværktøj, som du kan ændre størrelsen på i Power BI

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-desktop](../includes/yes-desktop.md)] [!INCLUDE [yes-service](../includes/yes-service.md)]

Dynamiske udsnitsværktøjer kan ændres i størrelsen, så de passer til at vilkårligt område i rapporten. Du kan ændre udsnitsværktøjets størrelse og form, fra vandret til firkantet til lodret, og værdierne i udsnitsværktøjet omarrangerer sig selv iht. dine ønsker. I Power BI Desktop og i Power BI-tjenesten kan du oprette vandrette udsnitsværktøjer og gøre udsnitsværktøjer til dato/område dynamiske. Udsnitsværktøjer til dato/område har også forbedrede berøringsområder, så det er lettere at ændre dem med en fingerspids. Du kan gøre dynamiske udsnitsværktøjer så små eller store, som du vil; de ændres også automatisk i størrelsen for at passe godt i rapporter i Power BI-tjenesten og også i Power BI-mobilapps. 

![Dynamisk udsnitsværktøjer kan have mange forskellige former](media/power-bi-slicer-filter-responsive/power-bi-slicer-filter-responsive-0-slicer.gif)

## <a name="create-a-slicer"></a>Opret et udsnit

Det første trin i at oprette et dynamisk udsnitsværktøj er at oprette et grundlæggende udsnitsværktøj. 

1. Vælg ![ikonet](media/power-bi-slicer-filter-responsive/power-bi-slicer-filter-responsive-0-slicer-icon.png)**Udsnitsværktøj** i ruden **Visualiseringer**.
2. Træk feltet, du vil filtrere, hen på **Felt**.

    ![Føj et felt til udsnitsværktøjet](media/power-bi-slicer-filter-responsive/power-bi-slicer-filter-responsive-1-create.png)

## <a name="convert-to-a-horizontal-slicer"></a>Konvertér til et vandret udsnitsværktøj

1. Med udsnitsværktøjet valgt skal du i ruden **Visualiseringer** vælge fanen **Format**.
2. Udvid sektionen **Generelt**, og vælg derefter **Retning** til at være **Vandret**.

    ![Sæt udsnitsværktøjet til vandret](media/power-bi-slicer-filter-responsive/power-bi-slicer-filter-responsive-2-horizontal.png) 

1.  Du skal muligvis gøre det større, så det viser flere værdier.

     ![Gør udsnitsværktøjet bredere](media/power-bi-slicer-filter-responsive/power-bi-slicer-filter-responsive-3-wider.png)

## <a name="make-it-responsive-and-experiment-with-it"></a>Gør det dynamisk og eksperimenter med det

Dette trin er let. 

1. Direkte under **Retning** i sektionen **Generelt** på fanen **Format** skal du skyde **Dynamisk** over på **Til**.  

    ![Udsnitsværktøjet er nu dynamisk](media/power-bi-slicer-filter-responsive/power-bi-slicer-filter-responsive-4-responsive-on.png)

1. Nu kan du lege med det. Træk i hjørnet for at gøre det kort, højt, bredt og smalt. Du kan gøre det så lille, at det blot bliver et filterikon.

    ![Dynamisk udsnitsværktøj – vist som et lille filterikon](media/power-bi-slicer-filter-responsive/power-bi-slicer-filter-responsive-5-mini-icon.png)

## <a name="add-it-to-a-phone-report-layout"></a>Føj det til en rapport med telefonlayout

I Power BI Desktop kan du oprette et telefonlayout for hver side i en rapport. Hvis en side har et telefonlayout, så vises den på en mobiltelefon i stående visning. Ellers er du nødt til at benytte den liggende visning. 

1. Vælg **Telefonlayout** på menuen **Vis**.

     ![Ikonet Telefonlayout, menuen Vis](media/power-bi-slicer-filter-responsive/power-bi-slicer-filter-responsive-6-phone-layout-button.png)
    
1. Træk alle de visuelle elementer, der skal være i telefonrapporten, hen til gitteret. Når du trækker det dynamiske udsnitsværktøj, kan du ændre det til den ønskede størrelse – i dette tilfælde blot et filterikon.

    ![Tilføj udsnitsværktøjet til rapporten med telefonlayout](media/power-bi-slicer-filter-responsive/power-bi-slicer-filter-responsive-7-phone-slicer-icon.png)

Læs mere om, hvordan du opretter [rapporter, der er optimeret til Power BI-mobilapps](desktop-create-phone-report.md).

## <a name="make-a-time-or-range-slicer-responsive"></a>Gør et udsnitsværktøj til tid eller område dynamisk

Du kan benytte den samme fremgangsmåde til at gøre et udsnitsværktøj til tid eller område dynamisk. Når du har slået **Dynamisk** **Til**, så vil du lægge mærke til et par ting:

- Visuelle elementer optimerer rækkefølgen af inputfelter afhængigt af, hvilken størrelse der er tilladt på lærredet. 
- Dataelementvisningen er optimeret for at gøre udsnitsværktøjet så praktisk anvendeligt som muligt, baseret på størrelsen der er tilladt på lærredet. 
- Nye runde håndtag på udsnitsværktøjerne afhjælper berøringsbevægelser. 
- Når et visuelt element bliver for lille til at være praktisk anvendeligt, så ændres det til et ikon, der repræsenterer den visuelle type. For at interagere med det skal du blot dobbeltklikke for at åbne det i fokustilstand. Det sparer værdifuld plads på rapportsiden, uden at funktionaliteten går tabt.

## <a name="next-steps"></a>De næste trin

- [Udsnitsværktøjer i Power BI-tjenesten](../visuals/power-bi-visualization-slicers.md)
- Har du flere spørgsmål? [Prøv at spørge Power BI-community'et](https://community.powerbi.com/)