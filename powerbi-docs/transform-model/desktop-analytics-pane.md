---
title: Brug ruden Analytics i Power BI Desktop
description: Opret dynamiske referencelinjer til visuelle effekter i Power BI Desktop
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-transform-model
ms.topic: how-to
ms.date: 01/10/2020
LocalizationGroup: Create reports
ms.openlocfilehash: 1437e680ac7dc4114d68bd534ba8ec93dd8ae508
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2020
ms.locfileid: "96416042"
---
# <a name="use-the-analytics-pane-in-power-bi-desktop"></a>Brug ruden Analytics i Power BI Desktop

Med ruden **Analytics** i Power BI Desktop kan du tilføje dynamiske *referencelinjer* for visuelle elementer og levere vigtige tendenser eller indsigt. Du finder ikonet og ruden **Analytics** i området **Visualiseringer** i Power BI Desktop.

![Ruden Analytics, Visualiseringer, Power BI Desktop](media/desktop-analytics-pane/analytics-pane_1.png)

> [!NOTE]
> Ruden **Analytics** vises kun, når du vælger en visuel effekt på Power BI Desktop-lærredet.

## <a name="search-within-the-analytics-pane"></a>Søg i ruden Analytics

Fra og med udgivelsen af Power BI Desktop i februar 2018 (version 2.55.5010.201 eller nyere) kan du søge i ruden **Analytics**, hvilket er et underafsnit af ruden **Visualiseringer**. Søgefeltet vises, når du vælger ikonet **Analytics**.

![Søgefelt, ruden Analytics, Visualiseringer, Power BI Desktop](media/desktop-analytics-pane/analytics-pane_1b.png)

## <a name="use-the-analytics-pane"></a>Brug ruden Analytics

Med ruden **Analytics** kan du oprette følgende typer dynamiske referencelinjer:

* Konstantlinje for X-akse
* Konstantlinje for Y-akse
* Minimumlinje
* Maksimumlinje
* Gennemsnitslinje
* Medianlinje
* Fraktillinje
* Symmetriskygge

> [!NOTE]
> Ikke alle linjer er tilgængelige for alle visualiseringstyper.

Følgende afsnit viser, hvordan du kan bruge ruden **Analytics** og dynamiske referencelinjer i dine visuelle effekter.

Få vist de tilgængelige dynamiske referencelinjer for en visuel effekt ved at følge disse trin:

1. Vælg eller opret en visuel effekt, og vælg derefter ikonet **Analytics** i ruden **Visualiseringer**.

    ![Vis Analytics for en visualisering, ruden Visualiseringer, Power BI Desktop](media/desktop-analytics-pane/analytics-pane_2.png)

2. Vælg den linjetype, du vil oprette, for at udvide dens indstillinger. I dette tilfælde vælger vi **Gennemsnitslinje**.

    ![Gennemsnitslinje, ruden Analytics, Visualiseringer, Power BI Desktop](media/desktop-analytics-pane/analytics-pane_3.png)

3. Vælg **+&nbsp;Tilføj** for at oprette en ny linje. Du kan derefter navngive linjen. Dobbeltklik på tekstfeltet, og angiv dit navn.

    Nu har du alle mulige forskellige muligheder for din linje. Du kan angive dens **farve**, procentdel for **gennemsigtighed**, **stregtype** og **placering** (sammenlignet med visualiseringens dataelementer). Du kan også vælge, om du vil medtage **datamærkatet**. Hvis du vil angive den visuelle måling, som linjen skal baseres på, skal du vælge rullelisten **Mål**, der automatisk udfyldes med dataelementer fra visualiseringen. I dette tilfælde vælger vi **Culture** som målingen, mærker den *Average of Culture* og tilpasser nogle af de andre indstillinger, som vist nedenfor.

    ![Gennemsnitslinje for kultur, ruden Analytics, Visualiseringer, Power BI Desktop](media/desktop-analytics-pane/analytics-pane_4.png)

4. Hvis du vil have vist et datamærkat, skal du slå skyderen **Datamærkat** fra **Fra** til **Til**. Når du gør dette, får du mange yderligere indstillinger for dit datamærkat.

    ![Indstillinger for datamærkat, ruden Analytics, Visualiseringer, Power BI Desktop](media/desktop-analytics-pane/analytics-pane_5.png)

5. Bemærk tallet, der vises ved siden af elementet **Gennemsnitslinje** i ruden **Analytics**. Det fortæller dig, hvor mange dynamiske linjer du på nuværende tidspunkt har på dine visuelle effekter og hvilken type. Hvis vi tilføjer en **Maksimumlinje** for **Affordability**, kan du se, at ruden **Analytics** viser, at vi nu også anvender en **Maksimumlinje** som dynamisk referencelinje for visualiseringen.

    ![Maks og totaler for gennemsnitslinje, ruden Analytics, Visualiseringer, Power BI Desktop](media/desktop-analytics-pane/analytics-pane_6.png)

Hvis der ikke kan anvendes dynamiske linjer for den valgte visualisering (i dette tilfælde visualiseringen **Kort**), får du vist følgende, når du vælger ruden **Analytics**.

![Ikke-tilgængelig analytics for en kortvisualisering, ruden Analytics, Visualiseringer, Power BI Desktop](media/desktop-analytics-pane/analytics-pane_7.png)

Der er mange typer interessant viden, du kan fremhæve ved at oprette dynamiske referencelinjer med ruden **Analytics**.

Vi planlægger flere funktioner og egenskaber herunder at udvide, hvilke visualiseringer dynamiske referencelinjer kan anvendes til. Vend tilbage ofte for at se nyheder.

## <a name="apply-forecasting"></a>Anvend Prognoser

Hvis du har klokkeslætsdata i datakilden, kan du bruge funktionen *Prognoser*. Du skal bare vælge en visualisering og derefter udvide afsnittet **Prognoser** i ruden **Analytics**. Du kan angive mange input for at redigere prognosen, f.eks. **Budgetteret længde** eller **Tillidsinterval**. På følgende billede vises en visualisering med basisstreger, hvor prognosen er anvendt. Brug din fantasi (og leg med prognoser) for at se, hvordan funktionen kan bruges til dine modeller.

![Funktionen Prognoser, ruden Analytics, Visualiseringer, Power BI Desktop](media/desktop-analytics-pane/analytics-pane_8.png)

> [!NOTE]
> Funktionen til prognoser er kun tilgængelig for linjediagrammer.

## <a name="limitations"></a>Begrænsninger

Muligheden for at bruge dynamiske referencelinjer er baseret på typen af visuel effekt, der bruges. På følgende liste beskrives disse begrænsninger mere udførligt.

Du kan bruge *x-aksens konstantlinje*, *y-aksens konstantlinje* og *symmetriskygge* på følgende visualisering:

* Punktdiagram

Brug af *konstantlinje*, *minimumlinje*, *maksimumlinje*, *gennemsnitlig linje*, *medianlinje* og *fraktillinje* er tilgængelig for disse visualiseringer:

* Områdediagram
* Grupperet liggende søjlediagram
* Grupperet søjlediagram
* Kurvediagram
* Punktdiagram

Følgende visuelle effekter kan kun bruge en *konstantlinje* fra ruden **Analytics**:

* Stablet områdediagram
* Stablet liggende søjlediagram
* Stablet søjlediagram
* Vandfaldsdiagram
* 100 % stablet liggende søjlediagram
* 100 % stablet søjlediagram

Følgende visualiseringer kan bruge en *tendenslinje*, hvis der er tidsdata:

* Områdediagram
* Grupperet søjlediagram
* Kurvediagram
* Kurvediagram og grupperet søjlediagram

Du kan i øjeblikket ikke anvende dynamiske linjer til mange visualiseringer, herunder (men ikke begrænset til):

* Tragt
* Kurvediagram og grupperet søjlediagram
* Kurvediagram og stablet søjlediagram
* Bånddiagram
* Ikke-kartesianske visuelle elementer, f.eks. kransediagram, måler, matrix, cirkeldiagram og tabel

*Percentillinjen* er kun tilgængelig, når importerede data bruges i Power BI Desktop, eller når der oprettes en direkte forbindelse til en model på en server, der kører **Analysis Service 2016** eller nyere, **Azure Analysis Services** eller et datasæt i Power BI-tjenesten.

## <a name="next-steps"></a>De næste trin

Du kan gøre mange forskellige ting med Power BI Desktop. Du kan finde flere oplysninger om funktionerne i følgende ressourcer:

* [Nyheder i Power BI Desktop](../fundamentals/desktop-latest-update.md)
* [Hent Power BI Desktop](../fundamentals/desktop-get-the-desktop.md)
* [Hvad er Power BI Desktop?](../fundamentals/desktop-what-is-desktop.md)
* [Oversigt over forespørgsler i Power BI Desktop](desktop-query-overview.md)
* [Datatyper i Power BI Desktop](../connect-data/desktop-data-types.md)
* [Udform og kombiner data med Power BI Desktop](../connect-data/desktop-shape-and-combine-data.md)
* [Udfør almindelige forespørgselsopgaver i Power BI Desktop](desktop-common-query-tasks.md)
